---
title: AktualizovatManifest úkol | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25e410ba3122e0065f92186195ee5a82d6a55c2f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631339"
---
# <a name="updatemanifest-task"></a>UpdateManifest – úloha

Aktualizuje vybrané vlastnosti v manifestu a odstoupí.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `UpdateManifest` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`ApplicationManifest`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje manifest aplikace.|
|`ApplicationPath`|Požadovaný parametr `String`.<br /><br /> Určuje cestu manifestu aplikace.|
|`InputManifest`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje manifest, který má být aktualizován.|
|`OutputManifest`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje manifest, který obsahuje aktualizované vlastnosti.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha <xref:Microsoft.Build.Utilities.Task> dědí parametry z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [Základní třída úlohy](../msbuild/task-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)