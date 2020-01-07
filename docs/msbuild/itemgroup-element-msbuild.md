---
title: ItemCollection – element (MSBuild) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 588118bf31c5d310e947b02fda476a63d0d9df7a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573440"
---
# <a name="itemgroup-element-msbuild"></a>Item – Element (MSBuild)
Obsahuje sadu uživatelsky definovaných prvků [položky](../msbuild/item-element-msbuild.md) . Každá položka, která se používá v projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], musí být zadána jako podřízená `ItemGroup` elementu.

\<Project> \<ItemGroup>

## <a name="syntax"></a>Syntaxe

```xml
<ItemGroup Condition="'String A' == 'String B'">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Condition`|Nepovinný atribut. Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|[Položka](../msbuild/item-element-msbuild.md)|Definuje vstupy procesu sestavení. V `ItemGroup`může být nula nebo více `Item` prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| [Cíl](../msbuild/target-element-msbuild.md) | Počínaje .NET Framework 3,5 se element `ItemGroup` může objevit uvnitř elementu `Target`. Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Příklad
Následující příklad kódu ukazuje uživatelsky definované kolekce položek `Res` a `CodeFiles` deklarované uvnitř elementu `ItemGroup`. Každá položka v kolekci `Res` Item obsahuje uživatelsky definovaný podřízený element [ItemMetadata –](../msbuild/itemmetadata-element-msbuild.md) .

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Res Include = "Strings.fr.resources" >
            <Culture>fr</Culture>
        </Res>
        <Res Include = "Dialogs.fr.resources" >
            <Culture>fr</Culture>
        </Res>

        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />
        <CodeFiles Include="..\..\Resources\Constants.cs" />
    </ItemGroup>
...
</Project>
```

## <a name="see-also"></a>Viz také:
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Položky](../msbuild/msbuild-items.md)
- [Společné položky projektu nástroje MSBuild](../msbuild/common-msbuild-project-items.md)
