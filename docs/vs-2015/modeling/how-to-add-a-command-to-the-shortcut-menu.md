---
title: 'Postupy: Přidání příkazu do místní nabídky | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: cd550399-05fc-4dbf-be4c-f5094bb752ce
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d5ddea477aa7295c41097177265b43483b7aa45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850406"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Postupy: Přidání příkazu do místní nabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Příkazy nabídky můžete přidat do jazyka DSL (Domain-Specific Language), aby uživatelé mohli provádět úlohy, které jsou specifické pro vaši DSL. Příkazy se zobrazí v místní nabídce (místní), když uživatelé na diagram klikne pravým tlačítkem myši. Můžete definovat příkaz, aby se v nabídce zobrazoval pouze v určitých případech. Příkaz lze například zobrazit pouze v případě, že uživatel klikne na konkrétní typy prvku nebo prvky v určitých stavech.

 V souhrnu jsou kroky provedeny v projektu DslPackage následujícím způsobem:

1. [Deklarovat příkaz v Commands. vsct](#VSCT)

2. [Aktualizujte číslo verze balíčku v Package.TT](#version). To je nutné provést pokaždé, když změníte příkazy. vsct

3. [Metody zápisu do třídy CommandSet](#CommandSet) , aby příkaz byl viditelný a definoval, co má příkaz dělat.

   Ukázky najdete na [webu sady SDK pro vizualizaci a modelování](https://www.visualstudio.com/).

> [!NOTE]
> Můžete také změnit chování některých existujících příkazů, jako je například vyjmout, vložit, vybrat vše a tisknout přepsáním metod v CommandSet.cs. Další informace naleznete v tématu [How to: Modify a Standard a Command nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="defining-a-command-using-mef"></a>Definování příkazu pomocí MEF
 Rozhraní Managed Extension Framework (MEF) poskytuje alternativní metodu definování příkazů nabídky v nabídce diagramu. Jeho hlavním účelem je umožnit, aby linka DSL rozšířila vámi nebo jiné strany. Uživatelé si můžou zvolit, že budou instalovat jenom DSL, nebo můžou nainstalovat jak DSL, tak rozšíření. Rozhraní MEF však také zkracuje práci s definováním příkazů místní nabídky po počáteční práci, která povoluje rozhraní MEF na DSL.

 Použijte metodu v tomto tématu, pokud:

1. Příkazy nabídky můžete definovat i v jiných nabídkách, než v místní nabídce pravého tlačítka myši.

2. Chcete v nabídce definovat konkrétní seskupení příkazů.

3. Nechcete ostatním uživatelům umožnit rozšiřování DSL pomocí vlastních příkazů.

4. Chcete definovat pouze jeden příkaz.

   V opačném případě zvažte použití metody MEF k definování příkazů. Další informace najdete v tématu věnovaném [rozšiřování DSL pomocí MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="declare-the-command-in-commandsvsct"></a><a name="VSCT"></a> Deklarovat příkaz v Commands. vsct
 Příkazy nabídky jsou deklarovány v DslPackage\Commands.vsct. Tyto definice určují popisky položek nabídky a tam, kde se zobrazují v nabídkách.

 Soubor, který upravujete, Commands. vsct, importuje definice z několika souborů. h, které jsou umístěny v adresáři *Instalační cesta sady Visual Studio SDK*\VisualStudioIntegration\Common\Inc. Obsahuje taky GeneratedVsct. vsct, který se generuje z definice DSL.

 Další informace o souborech. vsct naleznete v tématu [tabulka příkazů sady Visual Studio (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

#### <a name="to-add-the-command"></a>Přidání příkazu

1. V **Průzkumník řešení**v projektu **DslPackage** otevřete příkazy Commands. vsct.

2. V `Commands` elementu definujte jedno nebo více tlačítek a skupinu. *Tlačítko* je položka v nabídce. *Skupina* je oddílem v nabídce. Chcete-li definovat tyto položky, přidejte následující prvky:

    ```
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
    > Každé tlačítko nebo skupina je identifikován identifikátorem GUID a IDENTIFIKÁTORem celého čísla. Můžete vytvořit několik skupin a tlačítek se stejným identifikátorem GUID. Musí mít ale jiná ID. Názvy identifikátorů GUID a názvy ID jsou přeloženy na skutečné identifikátory GUID a číselné identifikátory v `<Symbols>` uzlu.

3. Přidejte omezení viditelnosti pro příkaz tak, aby bylo načteno pouze do kontextu vašeho jazyka specifického pro doménu. Další informace naleznete v tématu [VisibilityConstraints element](../extensibility/visibilityconstraints-element.md).

     Chcete-li to provést, přidejte následující prvky do `CommandTable` elementu za `Commands` elementem.

    ```
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4. Zadejte názvy, které jste použili pro identifikátory GUID a ID. Chcete-li to provést, přidejte `Symbols` element v `CommandTable` elementu za `Commands` element.

    ```
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5. Nahraďte `{000...000}` identifikátorem GUID, který identifikuje vaše skupiny a položky nabídky. Chcete-li získat nový identifikátor GUID, použijte nástroj **Create GUID** v nabídce **nástroje** .

    > [!NOTE]
    > Pokud přidáte více skupin nebo položek nabídky, můžete použít stejný identifikátor GUID. Je však nutné použít nové hodnoty pro `IDSymbols` .

6. V kódu, který jste zkopírovali z tohoto postupu, nahraďte všechny výskyty následujících řetězců vlastními řetězci:

    - `grpidMyMenuGroup`

    - `cmdidMyContextMenuCommand`

    - `guidCustomMenuCmdSet`

    - `My Context Menu Command`

## <a name="update-the-package-version-in-packagett"></a><a name="version"></a> Aktualizace verze balíčku v Package.tt
 Kdykoli přidáte nebo změníte příkaz, aktualizujte `version` parametr <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> , který se použije na třídu balíčku, a teprve potom uvolněte novou verzi vašeho jazyka specifického pro doménu.

 Vzhledem k tomu, že třída balíčku je definována ve vygenerovaném souboru, aktualizujte atribut v souboru textové šablony, který generuje soubor Package.cs.

#### <a name="to-update-the-packagett-file"></a>Aktualizace souboru Package.tt

1. V **Průzkumník řešení**v projektu **DslPackage** ve složce **GeneratedCode** otevřete soubor Package.tt.

2. Vyhledejte `ProvideMenuResource` atribut.

3. Zvyšte `version` parametr atributu, který je druhým parametrem. Pokud chcete, můžete název parametru napsat explicitně a připomenout vám jeho účel. Příklad:

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

## <a name="define-the-behavior-of-the-command"></a><a name="CommandSet"></a> Definování chování příkazu
 Vaše DSL už obsahuje některé příkazy, které jsou implementované v částečné třídě deklarované v DslPackage\GeneratedCode\CommandSet.cs.. Chcete-li přidat nové příkazy, je nutné tuto třídu roztáhnout vytvořením nového souboru, který obsahuje částečnou deklaraci stejné třídy. Název třídy je obvykle *\<YourDslName>* `CommandSet` . Je vhodné začít tím, že ověříte název třídy a zkontrolujete její obsah.

 Třída sady příkazů je odvozena z <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> .

#### <a name="to-extend-the-commandset-class"></a>Postup rozšiřování třídy CommandSet

1. V Průzkumník řešení v projektu DslPackage otevřete složku GeneratedCode a potom se podívejte do části CommandSet.tt a otevřete její vygenerovaný soubor CommandSet.cs. Poznamenejte si obor názvů a název první třídy, která je zde definována. Může se například zobrazit:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. V **DslPackage**vytvořte složku s názvem **vlastní kód**. V této složce vytvořte nový soubor třídy s názvem `CommandSet.cs` .

3. V novém souboru zapište částečnou deklaraci, která má stejný obor názvů a název jako vygenerovaná částečná třída. Příklad:

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     **Poznámka:** Pokud jste použili šablonu třídy k vytvoření nového souboru, je nutné opravit obor názvů i název třídy.

### <a name="extend-the-command-set-class"></a>Rozšíří třídu sady příkazů.
 Kód sady příkazů obvykle bude potřebovat importovat následující obory názvů:

```
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

 Upravte obor názvů a název třídy tak, aby odpovídaly hodnotám ve vygenerovaných CommandSet.cs:

```
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

 Je nutné definovat dvě metody, jednu pro určení, kdy bude příkaz viditelný v místní nabídce, a druhý k provedení příkazu. Tyto metody nejsou popsány. místo toho je zaregistrujete do seznamu příkazů.

### <a name="define-when-the-command-will-be-visible"></a>Definovat, kdy bude příkaz viditelný
 Pro každý příkaz definujte `OnStatus...` metodu, která určuje, zda se příkaz zobrazí v nabídce a zda bude povolen nebo šedý. Nastavte `Visible` vlastnosti a `Enabled` `MenuCommand` , jak je znázorněno v následujícím příkladu. Tato metoda je volána za účelem vytvoření místní nabídky pokaždé, když uživatel klikne pravým tlačítkem myši na diagram, takže musí pracovat rychle.

 V tomto příkladu je příkaz viditelný pouze v případě, že uživatel vybral konkrétní typ obrazce a je povolen pouze v případě, že je alespoň jeden z vybraných prvků v určitém stavu. Příklad je založen na šabloně třídy DSL diagramu tříd a ClassShape a ModelClass jsou typy, které jsou definovány v DSL:

```
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

 Následující fragmenty jsou často užitečné v metodách stavu:

- `this.CurrentSelection`. Tvar, na který uživatel klikne pravým tlačítkem, je vždy zahrnut v tomto seznamu. Pokud uživatel klikne na prázdnou část diagramu, diagram je jediným členem tohoto seznamu.

- `this.IsDiagramSelected()` - `true` Pokud uživatel klikl na prázdnou část diagramu.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` – uživatel nevybrali více objektů.

- `this.SingleSelection` – tvar nebo diagram, na který uživatel klikne pravým tlačítkem myši

- `shape.ModelElement as MyLanguageElement` – prvek modelu reprezentovaný obrazcem.

  Jako obecné pokyny nastavte `Visible` vlastnost na základě toho, co je vybráno, a nastavte `Enabled` vlastnost na základě stavu vybraných prvků.

  Metoda-status by neměla měnit stav úložiště.

### <a name="define-what-the-command-does"></a>Definice příkazu
 Pro každý příkaz definujte `OnMenu...` metodu, která provede požadovanou akci, když uživatel klikne na příkaz nabídky.

 Pokud provedete změny prvků modelu, je nutné provést v rámci transakce. Další informace naleznete v tématu [How to: Modify a Standard a Command nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 V tomto příkladu, `ClassShape` , `ModelClass` a `Comment` jsou typy, které jsou definovány v DSL, která je odvozena od šablony třídy pro schéma DSL.

```
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

 Další informace o tom, jak přecházet z objektu na objekt v modelu a o tom, jak vytvořit objekty a odkazy, naleznete v tématu [How to: Modify a příkaz standardní nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Registrace příkazu
 V jazyce C# opakujte deklarace identifikátorů GUID a ID, které jste provedli v části symboly v CommandSet. vsct:

```
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 Použijte stejnou hodnotu GUID, jakou jste vložili do **příkazů Commands. vsct**.

> [!NOTE]
> Pokud změníte oddíl symboly v souboru VSCT, je nutné změnit také tyto deklarace, aby odpovídaly. Měli byste také zvýšit číslo verze v Package.tt.

 Zaregistrujte příkazy nabídky jako součást této sady příkazů. `GetMenuCommands()` je volána jednou při inicializaci diagramu:

```
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
 Sestavte a spusťte DSL v experimentální instanci aplikace Visual Studio. Příkaz by měl být zobrazen v místní nabídce v situacích, které jste zadali.

#### <a name="to-exercise-the-command"></a>Postup při cvičení příkazu

1. Na panelu nástrojů **Průzkumník řešení** klikněte na možnost **transformovat všechny šablony**.

2. Stisknutím klávesy **F5** znovu sestavte řešení a spusťte ladění jazyka specifického pro doménu v experimentálním sestavení.

3. V experimentálním sestavení otevřete vzorový diagram.

4. Kliknutím pravým tlačítkem myši na různé položky v diagramu ověřte, zda je příkaz správně povolen nebo zakázán a odpovídajícím způsobem zobrazen nebo skryt v závislosti na vybrané položce.

## <a name="troubleshooting"></a>Řešení potíží
 **Příkaz se nezobrazuje v nabídce:**

- Příkaz se zobrazí pouze v instancích ladění sady Visual Studio, dokud nenainstalujete balíček DSL. Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md).

- Ujistěte se, že experimentální ukázka má pro tuto DSL správnou příponu názvu souboru. Chcete-li ověřit příponu názvu souboru, Otevřete DslDefinition. DSL v hlavní instanci aplikace Visual Studio. Pak v Průzkumníku DSL klikněte pravým tlačítkem myši na uzel editoru a pak klikněte na vlastnosti. V okno Vlastnosti Projděte vlastnost přípona.

- Provedli jste [zvýšení čísla verze balíčku](#version)?

- Nastavte zarážku na začátku své metody stavu. Měla by se přerušit, když kliknete pravým tlačítkem myši na jakoukoli část diagramu.

   **Metoda-status není volána**:

  - Ujistěte se, že identifikátory GUID a ID v kódu CommandSet se shodují s hodnotami v části symboly příkazů. vsct.

  - V příkazu Commands. vsct se ujistěte, že identifikátor GUID a ID v každém nadřazeném uzlu identifikují správnou nadřazenou skupinu.

  - Do příkazového řádku sady Visual Studio zadejte devenv/rootsuffix exp/Setup. Pak restartujte instanci ladění sady Visual Studio.

- Projděte si metodu "-stav", abyste ověřili, že příkaz. Visible a příkaz. Vlastnost Enabled je nastavena na hodnotu true.

  **Zobrazí se nesprávný text nabídky nebo se příkaz zobrazí na nesprávném místě**:

- Ujistěte se, že kombinace identifikátoru GUID a ID je pro tento příkaz jedinečná.

- Ujistěte se, že jste odinstalovali starší verze balíčku.

## <a name="see-also"></a>Viz také
 [Psaní kódu pro přizpůsobení jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md) [Postupy: Změna standardního příkazu nabídky](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md) [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md)
