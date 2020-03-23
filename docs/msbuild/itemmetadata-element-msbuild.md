---
title: Element ItemMetadata (MSBuild) | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 18e1722fcd6867ca5e8ae52e220ff0a3dd2a3b7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633613"
---
# <a name="itemmetadata-element-msbuild"></a>Element ItemMetadata (MSBuild)

Obsahuje uživatelem definovaný klíč metadat položky, který obsahuje hodnotu metadat položky. Položka může mít libovolný počet párů klíč hodnota metadata.

 \<> \<položky \<> položky položky položky položky skupiny položky> projektu

## <a name="syntax"></a>Syntaxe

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky

 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Položka](../msbuild/item-element-msbuild.md)|Uživatelem definovaný prvek, který definuje vstupy pro proces sestavení.|

## <a name="text-value"></a>Textová hodnota

 Textová hodnota je volitelná.

 Tento text určuje hodnotu metadat položky, která může být text nebo XML.

## <a name="example"></a>Příklad

 Následující příklad kódu ukazuje, `Culture` jak přidat `fr` metadata `CSFile`s hodnotou do položky .

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>Viz také

- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Items](../msbuild/msbuild-items.md)
