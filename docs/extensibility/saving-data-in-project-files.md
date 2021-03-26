---
title: Ukládání dat do souborů projektu | Microsoft Docs
description: Přečtěte si o rozhraních, která rozhraní Managed Package Framework poskytuje k ukládání a načítání dat specifických pro jednotlivé typy v souboru projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24f3f0b84f22532187537c31ba6e47a823eef8f7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060494"
---
# <a name="save-data-in-project-files"></a>Uložení dat v souborech projektu
Podtyp projektu může uložit a načíst data specifická pro podtypy v souboru projektu. Sada Managed Package Framework (MPF) poskytuje dvě rozhraní k provedení této úlohy:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>Rozhraní umožňuje přístup k hodnotám vlastností z oddílu **MSBuild** souboru projektu. Metody, které Poskytovatel <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> může vyvolat, kdykoli uživatel potřebuje načíst nebo uložit data související s sestavením.

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>Slouží k uchovávání dat souvisejících s sestavami v XML ve volném formátu. Metody poskytované pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> jsou volány [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vždy, když [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je nutné uchovat data související s sestavou sestavení v souboru projektu.

  Další informace o tom, jak uchovávat data o sestavení a nesouvisejících sestavách, naleznete [v tématu trvalá data v souboru projektu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).

## <a name="save-and-retrieve-build-related-data"></a>Uložit a načíst data související s sestavením

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Uložení dat souvisejících s sestavením v souboru projektu

- Voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metody uložte úplnou cestu k souboru projektu.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string newFullPath = GetNewFullPath();
    // Set a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));
    ```

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Načtení dat souvisejících s sestavením ze souboru projektu

- Voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> metody načtete úplnou cestu k souboru projektu.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string fullPath;
    // Get a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));
    ```

## <a name="save-and-retrieve-non-build-related-data"></a>Uložení a načtení dat souvisejících s nesestavením

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Uložení dat nesouvisejících s sestavením v souboru projektu

1. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> metodu pro zjištění, zda se změnil fragment XML od posledního uložení do aktuálního souboru.

    ```
    public int IsFragmentDirty(uint storage, out int pfDirty)
    {
        pfDirty = 0;
        switch (storage)
        {
            case (uint)_PersistStorageType.PST_PROJECT_FILE:
            {
                if (isDirty)
                    pfDirty |= 1;
                break;
            }
            case (uint)_PersistStorageType.PST_USER_FILE:
            {
                // We do not store anything in the user file.
                break;
            }
        }

        // Forward the call to inner flavor(s)
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);

        return VSConstants.S_OK;

    }
    ```

2. Implementací <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metody uložte data XML do souboru projektu.

    ```
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)
    {
        pbstrXMLFragment = null;

        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Create XML for our data.
                    XmlDocument doc = new XmlDocument();
                    XmlNode root = doc.CreateElement(this.GetType().Name);

                    XmlNode node = doc.CreateElement(targetsTag);
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));
                    root.AppendChild(node);

                    node = doc.CreateElement(updateTargetsTag);
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));
                    root.AppendChild(node);

                    doc.AppendChild(root);
                    // Get XML fragment representing our data
                    pbstrXMLFragment = doc.InnerXml;

                    if (fClearDirty != 0)
                        isDirty = false;
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);

        return VSConstants.S_OK;
    }
    ```

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Načtení dat nesouvisejících s buildem v souboru projektu

1. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> metodu pro inicializaci vlastností rozšíření projektu a dalších dat nezávislých na sestavení. Tato metoda je volána, pokud v souboru projektu nejsou žádná konfigurační data XML.

    ```
    public int InitNew(ref Guid guidFlavor, uint storage)
    {
        //Return,if it is our guid.
        if (IsMyFlavorGuid(ref guidFlavor))
            return VSConstants.S_OK;

        //Forward the call to inner flavor(s).
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);

        return VSConstants.S_OK;
    ```

2. Implementací <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> metody načtěte data XML ze souboru projektu.

    ```
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)
    {
        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Load our data from the XML fragment.
                    XmlDocument doc = new XmlDocument();
                    XmlNode node = doc.CreateElement(this.GetType().Name);
                    node.InnerXml = pszXMLFragment;
                    if (node == null
                        || node.FirstChild == null
                        || node.FirstChild.ChildNodes.Count == 0
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)
                        break;
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;

                    if (node.FirstChild.ChildNodes.Count <= 1
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)
                        break;
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);

        return VSConstants.S_OK;
    }
    ```

> [!NOTE]
> Všechny příklady kódu, které jsou uvedené v tomto tématu, jsou části většího příkladu v [ukázkách VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Viz také
- [Zachovat data v souboru projektu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
