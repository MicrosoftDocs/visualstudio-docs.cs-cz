---
title: Úloha UpdateManifest – | Microsoft Docs
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
ms.openlocfilehash: 215092d7fbcee8ec30210dd8332bc6ae5b7ad412
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578274"
---
# <a name="updatemanifest-task"></a>UpdateManifest – úloha
Aktualizuje vybrané vlastnosti v manifestu a znovu se podepíše.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `UpdateManifest`.

|Parametr|Popis|
|---------------|-----------------|
|`ApplicationManifest`|Vyžaduje se <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje manifest aplikace.|
|`ApplicationPath`|Vyžaduje se `String` parametr.<br /><br /> Určuje cestu k manifestu aplikace.|
|`InputManifest`|Vyžaduje se <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje manifest, který se má aktualizovat.|
|`OutputManifest`|Volitelný výstupní parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje manifest, který obsahuje aktualizované vlastnosti.|

## <a name="remarks"></a>Poznámky
 Kromě parametrů uvedených v tabulce zdědí tento úkol parametry z třídy <xref:Microsoft.Build.Utilities.Task>. Seznam těchto dalších parametrů a jejich popisů naleznete v tématu [základní třída Task](../msbuild/task-base-class.md).

## <a name="see-also"></a>Viz také
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)