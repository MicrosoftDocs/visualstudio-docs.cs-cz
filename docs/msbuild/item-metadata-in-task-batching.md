---
title: Metadata položky v dávkování úloh | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92613b96d5d85a959e3426df86168c7110b74fed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633652"
---
# <a name="item-metadata-in-task-batching"></a>Metadata položky v dávkování úloh

MSBuild má schopnost rozdělit seznamy položek do různých kategorií nebo dávek na základě metadat položky a spustit úlohu jednou s každou dávkou. Může být matoucí přesně pochopit, jaké položky jsou předávány s jakou dávkou. Toto téma popisuje následující běžné scénáře, které zahrnují dávkování.

- Rozdělení seznamu položek na dávky

- Rozdělení několika seznamů položek na dávky

- Dávkování jedné položky najednou

- Filtrování seznamů položek

Další informace o dávkování s MSBuild, naleznete v [tématu dávkování](../msbuild/msbuild-batching.md).

## <a name="divide-an-item-list-into-batches"></a>Rozdělení seznamu položek na dávky

Dávkování umožňuje rozdělit seznam položek do různých dávek na základě metadat položky a předat každou z dávek do úkolu samostatně. To je užitečné pro vytváření satelitních sestavení.

Následující příklad ukazuje, jak rozdělit seznam položek do dávek na základě metadat položky. Seznam `ExampColl` položek je rozdělen do tří dávek `Number` na základě metadat položky. Přítomnost `%(ExampColl.Number)`v atributu `Text` upozorní MSBuild, že dávkování by mělo být provedeno. Seznam `ExampColl` položek je rozdělen do tří dávek `Number` na základě metadat a každá dávka je předána samostatně do úlohy.

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

[Úloha Zpráva](../msbuild/message-task.md) zobrazuje následující informace:

`Number: 1 -- Items in ExampColl: Item1;Item4`

`Number: 2 -- Items in ExampColl: Item2;Item5`

`Number: 3 -- Items in ExampColl: Item3;Item6`

## <a name="divide-several-item-lists-into-batches"></a>Rozdělení několika seznamů položek do dávek

MSBuild můžete rozdělit více seznamů položek do dávek na základě stejných metadat. To usnadňuje rozdělení různých seznamů položek do dávek a sestavení více sestavení. Můžete mít například seznam položek *souborů CS* rozdělený na dávku aplikace a dávku sestavení a seznam položek souborů prostředků rozdělený na dávku aplikace a dávku sestavení. Potom můžete použít dávkování předat tyto seznamy položek do jednoho úkolu a sestavení aplikace a sestavení.

> [!NOTE]
> Pokud seznam položek předaný do úkolu neobsahuje žádné položky s odkazovanými metadaty, každá položka v tomto seznamu položek je předána do každé dávky.

Následující příklad ukazuje, jak rozdělit více seznam položek do dávek na základě metadat položky. `ExampColl` Seznamy `ExampColl2` a položky jsou rozděleny do `Number` tří dávek na základě metadat položky. Přítomnost `%(Number)`v atributu `Text` upozorní MSBuild, že dávkování by mělo být provedeno. `ExampColl` Seznamy `ExampColl2` a položky jsou rozděleny do `Number` tří dávek na základě metadat a každá dávka je předána samostatně do úlohy.

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

[Úloha Zpráva](../msbuild/message-task.md) zobrazuje následující informace:

`Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`

`Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`

`Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`

## <a name="batch-one-item-at-a-time"></a>Dávka po jedné položce

Dávkování lze také provést na známé položky metadata, která je přiřazena ke každé položce při vytváření. To zaručuje, že každá položka v kolekci bude mít některá metadata pro dávkování. Hodnota `Identity` metadat je jedinečná pro každou položku a je užitečná pro rozdělení každé položky v seznamu položek do samostatné dávky. Úplný seznam známých metadat položek naleznete v [tématu Známá metadata položek](../msbuild/msbuild-well-known-item-metadata.md).

Následující příklad ukazuje, jak dávkovat každou položku v seznamu položek po jednom. Vzhledem `Identity` k tomu, že hodnota `ExampColl` metadat každé položky je jedinečná, je seznam položek rozdělen do šesti dávek, z nichž každá obsahuje jednu položku seznamu položek. Přítomnost `%(Identity)`v atributu `Text` upozorní MSBuild, že dávkování by mělo být provedeno.

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

[Úloha Zpráva](../msbuild/message-task.md) zobrazuje následující informace:

```output
Identity: 'Item1' -- Items in ExampColl: Item1
Identity: 'Item2' -- Items in ExampColl: Item2
Identity: 'Item3' -- Items in ExampColl: Item3
Identity: 'Item4' -- Items in ExampColl: Item4
Identity: 'Item5' -- Items in ExampColl: Item5
Identity: 'Item6' -- Items in ExampColl: Item6
```

## <a name="filter-item-lists"></a>Filtrování seznamů položek

Dávkování lze odfiltrovat určité položky ze seznamu položek před předáním úkolu. Například filtrování `Extension` na známé hodnotě metadat položky umožňuje spustit úlohu pouze na souborech s určitou příponou.

Následující příklad ukazuje, jak rozdělit seznam položek do dávek na základě metadat položky a potom filtrovat tyto dávky, když jsou předány do úkolu. Seznam `ExampColl` položek je rozdělen do tří dávek `Number` na základě metadat položky. Atribut `Condition` úlohy určuje, že do úkolu `Number` `2` budou předány pouze dávky s hodnotou metadat položky.

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

[Úloha Zpráva](../msbuild/message-task.md) zobrazuje následující informace:

```
Items in ExampColl: Item2;Item5
```

## <a name="see-also"></a>Viz také

- [Známá metadata položek](../msbuild/msbuild-well-known-item-metadata.md)
- [Prvek položky (MSBuild)](../msbuild/item-element-msbuild.md)
- [Element ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Dávkování](../msbuild/msbuild-batching.md)
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
