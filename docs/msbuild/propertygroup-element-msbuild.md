---
title: PropertyGroup Element (MSBuild) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632924"
---
# <a name="propertygroup-element-msbuild"></a>Element PropertyGroup (MSBuild)

Obsahuje sadu uživatelem definovaných elementů [Vlastnosti.](../msbuild/property-element-msbuild.md) Každý `Property` prvek použitý v projektu MSBuild musí `PropertyGroup` být podřízený prvek.

 \<> \<skupiny vlastností projektu>

## <a name="syntax"></a>Syntaxe

```xml
<PropertyGroup Condition="'String A' == 'String B'">
    <Property1>...</Property1>
    <Property2>...</Property2>
</PropertyGroup>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Podmínka|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Vlastnost](../msbuild/property-element-msbuild.md)|Volitelný element.<br /><br /> Název vlastnosti definované uživatelem, který obsahuje hodnotu vlastnosti. Může být nula *Property* nebo více `PropertyGroup` Property prvky v elementu.|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Projektu](../msbuild/project-element-msbuild.md) | Požadovaný kořenový prvek souboru projektu MSBuild. |

## <a name="example"></a>Příklad

 Následující příklad kódu ukazuje, jak nastavit vlastnosti na základě podmínky. V tomto příkladu pokud `CompileConfig` `DEBUG`je hodnota `Optimization`vlastnosti , , `Obfuscate`a `OutputPath` vlastnosti uvnitř `PropertyGroup` prvku jsou nastaveny.

```xml
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >
    <Optimization>false</Optimization>
    <Obfuscate>false</Obfuscate>
    <OutputPath>$(OutputPath)\debug</OutputPath>
</PropertyGroup>
```

## <a name="see-also"></a>Viz také

- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Vlastnosti MSBuild](../msbuild/msbuild-properties.md)
