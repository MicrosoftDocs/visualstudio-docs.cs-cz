---
title: Úkol dotykového ovládání | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Touch
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Touch task
- Touch task [MSBuild]
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 873783196a3eebdaca9cc4278b091e084c1488b0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631650"
---
# <a name="touch-task"></a>Touch – úloha

Nastaví dobu přístupu a úprav souborů.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `Touch` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AlwaysCreate`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`vytvoří všechny soubory, které ještě neexistují.|
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje kolekci souborů, kterých se má dotknout.|
|`ForceTouch`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`vynutí dotyk souboru, i když jsou soubory jen pro čtení.|
|`Time`|Volitelný `String` parametr.<br /><br /> Určuje jiný čas než aktuální čas. Formát musí být formát, který je <xref:System.DateTime.Parse%2A> přijatelný pro metodu.|
|`TouchedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje kolekci položek, které byly úspěšně dotkl.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad používá `Touch` úkol ke změně doby přístupu a `Files` úprav y souborů zadaných v kolekci `FilesTouched` položek a umístí seznam úspěšně dotčených souborů do kolekce položek.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

<ItemGroup>
    <Files Include="File1.cs;File2.cs;File3.cs" />
</ItemGroup>

    <Target Name="TouchFiles">
        <Touch
            Files="@(Files)">
            <Output
                TaskParameter="TouchedFiles"
                ItemName="FilesTouched"/>
    </Touch>
</Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
