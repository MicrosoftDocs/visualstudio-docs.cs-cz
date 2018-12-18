---
title: Správa projektů univerzálních Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d4039b3d22206afb292e90d46608decd2cfa96a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930229"
---
# <a name="manage-universal-windows-projects"></a>Spravovat projekty pro Universal Windows
Univerzální aplikace pro Windows jsou aplikace, které se zaměřují na Windows 8.1 a Windows Phone 8.1, umožňuje vývojářům používat kód a další prostředky na obě platformy. Sdílený kód a prostředky se ukládají do sdíleného projektu, zatímco kód specifický pro platformu a prostředky jsou uloženy v samostatné projekty, jeden pro Windows a druhou pro Windows Phone. Další informace o univerzálních aplikací pro Windows najdete v tématu [Universal Windows apps](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Rozšíření sady Visual Studio, které spravují projekty je třeba si uvědomit, že projekty univerzálních aplikací pro Windows mají strukturu, která se liší od aplikace jednu platformu. Tento návod ukazuje, jak procházet sdíleného projektu a správě sdílených položek.  

## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  

### <a name="navigate-the-shared-project"></a>Přejděte sdílený projekt  

1.  Vytvořte projekt VSIX C# s názvem **TestUniversalProject**. (**Souboru** > **nové** > **projektu** a potom **jazyka C#**  >   **Rozšiřitelnost** > **balíčku sady Visual Studio**). Přidat **vlastního příkazu** šablony položky projektu (na **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **nová položka** , pak přejděte na **rozšiřitelnost**). Název souboru **TestUniversalProject**.  

2.  Přidejte odkaz na *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* a *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (v **rozšíření** části).  

3.  Otevřít *TestUniversalProject.cs* a přidejte následující `using` příkazy:  

    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.Internal.VisualStudio.PlatformUI;   
    using System.Collections.Generic;   
    using System.IO;  
    using System.Windows.Forms;  
    ```  

4.  V `TestUniversalProject` třídy přidat soukromé pole odkazující **výstup** okna.  

    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  

5.  Nastavení odkazu na podokno výstup uvnitř TestUniversalProject konstruktor:  

    ```csharp  
    private TestUniversalProject(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  

        this.package = package;  

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
        // get a reference to the Output window  
                    output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));  
    }  
    ```  

6.  Odebrat z existujícího kódu `ShowMessageBox` metody:  

    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  

7.  Získáte objekt DTE, který budeme používat v tomto návodu několika různým účelům. Také ujistěte se, že je načtené řešení, když dojde ke kliknutí na tlačítko nabídky.  

    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {   
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));  
        if (dte.Solution != null)   
        {  
            . . .  
        }  
        else   
        {  
            MessageBox.Show("No solution is open");  
            return;   
        }  
    }  
    ```  

8.  Najdete sdíleného projektu. Sdílený projekt je čistě kontejneru; nepodporuje sestavení ani vytvářet výstupy. Následující metoda vyhledá první sdíleného projektu v řešení tím, že hledají <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objekt, který má schopnost sdíleného projektu.  

    ```csharp  
    private IVsHierarchy FindSharedProject()  
    {  
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));  
        Guid empty = Guid.Empty;  
        IEnumHierarchies enumHiers;  

        //get all the projects in the solution  
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));  
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))  
        {  
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))  
            {  
                return hier;  
            }  
        }  
        return null;  
    }  
    ```  

9. V `ShowMessageBox` metody výstup titulek (název projektu, který se zobrazí **Průzkumníku řešení**) sdíleného projektu.  

    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  

        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
                }  
        else  
        {  
            MessageBox.Show("No solution is open");  
            return;  
        }  
    }  
    ```  

10. Získání projektu aktivní platformu. Platforma projekty jsou projekty, které obsahují kód specifický pro platformu a prostředky. Následující metoda používá nové pole <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> se získat projekt aktivní platformu.  

    ```csharp  
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)  
    {  
        IVsHierarchy activeProjectContext;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))  
        {  
            return activeProjectContext;  
        }  
        else  
        {  
            return null;  
        }  
    }  
    ```  

11. V `ShowMessageBox` metody výstup titulek aktivní platformu projektu.  

    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  

        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));  

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);  
                if (activePlatformHier != null)  
                {  
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,  
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);  
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));  
                }  
                else  
                {  
                MessageBox.Show("Shared project has no active platform project");  
                }  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
        }  
        else  
            {  
                MessageBox.Show("No solution is open");  
                return;  
            }  
        }  

    ```  

