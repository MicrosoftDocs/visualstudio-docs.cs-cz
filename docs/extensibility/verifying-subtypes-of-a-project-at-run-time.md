---
title: Ověření podtypů projektu za běhu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0d739a9f8734dd8941e3254d03364cbf4c77350
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698173"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Ověření podtypů projektu za běhu
VSPackage, který závisí na podtypu vlastního projektu, by měl obsahovat logiku pro hledání tohoto podtypu tak, aby mohl řádně selhat, pokud podtyp není k dispozici. Následující postup ukazuje, jak ověřit přítomnost zadaného podtypu.

### <a name="to-verify-the-presence-of-a-subtype"></a>Ověření přítomnosti podtypu

1. Získejte hierarchii projektu z objektů <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projektu a řešení jako objekt přidáním následujícího kódu do vašeho VSPackage.

    ```csharp
    EnvDTE.DTE dte;
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));

    EnvDTE.Project project;
    project = dte.Solution.Projects.Item(1);

    IVsSolution solution;
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));

    IVsHierarchy hierarchy;
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);

    ```

2. Přetypovat hierarchii do <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> rozhraní.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Seznam identifikátorů GUID typu projektu získáte vyvoláním rozhraní <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. V seznamu naleznete identifikátor GUID zadaného podtypu.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Viz také
- [Podtypy projektu](../extensibility/internals/project-subtypes.md)
- [Návrh podtypů projektu](../extensibility/internals/project-subtypes-design.md)
- [Vlastnosti a metody rozšířené podle podtypů projektu](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
