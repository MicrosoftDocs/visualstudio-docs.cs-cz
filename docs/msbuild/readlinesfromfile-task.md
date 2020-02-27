---
title: Úloha ReadLinesFromFile – | Microsoft Docs
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
ms.openlocfilehash: 7c926c131fab101563841bea3362e88e27674226
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632898"
---
# <a name="readlinesfromfile-task"></a>ReadLinesFromFile – úloha

Přečte seznam položek z textového souboru.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy `ReadLinesFromFile`.

|Parametr|Popis|
|---------------|-----------------|
|`File`|Vyžaduje se <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje soubor, který se má číst. Soubor musí mít jednu položku na každém řádku.|
|`Lines`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje řádky načtené ze souboru.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad používá úlohu `ReadLinesFromFile` k vytvoření položek ze seznamu v textovém souboru. Položky načtené ze souboru jsou uloženy v kolekci `ItemsFromFile` položky.

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

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
