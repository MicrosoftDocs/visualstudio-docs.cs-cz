---
title: Zachování vlastnosti položky projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4adcf0f5c5770f5d3ffc0e0ed9bffdb108869c7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795282"
---
# <a name="persisting-the-property-of-a-project-item"></a>Trvalé uložení vlastnosti položky projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možná budete chtít zachovat vlastnost, kterou přidáte do položky projektu, jako je například autor zdrojového souboru. To lze provést uložením vlastnosti do souboru projektu.  
  
 Prvním krokem pro zachování vlastnosti v souboru projektu je získat hierarchii projektu jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozhraní. Toto rozhraní můžete získat buď pomocí automatizace, nebo pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> . Jakmile rozhraní získáte, můžete ho použít k určení, která položka projektu je aktuálně vybraná. Jakmile budete mít ID položky projektu, můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> k přidání vlastnosti.  
  
 V následujících postupech budete uchovávat vlastnost VsPkg.cs `Author` s hodnotou `Tom` v souboru projektu.  
  
### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Získání hierarchie projektu s objektem DTE  
  
1. Do balíčku VSPackage přidejte následující kód:  
  
    ```csharp  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Chcete-li zachovat vlastnost položky projektu s objektem DTE  
  
1. Do kódu uvedeného v metodě v předchozím postupu přidejte následující kód:  
  
    ```csharp  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath = (string)project.ProjectItems.Item(  
            "VsPkg.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Získání hierarchie projektu pomocí IVsMonitorSelection  
  
1. Do balíčku VSPackage přidejte následující kód:  
  
    ```csharp  
    IVsHierarchy hierarchy = null;  
    IntPtr hierarchyPtr = IntPtr.Zero;  
    IntPtr selectionContainer = IntPtr.Zero;  
    uint itemid;  
  
    // Retrieve shell interface in order to get current selection  
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;  
    if (monitorSelection == null)  
        throw new InvalidOperationException();  
  
    try  
    {  
        // Get the current project hierarchy, project item, and selection container for the current selection  
        // If the selection spans multiple hierachies, hierarchyPtr is Zero  
        IVsMultiItemSelect multiItemSelect = null;  
        ErrorHandler.ThrowOnFailure(  
            monitorSelection.GetCurrentSelection(  
                out hierarchyPtr, out itemid,   
                out multiItemSelect, out selectionContainer));  
  
        // We only care if there is only one node selected in the tree  
        if (!(itemid == VSConstants.VSITEMID_NIL ||   
            hierarchyPtr == IntPtr.Zero ||  
            multiItemSelect != null ||  
            itemid == VSConstants.VSITEMID_SELECTION))  
        {  
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)  
                as IVsHierarchy;  
        }  
    }  
    finally  
    {  
        if (hierarchyPtr != IntPtr.Zero)  
            Marshal.Release(hierarchyPtr);  
        if (selectionContainer != IntPtr.Zero)  
            Marshal.Release(selectionContainer);  
    }  
    ```  
  
2. 
  
### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Chcete-li zachovat vybranou vlastnost položky projektu pro danou hierarchii projektu  
  
1. Do kódu uvedeného v metodě v předchozím postupu přidejte následující kód:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-verify-that-the-property-is-persisted"></a>Ověření, zda je vlastnost trvalá  
  
1. Spusťte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a pak otevřete nebo vytvořte řešení.  
  
2. Vyberte položku projektu VsPkg.cs v **Průzkumník řešení**.  
  
3. Použijte zarážku nebo jinak určete, že je váš VSPackage načten a že SetItemAttribute běží.  
  
    > [!NOTE]
    > V kontextu uživatelského rozhraní lze vytvořit automatické načtení VSPackage <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> . Další informace najdete v tématu [načítání VSPackage](../extensibility/loading-vspackages.md).  
  
4. Zavřete [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a otevřete soubor projektu v programu Poznámkový blok. Měla by se zobrazit \<Author> značka s hodnotou, jak je znázorněno níže:  
  
    ```  
    <Compile Include="VsPkg.cs">  
        <Author>Tom</Author>  
    </Compile>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Vlastní nástroje](../extensibility/internals/custom-tools.md)
