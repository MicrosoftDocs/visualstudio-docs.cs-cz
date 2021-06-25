---
title: Přidání atributu do seznamu položek | Microsoft Docs
description: Zjistěte, jak přidat atribut do položky projektu v Visual Studio pomocí metod interoperability Shell GetItemAttribute a SetItemAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 36fc5905fd2b1423865982a80a6cb2ba6a803cc5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902017"
---
# <a name="add-an-attribute-to-a-project-item"></a>Přidání atributu do položky projektu
Metody a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> získejte a nastavte hodnotu atributů položky projektu. SetItemAttribute vytvoří atribut , pokud ještě neexistuje, a přidá ho do metadat položky projektu.

## <a name="add-an-attribute-to-a-project-item"></a>Přidání atributu do položky projektu

- Následující kód používá objekt <xref:EnvDTE.DTE> automatizace <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> a metodu k přidání atributu do položky projektu. ID položky projektu se získá z názvu položky projektu "program.cs". K této položce projektu se přidá atribut "MyAttribute" s danou hodnotou "MyValue".

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "MyAttribute", "MyValue");
    }

    ```

## <a name="see-also"></a>Viz také
- [Zachování dat v souboru projektu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
