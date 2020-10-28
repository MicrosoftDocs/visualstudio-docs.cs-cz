---
title: Úloha CustomBuild | Microsoft Docs
description: Tento článek popisuje úlohu CustomBuild MSBuild, která je používána nástrojem MSBuild k podpoře přizpůsobení procesu sestavení C++.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 640c1e6ae286b45f8700709829140093452a9491
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796547"
---
# <a name="custombuild-task"></a>CustomBuild – úloha

Zabalí nástroj kompilátoru Microsoft C++, cmd.exe. Tato třída je odvozena z [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ale nepoužívá sledování souborů k zjišťování závislostí souborů. Všechny závislosti by měly být explicitně zadány jako AdditionalDependencies pro správné fungování přírůstkového sestavení.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy **CustomBuild** .

|Parametr|Popis|
|---------------|-----------------|
|**BuildSuffix**|Volitelný **řetězcový** parametr.|
|**Prostředky**|Povinný parametr **ITaskItem []** .|
|**TrackerLogDirectory**|Volitelný **řetězcový** parametr.|

## <a name="see-also"></a>Viz také

[Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
