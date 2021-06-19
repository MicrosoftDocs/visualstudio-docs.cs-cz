---
title: Příkaz upravit standardní nabídku v DSL
description: Zjistěte, jak můžete upravit chování některých standardních příkazů, které jsou definovány automaticky v DSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ccbc82801c3570c74e96010d5f9fc0e0e7940937
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387096"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Postupy: Úprava příkazu standardní nabídky v jazyce specifickém pro doménu

Můžete upravit chování některých standardních příkazů, které jsou definovány automaticky v DSL. Můžete například upravit možnost **Vyjmout** tak, aby vyloučila citlivé informace. Chcete-li to provést, přepište metody ve třídě sady příkazů. Tyto třídy jsou definovány v souboru CommandSet.cs v projektu DslPackage a jsou odvozeny z <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> .

> [!NOTE]
> Pokud chcete vytvořit vlastní příkazy nabídky, podívejte se na [postupy: Přidání příkazu](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)do místní nabídky .

## <a name="what-commands-can-you-modify"></a>Jaké příkazy můžete upravit?

### <a name="to-discover-what-commands-you-can-modify"></a>Zjištění příkazů, které můžete upravit

1. V `DslPackage` projektu otevřete `GeneratedCode\CommandSet.cs` . Tento soubor C# najdete v Průzkumník řešení jako pobočka `CommandSet.tt` .

2. Vyhledejte v tomto souboru třídy, jejichž názvy končí na `CommandSet` " ", například a `Language1CommandSet` `Language1ClipboardCommandSet` .

3. V každé třídě command set zadejte `override` " " následovaný mezerou. IntelliSense zobrazí seznam metod, které můžete přepsat. Každý příkaz má dvojici metod, jejichž názvy začínají " " a `ProcessOnStatus` " `ProcessOnMenu` ".

4. Všimněte si, které třídy sady příkazů obsahují příkaz, který chcete upravit.

5. Zavřete soubor bez uložení úprav.

    > [!NOTE]
    > Obvykle byste neměli upravovat soubory, které byly vygenerovány. Při příštím vygenerování souborů se všechny úpravy ztratí.

## <a name="extend-the-appropriate-command-set-class"></a>Rozšíření příslušné třídy sady příkazů

Vytvořte nový soubor, který obsahuje částečnou deklaraci třídy command set.

### <a name="to-extend-the-command-set-class"></a>Rozšíření třídy Command Set

1. V Průzkumník řešení projektu DslPackage otevřete složku GeneratedCode, vyhledejte soubor CommandSet.tt a otevřete jeho vygenerovaný soubor CommandSet.cs. Poznamenejte si obor názvů a název první třídy, která je zde definována. Můžete například vidět:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. V **DslPackage** vytvořte složku s názvem **Vlastní kód**. V této složce vytvořte nový soubor třídy s názvem `CommandSet.cs` .

3. V novém souboru zapište částečnou deklaraci, která má stejný obor názvů a název jako vygenerovaná částečná třída. Příklad:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

    > [!NOTE]
    > Pokud jste k vytvoření nového souboru použili šablonu souboru třídy, musíte opravit obor názvů i název třídy.

## <a name="override-the-command-methods"></a>Přepsání metod příkazů

Většina příkazů má dvě přidružené metody: metodu s názvem jako `ProcessOnStatus` ... určuje, jestli má být příkaz viditelný a povolený. Volá se pokaždé, když uživatel klikne pravým tlačítkem na diagram a měl by se rychle spustit a provádět žádné změny. `ProcessOnMenu`... se volá, když uživatel klikne na příkaz a měl by provést funkci příkazu . Můžete chtít přepsat jednu nebo obě tyto metody.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Změna, když se příkaz zobrazí v nabídce

Přepsat ProcessOnStatus... Metoda. Tato metoda by měla nastavit vlastnosti Visible a Enabled svého parametru MenuCommand. Obvykle se na to podívá příkaz . CurrentSelection určuje, zda se příkaz vztahuje na vybrané prvky, a může se také podívat na jejich vlastnosti a určit, zda lze příkaz použít v jejich aktuálním stavu.

Obecně platí, že vlastnost Visible by měla být určena vybranými prvky. Vlastnost Enabled (Povoleno), která určuje, jestli se příkaz v nabídce zobrazuje černě nebo šedě, by měla záviset na aktuálním stavu výběru.

Následující příklad zakáže položku nabídky Odstranit, pokud uživatel vybral více než jeden tvar.

> [!NOTE]
> Tato metoda nemá vliv na to, jestli je příkaz dostupný prostřednictvím stisknutí klávesy. Například zakázáním položky nabídky Odstranit nezabráníte vyvolání příkazu prostřednictvím klíče Delete.

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

Osvědčeným postupem je nejprve volat základní metodu , abyste se vypořádat se všemi případy a nastaveními, kterým se netýče.

Metoda ProcessOnStatus by neměla vytvářet, odstraňovat ani aktualizovat prvky ve Storu.

### <a name="to-change-the-behavior-of-the-command"></a>Změna chování příkazu

Přepsat ProcessOnMenu... Metoda. Následující příklad zabrání uživateli v odstranění více než jednoho prvku najednou, a to i pomocí klíče Delete.

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

Pokud váš kód provede změny ve Storu, jako je vytváření, odstraňování nebo aktualizace prvků nebo odkazů, musíte to udělat uvnitř transakce. Další informace najdete v tématu [Vytvoření a aktualizace prvků modelu.](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)

### <a name="write-the-code-of-the-methods"></a>Napsání kódu metod

V těchto metodách jsou často užitečné následující fragmenty:

- `this.CurrentSelection`. Tvar, na který uživatel klikl pravým tlačítkem, je vždy součástí tohoto seznamu tvarů a konektorů. Pokud uživatel klikne na prázdnou část diagramu, diagram je jediným členem seznamu.

- `this.IsDiagramSelected()` - `true` , pokud uživatel klikl na prázdnou část diagramu.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` – uživatel nevyberl více obrazců

- `this.SingleSelection` – tvar nebo diagram, na který uživatel klikl pravým tlačítkem

- `shape.ModelElement as MyLanguageElement` – prvek modelu reprezentovaný tvarem.

Další informace o tom, jak přejít z elementu na element a jak vytvářet objekty a odkazy, najdete v tématu Navigace a aktualizace [modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.Design.MenuCommand>
- [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Postupy: Přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [XML schéma VSCT – referenční informace](../extensibility/vsct-xml-schema-reference.md)
- [VMSDK – ukázka diagramů okruhu Rozsáhlé přizpůsobení DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
