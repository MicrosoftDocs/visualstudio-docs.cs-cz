---
title: Úloha RemoveDuplicates – | Microsoft Docs
ms.date: 03/01/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90366bab14eefd1be4edac81d6b09b3f57aa3332
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632781"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates – úloha

Odstraní duplicitní položky ze zadané kolekce položek.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `RemoveDuplicates` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Filtered`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje kolekci položek s odebranými duplicitními položkami. Pořadí vstupních položek je zachováno a zachová první instanci každé duplicitní položky.|
|`Inputs`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Kolekce položek, ze které se mají odebrat duplicitní položky|

## <a name="remarks"></a>Poznámky

 U této úlohy se nerozlišují malá a velká písmena a při určování duplicitních hodnot se neshodují metadata položek.

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad používá `RemoveDuplicates` úlohu k odebrání duplicitních položek z `MyItems` kolekce položek. Po dokončení úkolu `FilteredItems` kolekce položek obsahuje jednu položku.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile.cs"/>
        <MyItems Include="MyFile.cs">
            <Culture>fr</Culture>
        </MyItems>
        <MyItems Include="myfile.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

 Následující příklad ukazuje, že `RemoveDuplicates` úloha zachovává svou vstupní objednávku. Po dokončení úlohy `FilteredItems` kolekce položek obsahuje položky *MyFile2.cs*, *MyFile1.cs*a *MyFile3.cs* v tomto pořadí.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile2.cs"/>
        <MyItems Include="MyFile1.cs" />
        <MyItems Include="MyFile3.cs" />
        <MyItems Include="myfile1.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
