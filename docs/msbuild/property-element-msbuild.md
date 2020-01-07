---
title: Property – element (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: 99970bfbc955fe972d5e3c9a4e38ae6f57e0e0bf
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597422"
---
# <a name="property-element-msbuild"></a>Property – element (MSBuild)
Obsahuje uživatelsky definovaný název a hodnotu vlastnosti. Každá vlastnost použitá v projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] musí být zadána jako podřízený prvku `PropertyGroup` elementu.

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Syntaxe

```xml
<Property Condition="'String A' == 'String B'">
    Property Value
</Property>
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
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Seskupení elementu pro vlastnosti|

## <a name="text-value"></a>Textová hodnota
 Textová hodnota je volitelná.

 Tento text určuje hodnotu vlastnosti a může obsahovat XML.

## <a name="remarks"></a>Poznámky
 Názvy vlastností jsou omezeny pouze na znaky ASCII. Hodnoty vlastností jsou odkazovány v projektu umístěním názvu vlastnosti mezi "`$(`" a "`)`". Například `$(builddir)\classes` by se přeložila na *build\classes*, pokud má vlastnost `builddir` hodnotu `build`. Další informace o vlastnostech naleznete v tématu [vlastnosti MSBuild](../msbuild/msbuild-properties.md).

## <a name="example"></a>Příklad
 Následující kód nastaví vlastnost `Optimization` na `false` a vlastnost `DefaultVersion` na `1.0`, pokud je vlastnost `Version` prázdná.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Viz také:
- [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
