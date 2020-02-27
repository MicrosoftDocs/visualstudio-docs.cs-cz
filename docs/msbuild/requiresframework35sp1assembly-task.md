---
title: Úloha Requiresframework35sp1assembly – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: caefe0887ca23cd4cee60c3a4ba2a6133e9893df
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632768"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly – úloha

Určuje, jestli aplikace vyžaduje .NET Framework 3,5 SP1.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy `RequiresFramework35SP1Assembly`.

|Parametr|Popis|
|---------------|-----------------|
|`Assemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje sestavení, na která jsou odkazována v aplikaci.|
|`CreateDesktopShortcut`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, během instalace vytvoří ikonu zástupce na ploše.|
|`DeploymentManifestEntryPoint`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje název souboru manifestu pro aplikaci.|
|`EntryPoint`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje sestavení, které se má provést při spuštění aplikace.|
|`ErrorReportUrl`|Volitelný parametr `String`.<br /><br /> Určuje web, který se zobrazí v dialogových oknech, které se vyskytují během instalace ClickOnce.|
|`Files`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje seznam souborů, které budou nasazeny při publikování aplikace.|
|`ReferencedAssemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje sestavení, která jsou odkazována v projektu.|
|`RequiresMinimumFramework35SP1`|Volitelný výstupní parametr `Boolean`.<br /><br /> Pokud `true`, vyžaduje aplikace .NET Framework 3,5 SP1.|
|`SigningManifests`|Volitelný výstupní parametr `Boolean`.<br /><br /> Pokud `true`, manifesty ClickOnce jsou podepsány.|
|`SuiteName`|Volitelný parametr `String`.<br /><br /> Určuje název složky v nabídce **Start** , do které se aplikace nainstaluje.|
|`TargetFrameworkVersion`|Volitelný parametr `String`.<br /><br /> Určuje verzi .NET Framework, na kterou se tato aplikace zaměřuje.|

## <a name="remarks"></a>Poznámky

 Kromě toho, že mají parametry, které jsou uvedeny v tabulce, tato úloha dědí parametry z třídy <xref:Microsoft.Build.Tasks.TaskExtension>, kterou sám dědí z třídy <xref:Microsoft.Build.Utilities.Task>. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)