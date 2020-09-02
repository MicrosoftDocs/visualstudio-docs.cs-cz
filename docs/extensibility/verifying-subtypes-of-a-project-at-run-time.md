---
title: Ověřování podtypů projektu v době běhu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698173"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Ověření podtypů projektu v době běhu
VSPackage, který závisí na vlastním podtypu projektu, by měl obsahovat logiku pro vyhledání tohoto podtypu, aby mohl být řádně neúspěšný, pokud podtyp není k dispozici. Následující postup ukazuje, jak ověřit přítomnost zadaného podtypu.

### <a name="to-verify-the-presence-of-a-subtype"></a>Ověření přítomnosti podtypu

1. Získejte hierarchii projektu z projektu a objektů řešení jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objekt přidáním následujícího kódu do VSPackage.

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

2. Přetypujte hierarchii na <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> rozhraní.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Získání seznamu identifikátorů GUID typu projektu vyvoláním metody <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. V seznamu vyhledejte identifikátor GUID zadaného podtypu.

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
- [Vlastnosti a metody rozšířené podtypy projektu](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
