---
title: Úloha CreateProperty – | Microsoft Docs
description: Použijte úlohu CreateProperty – MSBuild k naplnění vlastností předaných hodnot, což umožní zkopírování hodnot z jedné vlastnosti nebo řetězce do jiného.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ea412f67629998eab035b8cca79111659ab8a0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901372"
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
