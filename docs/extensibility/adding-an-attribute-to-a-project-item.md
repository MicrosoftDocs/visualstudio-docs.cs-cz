---
title: Přidání atributu do položky projektu | Microsoft Docs
description: Naučte se, jak přidat atribut do položky projektu v aplikaci Visual Studio pomocí metod interoperability prostředí GetItemAttribute a SetItemAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee65a22e0a296047f5a401e00495ee25403d64e0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094910"
---
# <a name="add-an-attribute-to-a-project-item"></a>Přidání atributu do položky projektu
Metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> získat a nastavte hodnotu atributů položky projektu. SetItemAttribute vytvoří atribut, pokud ještě neexistuje, a přidá ho do metadat položky projektu.

## <a name="add-an-attribute-to-a-project-item"></a>Přidání atributu do položky projektu

- Následující kód používá <xref:EnvDTE.DTE> objekt automatizace a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> metodu pro přidání atributu do položky projektu. ID položky projektu se získá z názvu položky projektu "program. cs". Atribut "MyAttribute" se přidá do této položky projektu a bude mít nastavenou hodnotu "hodnota".

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
- [Zachovat data v souboru projektu MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
