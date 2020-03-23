---
title: Element skupiny položek (MSBuild) | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 8064ce4c13419238ca5877893a731d2ac53afb25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633639"
---
# <a name="itemgroup-element-msbuild"></a>Element ItemGroup (MSBuild)

Obsahuje sadu uživatelem definovaných prvků [item.](../msbuild/item-element-msbuild.md) Každá položka použitá v projektu MSBuild musí `ItemGroup` být zadána jako podřízený prvek.

\<> \<položky položky projektu>

## <a name="syntax"></a>Syntaxe

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Condition`|Nepovinný atribut. Podmínka, která má být vyhodnocena. Další informace naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).|
|`Label`|Nepovinný atribut. Identifikuje `ItemGroup`.|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Položka](../msbuild/item-element-msbuild.md)|Definuje vstupy pro proces sestavení. V rozhraní může `Item` být nula `ItemGroup`nebo více prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Projektu](../msbuild/project-element-msbuild.md) | Požadovaný kořenový prvek souboru projektu MSBuild. |
| [Cíl](../msbuild/target-element-msbuild.md) | Počínaje rozhraním .NET Framework `ItemGroup` 3.5 se `Target` prvek může zobrazit uvnitř prvku. Další informace naleznete v tématu [Cíle](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje uživatelem definované `Res` `CodeFiles` kolekce položek `ItemGroup` a deklarované uvnitř prvku. Každá z položek `Res` v kolekci položek obsahuje uživatelem definovaný podřízený element [ItemMetadata.](../msbuild/itemmetadata-element-msbuild.md)

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

## <a name="see-also"></a>Viz také

- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Items](../msbuild/msbuild-items.md)
- [Běžné položky projektu MSBuild](../msbuild/common-msbuild-project-items.md)
