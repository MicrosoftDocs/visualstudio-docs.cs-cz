---
title: Úloha ResolveManifestFiles – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ebbc2a036700c26ccd6ca3bec7b235722432e9f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595173"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles – úloha
Řeší následující položky v procesu sestavení do souborů pro generování manifestu: sestavené položky, závislosti, satelity, obsah, symboly ladění a dokumentace.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `ResolveManifestFiles`.

|Parametr|Popis|
|---------------|-----------------|
|`DeploymentManifestEntryPoint`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje název manifestu nasazení.|
|`EntryPoint`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje spravované sestavení nebo odkaz manifestu ClickOnce, který je vstupním bodem manifestu.|
|`ExtraFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje další soubory.|
|`ManagedAssemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje spravovaná sestavení.|
|`NativeAssemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje nativní sestavení.|
|`OutputAssemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Určuje generovaná sestavení.|
|`OutputDeploymentManifestEntryPoint`|Volitelný výstupní parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje výstupní vstupní bod manifestu nasazení.|
|`OutputEntryPoint`|Volitelný výstupní parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje výstupní vstupní bod.|
|`OutputFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Určuje výstupní soubory.|
|`PublishFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje soubory pro publikování.|
|`SatelliteAssemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje satelitní sestavení.|
|`SigningManifests`|Volitelný parametr `Boolean`.<br /><br /> Je-li `true`, manifesty jsou podepsány.|
|`TargetCulture`|Volitelný parametr `String`.<br /><br /> Určuje cílovou jazykovou verzi pro satelitní sestavení.|
|`TargetFrameworkVersion`|Volitelný parametr `String`.<br /><br /> Určuje cílovou verzi .NET Framework.|

## <a name="remarks"></a>Poznámky
 Kromě toho, že mají parametry, které jsou uvedeny v tabulce, tato úloha dědí parametry z třídy <xref:Microsoft.Build.Tasks.TaskExtension>, kterou sám dědí z třídy <xref:Microsoft.Build.Utilities.Task>. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
