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
ms.openlocfilehash: c058a5986f72192a86d0e554d9e0d0b9bdce1b42
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173509"
---
# <a name="itemgroup-element-msbuild"></a>Item – Element (MSBuild)

Obsahuje sadu uživatelsky definovaných prvků [položky](../msbuild/item-element-msbuild.md) . Všechny položky používané v projektu MSBuild musí být zadány jako podřízený `ItemGroup` prvek elementu.

\<Project>
\<ItemGroup>

## <a name="syntax"></a>Syntaxe

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
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
|`Label`|Nepovinný atribut. Identifikuje `ItemGroup` .|

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|[Položka](../msbuild/item-element-msbuild.md)|Definuje vstupy procesu sestavení. Může existovat nula nebo více `Item` prvků v `ItemGroup` .|

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu MSBuild. |
| [Cílové](../msbuild/target-element-msbuild.md) | Počínaje .NET Framework 3,5 se `ItemGroup` element může objevit uvnitř `Target` elementu. Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje uživatelsky definované kolekce položek `Res` a `CodeFiles` deklarované uvnitř `ItemGroup` elementu. Každá položka v `Res` kolekci položek obsahuje uživatelsky definovaný podřízený element [ItemMetadata –](../msbuild/itemmetadata-element-msbuild.md) .

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

V jednoduchém souboru projektu obvykle používáte jeden `ItemGroup` prvek, ale můžete také použít více `ItemGroup` prvků. Je-li `ItemGroup` použito více prvků, položky jsou zkombinovány do jediného prvku `ItemGroup` . Některé položky mohou být například obsaženy v samostatném `ItemGroup` prvku, který je definován v importovaném souboru.

ItemGroups může mít podmínky použité pomocí `Condition` atributu. V takovém případě jsou položky přidány do seznamu položek pouze v případě, že je podmínka splněna. Zobrazit [podmínky nástroje MSBuild](msbuild-conditions.md)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Items (Položky)](../msbuild/msbuild-items.md)
- [Společné položky projektu nástroje MSBuild](../msbuild/common-msbuild-project-items.md)
