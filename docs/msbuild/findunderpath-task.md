---
title: Úloha FindUnderPath – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d97b727dcba8cd16fe97ee33764947797c36db7
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634133"
---
# <a name="findunderpath-task"></a>FindUnderPath – úloha

Určuje, které položky v zadané kolekci položek mají cesty, které jsou v zadané složce nebo pod ní.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy `FindUnderPath`.

|Parametr|Popis|
|---------------|-----------------|
|`Files`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje soubory, jejichž cesty by měly být porovnány s cestou určenou parametrem `Path`.|
|`InPath`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje položky, které byly nalezeny v zadané cestě.|
|`OutOfPath`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje položky, které nebyly nalezeny v zadané cestě.|
|`Path`|Vyžaduje se <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje cestu ke složce, která se má použít jako odkaz.|
|`UpdateToAbsolutePaths`|Volitelný parametr `Boolean`.<br /><br /> Pokud má hodnotu true, cesty výstupních položek se aktualizují tak, aby byly absolutní cesty.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá úlohu `FindUnderPath` k určení, zda soubory obsažené v `MyFiles` položce mají cesty, které existují v cestě určené vlastností `SearchPath`. Po dokončení úlohy `FilesNotFoundInPath` položka obsahuje soubor *Soubor1. txt* a položka `FilesFoundInPath` obsahuje soubor *Soubor2. txt* .

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyFiles Include="C:\File1.txt" />
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />
    </ItemGroup>

    <PropertyGroup>
        <SearchPath>C:\Projects\MyProject</SearchPath>
    </PropertyGroup>

    <Target Name="FindFiles">
        <FindUnderPath
            Files="@(MyFiles)"
            Path="$(SearchPath)">
            <Output
                TaskParameter="InPath"
                ItemName="FilesFoundInPath" />
            <Output
                TaskParameter="OutOfPath"
                ItemName="FilesNotFoundInPath" />
        </FindUnderPath>
    </Target>

</Project>
```

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
