---
title: Příkaz Upravit standardní nabídku v DSL
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ae2aa04eb415ee5c4b7aaa41ea4c6abb49333f7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605254"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Postupy: Úprava příkazu standardní nabídky v jazyce specifickém pro doménu

Můžete upravit chování některých standardních příkazů, které jsou v DSL definovány automaticky. Můžete například upravit **Vyjmout** , aby vyloučil citlivé informace. Chcete-li to provést, přepište metody ve třídě sady příkazů. Tyto třídy jsou definovány v souboru CommandSet.cs v projektu DslPackage a jsou odvozeny z <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

> [!NOTE]
> Chcete-li vytvořit vlastní příkazy nabídky, přečtěte si téma [Postupy: Přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what-commands-can-you-modify"></a>Které příkazy můžete upravit?

### <a name="to-discover-what-commands-you-can-modify"></a>Zjištění příkazů, které lze upravit

1. V projektu `DslPackage` otevřete `GeneratedCode\CommandSet.cs`. Tento C# soubor najdete v Průzkumník řešení jako dceřinou společnost `CommandSet.tt`.

2. Najde v tomto souboru třídy, jejichž názvy končí řetězcem "`CommandSet`", například `Language1CommandSet` a `Language1ClipboardCommandSet`.

3. Do každé třídy sady příkazů zadejte "`override`" následovaný mezerou. IntelliSense zobrazí seznam metod, které lze přepsat. Každý příkaz má dvojici metod, jejichž názvy začínají na "`ProcessOnStatus`" a "`ProcessOnMenu`".

4. Všimněte si, že třídy sady příkazů obsahují příkaz, který chcete upravit.

5. Zavřete soubor bez uložení úprav.

    > [!NOTE]
    > Obvykle byste neměli upravovat soubory, které byly vygenerovány. Při příštím generování souborů dojde ke ztrátě všech úprav.

## <a name="extend-the-appropriate-command-set-class"></a>Rozšíříte příslušnou třídu sady příkazů.

Vytvořte nový soubor, který obsahuje částečnou deklaraci třídy sady příkazů.

### <a name="to-extend-the-command-set-class"></a>Postup při rozšiřování třídy sady příkazů

1. V Průzkumník řešení v projektu DslPackage otevřete složku GeneratedCode a potom se podívejte do části CommandSet.tt a otevřete její vygenerovaný soubor CommandSet.cs. Poznamenejte si obor názvů a název první třídy, která je zde definována. Může se například zobrazit:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. V **DslPackage**vytvořte složku s názvem **vlastní kód**. V této složce vytvořte nový soubor třídy s názvem `CommandSet.cs`.

3. V novém souboru zapište částečnou deklaraci, která má stejný obor názvů a název jako vygenerovaná částečná třída. Příklad:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

    > [!NOTE]
    > Pokud jste použili šablonu souboru třídy k vytvoření nového souboru, je nutné opravit obor názvů i název třídy.

## <a name="override-the-command-methods"></a>Přepsat metody příkazu

Většina příkazů má dvě přidružené metody: metoda s názvem, jako `ProcessOnStatus`... Určuje, zda má být příkaz viditelný a povolený. Je volána vždy, když uživatel klikne pravým tlačítkem myši na diagram a měl by být proveden rychle a neprovádí se žádné změny. `ProcessOnMenu`... se volá, když uživatel klikne na příkaz a měla by provádět funkci příkazu. Je možné, že budete chtít přepsat jednu nebo obě z těchto metod.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Změna při zobrazení příkazu v nabídce

Přepsat ProcessOnStatus... Metoda. Tato metoda by měla nastavovat vlastnosti Visible a Enabled parametru MenuCommand. Tento příkaz obvykle prohlíží. CurrentSelection určete, zda se příkaz vztahuje na vybrané prvky, a může také prohledat jejich vlastnosti a určit, zda lze příkaz použít v jejich aktuálním stavu.

V rámci obecného průvodce by vlastnost Visible měla být určena podle toho, jaké prvky jsou vybrány. Vlastnost Enabled, která určuje, zda se příkaz v nabídce zobrazí černě nebo šedě, by měl záviset na aktuálním stavu výběru.

Následující příklad zakáže položku nabídky odstranit, když uživatel vybere více než jeden tvar.

> [!NOTE]
> Tato metoda nemá vliv na to, zda je příkaz k dispozici prostřednictvím klávesových zkratek. Například zakázání položky nabídky odstranit nebrání vyvolání příkazu pomocí klávesy DELETE.

```csharp
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

```csharp
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

### <a name="write-the-code-of-the-methods"></a>Zapsat kód metod

Následující fragmenty jsou často užitečné v rámci těchto metod:

- `this.CurrentSelection`. Tvar, na který uživatel klikne pravým tlačítkem, je vždy zahrnut v tomto seznamu obrazců a konektorů. Pokud uživatel klikne na prázdnou část diagramu, diagram je jediným členem tohoto seznamu.

- `this.IsDiagramSelected()`  -  `true`, pokud uživatel klikl na prázdnou část diagramu.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` – uživatel nevybrali více obrazců.

- `this.SingleSelection` – tvar nebo diagram, na který uživatel klikne pravým tlačítkem myši

- `shape.ModelElement as MyLanguageElement` – prvek modelu reprezentovaný tvarem.

Další informace o tom, jak přejít z prvku na prvek a o tom, jak vytvořit objekty a odkazy, naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.Design.MenuCommand>
- [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Postupy: Přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [XML schéma VSCT – referenční informace](../extensibility/vsct-xml-schema-reference.md)
- [Ukázka diagramů VMSDK-okruhů. Rozsáhlé přizpůsobení DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
