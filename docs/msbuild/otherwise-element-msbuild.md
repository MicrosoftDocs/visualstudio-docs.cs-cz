---
title: Jinak – element (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: 384886ad4292661648f5cbfde1a583d8d75b1c03
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633041"
---
# <a name="otherwise-element-msbuild"></a>Jinak – element (MSBuild)

Určuje blok kódu, který se má provést, pokud a jenom v případě, že se vyhodnotí podmínky `When`ch prvků `false`.

 \<projektu \<> vyberte možnost > \<, když > \<vyberte >... \<jinak > \<zvolit >...

## <a name="syntax"></a>Syntaxe

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

 Žádné.

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|[Výběrem](../msbuild/choose-element-msbuild.md)|Volitelný element.<br /><br /> Vyhodnotí podřízené prvky a vybere jeden oddíl kódu, který se má provést. V elementu `Otherwise` může být nula nebo více `Choose` prvků.|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Volitelný element.<br /><br /> Obsahuje sadu uživatelsky definovaných prvků [položky](../msbuild/item-element-msbuild.md) . V elementu `Otherwise` může být nula nebo více `ItemGroup` prvků.|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Volitelný element.<br /><br /> Obsahuje sadu uživatelsky definovaných prvků [vlastností](../msbuild/property-element-msbuild.md) . V elementu `Otherwise` může být nula nebo více `PropertyGroup` prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|[Výběrem](../msbuild/choose-element-msbuild.md)|Vyhodnotí podřízené prvky a vybere jeden oddíl kódu, který se má provést.|

## <a name="remarks"></a>Poznámky

 V elementu `Choose` může být pouze jeden prvek `Otherwise` a musí se jednat o poslední prvek.

 Prvky `Choose`, `When`a `Otherwise` slouží společně k tomu, aby poskytovala možnost výběru jedné části kódu pro provedení několika možných alternativ. Další informace naleznete v tématu [podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Příklad

 Následující projekt používá prvek `Choose` k výběru sady hodnot vlastností v prvcích `When`, které chcete nastavit. Pokud `Condition` atributy `When` prvků vyhodnoceny jako `false`, jsou nastaveny hodnoty vlastností v elementu `Otherwise`.

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
