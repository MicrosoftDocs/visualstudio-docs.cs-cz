---
title: Třída TrackedVCToolTask | Microsoft Docs
description: Přečtěte si o parametrech, které třída Base TrackedVCToolTask přidá do úkolů, které z ní dědí.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 01b55e0ad88cb520078479217306bac948e6cd60
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047001"
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
