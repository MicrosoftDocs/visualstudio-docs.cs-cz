---
title: Ověřování podtypů projektu v době běhu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e3940097ac53255b7bdd2c12c9ccc64605016e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62584902"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Ověření podtypů projektu za běhu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage, který závisí na vlastním podtypu projektu, by měl obsahovat logiku pro vyhledání tohoto podtypu, aby mohl být řádně neúspěšný, pokud podtyp není k dispozici. Následující postup ukazuje, jak ověřit přítomnost zadaného podtypu.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Ověření přítomnosti podtypu  
  
1. Získejte hierarchii projektu z objektů projektu a řešení jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objekt přidáním následujícího kódu do balíčku VSPackage.  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2. Přetypujte hierarchii na <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> rozhraní.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3. Získání seznamu identifikátorů GUID typu projektu vyvoláním metody <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4. V seznamu vyhledejte identifikátor GUID zadaného podtypu.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Podtypy projektu](../extensibility/internals/project-subtypes.md)   
 [Návrh podtypů projektu](../extensibility/internals/project-subtypes-design.md)   
 [Vlastnosti a metody rozšířené prostřednictvím podtypů projektů](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
