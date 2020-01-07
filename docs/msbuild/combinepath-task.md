---
title: Úloha CombinePath – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a52e0d770a535b0fa7d29a379a7f6aba63e62d78
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593340"
---
# <a name="combinepath-task"></a>CombinePath – úloha
Zkombinuje zadané cesty do jedné cesty.

## <a name="task-parameters"></a>Parametry úlohy
 Následující tabulka popisuje parametry [úlohy CombinePath –](../msbuild/combinepath-task.md).

|Parametr|Popis|
|---------------|-----------------|
|`BasePath`|Vyžaduje se `String` parametr.<br /><br /> Základní cesta, která se má zkombinovat s ostatními cestami. Může se jednat o relativní cestu, absolutní cestu nebo prázdnou hodnotu.|
|`Paths`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Seznam jednotlivých cest, které mají být kombinovány s BasePath, aby tvořily kombinovanou cestu. Cesty mohou být relativní nebo absolutní.|
|`CombinedPaths`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Kombinovaná cesta, která je vytvořena touto úlohou.|

## <a name="remarks"></a>Poznámky
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
