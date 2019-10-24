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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 678068d1b6acc055fa65e6d0305b07152ed28695
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748102"
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
