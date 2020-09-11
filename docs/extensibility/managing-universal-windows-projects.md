---
title: Správa univerzálních projektů Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83e3b07bc3373070953709ffe913f37529e74bc7
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012305"
---
# <a name="manage-universal-windows-projects"></a>Správa univerzálních projektů pro Windows

Univerzální aplikace pro Windows jsou aplikace, které cílí na Windows 8.1 i Windows Phone 8,1 a umožňují vývojářům používat kód a další prostředky na obou platformách. Sdílený kód a prostředky jsou uchovávány ve sdíleném projektu, zatímco kód specifický pro platformu a prostředky jsou uchovávány v samostatných projektech, jeden pro systém Windows a druhý pro Windows Phone. Další informace o univerzálních aplikacích pro Windows najdete v tématu [univerzální aplikace pro Windows](/windows/uwp/get-started/create-uwp-apps). Rozšíření sady Visual Studio, která spravují projekty, by měla vědět, že projekty univerzálních aplikací pro Windows mají strukturu, která se liší od aplikací pro jednotlivé platformy. Tento návod ukazuje, jak navigovat sdílený projekt a spravovat sdílené položky.

## <a name="prerequisites"></a>Předpoklady

Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="navigate-the-shared-project"></a>Přejít na sdílený projekt

1. Vytvořte projekt VSIX v jazyce C# s názvem **TestUniversalProject**. (**Soubor**  >  **Nové**  >  **Projekt** a potom **C#**  >  **rozšiřitelný**  >  **balíček sady Visual Studio**v jazyce C#). Přidejte šablonu položky projektu **vlastního příkazu** (na **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte **Přidat**  >  **novou položku**a pak přejít na **rozšiřitelnost**). Název souboru **TestUniversalProject**.

2. Přidejte odkaz na *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* a *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (v části **rozšíření** ).

3. Otevřete *TestUniversalProject.cs* a přidejte následující `using` direktivy:

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

4. Ve `TestUniversalProject` třídě přidejte soukromé pole, které odkazuje na **výstupní** okno.

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Nastavte odkaz na podokno výstup uvnitř konstruktoru TestUniversalProject:

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

6. Odeberte existující kód z `ShowMessageBox` metody:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Získejte objekt DTE, který použijeme pro několik různých účelů v tomto návodu. Také se ujistěte, že je po kliknutí na tlačítko nabídky načteno řešení.

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

8. Vyhledejte sdílený projekt. Sdílený projekt je čistě kontejner; nevytváří ani nevytváří výstupy. Následující metoda najde první sdílený projekt v řešení hledáním <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objektu, který má schopnost sdíleného projektu.

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

9. V `ShowMessageBox` metodě výstup titulku (název projektu, který se zobrazí v **Průzkumník řešení**) sdíleného projektu.

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

10. Získejte projekt aktivní platformy. Projekty platformy jsou projekty, které obsahují kód specifický pro platformu a prostředky. Následující metoda používá nové pole <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> pro získání projektu aktivní platformy.

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

