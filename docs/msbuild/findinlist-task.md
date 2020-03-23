---
title: Úkol FindInList | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634146"
---
# <a name="findinlist-task"></a>FindInList – úloha

V zadaném seznamu vyhledá položku, která má odpovídající itemspec.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry [úlohy FindInList](../msbuild/findinlist-task.md).

|Parametr|Popis|
|---------------|-----------------|
|`CaseSensitive`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`hledání rozlišuje malá a velká písmena; v opačném případě tomu tak není. Výchozí hodnota `true`je .|
|`FindLastMatch`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`vrátíte poslední shodu; v opačném případě vraťte první shodu. Výchozí hodnota `false`je .|
|`ItemFound`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> První odpovídající položka nalezená v seznamu, pokud existuje.|
|`ItemSpecToFind`|Požadovaný parametr `String`.<br /><br /> Itemspec hledat.|
|`List`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Seznam, ve kterém chcete vyhledat položky pec.|
|`MatchFileNameOnly`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, zápas proti pouze název souboru část itemspec; v opačném případě zápas proti celé itemspec. Výchozí hodnota `true`je .|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
