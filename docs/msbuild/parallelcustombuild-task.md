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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: c6ea14e61eb2d62f3fc9ccdac3a17010ccc9194f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747222"
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

## <a name="see-also"></a>Viz také:

[Odkaz na úkol](../msbuild/msbuild-task-reference.md)