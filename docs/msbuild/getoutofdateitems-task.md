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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: d3dc343c595606faf5bd31d7f087f7ba8d95f69e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747310"
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
|**Prostředky**|Volitelný parametr **ITaskItem []** .|
|**TLogDirectory**|Povinný parametr **řetězce**|
|**TLogNamePrefix**|Povinný parametr **řetězce**|

## <a name="see-also"></a>Viz také:

[Odkaz na úkol](../msbuild/msbuild-task-reference.md)