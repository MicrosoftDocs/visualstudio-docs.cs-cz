---
title: Jinak – element (MSBuild) | Microsoft Docs
description: Přečtěte si, jak MSBuild používá prvek jinak k určení bloku kódu, který se má provést, pokud a pouze v případě, že jsou elementy false.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05cc8820f073ea8c620e4331c180ee1ddbfc2b65
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048928"
---
# <a name="otherwise-element-msbuild"></a>Jinak – element (MSBuild)

Určuje blok kódu, který se má provést, pokud a jenom v případě, že jsou podmínky všech `When` elementů vyhodnoceny jako `false` .

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Syntax

```xml
<Otherwise>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Choose>... </Choose>
</Otherwise>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

 Žádné

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Pomocí volby](../msbuild/choose-element-msbuild.md)|Volitelný element.<br /><br /> Vyhodnotí podřízené prvky a vybere jeden oddíl kódu, který se má provést. Element může obsahovat nula nebo více `Choose` prvků `Otherwise` .|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Volitelný element.<br /><br /> Obsahuje sadu uživatelsky definovaných prvků [položky](../msbuild/item-element-msbuild.md) . Element může obsahovat nula nebo více `ItemGroup` prvků `Otherwise` .|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Volitelný element.<br /><br /> Obsahuje sadu uživatelsky definovaných prvků [vlastností](../msbuild/property-element-msbuild.md) . Element může obsahovat nula nebo více `PropertyGroup` prvků `Otherwise` .|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Pomocí volby](../msbuild/choose-element-msbuild.md)|Vyhodnotí podřízené prvky a vybere jeden oddíl kódu, který se má provést.|

## <a name="remarks"></a>Poznámky

 V prvku může být pouze jeden `Otherwise` element `Choose` a musí být posledním prvkem.

 `Choose`Prvky, `When` a `Otherwise` jsou společně k dispozici k tomu, aby bylo možné vybrat jeden oddíl kódu, který se má vykonat z několika možných alternativ. Další informace naleznete v tématu [podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Příklad

 Následující projekt používá `Choose` prvek k výběru sady hodnot vlastností v prvcích, které `When` mají být nastaveny. Pokud `Condition` jsou atributy obou `When` prvků vyhodnocovány na `false` , jsou nastaveny hodnoty vlastností v `Otherwise` prvku.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='debug' ">
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <DebugType>full</DebugType>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\Debug\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
            <ItemGroup>
                <Compile Include="UnitTesting\*.cs" />
                <Reference Include="NUnit.dll" />
            </ItemGroup>
        </When>
        <When Condition=" '$(Configuration)'=='retail' ">
            <PropertyGroup>
                <DebugSymbols>false</DebugSymbols>
                <Optimize>true</Optimize>
                <OutputPath>.\bin\Release\</OutputPath>
                <DefineConstants>TRACE</DefineConstants>
            </PropertyGroup>
        </When>
        <Otherwise>
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\$(Configuration)\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
        </Otherwise>
        </Choose>
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="see-also"></a>Viz také

- [Podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
