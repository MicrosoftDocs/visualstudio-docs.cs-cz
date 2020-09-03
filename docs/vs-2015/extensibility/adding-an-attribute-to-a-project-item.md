---
title: Přidání atributu do položky projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1740ac4dfdeb64d5b4b2b0aab264845de9c186dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184822"
---
# <a name="adding-an-attribute-to-a-project-item"></a>Přidání atributu do položky projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> získat a nastavte hodnotu atributů položky projektu. SetItemAttribute vytvoří atribut, pokud ještě neexistuje, a přidá ho do metadat položky projektu.  
  
## <a name="adding-an-attribute-to-a-project-item"></a>Přidání atributu do položky projektu  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>Přidání atributu do položky projektu  
  
- Následující kód používá <xref:EnvDTE.DTE> objekt automatizace a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> metodu pro přidání atributu do položky projektu. ID položky projektu se získá z názvu položky projektu "program.cs". Atribut "MyAttribute" se přidá do této položky projektu a bude mít nastavenou hodnotu "hodnota".  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Trvalá data v souboru projektu nástroje MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
