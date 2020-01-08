---
title: Úloha CustomBuild | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d95b6e7d4197487adc13050572ac31310701c759
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595342"
---
# <a name="custombuild-task"></a>CustomBuild – úloha

Zabalí nástroj Microsoft C++ Compiler Tool, cmd. exe. Tato třída je odvozena z [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ale nepoužívá sledování souborů k zjišťování závislostí souborů. Všechny závislosti by měly být explicitně zadány jako AdditionalDependencies pro správné fungování přírůstkového sestavení.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy **CustomBuild** .

|Parametr|Popis|
|---------------|-----------------|
|**BuildSuffix**|Volitelný **řetězcový** parametr.|
|**Prostředky**|Povinný parametr **ITaskItem []** .|
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.|

## <a name="see-also"></a>Viz také:

[Odkaz na úkol](../msbuild/msbuild-task-reference.md)
