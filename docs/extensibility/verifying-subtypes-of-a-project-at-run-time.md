---
title: Ověření podtypů projektu za běhu | Microsoft Docs
description: Zjistěte, jak můžete pomocí balíčku VSPackage ověřit přítomnost zadaného podtypu vlastního projektu, na které závisí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 621a40e1857d7c78ec4c5be08a3b7c3808a0d48b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905470"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Ověření podtypů projektu za běhu
Balíček VSPackage, který závisí na podtypu vlastního projektu, by měl zahrnovat logiku pro vyhledávání tohoto podtypu, aby mohl bez selhání selhat, pokud podtyp není k dispozici. Následující postup ukazuje, jak ověřit přítomnost zadaného podtypu.

### <a name="to-verify-the-presence-of-a-subtype"></a>Ověření přítomnosti podtypu

1. Získejte hierarchii projektu z objektů projektu a řešení jako objekt přidáním následujícího kódu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> do balíčku VSPackage.

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

2. Přetypování hierarchie na <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> rozhraní.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Seznam identifikátorů GUID typu projektu získáte vyvoláním <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. V seznamu zkontrolujte identifikátor GUID zadaného podtypu.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Viz také
- [Podtypy projektů](../extensibility/internals/project-subtypes.md)
- [Návrh podtypů projektů](../extensibility/internals/project-subtypes-design.md)
- [Vlastnosti a metody rozšířené podtypy projektu](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
