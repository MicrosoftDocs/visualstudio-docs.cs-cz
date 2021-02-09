---
title: Metadata položek v dávkování úloh | Microsoft Docs
description: Naučte se, jak nástroj MSBuild používá metadata položek v dávkování úloh k rozdělení seznamů položek do různých kategorií nebo dávek a ke spuštění úlohy jednou za každou dávku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 28451b9bf317c33e1aff52a62247374ea2b6871e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913886"
---
# <a name="item-metadata-in-task-batching"></a>Metadata položek v dávkování úloh

Nástroj MSBuild má možnost rozdělit seznamy položek do různých kategorií nebo dávky na základě metadat položky a spustit úlohu jednou pro každou dávku. Může být matoucí pochopit přesně to, které položky jsou předávány se službou Batch. Toto téma se zabývá následujícími běžnými scénáři, které zahrnují dávkování.

- Rozdělení seznamu položek na dávky

- Dělení několika seznamů položek na dávky

- Dávkování jedné položky v čase

- Filtrování seznamů položek

Další informace o dávkování s nástrojem MSBuild najdete v tématu [dávkování](../msbuild/msbuild-batching.md).

## <a name="divide-an-item-list-into-batches"></a>Rozdělení seznamu položek na dávky

Dávkování umožňuje rozdělit seznam položek do různých dávek založených na metadatech položek a každou dávku předat samostatnému úkolu. To je užitečné při vytváření satelitních sestavení.

Následující příklad ukazuje, jak rozdělit seznam položek na dávky založené na metadatech položky. `ExampColl`Seznam položek je rozdělen na tři dávky na základě `Number` metadat položky. Přítomnost `%(ExampColl.Number)` v `Text` atributu upozorní nástroj MSBuild, že dávkování by mělo být provedeno. `ExampColl`Seznam položek je rozdělen na tři dávky založené na `Number` metadatech a každá dávka se předává do úlohy samostatně.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>
    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

V [úloze zprávy](../msbuild/message-task.md) se zobrazí následující informace:

`Number: 1 -- Items in ExampColl: Item1;Item4`

`Number: 2 -- Items in ExampColl: Item2;Item5`

`Number: 3 -- Items in ExampColl: Item3;Item6`

## <a name="divide-several-item-lists-into-batches"></a>Rozdělení několika seznamů položek na dávky

Nástroj MSBuild dokáže rozdělit více seznamů položek na dávky založené na stejných metadatech. Díky tomu je snadné rozdělit různé seznamy položek na dávky pro sestavení více sestavení. Například můžete mít seznam položek souborů *. cs* rozdělených do dávky aplikace a do dávky sestavení a seznam souborů prostředků rozdělených do dávky aplikace a do dávky sestavení. Potom můžete použít dávkování k předání těchto seznamů položek do jedné úlohy a sestavení aplikace i sestavení.

> [!NOTE]
> Pokud seznam položek předávaných do úkolu neobsahuje žádné položky s odkazovanými metadaty, každá položka v seznamu položek se předává do každé dávky.

Následující příklad ukazuje, jak rozdělit více seznamů položek na dávky založené na metadatech položek. `ExampColl` `ExampColl2` Seznamy položek a jsou rozděleny do tří dávek na základě `Number` metadat položky. Přítomnost `%(Number)` v `Text` atributu upozorní nástroj MSBuild, že dávkování by mělo být provedeno. `ExampColl` `ExampColl2` Seznam položek a je rozdělen na tři dávky založené na `Number` metadatech a každá dávka se předává do úlohy samostatně.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>

        <ExampColl2 Include="Item4">
            <Number>1</Number>
        </ExampColl2>
        <ExampColl2 Include="Item5">
            <Number>2</Number>
        </ExampColl2>
        <ExampColl2 Include="Item6">
            <Number>3</Number>
        </ExampColl2>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>
    </Target>

</Project>
```

V [úloze zprávy](../msbuild/message-task.md) se zobrazí následující informace:

`Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`

`Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`

`Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`

## <a name="batch-one-item-at-a-time"></a>Dávkové zpracování jedné položky najednou

Dávkování lze provést také na známých metadatech položek, které jsou přiřazeny ke každé položce při vytvoření. To zaručuje, že všechny položky v kolekci budou mít některá metadata, která se mají použít pro dávkování. `Identity`Hodnota metadat je pro každou položku jedinečná a je užitečná pro rozdělení každé položky v seznamu položek na samostatnou dávku. Úplný seznam známých metadat položek najdete v tématu [známá metadata položky](../msbuild/msbuild-well-known-item-metadata.md).

Následující příklad ukazuje, jak vytvořit dávku každé položky v seznamu položek v jednom okamžiku. Vzhledem k tomu `Identity` , že hodnota metadat každé položky je jedinečná, `ExampColl` seznam položek je rozdělen na šest dávek, každou dávku obsahující jednu položku seznamu položek. Přítomnost `%(Identity)` v `Text` atributu upozorní nástroj MSBuild, že dávkování by mělo být provedeno.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1"/>
        <ExampColl Include="Item2"/>
        <ExampColl Include="Item3"/>
        <ExampColl Include="Item4"/>
        <ExampColl Include="Item5"/>
        <ExampColl Include="Item6"/>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Identity: '%(Identity)' -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

V [úloze zprávy](../msbuild/message-task.md) se zobrazí následující informace:

```output
Identity: 'Item1' -- Items in ExampColl: Item1
Identity: 'Item2' -- Items in ExampColl: Item2
Identity: 'Item3' -- Items in ExampColl: Item3
Identity: 'Item4' -- Items in ExampColl: Item4
Identity: 'Item5' -- Items in ExampColl: Item5
Identity: 'Item6' -- Items in ExampColl: Item6
```

## <a name="filter-item-lists"></a>Filtrovat seznamy položek

Dávkování lze použít k vyfiltrování určitých položek ze seznamu položek před jejich předáním úkolu. Například filtrování na základě `Extension` hodnoty metadata dobře známé položky umožňuje spustit úlohu pouze v souborech s konkrétní příponou.

Následující příklad ukazuje, jak rozdělit seznam položek na dávky založené na metadatech položky a pak tyto dávky vyfiltrovat, když jsou předány do úlohy. `ExampColl`Seznam položek je rozdělen na tři dávky na základě `Number` metadat položky. `Condition`Atribut úlohy Určuje, že `Number` `2` do úlohy budou předány pouze dávky s hodnotou metadat položky.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>

    </ItemGroup>

    <Target Name="Exec">
        <Message
            Text = "Items in ExampColl: @(ExampColl)"
            Condition="'%(Number)'=='2'"/>
    </Target>

</Project>
```

V [úloze zprávy](../msbuild/message-task.md) se zobrazí následující informace:

```
Items in ExampColl: Item2;Item5
```

## <a name="see-also"></a>Viz také

- [Dobře známá metadata položky](../msbuild/msbuild-well-known-item-metadata.md)
- [Item – Element (MSBuild)](../msbuild/item-element-msbuild.md)
- [ItemMetadata – – element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Dávkování](../msbuild/msbuild-batching.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
