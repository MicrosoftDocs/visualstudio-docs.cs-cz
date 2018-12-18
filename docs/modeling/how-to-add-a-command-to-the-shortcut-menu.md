---
title: 'Postupy: Přidání příkazu do místní nabídky'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6cfbe7c83db57bbeb24089e7d3e794caaeca9d81
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967412"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Postupy: Přidání příkazu do místní nabídky
Příkazy nabídky můžete přidat do vašeho jazyka specifického pro doménu (DSL), tak, aby vaši uživatelé můžou provádět úlohy, které se týkají vašeho DSL. Příkazy se zobrazují v nabídce kontextu (místní), po kliknutí pravým tlačítkem myši v diagramu. Příkaz můžete definovat tak, aby se zobrazí jenom v nabídce za určitých okolností. Například můžete provést příkaz viditelné pouze v případě, že uživatel klikne na určité typy prvek nebo prvky v konkrétní stavy.

 Stručně řečeno kroky probíhají v projektu DslPackage následujícím způsobem:

1. [Příkaz v Commands.vsct deklarovat](#VSCT)

2. [Aktualizovat číslo verze balíčku v Package.tt](#version). Budete muset udělat při každé změně Commands.vsct

3. [Zápis metod ve třídě CommandSet](#CommandSet) zviditelnit příkazu a definovat, co chcete provést příkaz.

   Ukázky najdete v tématu [Visualization and Modeling SDK webu](http://go.microsoft.com/fwlink/?LinkID=185579).

> [!NOTE]
>  Můžete také upravit chování některé existující příkazy, jako je vyjmutí, vložení, Vybrat vše a tisk přepsáním metody v CommandSet.cs. Další informace najdete v tématu [postupy: úprava příkazu standardní nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="defining-a-command-using-mef"></a>Definování příkazu pomocí MEF
 Spravované rozšíření Framework (MEF) obsahuje alternativní metodu pro definování příkazy nabídky v nabídce diagramu. Jeho primárním účelem je umožnit DSL prodloužit vámi nebo jiné smluvní strany. Uživatele můžete nainstalovat jenom DSL nebo nainstalovat DSL a rozšíření. MEF, ale také snižuje práci po počáteční pracovní umožňující MEF v DSL definující příkazy místní nabídky.

 V tomto tématu použijte metodu, pokud:

1. Můžete definovat příkazy v nabídkách než místní nabídce klikněte pravým tlačítkem.

2. Můžete definovat konkrétní seskupení příkazů v nabídce.

3. Nechcete povolit ostatním uživatelům rozšíření DSL, své vlastní příkazy.

4. Chcete definovat jeden příkaz.

   V opačném případě zvažte použití metody rozhraní MEF pro definovat příkazy. Další informace najdete v tématu [rozšíření vašeho DSL pomocí MEF](../modeling/extend-your-dsl-by-using-mef.md).

##  <a name="VSCT"></a> Příkaz v Commands.Vsct deklarovat
 Příkazy nabídky jsou deklarovány v DslPackage\Commands.vsct. Tyto definice zadejte popisky, které položky nabídky a kde jsou uvedeny v nabídkách.

 Soubor, který upravíte, Commands.vsct, importuje definice z několika .h souborů, které jsou umístěné v adresáři *cesta pro instalaci sady Visual Studio SDK*\VisualStudioIntegration\Common\Inc. Zahrnuje také GeneratedVsct.vsct, který je generován z definice DSL.

 Další informace o souborech .vsct najdete v tématu [tabulky příkazů aplikace Visual Studio (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

#### <a name="to-add-the-command"></a>Chcete-li přidat příkaz

1.  V **Průzkumníka řešení**v části **DslPackage** projektu, otevřete Commands.vsct.

2.  V `Commands` elementu, definujte jedno nebo více tlačítek a skupinu. A *tlačítko* je položku v nabídce. A *skupiny* oddíl v nabídce. Pokud chcete definovat tyto položky, přidejte následující prvky:

    ```xml
    <!-- Define a group - a section in the menu -->
    <Groups>
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">
        <!-- These symbols are defined in GeneratedVSCT.vsct -->
        <Parent guid="guidCmdSet" id="menuidContext" />
      </Group>
    </Groups>
    <!-- Define a button - a menu item - inside the Group -->
    <Buttons>
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        priority="0x0100" type="Button">
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>
        <!-- If you do not want to place the command in your own Group,
             use Parent guid="guidCmdSet" id="grpidContextMain".
             These symbols are defined in GeneratedVSCT.vsct -->
        <CommandFlag>DynamicVisibility</CommandFlag>
        <Strings>
          <ButtonText>My Context Menu Command</ButtonText>
        </Strings>
      </Button>
    </Buttons>
    ```

    > [!NOTE]
    >  Každé tlačítko nebo skupiny je určený identifikátor GUID a identifikátor celé číslo. Můžete vytvořit několik skupin a tlačítka se stejným GUID. Musí však mít různé identifikátory. Názvy GUID a ID názvy jsou přeloženy na skutečné identifikátory GUID a číselné ID v `<Symbols>` uzlu.

3.  Přidáte omezení viditelnosti pro příkaz tak, aby se načetl pouze v rámci jazyka specifického pro doménu. Další informace najdete v tématu [visibilityconstraints – Element](../extensibility/visibilityconstraints-element.md).

     Chcete-li to provést, přidejte následující prvky v `CommandTable` elementu po `Commands` elementu.

    ```xml
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4.  Definujte názvy, které jste použili pro identifikátory GUID a ID. Chcete-li to provést, přidejte `Symbols` element v `CommandTable` elementu po `Commands` elementu.

    ```xml
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5.  Nahraďte `{000...000}` s identifikátorem GUID, který identifikuje skupiny a položkami nabídky. Chcete-li získat nový identifikátor GUID, použijte **Create GUID** nástroj **nástroje** nabídky.

    > [!NOTE]
    >  Pokud chcete přidat další skupiny nebo položky nabídky, můžete použít stejný identifikátor GUID. Ale musíte použít nové hodnoty `IDSymbols`.

6.  V kódu, který jste zkopírovali z tohoto postupu nahraďte každý výskyt následující řetězce s vlastními řetězci:

    -   `grpidMyMenuGroup`

    -   `cmdidMyContextMenuCommand`

    -   `guidCustomMenuCmdSet`

    -   `My Context Menu Command`

##  <a name="version"></a> Aktualizace verze balíčku v Package.tt
 Kdykoli přidat nebo změnit příkazu, aktualizujte `version` parametr <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> , která je použita na třídě balíčku ještě před vydáním nové verze jazyka specifického pro doménu.

 Protože třída balíčku je definováno ve vytvořeném souboru, aktualizujte atribut v souboru textové šablony, který generuje soubor Package.cs.

#### <a name="to-update-the-packagett-file"></a>K aktualizaci souboru Package.tt

1.  V **Průzkumníka řešení**v **DslPackage** v projektu **GeneratedCode** složku, otevřete soubor Package.tt.

2.  Vyhledejte `ProvideMenuResource` atribut.

3.  Přírůstek `version` parametr atributu, což je druhý parametr. Pokud chcete, můžete napsat název parametru explicitně na vás upozorní na její účel. Příklad:

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

##  <a name="CommandSet"></a> Definuje chování příkazu
 Některé příkazy, které jsou implementovány v dílčí třídě, která je deklarována v DslPackage\GeneratedCode\CommandSet.cs již vašeho DSL. Přidání nových příkazů, musí tato třída rozšířit tak, že vytvoříte nový soubor, který obsahuje deklaraci částečné stejné třídy. Název třídy je obvykle  *\<YourDslName >*`CommandSet`. To je užitečné začněte tím, že název třídy ověření a zkontrolujete jeho obsah.

 Třída set příkazu je odvozen z <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

#### <a name="to-extend-the-commandset-class"></a>Rozšíření třídy CommandSet

1.  V Průzkumníku řešení v projektu DslPackage otevřete složku GeneratedCode a podívejte se do části CommandSet.tt a otevřete její vygenerovaný soubor CommandSet.cs. Poznámka: obor názvů a název první třídy, která je definována existuje. Například může se zobrazit:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2.  V **DslPackage**, vytvořte složku s názvem **vlastní kód**. V této složce, vytvořte nový soubor třídy s názvem `CommandSet.cs`.

3.  V novém souboru zápisu částečná deklarace, který má stejný obor názvů a název jako vygenerovanou dílčí třídu. Příklad:

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     **Poznámka:** Pokud jste použili k vytvoření nového souboru šablony třídy, je nutné opravit obor názvů a název třídy.

### <a name="extend-the-command-set-class"></a>Rozšíření třídy sady příkazů
 Příkaz set kódu obvykle muset importujte následující obory názvů:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

 Nastavte obor názvů a název třídy tak, aby odpovídala těm v generované CommandSet.cs:

```csharp
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

 Musíte definovat dvě metody, jednu pro určení, kdy bude příkaz viditelný na místní nabídku a druhým k provedení příkazu. Tyto metody nejsou přepsání; Místo toho je zaregistrujete v seznamu příkazů.

### <a name="define-when-the-command-will-be-visible"></a>Definujte, kdy bude příkaz viditelný
 Pro každý příkaz definovat `OnStatus...` metodu, která určuje, zda příkaz zobrazí v nabídce, a určuje, zda bude povoleno nebo šedá. Nastavte `Visible` a `Enabled` vlastnosti `MenuCommand`, jak je znázorněno v následujícím příkladu. Tato metoda je volána, aby bylo možné vytvořit nabídku pokaždé, když uživatel klepne pravým tlačítkem myši diagram, musí pracovat rychle.

 V tomto příkladu je příkaz viditelný pouze v případě, že uživatel vybral konkrétní typ tvar a je povoleno pouze v případě alespoň jeden z vybraných elementů v určitém stavu. V příkladu je založen na šabloně DSL diagramu třídy a typy, které jsou definovány v DSL jsou ClassShape a ModelClass:

```csharp
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  command.Visible = command.Enabled = false;
  foreach (object selectedObject in this.CurrentSelection)
  {
    ClassShape shape = selectedObject as ClassShape;
    if (shape != null)
    {
      // Visibility depends on what is selected.
      command.Visible = true;
      ModelClass element = shape.ModelElement as ModelClass;
      // Enabled depends on state of selection.
      if (element != null && element.Comments.Count == 0)
      {
        command.Enabled = true;
        return; // seen enough
} } } }
```

 Následující fragmenty jsou často užitečné při OnStatus metody:

- `this.CurrentSelection`. Obrazec, který klikli pravým tlačítkem myši uživatele je vždy součástí tohoto seznamu. Pokud uživatel klikne na prázdnou část diagramu, diagramu je jediným členem seznamu.

- `this.IsDiagramSelected()` - `true` Pokud uživatel klikne na prázdnou část diagramu.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` -uživatel nevybrali více objektů

- `this.SingleSelection` – vybraný tvar nebo diagram, který klikli pravým tlačítkem myši uživatele

- `shape.ModelElement as MyLanguageElement` -prvku modelu reprezentovány ve tvaru.

  Ujistěte se, v rámci obecných pokynů, `Visible` vlastnost závisí na vybrané a ujistěte se, `Enabled` vlastnosti závisí na stavu vybraných elementů.

  Metodu OnStatus nesmí změnit stav Store.

### <a name="define-what-the-command-does"></a>Definujte, co dělá příkaz
 Pro každý příkaz definovat `OnMenu...` metodu, která provádí požadované akce, když uživatel klepne na příkaz nabídky.

 Pokud provedete změny k prvkům modelu, musíte tak učinit v transakci. Další informace najdete v tématu [postupy: úprava příkazu standardní nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 V tomto příkladu `ClassShape`, `ModelClass`, a `Comment` jsou typy, které jsou definovány v DSL, která je odvozena z třídy Diagram DSL šablony.

```csharp
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  Store store = this.CurrentDocData.Store;
  // Changes to elements and shapes must be performed in a Transaction.
  using (Transaction transaction =
       store.TransactionManager.BeginTransaction("My command"))
  {
    foreach (object selectedObject in this.CurrentSelection)
    {
      // ClassShape is defined in my DSL.
      ClassShape shape = selectedObject as ClassShape;
      if (shape != null)
      {
        // ModelClass is defined in my DSL.
        ModelClass element = shape.ModelElement as ModelClass;
        if (element != null)
        {
          // Do required action here - for example:

          // Create a new element. Comment is defined in my DSL.
          Comment newComment = new Comment(element.Partition);
          // Every element must be the target of an embedding link.
          element.ModelRoot.Comments.Add(newComment);
          // Set properties of new element.
          newComment.Text = "This is a comment";
          // Create a reference link to existing object.
          element.Comments.Add(newComment);
        }
      }
    }
    transaction.Commit(); // Don't forget this!
  }
}
```

 Další informace o tom, jak přejít z objektu v modelu a o tom, jak vytvořit objekty a propojení najdete v tématu [postupy: úprava příkazu standardní nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Zaregistrovat příkaz
 Opakujte v jazyce C# deklarace, které jste provedli v části symboly CommandSet.vsct hodnoty GUID a ID:

```csharp
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 Použijte stejnou hodnotu GUID jako vložený v **Commands.vsct**.

> [!NOTE]
>  Pokud změníte části symboly VSCT souboru, je nutné změnit tyto deklarace tak, aby odpovídaly. Také by se měl zvýšit číslo verze v Package.tt

 Zaregistrujte vaše příkazy nabídek jako součást této sady příkazů. `GetMenuCommands()` je volána při inicializaci diagramu:

```csharp
protected override IList<MenuCommand> GetMenuCommands()
{
  // Get the list of generated commands.
  IList<MenuCommand> commands = base.GetMenuCommands();
  // Add a custom command:
  DynamicStatusMenuCommand myContextMenuCommand =
    new DynamicStatusMenuCommand(
      new EventHandler(OnStatusMyContextMenuCommand),
      new EventHandler(OnMenuMyContextMenuCommand),
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));
  commands.Add(myContextMenuCommand);
  // Add more commands here.
  return commands;
}
```

## <a name="test-the-command"></a>Testování příkazu
 Sestavte a spusťte DSL v experimentální instanci sady Visual Studio. Příkaz se zobrazí v místní nabídce v situacích, které jste zadali.

#### <a name="to-exercise-the-command"></a>K příkazu

1.  Na **Průzkumníka řešení** nástrojů, klikněte na tlačítko **Transformovat všechny šablony**.

2.  Stisknutím klávesy **F5** znovu sestavte řešení a spusťte ladění jazyka specifického pro doménu v experimentální sestavení.

3.  V experimentální sestavení Otevřete diagram vzorku.

4.  Klikněte pravým tlačítkem na jednotlivé položky v diagramu, chcete-li ověřit, že příkaz správně povolené nebo zakázané a odpovídajícím způsobem zobrazený nebo skrytý, v závislosti na vybrané položky.

## <a name="troubleshooting"></a>Poradce při potížích
 **Příkaz v nabídce nezobrazí:**

- Příkaz se zobrazí jenom v ladění instance sady Visual Studio, dokud nenainstalujete balíček DSL. Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md).

- Ujistěte se, že je experimentální vzorku správnou příponu názvu souboru pro tento DSL. Pokud chcete zkontrolovat příponu názvu souboru, otevřete DslDefinition.dsl v instanci hlavní aplikace Visual Studio. V Průzkumníku DSL, klikněte pravým tlačítkem na uzel Editor a pak klikněte na vlastnosti. V okně Vlastnosti zkontrolujte vlastnost FileExtension.

- Měli jste [zvýší číslo verze balíčku](#version)?

- Nastavte zarážku na začátku OnStatus metodu. Ji by měl přerušit, když kliknete pravým tlačítkem na libovolnou část diagramu.

   **Není volána metoda OnStatus**:

  -   Ujistěte se, že identifikátory GUID a ID v kódu CommandSet shodovat s hodnotami v části symboly Commands.vsct.

  -   Commands.vsct Ujistěte se, že identifikátor GUID a ID v každé nadřazený uzel identifikovat správné nadřazené skupiny.

  -   V příkazovém řádku aplikace Visual Studio zadejte devenv/Setup exp /rootsuffix. Potom restartujte instanci ladění aplikace Visual Studio.

- Projděte skrze OnStatus metodu k ověření tohoto příkazu. Viditelné a příkaz. Povolena je nastaveno na hodnotu true.

  **Nesprávné nabídce text se zobrazí, nebo příkazu se zobrazí ve špatné místo**:

- Ujistěte se, že je kombinací identifikátoru GUID a ID jedinečné pro tento příkaz.

- Ujistěte se, že jste odinstalovali starší verze balíčku.

## <a name="see-also"></a>Viz také

- [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Postupy: Úprava příkazu standardní nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)
- [Nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md)
- [Ukázkový kód: diagramy okruh](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]