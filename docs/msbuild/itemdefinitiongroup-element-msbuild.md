---
title: ItemDefinitionGroup – Element (MSBuild) | Microsoft Docs
description: Naučte se, jak MSBuild používá element ItemDefinitionGroup k definování sady definic položek, hodnot metadat, které jsou použity pro všechny položky v projektu.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 466c753f986eeda233a7ff32bd51fa3e42b3f796
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913895"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>ItemDefinitionGroup – Element (MSBuild)

`ItemDefinitionGroup`Element umožňuje definovat sadu definic položek, což jsou hodnoty metadat, které jsou aplikovány na všechny položky v projektu, ve výchozím nastavení. ItemDefinitionGroup nahrazuje nutnost použití [úlohy CreateItem –](../msbuild/createitem-task.md) a [úkolu CreateProperty –](../msbuild/createproperty-task.md). Další informace naleznete v tématu [Definice položek](../msbuild/item-definitions.md).

\<Project>
\<ItemDefinitionGroup>

## <a name="syntax"></a>Syntax

```xml
<ItemDefinitionGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemDefinitionGroup>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Condition`|Nepovinný atribut. Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Položka](../msbuild/item-element-msbuild.md)|Definuje vstupy procesu sestavení. Může existovat nula nebo více `Item` prvků v `ItemDefinitionGroup` .|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu MSBuild. |

## <a name="example"></a>Příklad

Následující příklad kódu definuje dvě položky metadat, m a n v ItemDefinitionGroup. V tomto příkladu se výchozí metadata "m" aplikují na položku "i", protože metadata "m" nejsou explicitně definována položkou "i". Výchozí metadata "n" však nejsou použita na položku "i", protože metadata "n" jsou již definována položkou "i".

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemDefinitionGroup>
        <i>
            <m>m1</m>
            <n>n1</n>
        </i>
    </ItemDefinitionGroup>
    <ItemGroup>
        <i Include="a">
            <o>o1</o>
            <n>n2</n>
        </i>
    </ItemGroup>
    ...
</Project>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Položky](../msbuild/msbuild-items.md)
