---
title: MSBuild dávkování | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 78aeef8ea651aac1fe2a780207474399f4bbcf09
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633431"
---
# <a name="msbuild-batching"></a>Dávkování msbuildu

MSBuild má schopnost rozdělit seznamy položek do různých kategorií nebo listy na základě metadat položky a spustit cíl nebo úkol jednou s každou dávkou.

## <a name="task-batching"></a>Dávkování úloh

Dávkování úkolů umožňuje zjednodušit soubory projektu tím, že poskytuje způsob, jak rozdělit seznamy položek do různých dávek a předat každou z těchto dávek do úkolu samostatně. To znamená, že soubor projektu musí mít pouze úkol a jeho atributy deklarované jednou, i když jej lze spustit několikrát.

Určíte, že chcete, aby MSBuild prováděl dávkování s\<úkolem pomocí notace %( ItemMetaDataName>) v jednom z atributů úkolu. Následující příklad rozdělí `Example` seznam položek na dávky `Color` na základě hodnoty metadat položky a `MyTask` předá každou dávku úkolu samostatně.

> [!NOTE]
> Pokud neodkazujete na seznam položek jinde v atributech úkolu nebo název metadat může být\<nejednoznačný, můžete použít notaci %( ItemCollection.ItemMetaDataName>) k úplnému kvalifikaci hodnoty metadat položky, která má být pro dávkování.

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

Konkrétní příklady dávkování naleznete [v tématu Metadata položky v dávkování úloh](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Cílové dávkování

MSBuild zkontroluje, zda vstupy a výstupy cíle jsou aktuální před spuštěním cíle. Pokud jsou vstupy i výstupy aktuální, cíl je přeskočen. Pokud úloha uvnitř cíle používá dávkování, MSBuild potřebuje určit, zda vstupy a výstupy pro každou dávku položek je aktuální. V opačném případě je cíl proveden pokaždé, když je přístupů.

Následující příklad ukazuje `Target` prvek, `Outputs` který obsahuje atribut\<s notací %( ItemMetaDataName>). MSBuild rozdělí `Example` seznam položek na dávky `Color` na základě metadat položky a analyzovat časová razítka výstupních souborů pro každou dávku. Pokud výstupy z dávky nejsou aktuální, cíl je spuštěn. V opačném případě je cíl přeskočen.

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

Další příklad cílového dávkování naleznete [v tématu Metadata položky v cílové dávkování](../msbuild/item-metadata-in-target-batching.md).

## <a name="property-functions-using-metadata"></a>Funkce vlastností pomocí metadat

Dávkování lze řídit funkcemi vlastností, které obsahují metadata. Například:

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

používá <xref:System.IO.Path.Combine%2A> ke zkombinování cesty kořenové složky s cestou compile položky.

Funkce vlastností se nemusí zobrazit v rámci hodnot metadat. Například:

`%(Compile.FullPath.Substring(0,3))`

není povoleno.

Další informace o funkcích vlastností naleznete v [tématu Property functions](../msbuild/property-functions.md).

## <a name="see-also"></a>Viz také

- [Element ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