11. V `ShowMessageBox` metodě je výstupem titulku projektu aktivní platformy.

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
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
        }
    }
    ```

12. Iterujte v projektech platformy. Následující metoda získá všechny projekty import (platforma) ze sdíleného projektu.

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
    > Pokud uživatel otevřel projekt C++ Universal Windows App v experimentální instanci, kód výše vyvolá výjimku. Jedná se o známý problém. Chcete-li se vyhnout výjimce, nahraďte `foreach` blok výše následujícím způsobem:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. V `ShowMessageBox` metodě výstup titulku jednotlivých projektů platformy. Vložte následující kód za řádek, který vytvoří výstup popisku projektu aktivní platformy. V tomto seznamu se zobrazí pouze projekty platformy, které jsou načteny.

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

14. Změňte projekt aktivní platformy. Následující metoda nastaví aktivní projekt pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A> .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. V `ShowMessageBox` metodě změňte projekt aktivní platformy. Vložte tento kód do `foreach` bloku.

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

16. Nyní to vyzkoušejte. Stiskněte klávesu F5 ke spuštění experimentální instance. Vytvoření projektu aplikace univerzálního středu v jazyce C# v experimentální instanci (v dialogovém okně **Nový projekt** , aplikace pro univerzální centrum **Visual C#**  >  **Windows**  >  **8**  >  **Universal**  >  **Hub App**). Po načtení řešení přejděte do nabídky **nástroje** , klikněte na **vyvolat TestUniversalProject**a pak zkontrolujte text v podokně **výstup** . Mělo by se zobrazit něco podobného:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Správa sdílených položek v projektu platformy

1. Vyhledejte sdílené položky v projektu platformy. Položky ve sdíleném projektu se zobrazí v projektu platformy jako sdílené položky. Nevidíte je v **Průzkumník řešení**, ale můžete se podívat na hierarchii projektu, abyste je našli. Následující metoda provede hierarchii a shromáždí všechny sdílené položky. Volitelně vytvoří výstup titulků každé položky,. Sdílené položky jsou identifikovány novou vlastností <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem> .

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

2. V `ShowMessageBox` metodě přidejte následující kód, který bude procházet položky hierarchie projektu platformy. Vložte ho do `foreach` bloku.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Přečtěte si sdílené položky. Sdílené položky se zobrazí v projektu platformy jako skryté propojené soubory a všechny vlastnosti můžete číst jako běžné propojené soubory. Následující kód přečte úplnou cestu první sdílené položky.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Nyní to vyzkoušejte. Stiskněte klávesu **F5** ke spuštění experimentální instance. Vytvoření projektu aplikace univerzálního centra v C# v experimentální instanci (v dialogovém okně **Nový projekt** **,**  >  aplikace Universal hub v**systému Windows**  >  **Windows 8**  >  **Universal**  >  **Hub App**) přejděte do nabídky **nástroje** a klikněte na **vyvolat TestUniversalProject**a pak zkontrolujte text v podokně **výstup** . Mělo by se zobrazit něco podobného:

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

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Detekce změn v projektech platforem a sdílených projektech

1. Můžete použít události hierarchie a projektu k detekci změn ve sdílených projektech, stejně jako u projektů platforem. Položky projektu ve sdíleném projektu nejsou viditelné, což znamená, že některé události se neaktivují při změně sdílených položek projektu.

    Vzít v úvahu sekvenci událostí při přejmenování souboru v projektu:

   1. Název souboru se změnil na disku.

   2. Soubor projektu je aktualizován tak, aby obsahoval nový název souboru.

      Události hierarchie (například <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> ) obecně sledují změny zobrazené v uživatelském rozhraní, jako v **Průzkumník řešení**. Události hierarchie berou v úvahu operaci přejmenování souboru, která se skládá z odstranění souboru a pak přidáním souboru. Pokud však dojde ke změně neviditelných položek, systém událostí v hierarchii vyvolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> událost, ale ne <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> událost. Proto Pokud přejmenujete soubor v projektu platformy, získáte obojí <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> , ale pokud soubor přejmenujete do sdíleného projektu, získáte pouze <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> .

      Chcete-li sledovat změny v položkách projektu, můžete zpracovávat události položek projektu DTE (ty se nacházejí v <xref:EnvDTE.ProjectItemsEventsClass> ). Pokud však zpracováváte velký počet událostí, můžete získat lepší výkon při zpracování událostí v nástroji <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> . V tomto návodu zobrazujeme jenom události hierarchie a události DTE. V tomto postupu přidáte naslouchací proces událostí do sdíleného projektu a projektu platformy. Pak při přejmenování jednoho souboru ve sdíleném projektu a jiném souboru v projektu platformy můžete zobrazit události, které jsou aktivovány pro každou operaci přejmenování.

      V tomto postupu přidáte naslouchací proces událostí do sdíleného projektu a projektu platformy. Pak při přejmenování jednoho souboru ve sdíleném projektu a jiném souboru v projektu platformy můžete zobrazit události, které jsou aktivovány pro každou operaci přejmenování.

2. Přidejte naslouchací proces událostí. Přidejte do projektu nový soubor třídy a zavolejte ho *HierarchyEventListener.cs*.

3. Otevřete soubor *HierarchyEventListener.cs* a přidejte následující direktivy using:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. Musí `HierarchyEventListener` implementovat třídu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> :

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Implementujte členy <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> , jako v následujícím kódu.

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

6. Ve stejné třídě přidejte další obslužnou rutinu události pro událost DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> , ke které dojde při každém přejmenování položky projektu.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Zaregistrujte se do událostí hierarchie. Musíte se zaregistrovat samostatně pro každý projekt, který sledujete. Přidejte následující kód do `ShowMessageBox` , jeden pro sdílený projekt a druhý pro jeden z projektů platformy.

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

8. Zaregistrujte se do události položky projektu DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> . Po zapojování druhého naslouchacího procesu přidejte následující kód.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Upravte sdílenou položku. V projektu platformy nemůžete upravovat sdílené položky; místo toho je třeba je upravit ve sdíleném projektu, který je skutečným vlastníkem těchto položek. Můžete získat ID odpovídající položky ve sdíleném projektu s <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> a poskytnout tak úplnou cestu sdílené položky. Pak můžete sdílenou položku Upravit. Tato změna se rozšíří na projekty platformy.

    > [!IMPORTANT]
    > Před úpravou je třeba zjistit, zda je položka projektu sdílenou položkou.

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

10. Tuto metodu volejte za všechny ostatní kódy v `ShowMessageBox` pro úpravu názvu souboru položky ve sdíleném projektu. Vložte tento kód po kódu, který získá úplnou cestu položky ve sdíleném projektu.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Sestavte a spusťte projekt. V experimentální instanci vytvořte aplikaci univerzálního centra C#, přejděte do nabídky **nástroje** , klikněte na **vyvolat TestUniversalProject**a zaškrtněte text v podokně obecné výstup. Název první položky ve sdíleném projektu (očekáváme, že se jedná o soubor *App. XAML* ), který by měl být změněn a měla by se zobrazit, že <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> událost byla vyvolána. V takovém případě, protože přejmenování *App. XAML* způsobí, že se přejmenuje *App.XAML.cs* , měli byste vidět čtyři události (dvě pro každý projekt platformy). (Události DTE nesleduje položky ve sdíleném projektu.) Měly by se zobrazit dvě <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> události (jeden pro každý projekt platformy), ale žádné <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> události.

12. Nyní se pokuste přejmenovat soubor v projektu platformy a v událostech, které se aktivují, můžete zobrazit rozdíl. `ShowMessageBox`Po volání metody přidejte následující kód `ModifyFileName` .

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

13. Sestavte a spusťte projekt. V experimentální instanci vytvořte univerzální projekt C#, přejděte do nabídky **nástroje** , klikněte na **vyvolat TestUniversalProject**a zaškrtněte text v podokně obecné výstup. Po přejmenování souboru v projektu platformy by se měla zobrazit <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> událost a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> událost. Vzhledem k tomu, že změna souboru nezpůsobila změnu žádné jiné soubory a vzhledem k tomu, že se změny položek v projektu platformy nerozšíří odkudkoli, je k dispozici pouze jedna z těchto událostí.