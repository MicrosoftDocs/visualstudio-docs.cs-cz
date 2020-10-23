---
title: Úloha FindAppConfigFile – | Microsoft Docs
description: Naučte se pomocí úlohy MSBuild FindAppConfigFile – najít soubor app.config, pokud existuje, v uvedených seznamech.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d186a72bcc7af18671c279ff392de066b6fd9fee
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2020
ms.locfileid: "92435674"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile – úloha

Vyhledá soubor *app.config* , pokud existuje, v zadaných seznamech.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `FindAppConfigFile` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AppConfigFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje první vyhovující položku, která se nachází v seznamu, pokud existuje.|
|`PrimaryList`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje primární seznam, pomocí kterého se bude hledat.|
|`SecondaryList`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje sekundární seznam, přes který se má prohledat.|
|`TargetPath`|Požadovaný parametr `String`.<br /><br /> Určuje hodnotu, která se má přidat jako metadata.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
