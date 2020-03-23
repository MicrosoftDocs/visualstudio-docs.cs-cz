---
title: Třída TrackedVCToolTask | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594926"
---
# <a name="trackedvctooltask-base-class"></a>Základní třída TrackedVCToolTask

Mnoho úkolů nakonec dědí z třídy <xref:Microsoft.Build.Utilities.Task> a [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) třídy. Tato třída přidá několik parametrů k úkolům, které jsou odvozeny z [VCToolTask](../msbuild/vctooltask-base-class.md). Tyto parametry jsou uvedeny v tomto dokumentu.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry základní třídy **TrackedVCToolTask.**

|Parametr|Popis|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Volitelný **parametr bool.**|
|**EnableExecuteTool**|Volitelný **parametr bool.**|
|**ExcludedInputPaths**|Volitelný parametr **ITaskItem[].**|
|**MinimalRebuildFromTracking**|Volitelný **parametr bool.**|
|**PathOverride**|Volitelný parametr **řetězce.**|
|**PostBuildTrackingCleanup**|Volitelný **parametr bool.**|
|**Kořenový zdroj**|Volitelný parametr **řetězce.**|
|**Přeskočené provedení**|Volitelný výstupní parametr **bool.**|
|**Zkompilované zdroje**|Volitelný výstupní parametr **ITaskItem[].**|
|**Soubor TLogCommandFile**|Volitelný parametr **ITaskItem.**|
|**Tlogready**|Volitelný parametr **ITaskItem[].**|
|**Tlogwritefiles**|Volitelný parametr **ITaskItem[].**|
|**Architektura nástrojů**|Volitelný parametr **řetězce.**|
|**TrackCommandLines**|Volitelný **parametr bool.**|
|**Přístup trackfileaccess**|Volitelný **parametr bool.**|
|**TrackedInputFilesToignore**|Volitelný parametr **ITaskItem[].**|
|**SledováníVýstupFilesToIgnore**|Volitelný parametr **ITaskItem[].**|
|**Cesta trackeru FrameworkPath**|Volitelný parametr **řetězce.**|
|**Cesta trackersdk**|Volitelný parametr **řetězce.**|

## <a name="see-also"></a>Viz také

[Odkaz na úkol](../msbuild/msbuild-task-reference.md)<br/>
[Úlohy](../msbuild/msbuild-tasks.md)
