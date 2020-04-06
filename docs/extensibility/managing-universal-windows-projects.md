---
title: Správa univerzálních projektů Systému Windows | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbbf9b6aaf983bb36291611a7b9b50f7886915b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702690"
---
# <a name="manage-universal-windows-projects"></a>Správa univerzálních projektů systému Windows

Univerzální aplikace pro Windows jsou aplikace, které cílí na Windows 8.1 i Windows Phone 8.1 a umožňují vývojářům používat kód a další datové zdroje na obou platformách. Sdílený kód a prostředky jsou uloženy ve sdíleném projektu, zatímco kód a prostředky specifické pro platformu jsou uloženy v samostatných projektech, jeden pro Windows a druhý pro Windows Phone. Další informace o univerzálních aplikacích pro Windows najdete [v tématu Univerzální aplikace pro Windows](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Rozšíření Sady Visual Studio, která spravují projekty, by si měla být vědoma toho, že projekty univerzálních aplikací pro Windows mají strukturu, která se liší od aplikací s jednou platformou. Tento návod ukazuje, jak procházet sdílený projekt a spravovat sdílené položky.

## <a name="prerequisites"></a>Požadavky

Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="navigate-the-shared-project"></a>Navigace ve sdíleném projektu

1. Vytvořte projekt C# VSIX s názvem **TestUniversalProject**. (File**File** > **New** > **Project** a potom **C#** > **Rozšiřitelnost** > Visual Studio**balíček).** Přidejte šablonu položky projektu **vlastní příkaz** (v **Průzkumníku řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte **Přidat** > **novou položku**a pak přejděte na **Rozšiřitelnost).** Pojmenujte soubor **TestUniversalProject**.

2. Přidejte odkaz na *microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* a *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (v části **Rozšíření).**

3. Otevřete *TestUniversalProject.cs* a `using` přidejte následující direktivy:

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

4. Ve `TestUniversalProject` třídě přidejte soukromé pole směřující do okna **Výstup.**

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Nastavte odkaz na výstupní podokno uvnitř konstruktoru TestUniversalProject:

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

6. Odeberte existující `ShowMessageBox` kód z metody:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Získejte DTE objekt, který budeme používat pro několik různých účelů v tomto návodu. Také se ujistěte, že řešení je načten po klepnutí na tlačítko nabídky.

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

8. Najděte sdílený projekt. Sdílený projekt je čistý kontejner; nevytváří ani nevytváří výstupy. Následující metoda vyhledá první sdílený projekt v řešení <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> vyhledání objektu, který má sdílené projektschopnosti.

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

9. V `ShowMessageBox` metodě nakonto titulek (název projektu, který se zobrazí v **Průzkumníku řešení)** sdíleného projektu.

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

10. Získejte aktivní projekt platformy. Projekty platformy jsou projekty, které obsahují kód a prostředky specifické pro platformu. Následující metoda používá nové <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> pole k získání aktivního projektu platformy.

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

11. V `ShowMessageBox` metodě vyjáděte titulek projektu aktivní platformy.

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
    }
    ```

12. Iterate prostřednictvím projektů platformy. Následující metoda získá všechny importující (platforma) projekty ze sdíleného projektu.

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
    > Pokud uživatel otevřel projekt aplikace pro univerzální Windows pro Systém Windows v experimentální instanci, výše uvedený kód vyvolá výjimku. Jedná se o známý problém. Chcete-li se vyhnout `foreach` výjimce, nahraďte výše uvedený blok následujícím:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. V `ShowMessageBox` metodě výstup titulek každého projektu platformy. Za řádek, který vyvádí titulek aktivního projektu platformy, vložte následující kód. V tomto seznamu se zobrazí pouze projekty platformy, které jsou načteny.

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

14. Změňte projekt aktivní platformy. Následující metoda nastaví aktivní <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>projekt pomocí .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. V `ShowMessageBox` metodě změňte projekt aktivní platformy. Vložte tento `foreach` kód do bloku.

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

16. Teď to vyzkoušejte. Stisknutím klávesy F5 spusťte experimentální instanci. Vytvořte projekt univerzální aplikace jazyka C# v experimentální instanci (v dialogovém okně **Nový projekt** **Visual C#** > **Windows** > **Windows 8** > **Universal** > **Hub App).** Po načtení řešení přejděte do nabídky **Nástroje** a klepněte na **tlačítko Vyvolat testUniversalProject**a potom zkontrolujte text v podokně **Výstup.** Mělo by se zobrazit něco podobného:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Správa sdílených položek v projektu platformy

1. Najděte sdílené položky v projektu platformy. Položky ve sdíleném projektu se zobrazí v projektu platformy jako sdílené položky. V **Průzkumníku řešení**je nevidíte , ale můžete je najít v hierarchii projektu. Následující metoda prochází hierarchii a shromažďuje všechny sdílené položky. Volitelně výstupy titulek každé položky,. Sdílené položky jsou identifikovány <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem>novou vlastností .

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

2. V `ShowMessageBox` metodě přidejte následující kód pro zobrazení hierarchie projektu platformy. Vložte jej `foreach` do bloku.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Přečtěte si sdílené položky. Sdílené položky se v projektu platformy zobrazí jako skryté propojené soubory a všechny vlastnosti můžete číst jako běžné propojené soubory. Následující kód přečte úplnou cestu první sdílené položky.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Teď to vyzkoušejte. Stisknutím **klávesy F5** spusťte experimentální instanci. Vytvořte projekt univerzální aplikace jazyka C# v experimentální instanci (v dialogovém okně **Nový projekt** **Visual C#** > **Windows** > **Windows 8** > **Universal** > **Hub App**) přejděte do nabídky **Nástroje** a klepněte na tlačítko **Vyvolat TestUniversalProject**a pak zkontrolujte text v podokně **Výstup.** Mělo by se zobrazit něco podobného:

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

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Zjišťování změn v projektech platformy a sdílených projektech

1. Události hierarchie a projektu můžete použít ke zjišťování změn ve sdílených projektech, stejně jako u projektů platformy. Položky projektu ve sdíleném projektu však nejsou viditelné, což znamená, že některé události nejsou požární při změně sdílené položky projektu.

    Zvažte posloupnost událostí při přejmenování souboru v projektu:

   1. Název souboru se změní na disku.

   2. Soubor projektu je aktualizován tak, aby zahrnoval nový název souboru.

      Události hierarchie (například <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) obvykle sledují změny zobrazené v unovém rozhraní, jako v **Průzkumníku řešení**. Události hierarchie považují operaci přejmenování souboru za skládající se z odstranění souboru a přidání souboru. Při změně neviditelných položek však systém <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> událostí hierarchie vyvolá událost, ale nikoli <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> událost. Proto pokud přejmenujete soubor v projektu platformy, získáte oba <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, ale pokud přejmenujete <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>soubor ve sdíleném projektu, získáte pouze .

      Chcete-li sledovat změny v položkách projektu, můžete zpracovat <xref:EnvDTE.ProjectItemsEventsClass>události položky projektu DTE (ty, které se nacházejí v ). Pokud však zpracováváte velký počet událostí, můžete získat lepší <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>výkon zpracování událostí v . V tomto návodu zobrazíme pouze události hierarchie a události DTE. V tomto postupu přidáte posluchače událostí do sdíleného projektu a projektu platformy. Potom při přejmenování jednoho souboru ve sdíleném projektu a jiný soubor v projektu platformy, můžete zobrazit události, které jsou aktivovány pro každou operaci přejmenování.

      V tomto postupu přidáte posluchače událostí do sdíleného projektu a projektu platformy. Potom při přejmenování jednoho souboru ve sdíleném projektu a jiný soubor v projektu platformy, můžete zobrazit události, které jsou aktivovány pro každou operaci přejmenování.

2. Přidejte posluchače události. Přidejte do projektu nový soubor třídy a nazvěte jej *HierarchyEventListener.cs*.

3. Otevřete soubor *HierarchyEventListener.cs* a přidejte následující příkazy pomocí direktiv:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. Mají `HierarchyEventListener` třídy <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>implementovat :

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Implementujte členy <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>písmene , jako v níže uvedeném kódu.

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

6. Ve stejné třídě přidejte další obslužnou rutinu události pro událost <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>DTE , ke které dochází při každém přejmenování položky projektu.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Zaregistrujte se k událostem hierarchie. Musíte se zaregistrovat samostatně pro každý projekt, který sledujete. Přidejte následující `ShowMessageBox`kód v , jeden pro sdílený projekt a druhý pro jeden z projektů platformy.

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

8. Zaregistrujte se na akci <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>položky projektu DTE . Přidejte následující kód po připojení druhého naslouchací proces.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Upravte sdílenou položku. Sdílené položky v projektu platformy nelze upravovat. místo toho je nutné upravit ve sdíleném projektu, který je skutečným vlastníkem těchto položek. Můžete získat odpovídající ID položky ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>sdíleném projektu s , která mu poskytuje úplnou cestu sdílené položky. Poté můžete upravit sdílenou položku. Změna je šířena do projektů platformy.

    > [!IMPORTANT]
    > Měli byste zjistit, zda položka projektu je sdílená položka před úpravou.

     Následující metoda upravuje název souboru položky projektu.

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

10. Volání této metody po všech `ShowMessageBox` ostatních kód v změnit název souboru položky ve sdíleném projektu. Vložte tento po kód, který získá úplnou cestu položky ve sdíleném projektu.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Sestavení a spuštění projektu. Vytvořte aplikaci univerzálního rozbočovače Jazyka C# v experimentální instanci, přejděte do nabídky **Nástroje** a klepněte na **tlačítko Vyvolat TestUniversalProject**a zkontrolujte text v obecném výstupním podokně. Název první položky ve sdíleném projektu (očekáváme, že bude soubor *App.xaml)* by <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> měla být změněna a měli byste vidět, že událost byla aktivována. V tomto případě od přejmenování *App.xaml* *způsobí, že App.xaml.cs* přejmenovat také, měli byste vidět čtyři události (dva pro každý projekt platformy). (Události DTE nesledují položky ve sdíleném projektu.) Měli byste <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> vidět dvě události (jeden pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> každý projekty platformy), ale žádné události.

12. Nyní zkuste přejmenovat soubor v projektu platformy a můžete vidět rozdíl v událostech, které se vyhodí. Přidejte následující `ShowMessageBox` kód po `ModifyFileName`volání do .

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

13. Sestavení a spuštění projektu. Vytvořte univerzální projekt jazyka C# v experimentální instanci, přejděte do nabídky **Nástroje** a klepněte na **tlačítko Vyvolat testUniversalProject**a zkontrolujte text v podokně obecného výstupu. Po přejmenování souboru v projektu platformy byste <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> měli <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> vidět událost i událost. Vzhledem k tomu, že změna souboru nezpůsobila změnu žádných dalších souborů a protože změny položek v projektu platformy se nikde nešíří, je pouze jedna z těchto událostí.
