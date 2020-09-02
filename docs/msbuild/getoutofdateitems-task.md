---
title: Úloha GetOutOfDateItems | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: bfa60ff0f7e4060f5725fe54bd5950d858b86a22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77272402"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems – úloha

Pomocný úkol, který čte starou tlogs, zapisuje nové tlogs a vrátí sadu položek, které nejsou aktuální.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy **GetOutOfDateItems** .

|Parametr|Popis|
|---------------|-----------------|
|**CheckForInterdependencies**|Volitelný parametr **bool** .|
|**CommandMetadataName**|Volitelný **řetězcový** parametr.|
|**DependenciesMetadataName**|Volitelný **řetězcový** parametr.|
|**HasInterdependencies**|Volitelný výstupní parametr **bool**|
|**OutOfDateSources**|Volitelný výstupní parametr **ITaskItem []** .|
|**OutputsMetadataName**|Povinný parametr **řetězce**|
|**zdroje**|Volitelný parametr **ITaskItem []** .|
|**TLogDirectory**|Povinný parametr **řetězce**|
|**TLogNamePrefix**|Povinný parametr **řetězce**|

## <a name="see-also"></a>Viz také

[Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)