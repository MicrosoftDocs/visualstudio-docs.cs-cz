---
title: Úloha ReadLinesFromFile | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632898"
---
# <a name="readlinesfromfile-task"></a>ReadLinesFromFile – úloha

Načte seznam položek z textového souboru.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `ReadLinesFromFile` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`File`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje soubor, který má být přečten. Soubor musí mít jednu položku na každém řádku.|
|`Lines`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje řádky přečtené ze souboru.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad používá `ReadLinesFromFile` úkol k vytvoření položek ze seznamu v textovém souboru. Položky přečtené ze souboru `ItemsFromFile` jsou uloženy v kolekci položek.

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
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
