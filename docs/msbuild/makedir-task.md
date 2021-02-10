---
title: Úloha MakeDir – | Microsoft Docs
description: Naučte se, jak MSBuild používá úlohu MakeDir – k vytváření adresářů a v případě potřeby i všech nadřazených adresářů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MakeDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MakeDir task [MSBuild]
- MSBuild, MakeDir task
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa7b853ea6706c4958635c399bbc6134e823223c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966224"
---
# <a name="makedir-task"></a>MakeDir – úloha

Vytvoří adresáře a v případě potřeby i všechny nadřazené adresáře.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `MakeDir` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Directories`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Sada adresářů, které se mají vytvořit.|
|`DirectoriesCreated`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Adresáře, které jsou vytvořeny touto úlohou. Pokud některé adresáře nelze vytvořit, nemusí obsahovat všechny položky, které byly předány do `Directories` parametru.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad kódu používá `MakeDir` úlohu k vytvoření adresáře určeného `OutputDirectory` vlastností.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <OutputDirectory>\Output\</OutputDirectory>
    </PropertyGroup>

    <Target Name="CreateDirectories">
        <MakeDir
            Directories="$(OutputDirectory)"/>
    </Target>

</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
