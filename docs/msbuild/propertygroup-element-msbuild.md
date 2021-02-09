---
title: Property – element (MSBuild) | Microsoft Docs
description: Přečtěte si o prvku vlastností MSBuild, který obsahuje sadu uživatelsky definovaných prvků vlastností.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5182708e848587439795f5d6c04d87382b36f84a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931991"
---
# <a name="propertygroup-element-msbuild"></a>Property – element (MSBuild)

Obsahuje sadu uživatelsky definovaných prvků [vlastností](../msbuild/property-element-msbuild.md) . Každý `Property` prvek použitý v projektu MSBuild musí být podřízeným `PropertyGroup` prvkem elementu.

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Syntax

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

|Element|Popis|
|-------------|-----------------|
|[Vlastnost](../msbuild/property-element-msbuild.md)|Volitelný element.<br /><br /> Uživatelsky definovaný název vlastnosti, který obsahuje hodnotu vlastnosti. Element může obsahovat nula nebo více prvků *vlastností* `PropertyGroup` .|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu MSBuild. |

## <a name="example"></a>Příklad

 Následující příklad kódu ukazuje, jak nastavit vlastnosti na základě podmínky. V tomto příkladu, pokud `CompileConfig` je hodnota vlastnosti `DEBUG` ,, `Optimization` `Obfuscate` a `OutputPath` vlastností uvnitř `PropertyGroup` elementu, jsou nastaveny.

```xml
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >
    <Optimization>false</Optimization>
    <Obfuscate>false</Obfuscate>
    <OutputPath>$(OutputPath)\debug</OutputPath>
</PropertyGroup>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md)
