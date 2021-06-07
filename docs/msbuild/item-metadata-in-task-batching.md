---
title: Metadata položek v dávkovém | Microsoft Docs
description: Zjistěte, jak nástroj MSBuild používá metadata položek v dávkování úkolů k rozdělení seznamů položek do různých kategorií nebo dávek a k jednomu spuštění úkolu s každou dávku.
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
ms.openlocfilehash: 1675cf43cb9632d4480265f00a377c1f5c530b51
ms.sourcegitcommit: c5f2a142ebf9f00808314f79a4508a82e6df1198
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2021
ms.locfileid: "111395355"
---
# <a name="item-metadata-in-task-batching"></a>Metadata položek v dávkování úloh

Nástroj MSBuild umožňuje rozdělit seznamy položek do různých kategorií nebo dávek na základě metadat položek a spustit úkol jednou s každou dávku. Může být matoucí přesně pochopit, jaké položky se předá s jakou dávku. Toto téma popisuje následující běžné scénáře, které zahrnují dávkování.

- Rozdělení seznamu položek do dávek

- Rozdělení několika seznamů položek do dávek

- Dávkování po jedné položce

- Filtrování seznamů položek

Další informace o dávkování pomocí nástroje MSBuild najdete v tématu [Dávkování](../msbuild/msbuild-batching.md).

## <a name="divide-an-item-list-into-batches"></a>Rozdělení seznamu položek do dávek

Dávkování umožňuje rozdělit seznam položek do různých dávek na základě metadat položek a předávat jednotlivé dávky do úkolu samostatně. To je užitečné pro vytváření satelitních sestavení.

Následující příklad ukazuje, jak rozdělit seznam položek do dávek na základě metadat položek. Seznam `ExampColl` položek je rozdělen do tří dávek na základě `Number` metadat položky. Přítomnost v `%(ExampColl.Number)` atributu `Text` upozorní nástroj MSBuild, že by mělo být provedeno dávkování. Seznam položek je rozdělen do tří dávek na základě metadat a každá dávka se `ExampColl` `Number` do úkolu předá samostatně.

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

Úloha [Zpráva](../msbuild/message-task.md) zobrazí následující informace:

`Number: 1 -- Items in ExampColl: Item1;Item4`

`Number: 2 -- Items in ExampColl: Item2;Item5`

`Number: 3 -- Items in ExampColl: Item3;Item6`

## <a name="divide-several-item-lists-into-batches"></a>Rozdělení několika seznamů položek do dávek

Nástroj MSBuild může rozdělit více seznamů položek do dávek na základě stejných metadat. To usnadňuje rozdělení různých seznamů položek do dávek pro sestavení více sestavení. Můžete mít například seznam položek se soubory *.cs* rozdělené do dávky aplikace a dávky sestavení a seznam položek souborů prostředků rozdělených do dávky aplikace a dávky sestavení. Pak můžete pomocí dávkování předat tyto seznamy položek do jednoho úkolu a sestavit aplikaci i sestavení.

> [!NOTE]
> Pokud seznam položek předaný úkolu neobsahuje žádné položky s odkazovaným metadatem, předá se každá položka v tomto seznamu položek každé dávce.

Následující příklad ukazuje, jak rozdělit více seznamů položek do dávek na základě metadat položek. Seznamy `ExampColl` `ExampColl2` položek a jsou rozdělené do tří dávek na základě `Number` metadat položky. Přítomnost v `%(Number)` atributu `Text` upozorní nástroj MSBuild, že by mělo být provedeno dávkování. Seznamy položek a jsou rozdělené do tří dávek na základě metadat a každá dávka se `ExampColl` `ExampColl2` do `Number` úkolu předá samostatně.

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

Úloha [Zpráva](../msbuild/message-task.md) zobrazí následující informace:

`Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`

`Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`

`Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`

## <a name="batch-one-item-at-a-time"></a>Dávkové zpracování po jedné položce

Dávkování lze provádět také s metadaty známých položek, která jsou přiřazena ke každé položce při vytvoření. To zaručuje, že každá položka v kolekci bude mít metadata, která se mají použít pro dávkování. Hodnota metadat je užitečná pro rozdělení každé položky v seznamu `Identity` položek do samostatné dávky. Úplný seznam známých metadat položek najdete v tématu Metadata [dobře známých položek.](../msbuild/msbuild-well-known-item-metadata.md)

Následující příklad ukazuje, jak každou položku v seznamu položek dávkova po jedné. Seznam položek je rozdělen do šesti dávek, z nichž každá `ExampColl` obsahuje jednu položku v seznamu položek. Přítomnost v `%(Identity)` atributu `Text` upozorní nástroj MSBuild, že by mělo být provedeno dávkování.

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

Úloha [Zpráva](../msbuild/message-task.md) zobrazí následující informace:

```output
Identity: 'Item1' -- Items in ExampColl: Item1
Identity: 'Item2' -- Items in ExampColl: Item2
Identity: 'Item3' -- Items in ExampColl: Item3
Identity: 'Item4' -- Items in ExampColl: Item4
Identity: 'Item5' -- Items in ExampColl: Item5
Identity: 'Item6' -- Items in ExampColl: Item6
```

Není však `Identity` zaručeno, že bude jedinečný; jeho hodnota je vyhodnocená konečná hodnota `Include` atributu. Proto pokud se `Include` nějaké atributy používají vícekrát, jsou dávkové. Jak ukazuje následující příklad, tato technika vyžaduje, aby atributy byly `Include` jedinečné pro každou položku ve skupině. Pro ilustraci tohoto bodu zvažte následující kód:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Item Include="1">
      <M>1</M>
    </Item>
    <Item Include="1">
      <M>2</M>
    </Item>
    <Item Include="2">
      <M>3</M>
    </Item>
  </ItemGroup>

  <Target Name="Batching">
    <Warning Text="@(Item->'%(Identity): %(M)')" Condition=" '%(Identity)' != '' "/>
  </Target>
</Project>
```

Výstup ukazuje, že první dvě položky jsou ve stejné dávce, protože atribut je `Include` pro ně stejný:

```output
test.proj(15,5): warning : 1: 1;1: 2
test.proj(15,5): warning : 2: 3
```

## <a name="filter-item-lists"></a>Filtrování seznamů položek

Dávkování lze použít k odfiltrování určitých položek ze seznamu položek před jejich předáním úkolu. Například filtrování hodnoty metadat dobře známé položky umožňuje spustit úlohu pouze u souborů s `Extension` konkrétní příponou.

Následující příklad ukazuje, jak rozdělit seznam položek do dávek na základě metadat položek a pak tyto dávky filtrovat, když jsou předány do úkolu. Seznam `ExampColl` položek je rozdělen do tří dávek na základě `Number` metadat položky. Atribut úkolu určuje, že se do úlohy předá pouze dávky s hodnotou `Condition` `Number` metadat položky `2` .

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

Úloha [Zpráva](../msbuild/message-task.md) zobrazí následující informace:

```
Items in ExampColl: Item2;Item5
```

## <a name="see-also"></a>Viz také

- [Metadata dobře známých položek](../msbuild/msbuild-well-known-item-metadata.md)
- [Item – element (MSBuild)](../msbuild/item-element-msbuild.md)
- [ItemMetadata – element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Dávkování](../msbuild/msbuild-batching.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
