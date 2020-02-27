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
ms.openlocfilehash: 533f87eba9032efa7dc60ac682bbe400cb640727
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634432"
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

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
