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
ms.openlocfilehash: 235f96b3d67b0ad2e3c3bd1c486c5c9f2eeb86c2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596005"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates – úloha
Odstraní duplicitní položky ze zadané kolekce položek.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `RemoveDuplicates`.

|Parametr|Popis|
|---------------|-----------------|
|`Filtered`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje kolekci položek s odebranými duplicitními položkami. Pořadí vstupních položek je zachováno a zachová první instanci každé duplicitní položky.|
|`Inputs`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Kolekce položek, ze které se mají odebrat duplicitní položky|

## <a name="remarks"></a>Poznámky
 U této úlohy se nerozlišují malá a velká písmena a při určování duplicitních hodnot se neshodují metadata položek.

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad
 Následující příklad používá úlohu `RemoveDuplicates` k odebrání duplicitních položek z kolekce `MyItems` Item. Po dokončení úkolu obsahuje kolekce `FilteredItems` položky jednu položku.

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

 Následující příklad ukazuje, že úloha `RemoveDuplicates` zachovává vstupní objednávku. Po dokončení úkolu obsahuje kolekce `FilteredItems` položky položky *MyFile2.cs*, *MyFile1.cs*a *MyFile3.cs* v tomto pořadí.

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

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
