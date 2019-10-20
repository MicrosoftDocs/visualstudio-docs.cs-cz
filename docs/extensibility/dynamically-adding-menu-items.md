---
title: Dynamické přidávání položek nabídky | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7901cf19b112b1a9d87dcae5bce594f5cc431d78
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633357"
---
# <a name="dynamically-add-menu-items"></a>Dynamické přidávání položek nabídky
Položky nabídky lze za běhu přidat zadáním příznaku příkazu `DynamicItemStart` v definici tlačítka zástupného symbolu v souboru příkazu aplikace Visual Studio ( *. vsct*) a následným definováním (v kódu) počtu položek nabídky, které se mají zobrazit a zpracování příkazů (y). Po načtení rozhraní VSPackage je zástupný symbol nahrazen dynamickými položkami nabídky.

 Visual Studio používá dynamické seznamy v seznamu **naposledy použitých** (MRU), ve kterém se zobrazují názvy dokumentů, které byly nedávno otevřeny, a seznam **Windows** , ve kterém se zobrazují názvy aktuálně otevřených oken.   Příznak `DynamicItemStart` v definici příkazu určuje, že příkaz je zástupný symbol, dokud není otevřen VSPackage. Po otevření VSPackage je zástupný symbol nahrazen 0 nebo více příkazy, které jsou vytvořeny v době běhu a přidány do dynamického seznamu. Je možné, že nebudete moci zobrazit umístění v nabídce, kde se zobrazí dynamický seznam, dokud není otevřeno VSPackage.  Chcete-li naplnit dynamický seznam, Visual Studio požádá VSPackage, aby vyhledal příkaz s IDENTIFIKÁTORem, jehož první znaky jsou stejné jako ID zástupného symbolu. Když Visual Studio najde shodný příkaz, přidá název příkazu do dynamického seznamu. Pak zvýší ID a vyhledá další vyhovující příkaz pro přidání do dynamického seznamu, dokud nebudou existovat žádné další dynamické příkazy.

 Tento návod ukazuje, jak nastavit projekt po spuštění v řešení aplikace Visual Studio pomocí příkazu na panelu nástrojů **Průzkumník řešení** . Používá kontroler nabídek, který obsahuje dynamický rozevírací seznam projektů v aktivním řešení. Chcete-li zabránit tomuto příkazu v zobrazení, když není otevřeno žádné řešení nebo pokud má otevřené řešení pouze jeden projekt, VSPackage je načteno pouze v případě, že má řešení více projektů.

 Další informace o souborech *. vsct* naleznete v tématu [soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Vytvoření rozšíření pomocí příkazu nabídky

1. Vytvořte projekt VSIX s názvem `DynamicMenuItems`.

2. Po otevření projektu přidejte vlastní šablonu položky příkazu a pojmenujte ji **DynamicMenu**. Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Nastavení prvků v souboru *. vsct*
 Chcete-li vytvořit kontroler nabídek s dynamickými položkami nabídky na panelu nástrojů, zadejte následující prvky:

- Dvě skupiny příkazů, jeden, který obsahuje kontroler nabídek a druhý, který obsahuje položky nabídky v rozevírací nabídce

- Jeden prvek nabídky typu `MenuController`

- Dvě tlačítka, která fungují jako zástupný symbol pro položky nabídky a další, které doplní ikonu a popis tlačítka na panelu nástrojů.

1. V *DynamicMenuPackage. vsct*definujte identifikátory příkazů. Přejít do oddílu symboly a nahradit elementy IDSymbol v bloku GuidSymbol **guidDynamicMenuPackageCmdSet** . Je nutné definovat prvky IDSymbol pro tyto dvě skupiny, kontroler nabídek, zástupný příkaz a příkaz Ukotvit.

    ```xml
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />
        <IDSymbol name="MyMenuController" value ="0x1030"/>
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />
        <!-- NOTE: The following command expands at run time to some number of ids.
         Try not to place command ids after it (e.g. 0x0105, 0x0106).
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />
    </GuidSymbol>
    ```

2. V části skupiny odstraňte existující skupiny a přidejte dvě skupiny, které jste právě definovali:

    ```xml
    <Groups>
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.
             The 0x4000 priority adds this group after the group that contains the
             Preview Selected Items button, which is normally at the far right of the toolbar. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />
        </Group>
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />
        </Group>
    </Groups>
    ```

     Přidejte MenuController. Nastavte příznak příkazu DynamicVisibility, protože není vždycky viditelný. ButtonText se nezobrazí.

    ```xml
    <Menus>
        <!-- The MenuController to display on the Solution Explorer toolbar.
             Place it in the ToolbarItemGroup.-->
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />
            <CommandFlag>DynamicVisibility</CommandFlag>
            <Strings>
               <ButtonText></ButtonText>
           </Strings>
        </Menu>
    </Menus>
    ```

3. Přidejte dvě tlačítka, jednu jako zástupný symbol pro dynamické položky nabídky a jednu jako kotvu pro MenuController.

     Nadřazeným tlačítkem zástupného tlačítka je **MyMenuControllerGroup**. Přidejte do tlačítka zástupný text příznaky příkazu DynamicItemStart, DynamicVisibility a TextChanges. ButtonText se nezobrazí.

     Tlačítko ukotvení obsahuje ikonu a text popisu tlačítka. Nadřazeným tlačítkem ukotvení je také **MyMenuControllerGroup**. Přidáte příznak příkazu NoShowOnMenuController, aby se zajistilo, že se tlačítko v rozevíracím seznamu řadiče nabídky ve skutečnosti nezobrazí a příznak příkazu FixMenuController nastaví trvalý kotvu.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
    <Buttons>
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <CommandFlag>DynamicItemStart</CommandFlag>
          <CommandFlag>DynamicVisibility</CommandFlag>
          <CommandFlag>TextChanges</CommandFlag>
          <!-- This text does not appear. -->
          <Strings>
            <ButtonText>Project</ButtonText>
          </Strings>
        </Button>

        <!-- The anchor item to supply the icon/tooltip for the MenuController -->
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->
          <Icon guid="guidImages" id="bmpPicArrows"/>
          <!-- Do not show on the menu controller's drop down list-->
          <CommandFlag>NoShowOnMenuController</CommandFlag>
          <!-- Become the permanent anchor item for the menu controller -->
          <CommandFlag>FixMenuController</CommandFlag>
          <!-- The text that appears in the tooltip.-->
          <Strings>
            <ButtonText>Set Startup Project</ButtonText>
          </Strings>
        </Button>
    </Buttons>
    ```

4. Přidejte do projektu ikonu (ve složce *Resources* ) a pak do ní přidejte odkaz v souboru *. vsct* . V tomto návodu použijeme ikonu šipky, která je součástí šablony projektu.

5. Přidejte část VisibilityConstraints mimo oddíl Commands těsně před oddíl symboly. (Upozornění se může zobrazit, když ho přidáte za symboly.) V této části se ujistěte, že se kontroler nabídek zobrazuje pouze v případě, že je načteno řešení s více projekty.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Implementace dynamického příkazu nabídky
 Vytvoříte dynamickou třídu příkazu nabídky, která dědí z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. V této implementaci konstruktor určuje predikát, který se má použít pro porovnání příkazů. Chcete-li pomocí tohoto predikátu nastavit vlastnost <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>, která identifikuje příkaz, který má být vyvolán, je nutné přepsat metodu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>.

1. Vytvořte nový C# soubor třídy s názvem *DynamicItemMenuCommand.cs*a přidejte třídu s názvem **DynamicItemMenuCommand** , která dědí z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Přidejte následující direktivy using:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Přidejte soukromé pole pro uložení predikátu shody:

    ```csharp
    private Predicate<int> matches;

    ```

4. Přidejte konstruktor, který dědí z konstruktoru <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> a určuje obslužnou rutinu příkazu a obslužnou rutinu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>. Přidejte predikát pro porovnání příkazu:

    ```csharp
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)
    {
        if (matches == null)
        {
            throw new ArgumentNullException("matches");
        }

        this.matches = matches;
    }
    ```

5. Přepište metodu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> tak, aby volala predikát matchs a nastaví vlastnost <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>:

    ```csharp
    public override bool DynamicItemMatch(int cmdId)
    {
        // Call the supplied predicate to test whether the given cmdId is a match.
        // If it is, store the command id in MatchedCommandid
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.
        if (this.matches(cmdId))
        {
            this.MatchedCommandId = cmdId;
            return true;
        }

        this.MatchedCommandId = 0;
        return false;
    }
    ```

## <a name="add-the-command"></a>Přidat příkaz
 Konstruktor DynamicMenu je místo, kde jste nastavili příkazy nabídky, včetně dynamických nabídek a položek nabídky.

1. Do *DynamicMenuPackage.cs*přidejte GUID sady příkazů a ID příkazu:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. Do souboru *DynamicMenu.cs* přidejte následující direktivy using:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. Ve třídě `DynamicMenu` přidejte soukromé pole **DTE2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Přidejte soukromé pole rootItemId:

    ```csharp
    private int rootItemId = 0;
    ```

5. V konstruktoru DynamicMenu přidejte příkaz nabídky. V další části definujeme obslužnou rutinu příkazu, obslužnou rutinu události `BeforeQueryStatus` a predikát Match.

    ```csharp
    private DynamicMenu(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,
                IsValidDynamicItem,
                OnInvokedDynamicItem,
                OnBeforeQueryStatusDynamicItem);
                commandService.AddCommand(dynamicMenuCommand);
                }

        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));
    }
    ```

## <a name="implement-the-handlers"></a>Implementace obslužných rutin
 Chcete-li implementovat dynamické položky nabídky na řadiči nabídky, je nutné zpracovat příkaz při kliknutí na dynamickou položku. Je také nutné implementovat logiku, která nastaví stav položky nabídky. Přidejte obslužné rutiny do třídy `DynamicMenu`.

1. Chcete-li implementovat příkaz **nastavit spouštěný projekt** , přidejte obslužnou rutinu události **OnInvokedDynamicItem** . Vyhledá projekt, jehož název je stejný jako text příkazu, který byl vyvolán, a nastaví jej jako spouštěný projekt nastavením jeho absolutní cesty ve vlastnosti <xref:EnvDTE.SolutionBuild.StartupProjects%2A>.

    ```csharp
    private void OnInvokedDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;
        // If the command is already checked, we don't need to do anything
        if (invokedCommand.Checked)
            return;

        // Find the project that corresponds to the command text and set it as the startup project
        var projects = dte2.Solution.Projects;
        foreach (Project proj in projects)
        {
            if (invokedCommand.Text.Equals(proj.Name))
            {
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;
                return;
            }
        }
    }
    ```

2. Přidejte obslužnou rutinu události `OnBeforeQueryStatusDynamicItem`. Toto je obslužná rutina volaná před událostí `QueryStatus`. Určuje, zda je položka nabídky "skutečná" položka, tzn. ne zástupná položka a zda je položka již zaškrtnuta (tzn. že projekt je již nastaven jako spouštěný projekt).

    ```csharp
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;
        matchedCommand.Enabled = true;
        matchedCommand.Visible = true;

        // Find out whether the command ID is 0, which is the ID of the root item.
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,
         // and IsValidDynamicItem won't be called.
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);

        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);

        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;

        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));

        // Check the command if it isn't checked already selected
        matchedCommand.Checked = (matchedCommand.Text == startupProject);

        // Clear the ID because we are done with this item.
        matchedCommand.MatchedCommandId = 0;
    }
    ```

## <a name="implement-the-command-id-match-predicate"></a>Implementace predikátu shody ID příkazu

Nyní implementuje predikát porovnávání. Musíme určit dvě věci: nejdřív, zda je ID příkazu platné (je větší nebo rovno deklarovanému ID příkazu) a druhý, zda určuje možný projekt (je menší než počet projektů v řešení).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Nastavte VSPackage na Load pouze v případě, že má řešení více projektů.
 Vzhledem k tomu, že příkaz **nastavit spouštěný projekt** nedává smysl, pokud aktivní řešení nemá více než jeden projekt, můžete sadu VSPackage nastavit na automatické načítání pouze v takovém případě. Použijete <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> společně s kontextem uživatelského rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. V souboru *DynamicMenuPackage.cs* přidejte následující atributy do třídy DynamicMenuPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Test nastavení spouštěného projektu jako příkazu
 Nyní můžete testovat svůj kód.

1. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance.

2. V experimentální instanci otevřete řešení, které má více než jeden projekt.

     Na panelu nástrojů **Průzkumník řešení** by se měla zobrazit ikona šipky. Když ho rozbalíte, zobrazí se položky nabídky, které reprezentují různé projekty v řešení.

3. Když zkontrolujete jeden z projektů, vytvoří se projekt po spuštění.

4. Když řešení zavřete nebo otevřete řešení, které má pouze jeden projekt, ikona panelu nástrojů by měla zmizet.

## <a name="see-also"></a>Viz také:
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
- [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
