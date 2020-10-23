---
title: Úloha FindInList – | Microsoft Docs
description: Naučte se pomocí úlohy MSBuild FindInList – najít položku, která má odpovídající itemspec v zadaném seznamu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b4afc20b7845f3af71de1fbbb89f074801e08d1d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2020
ms.locfileid: "92435695"
---
# <a name="findinlist-task"></a>FindInList – úloha

V zadaném seznamu najde položku, která má odpovídající itemspec.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry [úlohy FindInList –](../msbuild/findinlist-task.md).

|Parametr|Popis|
|---------------|-----------------|
|`CaseSensitive`|Volitelný `Boolean` parametr.<br /><br /> V případě `true` , že vyhledávání rozlišuje velká a malá písmena; v opačném případě ne. Výchozí hodnota je `true`.|
|`FindLastMatch`|Volitelný `Boolean` parametr.<br /><br /> `true`Vrátí poslední shodu. v opačném případě vrátí první shodu. Výchozí hodnota je `false`.|
|`ItemFound`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> První shodná položka, která se nachází v seznamu, pokud existuje.|
|`ItemSpecToFind`|Požadovaný parametr `String`.<br /><br /> ItemSpec, který se má vyhledat.|
|`List`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Seznam, ve kterém se má hledat ItemSpec|
|`MatchFileNameOnly`|Volitelný `Boolean` parametr.<br /><br /> IF `true` se shoduje s pouze částí názvu souboru ItemSpec. v opačném případě se porovná s celým ItemSpec. Výchozí hodnota je `true`.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
