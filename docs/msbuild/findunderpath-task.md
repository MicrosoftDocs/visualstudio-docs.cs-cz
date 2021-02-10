---
title: Úloha FindUnderPath – | Microsoft Docs
description: Pomocí úlohy MSBuild FindUnderPath – můžete vyhledat položky v zadané kolekci položek s cestami v zadané složce nebo pod ní.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 82275b14fbda0d63e6235b87b55a0dbb5f2416b0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949425"
---
# <a name="findunderpath-task"></a>FindUnderPath – úloha

Určuje, které položky v zadané kolekci položek mají cesty, které jsou v zadané složce nebo pod ní.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `FindUnderPath` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Files`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje soubory, jejichž cesty by měly být porovnány s cestou zadanou `Path` parametrem.|
|`InPath`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje položky, které byly nalezeny v zadané cestě.|
|`OutOfPath`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje položky, které nebyly nalezeny v zadané cestě.|
|`Path`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje cestu ke složce, která se má použít jako odkaz.|
|`UpdateToAbsolutePaths`|Volitelný `Boolean` parametr.<br /><br /> Pokud má hodnotu true, cesty výstupních položek se aktualizují tak, aby byly absolutní cesty.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá `FindUnderPath` úlohu k určení, zda soubory obsažené v `MyFiles` položce mají cesty, které existují v cestě určené `SearchPath` vlastností. Po dokončení úkolu `FilesNotFoundInPath` položka obsahuje soubor *File1.txt* a `FilesFoundInPath` položka obsahuje *File2.txt* soubor.

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

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
