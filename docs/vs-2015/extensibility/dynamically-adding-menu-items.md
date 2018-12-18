---
title: Dynamické přidávání položek nabídky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8f188c71cb1e25364cee34c6a97c87b3a265ee7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809750"
---
# <a name="dynamically-adding-menu-items"></a>Dynamické přidávání položek nabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete přidat položky nabídky v době běhu tak, že zadáte `DynamicItemStart` příkazu příznak na definici tlačítko zástupný symbol v souboru sady Visual Studio (.vsct) tabulky příkazů, a definování (v kódu) číslo nabídky položky k zobrazení a zpracování příkazy. Při načítání sady VSPackage zástupný text nahrazen dynamickou nabídku položky.  
  
 Visual Studio používá dynamické seznamy **naposledy použitých** seznam (MRU), který zobrazuje názvy dokumentů, které byly naposledy otevřeny, a **Windows** seznam, který zobrazuje názvy systému windows které jsou aktuálně otevřené.   `DynamicItemStart` Definice příkazu příznak určuje, že příkaz je zástupný symbol, dokud je otevřen sady VSPackage. Při otevření sady VSPackage zástupný text nahrazen 0 nebo více příkazů, které jsou vytvořeny v době běhu a přidat do seznamu dynamického. Nebude moct zobrazit na pozici v nabídce, kde se zobrazí v seznamu dynamického, dokud je otevřen sady VSPackage.  K naplnění seznamu dynamického Visual Studio se vás zeptá VSPackage k vyhledání příkazu s ID jehož první znaky jsou stejné jako ID zástupný symbol. Když Visual Studio vyhledá odpovídajícího příkazu, přidá název příkazu dynamického seznamu. Zvýší hodnotu ID a vyhledá další odpovídající příkaz pro přidání do seznamu dynamického až nebudou existovat žádné další dynamické příkazy.  
  
 Tento návod ukazuje, jak nastavit spouštěný projekt v řešení sady Visual Studio pomocí příkazu na **Průzkumníka řešení** nástrojů. Používá kontroleru nabídky, která má dynamické rozevírací seznam projektů v aktivním řešení. Aby tento příkaz povolí, když žádné řešení je otevřena nebo když otevřete řešení má pouze jeden projekt, sady VSPackage je načtena, pouze když řešení obsahuje více projektů.  
  
 Další informace o souborech .vsct najdete v tématu [tabulky příkazů aplikace Visual Studio (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Vytváření rozšíření pomocí příkazu nabídky  
  
1.  Vytvořte projekt VSIX s názvem `DynamicMenuItems`.  
  
2.  Po otevření projektu přidejte šablonu položky příkazu vlastní a pojmenujte ho **kódu**. Další informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>Nastavení prvků v souboru .vsct  
 Vytvoření kontroleru nabídky s dynamické položky nabídky na panelu nástrojů, zadejte následující prvky:  
  
-   Dvě příkaz skupin, ten, který obsahuje kontroleru nabídky a další vlastnost, která obsahuje položky nabídky v rozevírací nabídce  
  
-   Element jednu nabídku typu `MenuController`  
  
-   Dvě tlačítka, který slouží jako zástupný symbol pro položky nabídky a druhý, který poskytuje ikonu a popis tlačítka na panelu nástrojů.  
  
1.  V DynamicMenuPackage.vsct definice ID příkazů. Přejděte do části symboly a nahradit idsymbol – prvky v **guidDynamicMenuPackageCmdSet** guidsymbol – blok. Budete muset definovat idsymbol – prvky pro dvě skupiny, kontroleru nabídky, zástupný text příkazu a příkaz ukotvení.  
  
    ```csharp  
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
  
2.  V části skupiny odstraňte existující skupiny a přidejte dvě skupiny, kterou jste právě definovali:  
  
    ```  
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
  
     Přidejte MenuController. Nastavte příznak DynamicVisibility příkaz, protože není vždy viditelné. ButtonText se nezobrazí.  
  
    ```  
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
  
3.  Přidejte dvě tlačítka, jeden jako zástupný symbol pro dynamickou nabídku položky a druhý jako ukotvení pro MenuController.  
  
     Nadřazený prvek tlačítka pro zástupný text je **MyMenuControllerGroup**. Přidat DynamicItemStart DynamicVisibility, a příkaz TextChanges příznaky pro tlačítko zástupný symbol. ButtonText se nezobrazí.  
  
     Tlačítko ukotvení obsahuje ikonu a text popisku. Nadřazený prvek tlačítka ukotvení je také **MyMenuControllerGroup**. Přidání příkazu příznak NoShowOnMenuController zajistit, aby že na tlačítko ve skutečnosti nezobrazí v rozevírací nabídce kontroleru nabídky a příznaku příkaz FixMenuController k němu trvalé ukotvení.  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
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
  
4.  Ikona Přidat do projektu (ve složce prostředky) a pak přidejte na ni odkaz v souboru .vsct. V tomto názorném postupu používáme ikonu šipky, která je součástí šablony projektu.  
  
5.  Přidáte oddíl visibilityconstraints – mimo oddíl příkazy těsně před části symboly. (Upozornění může získat, pokud chcete přidat po symboly.) Tato část zajišťuje, že kontroleru nabídky se zobrazí, jenom když je načtené řešení s více projekty.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implementing-the-dynamic-menu-command"></a>Implementace příkazu dynamická nabídka  
 Vytvořte třídu příkazu dynamickou nabídku, která dědí z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. V této implementaci konstruktoru určuje predikátu k se použije k porovnání příkazů. Je nutné přepsat <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metoda se má použít tento predikát nastavit <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> vlastnosti, které identifikuje příkaz, který má být volána.  
  
1.  Vytvořte nový soubor jazyka C# třída s názvem DynamicItemMenuCommand.cs a přidejte třídu s názvem **DynamicItemMenuCommand** , která dědí z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```csharp  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Přidejte následující příkazy using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Přidáte soukromé pole k uložení predikát shody:  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4.  Přidat konstruktor, který dědí z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> konstruktor a určuje obslužná rutina příkazu a <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> obslužné rutiny. Přidáte predikát pro párování příkazu:  
  
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
  
5.  Přepsat <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodu tak, že volá shody predikát a nastaví <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> vlastnost:  
  
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
  
## <a name="adding-the-command"></a>Přidání příkazu  
 Konstruktor kódu je, ve kterém nastavujete příkazy nabídek, včetně dynamických nabídek a položkami nabídky.  
  
1.  V DynamicMenuPackageGuids.cs přidejte identifikátor GUID sady příkazů a ID příkazu:  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  V souboru DynamicMenu.cs, přidejte následující příkazy using:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Ve třídě kódu přidat soukromé pole **dte2**.  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4.  Přidejte privátní rootItemId pole:  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5.  V konstruktoru kódu přidejte příkaz nabídky. V další části budeme definovat obslužnou rutinu příkazu `BeforeQueryStatus` obslužná rutina události a predikát shoda.  
  
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
  
## <a name="implementing-the-handlers"></a>Implementace obslužné rutiny  
 Pokud chcete implementovat dynamické položky nabídky na kontroleru nabídky, musí zpracovat příkaz dynamické položky se při kliknutí na. Musíte také implementovat do logiky, která nastaví stav položky nabídky. Přidejte obslužné rutiny třídy kódu.  
  
1.  K implementaci **nastavte projekt po spuštění** příkazu, přidá se **OnInvokedDynamicItem** obslužné rutiny události. Vyhledá projektu, jehož název je stejný jako text příkazu, který zavolání a nastaví jej jako spouštěný projekt tak, že nastavíte její absolutní cestu <xref:EnvDTE.SolutionBuild.StartupProjects%2A> vlastnost.  
  
    ```csharp  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don’t need to do anything  
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
  
2.  Přidat `OnBeforeQueryStatusDynamicItem` obslužné rutiny události. To je obslužná rutina volána před provedením `QueryStatus` událostí. Určuje, zda je položka nabídky položku "real", tedy ne zástupný symbol položky, a zda je položka již zaškrtnuta (to znamená, že projekt je již nastaven jako projekt po spuštění).  
  
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
  
## <a name="implementing-the-command-id-match-predicate"></a>Implementace predikátu shoda ID příkazu  
  
1.  Teď implementujte predikát shoda. Potřebujeme k určení dvě věci: nejprve, zda ID příkazu, který je platný (je větší než nebo rovna hodnotě Identifikátor deklarovaný příkazu) a druhý, zda určuje projekt je to možné (je menší než počet projektů v řešení).  
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="setting-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>Nastavení balíčku VSPackage pro načtení pouze při řešení obsahuje více projektů  
 Protože **nastavte projekt po spuštění** příkaz nedává smysl, pokud aktivního řešení neobsahuje více než jeden projekt, můžete nastavit vašeho balíčku VSPackage pro automatické načtení pouze v tom případě. Použijete <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> spolu s kontextu uživatelského rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. V souboru DynamicMenuPackage.cs přidejte do třídy DynamicMenuPackage následující atributy:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## <a name="testing-the-set-startup-project-command"></a>Testování nastavte projekt po spuštění příkazu  
 Nyní můžete otestovat kód.  
  
1.  Sestavte projekt a spusťte ladění. Experimentální instanci aplikace by se zobrazit.  
  
2.  V experimentální instanci aplikace otevřete řešení, která má více než jeden projekt.  
  
     Zobrazí se ikona šipky na **Průzkumníka řešení** nástrojů. Když ho rozbalíte, by se zobrazit položky nabídky, které představují různé projekty v řešení.  
  
3.  Při kontrole projektů bude projekt po spuštění.  
  
4.  Při zavření řešení, nebo otevřete řešení, která má pouze jeden projekt, na panelu nástrojů ikonu by měla zmizet.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)

