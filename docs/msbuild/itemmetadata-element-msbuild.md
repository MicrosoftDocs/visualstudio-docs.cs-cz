---
title: ItemMetadata – – element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66c19dbd74176babbf9e26030a68a6095992b660
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589367"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata – – element (MSBuild)
Obsahuje klíč metadat položky definovaný uživatelem, který obsahuje hodnotu metadat položky. Položka může mít libovolný počet párů klíč-hodnota metadat.

 \<Project> \<ItemGroup> \<Item>

## <a name="syntax"></a>Syntaxe

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|[Položka](../msbuild/item-element-msbuild.md)|Uživatelsky definovaný element definující vstupy procesu sestavení.|

## <a name="text-value"></a>Textová hodnota
 Textová hodnota je volitelná.

 Tento text určuje hodnotu metadat položky, která může být buď text, nebo XML.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak přidat `Culture` metadata s hodnotou `fr` do `CSFile`položky.

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>Viz také:
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Položky](../msbuild/msbuild-items.md)
