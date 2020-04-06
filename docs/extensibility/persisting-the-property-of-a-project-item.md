---
title: Trvalé vlastnosti položky projektu | Dokumenty společnosti Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15c280f15436a5e27bcc0dcc4d2fb9e9bdd82933
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702207"
---
# <a name="persist-the-property-of-a-project-item"></a>Zachovat vlastnost položky projektu
Můžete chtít zachovat vlastnost, kterou přidáte do položky projektu, jako je například autor zdrojového souboru. To lze provést uložením vlastnosti v souboru projektu.

 Prvním krokem k zachování vlastnosti v souboru projektu je získat <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> hierarchii projektu jako rozhraní. Toto rozhraní můžete získat buď pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>automatizace nebo pomocí aplikace . Jakmile získáte rozhraní, můžete jej použít k určení, která položka projektu je aktuálně vybrána. Jakmile budete mít ID položky <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> projektu, můžete přidat vlastnost.

 V následujících postupech přetrvávají *vlastnost VsPkg.cs* `Author` s hodnotou `Tom` v souboru projektu.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Získání hierarchie projektu s objektem DTE

1. Přidejte do balíčku VSPackage následující kód:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Chcete-li zachovat vlastnost položky projektu s objektem DTE

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Získání hierarchie projektu pomocí iVsMonitorSelection

1. Přidejte do balíčku VSPackage následující kód:

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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Chcete-li zachovat vybranou vlastnost položky projektu vzhledem k hierarchii projektu

1. Do kódu uvedeného v metodě v předchozím postupu přidejte následující kód:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Ověření trvalé vlastnosti

1. Spusťte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a otevřete nebo vytvořte řešení.

2. Vyberte položku projektu VsPkg.cs v **Průzkumníku řešení**.

3. Použijte zarážku nebo jinak určete, že je načten váš VSPackage a že SetItemAttribute běží.

   > [!NOTE]
   > Vkontextu VSPackage můžete automaticky načíst <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>v kontextu ui . Další informace naleznete v [tématu Load VSPackages](../extensibility/loading-vspackages.md).

4. Zavřete [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a otevřete soubor projektu v poznámkovém bloku. Měli byste \<vidět značku autora> s hodnotou Tom, a to následovně:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Viz také

- [Vlastní nástroje](../extensibility/internals/custom-tools.md)
