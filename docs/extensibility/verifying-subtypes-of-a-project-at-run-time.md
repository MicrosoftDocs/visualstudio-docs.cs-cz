---
title: Ověřování podtypů projektu v době běhu | Microsoft Docs
description: Naučte se, jak vaše VSPackage ověří přítomnost zadaného vlastního podtypu projektu, na kterém závisí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c52d3297ce4903cb8f8e7cb2f9ab5169d21ac94e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062600"
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
