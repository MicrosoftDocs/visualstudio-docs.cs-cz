---
title: Úloha ParallelCustomBuild | Microsoft Docs
description: Přečtěte si, jak MSBuild používá úlohu ParallelCustomBuild ke spuštění paralelních instancí úlohy CustomBuild.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f4491d0a5e9c9d3a2554bd32211fd1fa8f7be2d2
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048898"
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

[Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)