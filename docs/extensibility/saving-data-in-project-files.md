---
title: Ukládání dat v souborech projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adc7d06b8479da4aef7042fd64702cff5ca3be60
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900654"
---
# <a name="save-data-in-project-files"></a>Ukládání dat v souborech projektu
Podtyp projektu můžete uložit a načíst data specifická pro podtyp v souboru projektu. Managed Package Framework (MPF) poskytuje dvě rozhraní k provedení této úlohy:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> Rozhraní umožňuje přístup k hodnoty vlastností z **MSBuild** části souboru projektu. Metody, které poskytuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> lze volat žádný uživatel pokaždé, když se související data sestavení které uživatel potřebuje k načtení nebo uložení.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Použité k uchování související data bez sestavení ve volném formátu XML. Metody, které poskytuje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> jsou volány [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pokaždé, když [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] musí zachovat související data bez sestavení v souboru projektu.  
  
  Další informace o tom, jak zachovat sestavení a související data mimo sestavení, naleznete v tématu [uchovávat data v souboru projektu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  
  
## <a name="save-and-retrieve-build-related-data"></a>Uložení a načtení sestavení souvisejících dat  
  
### <a name="to-save-a-build-related-data-in-the-project-file"></a>Chcete-li uložit sestavení související data v souboru projektu  
  
-   Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metody uložte úplnou cestu souboru projektu.  
  
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
  
### <a name="to-retrieve-build-related-data-from-the-project-file"></a>K načtení sestavení související data ze souboru projektu  
  
-   Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> metodu pro načtení úplnou cestu souboru projektu.  
  
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
  
## <a name="save-and-retrieve-non-build-related-data"></a>Ukládání a načítání souvisejících dat bez sestavení  
  
### <a name="to-save-non-build-related-data-in-the-project-file"></a>Chcete-li uložit mimo sestavení související data v souboru projektu  
  
1.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> metodou ke zjištění, zda XML fragment se změnila od posledního uložení do jeho aktuálního souboru.  
  
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
  
2.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metody k uložení dat XML v souboru projektu.  
  
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
  
### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Načíst související data bez sestavení v souboru projektu  
  
1.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> metody k inicializaci vlastnosti rozšíření projektu a další data nezávislé na sestavení. Tato metoda je volána, pokud neexistuje žádná data konfigurace XML v souboru projektu.  
  
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
  
2.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> metodu pro načtení dat XML ze souboru projektu.  
  
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
>  Všechny příklady kódu, které jsou uvedeny v tomto tématu jsou součástí většího příkladu v [VSSDK ukázky](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Viz také:  
 [Zachovat data v souboru projektu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)