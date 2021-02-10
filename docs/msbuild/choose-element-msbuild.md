---
title: Choose – element (MSBuild) | Microsoft Docs
description: Použijte prvek MSBuild zvolit pro vyhodnocení podřízených elementů a vyberte jednu sadu skupiny položek nebo prvků vlastností, které chcete vyhodnotit.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a3cb3ae9ef120954bb3c299cdf310a32da69845
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939510"
---
# <a name="choose-element-msbuild"></a>Choose – element (MSBuild)

Vyhodnotí podřízené prvky a vybere jednu sadu `ItemGroup` prvků a/nebo `PropertyGroup` prvků k vyhodnocení.

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Syntax

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

 Žádné

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Případech](../msbuild/otherwise-element-msbuild.md)|Volitelný element.<br /><br /> Určuje blok kódu `PropertyGroup` a `ItemGroup` prvků, které mají být vyhodnoceny, pokud jsou podmínky všech `When` elementů vyhodnocovány `false` . V prvku může být nula nebo jeden `Otherwise` element `Choose` a musí se jednat o poslední prvek.|
|[Když](../msbuild/when-element-msbuild.md)|Požadovaný element.<br /><br /> Určuje možný blok kódu pro `Choose` prvek, který chcete vybrat. Element může obsahovat jeden nebo více `When` prvků `Choose` .|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Případech](../msbuild/otherwise-element-msbuild.md) | Určuje blok kódu, který se má provést, pokud jsou podmínky všech `When` prvků vyhodnoceny jako `false` . |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu MSBuild. |
| [Když](../msbuild/when-element-msbuild.md) | Určuje možný blok kódu pro `Choose` prvek, který chcete vybrat. |

## <a name="remarks"></a>Poznámky

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
