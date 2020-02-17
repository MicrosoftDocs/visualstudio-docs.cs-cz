---
title: Úloha ParallelCustomBuild | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 0d8a171d393f629d0b6ab3a7fc61ad37862b0da1
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279263"
---
# <a name="parallelcustombuild-task"></a>ParallelCustomBuild – úloha

Spusťte paralelní instance [CustomBuild úlohy](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy **ParallelCustomBuild** .

|Parametr|Popis|
|---------------|-----------------|
|**BreakOnFirstFailure**|Volitelný parametr **bool** .|
|**MaxItemsInBatch**|Volitelný parametr **int**|
|**MaxProcesses**|Volitelný parametr **int**|
|**Prostředky**|Povinný parametr **ITaskItem []** .|

## <a name="see-also"></a>Viz také

[Odkaz na úkol](../msbuild/msbuild-task-reference.md)