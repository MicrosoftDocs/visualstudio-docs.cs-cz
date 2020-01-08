---
title: Třída TrackedVCToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8a4272f7800e0532c0674fe7117e839cb16557d5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594926"
---
# <a name="trackedvctooltask-base-class"></a>Základní třída TrackedVCToolTask

Mnoho úloh je v konečném důsledku dědění z třídy <xref:Microsoft.Build.Utilities.Task> a třídy [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) . Tato třída přidá několik parametrů k úkolům odvozeným od [VCToolTask](../msbuild/vctooltask-base-class.md). Tyto parametry jsou uvedeny v tomto dokumentu.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry základní třídy **TrackedVCToolTask** .

|Parametr|Popis|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Volitelný parametr **bool** .|
|**EnableExecuteTool**|Volitelný parametr **bool** .|
|**ExcludedInputPaths**|Volitelný parametr **ITaskItem []** .|
|**MinimalRebuildFromTracking**|Volitelný parametr **bool** .|
|**PathOverride**|Volitelný **řetězcový** parametr.|
|**PostBuildTrackingCleanup**|Volitelný parametr **bool** .|
|**RootSource**|Volitelný **řetězcový** parametr.|
|**SkippedExecution**|Volitelný výstupní parametr **bool**|
|**SourcesCompiled**|Volitelný výstupní parametr **ITaskItem []** .|
|**TLogCommandFile**|Volitelný parametr **ITaskItem**|
|**TLogReadFiles**|Volitelný parametr **ITaskItem []** .|
|**TLogWriteFiles**|Volitelný parametr **ITaskItem []** .|
|**ToolArchitecture**|Volitelný **řetězcový** parametr.|
|**TrackCommandLines**|Volitelný parametr **bool** .|
|**TrackFileAccess**|Volitelný parametr **bool** .|
|**TrackedInputFilesToIgnore**|Volitelný parametr **ITaskItem []** .|
|**TrackedOutputFilesToIgnore**|Volitelný parametr **ITaskItem []** .|
|**TrackerFrameworkPath**|Volitelný **řetězcový** parametr.|
|**TrackerSdkPath**|Volitelný **řetězcový** parametr.|

## <a name="see-also"></a>Viz také:

[Odkaz na úkol](../msbuild/msbuild-task-reference.md)<br/>
[Úlohy](../msbuild/msbuild-tasks.md)