12. Iterujte přes projekty platformy. Následující metoda získá všechny importu projektů (platforma) ze sdíleného projektu.  

    ```csharp  
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)  
    {  
        IVsSharedAssetsProject sharedAssetsProject;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)  
            && sharedAssetsProject != null)  
        {  
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())  
            {  
                yield return importingProject;  
            }  
        }  
    }  
    ```  

    > [!IMPORTANT]
    >  Pokud uživatel otevřel v experimentální instanci projektu aplikace C++ universal Windows, kódu výše vyvolá výjimku. Jedná se o známý problém. Chcete-li zabránit výjimku, nahraďte `foreach` blokovat nad následujícím kódem:  

    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  

13. V `ShowMessageBox` výstupní metoda, titulek každého projektu platformy. Vložte následující kód za řádkem, jejichž výstupem jsou titulek aktivní platformu projektu. V tomto seznamu se zobrazí pouze projekty platformy, které jsou načteny.  

    ```csharp  
    output.OutputStringThreadSafe("Platform projects:\n");  

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);  

    bool isActiveProjectSet = false;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
    }  
    ```  

14. Změňte aktivní platformu projektu. Následující metoda nastaví aktivní projekt pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  

    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  

15. V `ShowMessageBox` metody změnit aktivní platformu projektu. Vložte tento kód uvnitř `foreach` bloku.  

    ```csharp  
    bool isActiveProjectSet = false;  
    string platformCaption = null;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  

        // if this project is neither the shared project nor the current active platform project,   
        // set it to be the active project  
        if (!isActiveProjectSet && platformHier != activePlatformHier)  
        {  
            this.SetActiveProjectContext(sharedHier, platformHier);  
            activePlatformHier = platformHier;  
            isActiveProjectSet = true;  
        }  
    }  
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');  
    ```  

16. Nyní vyzkoušejte. Stisknutím klávesy F5 spusťte experimentální instanci aplikace. Vytvoření projektu aplikace pro univerzální centra C# v experimentální instanci aplikace (v **nový projekt** dialogovém okně **Visual C#** > **Windows**  >   **Windows 8** > **univerzální** > **aplikace rozcestníku**). Po načtení řešení, přejděte na **nástroje** nabídky a klikněte na tlačítko **vyvolat TestUniversalProject**a vrátit se změnami text **výstup** podokně. By měl vypadat přibližně takto:  

    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  

### <a name="manage-the-shared-items-in-the-platform-project"></a>Správa sdílených položek v projektu platformy  

1.  Najdete sdílené položky v projektu platformy. Položky ve sdíleném projektu se zobrazí v projektu platformy jako sdílené položky. Nelze zobrazit, je **Průzkumníku řešení**, ale můžete procházet hierarchii projektu je vyhledat. Následující metoda provede hierarchii a shromažďuje všechny sdílené položky. Volitelně vypíše titulek každé položky. Sdílené položky jsou označeny novou vlastnost <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.  

    ```csharp  
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)  
    {  
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);  
        if (printItems)  
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));  

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items  
        bool isSharedItem;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)  
            && (isSharedItem == getSharedItems))  
        {  
            itemIds.Add(itemid);  
        }  

        uint child;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)  
            && child != (uint)VSConstants.VSITEMID.Nil)  
        {  
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)  
                && child != (uint)VSConstants.VSITEMID.Nil)  
            {  
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
            }  
                    }  
    }  
    ```  

2.  V `ShowMessageBox` metodu, přidejte následující kód, který vás položky hierarchie projektu platformy. Vložit jej `foreach` bloku.  

    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  

3.  Čtení sdílené položky. Sdílené položky se zobrazí v projektu platformy jako skryté propojené soubory a může číst všechny vlastnosti jako běžný propojené soubory. Následující kód načte úplnou cestu první sdílené položky.  

    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  

