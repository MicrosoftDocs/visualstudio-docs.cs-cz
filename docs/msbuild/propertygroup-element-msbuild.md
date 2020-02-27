---
title: Property – element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#PropertyGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <PropertyGroup> element [MSBuild]
- PropertyGroup element [MSBuild]
ms.assetid: ff1e6c68-b9a1-4263-a1ce-dc3b829a64d4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b94cf266be81b81aca9c83fe8d29b9777ee9114b
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632924"
---
# <a name="propertygroup-element-msbuild"></a>Property – element (MSBuild)

Obsahuje sadu uživatelsky definovaných prvků [vlastností](../msbuild/property-element-msbuild.md) . Každý prvek `Property` použitý v projektu MSBuild musí být podřízeným prvkem `PropertyGroup` elementu.

 \<> projektu \<vlastnost >

## <a name="syntax"></a>Syntaxe

```xml
<PropertyGroup Condition="'String A' == 'String B'">
    <Property1>...</Property1>
    <Property2>...</Property2>
</PropertyGroup>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Podmínka|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|[Vlastnost](../msbuild/property-element-msbuild.md)|Volitelný element.<br /><br /> Uživatelsky definovaný název vlastnosti, který obsahuje hodnotu vlastnosti. V prvku `PropertyGroup` může existovat nula nebo více prvků *vlastností* .|

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| - | - |
| [Projektem](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu MSBuild. |

## <a name="example"></a>Příklad

 Následující příklad kódu ukazuje, jak nastavit vlastnosti na základě podmínky. V tomto příkladu, pokud je hodnota vlastnosti `CompileConfig` `DEBUG`, jsou nastaveny vlastnosti `Optimization`, `Obfuscate`a `OutputPath` uvnitř prvku `PropertyGroup`.

```xml
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >
    <Optimization>false</Optimization>
    <Obfuscate>false</Obfuscate>
    <OutputPath>$(OutputPath)\debug</OutputPath>
</PropertyGroup>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md)
