---
title: Prvek ItemDefinitionGroup (MSBuild) | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21e3b6554a9d6e0024cc21fd898962177acfffa7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633626"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>Element ItemDefinitionGroup (MSBuild)

Prvek `ItemDefinitionGroup` umožňuje definovat sadu definic položek, které jsou hodnoty metadat, které jsou použity pro všechny položky v projektu, ve výchozím nastavení. ItemDefinitionGroup nahrazuje potřebu použít [úlohu CreateItem](../msbuild/createitem-task.md) a [úlohu CreateProperty](../msbuild/createproperty-task.md). Další informace naleznete v [tématu Definice položek](../msbuild/item-definitions.md).

\<Projekt \<> ItemDefinitionGroup>

## <a name="syntax"></a>Syntaxe

```xml
<ItemDefinitionGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemDefinitionGroup>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Condition`|Nepovinný atribut. Podmínka, která má být vyhodnocena. Další informace naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Položka](../msbuild/item-element-msbuild.md)|Definuje vstupy pro proces sestavení. V rozhraní může `Item` být nula `ItemDefinitionGroup`nebo více prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Projektu](../msbuild/project-element-msbuild.md) | Požadovaný kořenový prvek souboru projektu MSBuild. |

## <a name="example"></a>Příklad

Následující příklad kódu definuje dvě položky metadat, m a n, v ItemDefinitionGroup. V tomto příkladu je výchozí metadata "m" použita pro položku "i", protože metadata "m" nejsou explicitně definována položkou "i". Výchozí metadata "n" se však nepoužijí na položku "i", protože metadata "n" jsou již definována položkou "i".

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

- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Items](../msbuild/msbuild-items.md)