4.  Nyní vyzkoušejte. Stisknutím klávesy **F5** spustit experimentální instanci aplikace. Vytvoření C# projekt aplikace pro univerzální centra v experimentální instanci aplikace (v **nový projekt** dialogovém okně **Visual C#**   >  **Windows**  >  **Windows 8** > **univerzální** > **aplikace rozcestníku**) přejděte **nástroje** nabídky a klikněte na tlačítko  **Vyvolání TestUniversalProject**a vrátit se změnami text **výstup** podokně. By měl vypadat přibližně takto:  

    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    Walk the active platform project:  
        HubApp.WindowsPhone  
            <HubApp.Shared>  
                App.xaml  
                    App.xaml.cs  
                Assets  
                    DarkGray.png  
                    LightGray.png  
                    MediumGray.png  
                Common  
                    NavigationHelper.cs  
                    ObservableDictionary.cs  
                    RelayCommand.cs  
                    SuspensionManager.cs  
                DataModel  
                    SampleData.json  
                    SampleDataSource.cs  
                HubApp.Shared.projitems  
                Strings  
                    en-US  
                        Resources.resw  
            Assets  
                HubBackground.theme-dark.png  
                HubBackground.theme-light.png  
                Logo.scale-240.png  
                SmallLogo.scale-240.png  
                SplashScreen.scale-240.png  
                Square71x71Logo.scale-240.png  
                StoreLogo.scale-240.png  
                WideLogo.scale-240.png  
            HubPage.xaml  
                HubPage.xaml.cs  
            ItemPage.xaml  
                ItemPage.xaml.cs  
            Package.appxmanifest  
            Properties  
                AssemblyInfo.cs  
            References  
                .NET for Windows Store apps  
                HubApp.Shared  
                Windows Phone 8.1  
            SectionPage.xaml  
                SectionPage.xaml.cs  
    ```  

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Zjištění změn v projektech platformy a sdílené projekty  

1. Události hierarchie a projektu můžete použít ke zjištění změny ve sdílených projektech, stejně jako u projektů platformy. Nicméně položky projektu ve sdíleném projektu nejsou viditelné, což znamená, že některé události neaktivuje při změně položky sdíleného projektu.  

    Vezměte v úvahu posloupnost událostí při přejmenování souboru v projektu:  

   1. Název souboru se změní na disku.  

   2. Soubor projektu je aktualizován pro vložení nového názvu souboru.  

      Hierarchie událostí (například <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) obecně sledovat změny zobrazí v uživatelském rozhraní, jako v **Průzkumníka řešení**. Událostem hierarchie Zvažte operaci přejmenovat soubor sestává z odstranění souboru a pak přidání souboru. Ale když neviditelné položky budou změněny, systém hierarchii událostí aktivuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> události, ale ne <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> událostí. Proto Pokud přejmenujete soubor projektu pro platformy, můžete získat i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, ale Pokud přejmenujete soubor ve sdíleném projektu, můžete získat pouze <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.  

      Ke sledování změn v položkách projektu, můžete zpracovávat události položky projektu DTE (těm, které jsou součástí <xref:EnvDTE.ProjectItemsEventsClass>). Ale pokud se zpracování velkého počtu událostí, můžete získat lepší výkon zpracování událostí v <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. V tomto názorném postupu vám ukážeme pouze hierarchie události a události DTE. V tomto postupu přidáte do sdíleného projektu a projekt platformy naslouchací proces událostí. Potom při přejmenování jeden soubor ve sdíleném projektu a další soubor v projektu platformy, se zobrazí události, které jsou aktivovány pro jednotlivé operace přejmenování.  

      V tomto postupu přidáte do sdíleného projektu a projekt platformy naslouchací proces událostí. Potom při přejmenování jeden soubor ve sdíleném projektu a další soubor v projektu platformy, se zobrazí události, které jsou aktivovány pro jednotlivé operace přejmenování.  

2. Přidáte naslouchací proces událostí. Přidejte nový soubor třídy do projektu a jeho volání *HierarchyEventListener.cs*.  

3. Otevřít *HierarchyEventListener.cs* soubor a přidejte následující příkazy using:  

   ```csharp  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio;  
   using System.IO;  

   ```  

4. Máte `HierarchyEventListener` implementaci třídy <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  

   ```csharp  
   class HierarchyEventListener : IVsHierarchyEvents  
   { }  

   ```  

5. Implementovat členy <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, jako v následujícím kódu.  

   ```csharp  
   class HierarchyEventListener : IVsHierarchyEvents  
   {  
       private IVsHierarchy hierarchy;  
       IVsOutputWindowPane output;   

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {  
            this.hierarchy = hierarchy;  
            this.output = outputWindow;  
       }  

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {  
           return VSConstants.S_OK;  
       }  

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {  
           return VSConstants.S_OK;  
       }  

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {  
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");  
           return VSConstants.S_OK;  
       }  

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {  
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");  
           return VSConstants.S_OK;  
       }  

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {  
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");  
           return VSConstants.S_OK;  
       }  

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {  
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");  
           return VSConstants.S_OK;  
       }  
   }  

   ```  

6. Ve stejné třídě, přidat další obslužné rutiny události pro událost DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, která vyvolá se při každém přejmenování položky projektu.  

   ```csharp  
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
   {  
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
   }  
   ```  

7. Registrace k událostem hierarchie. Budete muset zaregistrovat samostatně pro každý projekt, které sledujete. Přidejte následující kód do `ShowMessageBox`, jeden pro sdílený projekt a druhou pro jeden z projektů platformy.  

   ```csharp  
   // hook up the event listener for hierarchy events on the shared project  
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);  
   uint cookie1;  
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);  

   // hook up the event listener for hierarchy events on the   
   active project  
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);  
   uint cookie2;  
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);  
   ```  

8. Zaregistrujte si událost položky projektu DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. Po připojení druhé naslouchací proces, přidejte následující kód.  

   ```csharp  
   // hook up DTE events for project items  
   Events2 dteEvents = (Events2)dte.Events;  
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  

   ```  

9. Změna sdílené položky. Nelze změnit sdílené položky v projektu platformy. Místo toho je třeba upravit ve sdíleném projektu, který je vlastníkem skutečné z těchto položek. Můžete získat ID odpovídající položky ve sdíleném projektu s <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, poskytují úplnou cestu sdílené položky. Potom můžete upravit sdílené položky. Pro projekty, které platformy jsou příslušné změny distribuovány.  

    > [!IMPORTANT]
    >  Měli byste najít položku projektu určuje, jestli je sdílené položky před změnou ho.  

     Následující metoda upraví název souboru položky projektu.  

    ```csharp  
    private void ModifyFileNameInProject(IVsHierarchy project, string path)  
    {    
        int found;  
        uint projectItemID;  
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];  
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))  
            && found != 0)  
        {  
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);  
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);  
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));  
        }  
    }  
    ```  

10. Tuto metodu volat po všech jiný kód v `ShowMessageBox` změnit název souboru položky ve sdíleném projektu. Vložte tento kód, který získá úplnou cestu položky ve sdíleném projektu.  

    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  

11. Sestavte a spusťte projekt. Vytvoření univerzální centra aplikace C# v experimentální instanci aplikace, přejděte na **nástroje** nabídky a klikněte na tlačítko **vyvolat TestUniversalProject**a zkontrolujte text v podokně výstupů Obecné. Název první položky ve sdíleném projektu (Očekáváme, že bude *App.xaml* souboru) by měla být změněna, a měli byste vidět, který <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> byla aktivována událost. V takovém případě od přejmenování *App.xaml* způsobí, že *App.xaml.cs* Pokud chcete také přejmenovat, měli byste vidět čtyři události (dvě pro každou platformu projektu). (DTE událostí sledování není položek ve sdíleném projektu.) Měli byste vidět dvě <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> události (jeden pro každou platformu projektů), ale ne <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> události.  

12. Teď si vyzkoušejte přejmenování souboru v projektu platformy a uvidíte rozdíl v události, které vzplaňte. Přidejte následující kód do `ShowMessageBox` po volání `ModifyFileName`.  

    ```csharp  
    // change the file name of an item in a platform project  
    var unsharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);  

    var unsharedItemId = unsharedItemIds[0];  
    string unsharedPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));  
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));  

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);  
    ```  

13. Sestavte a spusťte projekt. Vytvořte univerzální projekt C# v experimentální instanci aplikace, přejděte na **nástroje** nabídky a klikněte na tlačítko **vyvolat TestUniversalProject**a zkontrolujte text v podokně výstupů Obecné. Po přejmenování souboru v projektu platformy, měli byste vidět i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> událostí a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> událostí. Protože změna souboru způsobila žádné další soubory změnit a od změny položek projektu pro platformy není získat rozšíří kdekoli, je pouze jeden každý z těchto událostí.
