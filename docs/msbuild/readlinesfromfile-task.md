---
title: Úloha ReadLinesFromFile – | Microsoft Docs
description: Přečtěte si, jak MSBuild používá úlohu ReadLinesFromFile – ke čtení seznamu položek z textového souboru. Soubor musí mít jednu položku na každém řádku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ReadLinesFromFile task
- ReadLinesFromFile task [MSBuild]
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff2c43af40ea429714f0624db67c53fa46eb6427
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048777"
---
# <a name="readlinesfromfile-task"></a>ReadLinesFromFile – úloha

Přečte seznam položek z textového souboru.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `ReadLinesFromFile` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`File`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje soubor, který se má číst. Soubor musí mít jednu položku na každém řádku.|
|`Lines`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje řádky načtené ze souboru.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad používá `ReadLinesFromFile` úlohu k vytvoření položek ze seznamu v textovém souboru. Položky načtené ze souboru jsou uloženy v `ItemsFromFile` kolekci položek.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
    </ItemGroup>

    <Target Name="ReadFromFile">
        <ReadLinesFromFile
            File="@(MyTextFile)" >
            <Output
                TaskParameter="Lines"
                ItemName="ItemsFromFile"/>
        </ReadLinesFromFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
