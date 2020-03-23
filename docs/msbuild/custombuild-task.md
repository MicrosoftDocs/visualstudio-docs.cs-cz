---
title: Úkol CustomBuild | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595342"
---
# <a name="custombuild-task"></a>Úkol CustomBuild

Zabalí kompilátor ový nástroj Microsoft C++, cmd.exe. Tato třída je odvozena od [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), ale nepoužívá sledování souborů ke zjišťování závislostí souborů. Všechny závislosti by měly být explicitně zadány jako AdditionalDependencies pro přírůstkové sestavení pracovat správně.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy **CustomBuild.**

|Parametr|Popis|
|---------------|-----------------|
|**BuildSuffix**|Volitelný parametr **řetězce.**|
|**Zdrojů**|Povinný parametr **ITaskItem[].**|
|**TrackerLogDirectory**|Volitelný parametr **řetězce.**|

## <a name="see-also"></a>Viz také

[Odkaz na úkol](../msbuild/msbuild-task-reference.md)
