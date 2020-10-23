---
title: Úloha GetOutOfDateItems | Microsoft Docs
description: Použijte úlohu pomocníka MSBuild GetOutOfDateItems ke čtení a zápisu protokolů transakcí (TLOGs) a vrácení sad položek, které nejsou aktuální.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6cc80d4e1aa3580e0185460d19f78e9737b73220
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436818"
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

## <a name="see-also"></a>Viz také

[Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)