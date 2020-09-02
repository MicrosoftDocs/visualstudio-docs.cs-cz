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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595342"
---
# <a name="custombuild-task"></a>CustomBuild – úloha

Zabalí nástroj kompilátoru Microsoft C++, cmd.exe. Tato třída je odvozena z [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ale nepoužívá sledování souborů k zjišťování závislostí souborů. Všechny závislosti by měly být explicitně zadány jako AdditionalDependencies pro správné fungování přírůstkového sestavení.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy **CustomBuild** .

|Parametr|Popis|
|---------------|-----------------|
|**BuildSuffix**|Volitelný **řetězcový** parametr.|
|**zdroje**|Povinný parametr **ITaskItem []** .|
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.|

## <a name="see-also"></a>Viz také

[Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
