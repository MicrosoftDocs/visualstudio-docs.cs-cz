---
title: Úloha FindInList – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 915265a775f572467ad1296499bdd3201adc1f8b
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634146"
---
# <a name="findinlist-task"></a>FindInList – úloha

V zadaném seznamu najde položku, která má odpovídající itemspec.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry [úlohy FindInList –](../msbuild/findinlist-task.md).

|Parametr|Popis|
|---------------|-----------------|
|`CaseSensitive`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, hledání rozlišuje velká a malá písmena; v opačném případě není. Výchozí hodnota je `true`.|
|`FindLastMatch`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vraťte poslední shodu; v opačném případě vrátí první shodu. Výchozí hodnota je `false`.|
|`ItemFound`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` výstupní parametr jen pro čtení.<br /><br /> První shodná položka, která se nachází v seznamu, pokud existuje.|
|`ItemSpecToFind`|Vyžaduje se `String` parametr.<br /><br /> ItemSpec, který se má vyhledat.|
|`List`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Seznam, ve kterém se má hledat ItemSpec|
|`MatchFileNameOnly`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, porovná se jenom s názvem souboru, který je součástí ItemSpec; jinak se porovná s celým ItemSpec. Výchozí hodnota je `true`.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
