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
ms.openlocfilehash: 155e8e6b57cc388e8c2981297be8b26ef5444c1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634315"
---
# <a name="createproperty-task"></a>CreateProperty – úloha

Naplní vlastnosti pomocí předaných hodnot. To umožňuje zkopírování hodnot z jedné vlastnosti nebo řetězce do jiného.

## <a name="attributes"></a>Atributy

Následující tabulka popisuje parametry `CreateProperty` úkolu.

| Parametr | Popis |
|------------------| - |
| `Value` | Volitelný `String` výstupní parametr.<br /><br /> Určuje hodnotu, která má být zkopírována do nové vlastnosti. |
| `ValueSetByTask` | Volitelný `String` výstupní parametr.<br /><br /> Obsahuje stejnou hodnotu jako `Value` parametr. Tento parametr použijte pouze v případě, že chcete zabránit tomu, aby vlastnost Output byla nastavena nástrojem MSBuild, když přeskočí nadřazený cíl, protože výstupy jsou aktuální. |

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá `CreateProperty` úlohu k vytvoření `NewFile` vlastnosti pomocí kombinace hodnot `SourceFilename` `SourceFileExtension` vlastnosti a.

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

Po spuštění projektu `NewFile` je hodnota vlastnosti *Module1. vb*.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
