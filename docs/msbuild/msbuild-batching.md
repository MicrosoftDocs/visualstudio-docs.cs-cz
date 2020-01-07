---
title: Dávkování nástroje MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d62e1824d72933d8cb5c3c345ed8788435a6f20
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592097"
---
# <a name="msbuild-batching"></a>Dávkování nástroje MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] má možnost rozdělit seznamy položek do různých kategorií nebo dávky na základě metadat položky a spustit cíl nebo úlohu jednou pro každou dávku.

## <a name="task-batching"></a>Dávkování úloh
Dávkování úloh umožňuje zjednodušit soubory projektu tím, že poskytuje způsob, jak rozdělit seznamy položek do různých dávek a předat každou z těchto dávek do úlohy samostatně. To znamená, že soubor projektu potřebuje mít úlohu a její atributy deklarované pouze jednou, i když je možné ji spustit několikrát.

V jednom z atributů úlohy určíte, že má [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] provádět dávkování s úkolem pomocí notace%(\<ItemMetaDataName >). Následující příklad rozdělí seznam `Example` položky na dávky založené na hodnotě metadat `Color` položky a všechny dávky předává do úlohy `MyTask` samostatně.

> [!NOTE]
> Pokud neodkazujte na seznam položek jinde v atributech úlohy nebo název metadat může být nejednoznačný, můžete použít notaci%(\<ItemCollection. ItemMetaDataName >) k úplnému zařazení hodnoty metadat položky, která se má použít pro dávkování.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Konkrétnější příklady dávkování najdete [v tématu Metadata položek v dávkování úloh](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Dávkování cíle
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kontroluje, zda jsou vstupy a výstupy cíle aktuální, než spustí cíl. Pokud jsou vstupy i výstupy aktuální, přeskočí se cíl. Pokud úloha v cíli používá dávkování, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nutné určit, jestli jsou vstupy a výstupy pro každou dávku položek aktuální. V opačném případě se cíl spustí pokaždé, když je dosaženo.

Následující příklad ukazuje `Target` element, který obsahuje atribut `Outputs` se zápisem%(\<ItemMetaDataName >). [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rozdělí seznam položek `Example` na dávky založené na metadatech `Color` položky a analyzuje časová razítka výstupních souborů pro každou dávku. Pokud výstupy z dávky nejsou aktuální, je cíl spuštěn. V opačném případě se cíl přeskočí.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Další příklad cílového dávkování najdete v tématu [Metadata položek v cílové dávce](../msbuild/item-metadata-in-target-batching.md).

## <a name="property-functions-using-metadata"></a>Funkce vlastností pomocí metadat
Dávkování lze řídit funkcemi vlastností, které zahrnují metadata. Například

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

používá <xref:System.IO.Path.Combine%2A> ke kombinování cesty ke kořenové složce s cestou položky kompilace.

Funkce vlastností se nesmí vyskytovat v hodnotách metadat. Například

`%(Compile.FullPath.Substring(0,3))`

není povoleno.

Další informace o funkcích vlastností naleznete v tématu [funkce vlastností](../msbuild/property-functions.md).

## <a name="see-also"></a>Viz také:
- [ItemMetadata – – element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
