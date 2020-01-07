---
title: Dotyková úloha | Microsoft Docs
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
ms.openlocfilehash: 4d34d8edca64987f9b6c4648bef1f239aca4d5ba
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594939"
---
# <a name="touch-task"></a>Touch – úloha
Nastaví dobu přístupu a úprav souborů.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `Touch`.

|Parametr|Popis|
|---------------|-----------------|
|`AlwaysCreate`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vytvoří soubory, které ještě neexistují.|
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje kolekci souborů, které se mají kontaktovat.|
|`ForceTouch`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vynutí soubor dotykový i v případě, že jsou soubory jen pro čtení.|
|`Time`|Volitelný parametr `String`.<br /><br /> Určuje jiný čas než aktuální čas. Formát musí být formát, který je přijatelný pro metodu <xref:System.DateTime.Parse%2A>.|
|`TouchedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje kolekci položek, které byly úspěšně změněny.|

## <a name="remarks"></a>Poznámky
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad
 Následující příklad používá úlohu `Touch` ke změně doby přístupu a úprav souborů zadaných v kolekci položek `Files` a k vložení seznamu úspěšně dodaných souborů do kolekce `FilesTouched` položek.

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

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
