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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594926"
---
# <a name="trackedvctooltask-base-class"></a>TrackedVCToolTask – základní třída

Mnohé úlohy jsou nakonec děděny ze třídy <xref:Microsoft.Build.Utilities.Task> a třídy [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) . Tato třída přidá několik parametrů k úkolům odvozeným od [VCToolTask](../msbuild/vctooltask-base-class.md). Tyto parametry jsou uvedeny v tomto dokumentu.

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

## <a name="see-also"></a>Viz také

[Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)<br/>
[Úlohy](../msbuild/msbuild-tasks.md)
