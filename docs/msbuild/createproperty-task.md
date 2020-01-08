---
title: Úloha CreateProperty – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cac0af3371a5c4ae385cc19367b360b8e8f608fd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590056"
---
# <a name="createproperty-task"></a>CreateProperty – úloha
Naplní vlastnosti pomocí předaných hodnot. To umožňuje zkopírování hodnot z jedné vlastnosti nebo řetězce do jiného.

## <a name="attributes"></a>Atributy
Následující tabulka popisuje parametry úlohy `CreateProperty`.

| Parametr | Popis |
|------------------| - |
| `Value` | Volitelný výstupní parametr `String`.<br /><br /> Určuje hodnotu, která má být zkopírována do nové vlastnosti. |
| `ValueSetByTask` | Volitelný výstupní parametr `String`.<br /><br /> Obsahuje stejnou hodnotu jako parametr `Value`. Tento parametr použijte pouze v případě, že chcete zabránit tomu, aby vlastnost Output byla nastavena [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], když přeskočí nadřazený cíl, protože výstupy jsou aktuální. |

## <a name="remarks"></a>Poznámky
Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad
Následující příklad používá úlohu `CreateProperty` k vytvoření vlastnosti `NewFile` pomocí kombinace hodnot vlastnosti `SourceFilename` a `SourceFileExtension`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <SourceFilename>Module1</SourceFilename>
        <SourceFileExtension>vb</SourceFileExtension>
    </PropertyGroup>

    <Target Name="CreateProperties">

        <CreateProperty
            Value="$(SourceFilename).$(SourceFileExtension)">
            <Output
                TaskParameter="Value"
                PropertyName="NewFile" />
        </CreateProperty>

    </Target>

</Project>
```

Po spuštění projektu je hodnota vlastnosti `NewFile` *Module1. vb*.

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
