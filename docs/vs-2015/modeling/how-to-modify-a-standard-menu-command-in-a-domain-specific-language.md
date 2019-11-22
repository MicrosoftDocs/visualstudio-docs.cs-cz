---
title: 'Postupy: Úprava příkazu standardní nabídky v jazyce specifickém pro doménu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
ms.assetid: 9b9d8314-d0d8-421a-acb9-d7e91e69825c
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 989367d395abb56e4f57c4aa2694b5f4ef17fb6e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300874"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Postupy: Úprava příkazu standardní nabídky v jazyce specifickém pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete upravit chování některých standardních příkazů, které jsou v DSL definovány automaticky. Můžete například upravit **Vyjmout** , aby vyloučil citlivé informace. Chcete-li to provést, přepište metody ve třídě sady příkazů. Tyto třídy jsou definovány v souboru CommandSet.cs v projektu DslPackage a jsou odvozeny z <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

 V souhrnu pro úpravu příkazu:

1. [Zjistěte, jaké příkazy můžete upravit](#what).

2. [Vytvořte částečnou deklaraci příslušné třídy sady příkazů](#extend).

3. [Přepište metody ProcessOnStatus a ProcessOnMenu](#override) pro příkaz.

   Toto téma vysvětluje tento postup.

> [!NOTE]
> Chcete-li vytvořit vlastní příkazy nabídky, přečtěte si téma [Postupy: Přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what"></a>Které příkazy můžete upravit?

#### <a name="to-discover-what-commands-you-can-modify"></a>Zjištění příkazů, které lze upravit

1. V projektu `DslPackage` otevřete `GeneratedCode\CommandSet.cs`. Tento C# soubor najdete v Průzkumník řešení jako dceřinou společnost `CommandSet.tt`.

2. Najde v tomto souboru třídy, jejichž názvy končí řetězcem "`CommandSet`", například `Language1CommandSet` a `Language1ClipboardCommandSet`.

3. Do každé třídy sady příkazů zadejte "`override`" následovaný mezerou. IntelliSense zobrazí seznam metod, které lze přepsat. Každý příkaz má dvojici metod, jejichž názvy začínají na "`ProcessOnStatus`" a "`ProcessOnMenu`".

4. Všimněte si, že třídy sady příkazů obsahují příkaz, který chcete upravit.

5. Zavřete soubor bez uložení úprav.

    > [!NOTE]
    > Obvykle byste neměli upravovat soubory, které byly vygenerovány. Při příštím generování souborů dojde ke ztrátě všech úprav.

## <a name="extend"></a>Rozšíříte příslušnou třídu sady příkazů.
 Vytvořte nový soubor, který obsahuje částečnou deklaraci třídy sady příkazů.

#### <a name="to-extend-the-command-set-class"></a>Postup při rozšiřování třídy sady příkazů

1. V Průzkumník řešení v projektu DslPackage otevřete složku GeneratedCode a potom se podívejte do části CommandSet.tt a otevřete její vygenerovaný soubor CommandSet.cs. Poznamenejte si obor názvů a název první třídy, která je zde definována. Může se například zobrazit:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. V **DslPackage**vytvořte složku s názvem **vlastní kód**. V této složce vytvořte nový soubor třídy s názvem `CommandSet.cs`.

3. V novém souboru zapište částečnou deklaraci, která má stejný obor názvů a název jako vygenerovaná částečná třída. Příklad:

    ```
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

     **Poznámka:** Pokud jste použili šablonu souboru třídy k vytvoření nového souboru, je nutné opravit obor názvů i název třídy.

## <a name="override"></a>Přepsat metody příkazu
 Většina příkazů má dvě přidružené metody: metoda s názvem, jako `ProcessOnStatus`... Určuje, zda má být příkaz viditelný a povolený. Je volána vždy, když uživatel klikne pravým tlačítkem myši na diagram a měl by být proveden rychle a neprovádí se žádné změny. `ProcessOnMenu`... se volá, když uživatel klikne na příkaz a měla by provádět funkci příkazu. Je možné, že budete chtít přepsat jednu nebo obě z těchto metod.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Změna při zobrazení příkazu v nabídce
 Přepsat ProcessOnStatus... Metoda. Tato metoda by měla nastavovat vlastnosti Visible a Enabled parametru MenuCommand. Tento příkaz obvykle prohlíží. CurrentSelection určete, zda se příkaz vztahuje na vybrané prvky, a může také prohledat jejich vlastnosti a určit, zda lze příkaz použít v jejich aktuálním stavu.

 V rámci obecného průvodce by vlastnost Visible měla být určena podle toho, jaké prvky jsou vybrány. Vlastnost Enabled, která určuje, zda se příkaz v nabídce zobrazí černě nebo šedě, by měl záviset na aktuálním stavu výběru.

 Následující příklad zakáže položku nabídky odstranit, když uživatel vybere více než jeden tvar.

> [!NOTE]
> Tato metoda nemá vliv na to, zda je příkaz k dispozici prostřednictvím klávesových zkratek. Například zakázání položky nabídky odstranit nebrání vyvolání příkazu pomocí klávesy DELETE.

```
/// <summary>
/// Called when user right-clicks on the diagram or clicks the Edit menu.
/// </summary>
/// <param name="command">Set Visible and Enabled properties.</param>
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)
{
  // Default settings from the base method.
  base.ProcessOnStatusDeleteCommand(command);
  if (this.CurrentSelection.Count > 1)
  {
    // If user has selected more than one item, Delete is greyed out.
    command.Enabled = false;
  }
}
```

 Je vhodné nejdřív volat základní metodu a řešit všechny případy a nastavení, se kterými se nejste zvyklí.

 Metoda ProcessOnStatus by neměla vytvářet, odstraňovat ani aktualizovat prvky v úložišti.

### <a name="to-change-the-behavior-of-the-command"></a>Změna chování příkazu
 Přepsat ProcessOnMenu... Metoda. Následující příklad brání uživateli v odstranění více než jednoho prvku v čase, a to i pomocí klíče DELETE.

```
/// <summary>
/// Called when user presses Delete key
/// or clicks the Delete command on a menu.
/// </summary>
protected override void ProcessOnMenuDeleteCommand()
{
  // Allow users to delete only one thing at a time.
  if (this.CurrentSelection.Count <= 1)
  {
    base.ProcessOnMenuDeleteCommand();
  }
}
```

 Pokud váš kód provede změny v úložišti, jako je například vytváření, odstraňování nebo aktualizace elementů nebo propojení, je nutné provést v rámci transakce. Další informace naleznete v tématu [jak vytvořit a aktualizovat prvky modelu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="writing-the-code-of-the-methods"></a>Zápis kódu metod
 Následující fragmenty jsou často užitečné v rámci těchto metod:

- `this.CurrentSelection`. Tvar, na který uživatel klikne pravým tlačítkem, je vždy zahrnut v tomto seznamu obrazců a konektorů. Pokud uživatel klikne na prázdnou část diagramu, diagram je jediným členem tohoto seznamu.

- `this.IsDiagramSelected()` - `true`, pokud uživatel klikl na prázdnou část diagramu.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` – uživatel nevybrali více obrazců.

- `this.SingleSelection` – tvar nebo diagram, na který uživatel klikne pravým tlačítkem myši

- `shape.ModelElement as MyLanguageElement` – prvek modelu reprezentovaný tvarem.

  Další informace o tom, jak přejít z prvku na prvek a o tom, jak vytvořit objekty a odkazy, naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Viz také
 <xref:System.ComponentModel.Design.MenuCommand> [psaní kódu pro přizpůsobení jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md) [Postupy: Přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md) [Návod: získání informací z vybraného odkazu](../misc/walkthrough-getting-information-from-a-selected-link.md) [Jak sady VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md) [příkazová tabulka sady Visual Studio (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [vsct XML Schema Reference](../extensibility/vsct-xml-schema-reference.md)
