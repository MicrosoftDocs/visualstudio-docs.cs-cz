---
title: Úloha ConvertToAbsolutePath – | Microsoft Docs
description: Použijte úlohu ConvertToAbsolutePath – MSBuild k převedení relativní cesty nebo odkazu na absolutní cestu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ConvertToAbsolutePath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ConvertToAbsolutePath task [MSBuild]
- MSBuild, ConvertToAbsolutePath task
ms.assetid: f1af2cb8-b4ef-4a72-be80-22fa526c4491
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ecf9695b36f341fa350abf53062e70095c03c374
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796157"
---
# <a name="converttoabsolutepath-task"></a>ConvertToAbsolutePath – úloha

Převede relativní cestu nebo odkaz na absolutní cestu.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `ConvertToAbsolutePath` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Paths`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Seznam relativních cest, které chcete převést na absolutní cesty.|
|`AbsolutePaths`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Seznam absolutních cest pro položky, které byly předány.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
