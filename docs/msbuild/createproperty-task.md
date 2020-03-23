---
title: Úloha Vytvořit vlastnost | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634315"
---
# <a name="createproperty-task"></a>CreateProperty – úloha

Naplní vlastnosti předanými hodnotami. To umožňuje zkopírovat hodnoty z jedné vlastnosti nebo řetězce do jiného.

## <a name="attributes"></a>Atributy

Následující tabulka popisuje parametry `CreateProperty` úkolu.

| Parametr | Popis |
|------------------| - |
| `Value` | Volitelný `String` výstupní parametr.<br /><br /> Určuje hodnotu, která se má kopírovat do nové vlastnosti. |
| `ValueSetByTask` | Volitelný `String` výstupní parametr.<br /><br /> Obsahuje stejnou hodnotu `Value` jako parametr. Tento parametr použijte pouze v případě, že chcete zabránit tomu, aby výstupní vlastnost nastavená msbuild, když přeskočí ohraničující cíl, protože výstupy jsou aktuální. |

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá `CreateProperty` úkol k `NewFile` vytvoření vlastnosti pomocí kombinace `SourceFilename` `SourceFileExtension` hodnot vlastnosti a.

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

Po spuštění projektu je hodnota `NewFile` vlastnosti *Module1.vb*.

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
