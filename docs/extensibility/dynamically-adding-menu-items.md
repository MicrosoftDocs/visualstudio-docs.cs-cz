---
title: Dynamické přidávání položek nabídky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4387c1930e09e49c0ec5c36ccedc1bb83dc273f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712057"
---
# <a name="dynamically-add-menu-items"></a>Dynamické přidávání položek nabídky
Položky nabídky můžete přidat za běhu `DynamicItemStart` zadáním příznaku příkazu v definici zástupného tlačítka v souboru příkazu Visual Studio (*.vsct*) a poté definovat (v kódu) počet položek nabídky pro zobrazení a zpracování příkazů. Po načtení balíčku VSPackage je zástupný symbol nahrazen položkami dynamické nabídky.

 Visual Studio používá dynamické seznamy v seznamu **Naposledy použitý** (MRU), který zobrazuje názvy dokumentů, které byly otevřeny nedávno, a seznam **systému Windows,** který zobrazuje názvy oken, které jsou aktuálně otevřeny.   Příznak `DynamicItemStart` v definici příkazu určuje, že příkaz je zástupný symbol, dokud není otevřen VSPackage. Při otevření VSPackage zástupný symbol je nahrazen 0 nebo více příkazů, které jsou vytvořeny za běhu a přidány do dynamického seznamu. Je možné, že nebude možné zobrazit pozici v nabídce, kde se zobrazí dynamický seznam, dokud není otevřen VSPackage.  Chcete-li naplnit dynamický seznam, Visual Studio požádá VSPackage hledat příkaz s ID, jehož první znaky jsou stejné jako ID zástupného symbolu. Když Visual Studio najde odpovídající příkaz, přidá název příkazu do dynamického seznamu. Potom zvýší ID a vyhledá jiný odpovídající příkaz přidat do dynamického seznamu, dokud neexistují žádné další dynamické příkazy.

 Tento návod ukazuje, jak nastavit projekt po spuštění v řešení sady Visual Studio pomocí příkazu na panelu nástrojů **Průzkumníka řešení.** Používá řadič nabídky, který má dynamický rozevírací seznam projektů v aktivním řešení. Chcete-li zabránit tomu, aby se tento příkaz zobrazoval, když není otevřeno žádné řešení nebo pokud otevřené řešení obsahuje pouze jeden projekt, je VSPackage načten pouze v případě, že řešení má více projektů.

 Další informace o *souborech .vsct* naleznete v [tématu Soubory příkazů sady Visual Studio (.vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

## <a name="create-an-extension-with-a-menu-command"></a>Vytvoření rozšíření pomocí příkazu nabídky

1. Vytvořte projekt VSIX s názvem `DynamicMenuItems`.

2. Po otevření projektu přidejte vlastní šablonu příkazu a pojmenujte ji **DynamicMenu**. Další informace naleznete [v tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>Nastavení prvků v souboru *.vsct*
 Chcete-li vytvořit řadič nabídky s dynamickými položkami nabídky na panelu nástrojů, určete následující prvky:

- Dvě skupiny příkazů, jedna obsahující řadič nabídky a druhá, která obsahuje položky nabídky v rozevíracím přehledu

- Jeden prvek nabídky typu`MenuController`

- Dvě tlačítka, jedno, které funguje jako zástupný symbol pro položky nabídky, a druhé, které poskytuje ikonu a popisek na panelu nástrojů.

1. V *souboru DynamicMenuPackage.vsct*definujte ID příkazů. Přejděte do části Symboly a nahraďte prvky IDSymbol v bloku **guidDynamicMenuPackageCmdSet** GuidSymbol. Je třeba definovat prvky IDSymbol pro dvě skupiny, řadič nabídky, zástupný příkaz a příkaz kotvy.

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

2. V části Skupiny odstraňte existující skupiny a přidejte dvě skupiny, které jste právě definovali:

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

     Přidejte MenuController. Nastavte příznak příkazu DynamicVisibility, protože není vždy viditelný. ButtonText se nezobrazí.

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

3. Přidejte dvě tlačítka, jedno jako zástupný symbol pro položky dynamické nabídky a jedno jako kotvu pro MenuController.

     Nadřazenou zástupnou položkou je **MyMenuControllerGroup**. Přidejte příznaky příkazu DynamicItemStart, DynamicVisibility a TextChanges do zástupného tlačítka. ButtonText se nezobrazí.

     Kotevní tlačítko obsahuje ikonu a text popisu. Nadřazenou položkou kotevního tlačítka je také **MyMenuControllerGroup**. Přidáte příznak příkazu NoShowOnMenuController, abyste se ujistili, že se tlačítko ve skutečnosti nezobrazí v rozevíracím lístku řadiče nabídky, a příznak příkazu FixMenuController, aby se stal trvalou kotvou.

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

4. Přidejte do projektu ikonu (ve složce *Zdroje)* a pak na ni přidejte odkaz do souboru *.vsct.* V tomto návodu použijeme ikonu Šipky, která je součástí šablony projektu.

5. Přidejte oddíl VisibilityConstraints mimo oddíl Příkazy těsně před oddíl Symboly. (Pokud jej přidáte za symboly, může se vám dostat upozornění.) Tato část zajišťuje, že řadič nabídky se zobrazí pouze v případě, že je načteno řešení s více projekty.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Implementace příkazu dynamické nabídky
 Vytvoříte třídu příkazů dynamické nabídky, která dědí z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. V této implementaci konstruktor určuje predikát, který se má použít pro odpovídající příkazy. Je nutné přepsat <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodu použít tento predikát nastavit <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> vlastnost, která identifikuje příkaz, který má být vyvolán.

1. Vytvořte nový soubor třídy C# s názvem *DynamicItemMenuCommand.cs*a přidejte <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>třídu s názvem **DynamicItemMenuCommand,** která dědí z :

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Pomocí direktiv přidejte následující příkazy:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Přidejte soukromé pole pro uložení predikátu shody:

    ```csharp
    private Predicate<int> matches;

    ```

4. Přidejte konstruktor, který <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> dědí z konstruktoru a <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> určuje obslužnou rutinu příkazu a obslužnou rutinu. Přidejte predikát pro porovnávání příkazu:

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

5. Přepište <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodu tak, aby volá predikát <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> shody a nastaví vlastnost:

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
 Konstruktor DynamicMenu je místo, kde můžete nastavit příkazy nabídky, včetně dynamických nabídek a položek nabídky.

1. V *DynamicMenuPackage.cs*přidejte identifikátor GUID sady příkazů a ID příkazu:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. Do souboru *DynamicMenu.cs* přidejte následující příkazy pomocí direktiv:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. Do `DynamicMenu` třídy přidejte soukromé pole **dte2**.

    ```csharp
    private DTE2 dte2;
    ```

4. Přidejte privátní kořenové poleItemId:

    ```csharp
    private int rootItemId = 0;
    ```

5. V konstruktoru DynamicMenu přidejte příkaz nabídky. V další části definujeme obslužnou rutinu příkazu, obslužnou rutinu `BeforeQueryStatus` události a predikát shody.

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
 Chcete-li implementovat položky dynamické nabídky na řadiči nabídky, je nutné zpracovat příkaz při klepnutí na dynamickou položku. Musíte také implementovat logiku, která nastaví stav položky nabídky. Přidejte obslužné rutiny do `DynamicMenu` třídy.

1. Chcete-li implementovat příkaz **Nastavit projekt po spuštění,** přidejte obslužnou rutinu události **OnInvokedDynamicItem.** Hledá projekt, jehož název je stejný jako text příkazu, který byl vyvolán, a nastaví jej <xref:EnvDTE.SolutionBuild.StartupProjects%2A> jako projekt po spuštění nastavením jeho absolutní cestu ve vlastnosti.

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

2. Přidejte `OnBeforeQueryStatusDynamicItem` obslužnou rutinu události. Toto je obslužná rutina volaná `QueryStatus` před událostí. Určuje, zda je položka nabídky "skutečná" položka, tedy ne zástupná položka, a zda je položka již zaškrtnuta (což znamená, že projekt je již nastaven jako projekt při spuštění).

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

## <a name="implement-the-command-id-match-predicate"></a>Implementace predikátu id příkazu odpovídá

Nyní implementujte predikát zápasu. Musíme určit dvě věci: za prvé, zda id příkazu je platný (je větší než nebo rovno deklarované id příkazu), a za druhé, zda určuje možný projekt (je menší než počet projektů v řešení).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Nastavte VSPackage načíst pouze v případě, že řešení má více projektů
 Vzhledem k **tomu, že** příkaz Nastavit spuštění projektu nemá smysl, pokud aktivní řešení obsahuje více než jeden projekt, můžete nastavit VSPackage automaticky načíst pouze v takovém případě. Používáte <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> společně s kontextem <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>ui . V *souboru DynamicMenuPackage.cs* přidejte do třídy DynamicMenuPackage následující atributy:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Otestovat příkaz nastavit spouštěcí projekt
 Nyní můžete otestovat svůj kód.

1. Sestavení projektu a začít ladění. Experimentální instance by se měla zobrazit.

2. V experimentální instanci otevřete řešení, které má více než jeden projekt.

     Na panelu nástrojů **Průzkumníka řešení** by se měla zobrazit ikona šipky. Při rozbalení by se měly zobrazit položky nabídky, které představují různé projekty v řešení.

3. Při kontrole jednoho z projektů se stane projekt po spuštění.

4. Když zavřete řešení nebo otevřete řešení, které má pouze jeden projekt, ikona panelu nástrojů by měla zmizet.

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
- [Jak VSPackages přidat prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
