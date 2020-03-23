---
title: Prvek vlastnosti (MSBuild) | Dokumenty společnosti Microsoft
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e50a6dd66c2dca7fa4159c578ccd334ed1d26cae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632950"
---
# <a name="property-element-msbuild"></a>Element vlastnosti (MSBuild)

Obsahuje uživatelem definovaný název a hodnotu vlastnosti. Každá vlastnost použitá v projektu MSBuild musí `PropertyGroup` být zadána jako podřízený prvek.

 \<> \<skupiny vlastností projektu>

## <a name="syntax"></a>Syntaxe

```xml
<Property Condition="'String A' == 'String B'">
    Property Value
</Property>
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
|[Propertygroup](../msbuild/propertygroup-element-msbuild.md)|Seskupení element pro vlastnosti.|

## <a name="text-value"></a>Textová hodnota

 Textová hodnota je volitelná.

 Tento text určuje hodnotu vlastnosti a může obsahovat XML.

## <a name="remarks"></a>Poznámky

 Názvy vlastností jsou omezeny pouze na znaky ASCII. Hodnoty vlastností jsou v projektu odkazovány umístěním názvu vlastnosti mezi "`$(`" a "`)`". Například `$(builddir)\classes` by přeložit *build\classes*, `builddir` pokud vlastnost `build`měla hodnotu . Další informace o vlastnostech naleznete v tématu [MSBuild properties](../msbuild/msbuild-properties.md).

## <a name="example"></a>Příklad

 Následující kód `Optimization` nastaví `false` vlastnost `DefaultVersion` a `1.0` vlastnost, `Version` pokud je vlastnost prázdná.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Viz také

- [Vlastnosti MSBuild](../msbuild/msbuild-properties.md)
- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
