---
title: Vyžaduje Framework35SP1Úloha sestavení | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632768"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly – úloha

Určuje, zda aplikace vyžaduje rozhraní .NET Framework 3.5 SP1.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `RequiresFramework35SP1Assembly` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Assemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje sestavení, na která se odkazuje v aplikaci.|
|`CreateDesktopShortcut`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`vytvoří ikonu zástupce na ploše během instalace.|
|`DeploymentManifestEntryPoint`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje název souboru manifestu pro aplikaci.|
|`EntryPoint`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje sestavení, které by mělo být spuštěno při spuštění aplikace.|
|`ErrorReportUrl`|Volitelný `String` parametr.<br /><br /> Určuje web, který je zobrazen v dialogových oknech, ke kterým došlo během instalace ClickOnce.|
|`Files`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje seznam souborů, které budou nasazeny při publikování aplikace.|
|`ReferencedAssemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje sestavení, na která se odkazuje v projektu.|
|`RequiresMinimumFramework35SP1`|Volitelný `Boolean` výstupní parametr.<br /><br /> Pokud `true`aplikace vyžaduje rozhraní .NET Framework 3.5 SP1.|
|`SigningManifests`|Volitelný `Boolean` výstupní parametr.<br /><br /> Pokud `true`jsou podepsány manifesty ClickOnce.|
|`SuiteName`|Volitelný `String` parametr.<br /><br /> Určuje název složky v nabídce **Start,** ve které bude aplikace nainstalována.|
|`TargetFrameworkVersion`|Volitelný `String` parametr.<br /><br /> Určuje verzi rozhraní .NET Framework, na kterou se tato aplikace zaměřuje.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha <xref:Microsoft.Build.Tasks.TaskExtension> dědí parametry z <xref:Microsoft.Build.Utilities.Task> třídy, která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)