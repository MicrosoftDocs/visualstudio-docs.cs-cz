---
title: Úloha FindAppConfigFile – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c54f3c222588cd13711c832d12f7598f0cc5e223
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634172"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile – úloha

Vyhledá soubor *App. config* , pokud existuje, v uvedených seznamech.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy `FindAppConfigFile`.

|Parametr|Popis|
|---------------|-----------------|
|`AppConfigFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Určuje první vyhovující položku, která se nachází v seznamu, pokud existuje.|
|`PrimaryList`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje primární seznam, pomocí kterého se bude hledat.|
|`SecondaryList`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje sekundární seznam, přes který se má prohledat.|
|`TargetPath`|Vyžaduje se `String` parametr.<br /><br /> Určuje hodnotu, která se má přidat jako metadata.|

## <a name="remarks"></a>Poznámky

 Kromě toho, že mají parametry, které jsou uvedeny v tabulce, tato úloha dědí parametry z třídy <xref:Microsoft.Build.Tasks.TaskExtension>, kterou sám dědí z třídy <xref:Microsoft.Build.Utilities.Task>. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
