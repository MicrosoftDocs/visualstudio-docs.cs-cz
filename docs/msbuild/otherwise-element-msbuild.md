---
title: Jinak Element (MSBuild) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633041"
---
# <a name="otherwise-element-msbuild"></a>Jinak prvek (MSBuild)

Určuje blok kódu, který má být spuštěn pouze `When` v `false`případě, že podmínky všech prvků vyhodnotí .

 \<> \<projektu \<Zvolte \<>, když> vybrat> ... \<V \<opačném případě> zvolte> ...

## <a name="syntax"></a>Syntaxe

```xml
<Otherwise>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Choose>... </Choose>
</Otherwise>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

 Žádné.

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Pomocí volby](../msbuild/choose-element-msbuild.md)|Volitelný element.<br /><br /> Vyhodnotí podřízené prvky a vybere jednu část kódu, kterou chcete spustit. V prvku může `Choose` být nula `Otherwise` nebo více prvků.|
|[Skupina položek](../msbuild/itemgroup-element-msbuild.md)|Volitelný element.<br /><br /> Obsahuje sadu uživatelem definovaných prvků [item.](../msbuild/item-element-msbuild.md) V prvku může `ItemGroup` být nula `Otherwise` nebo více prvků.|
|[Propertygroup](../msbuild/propertygroup-element-msbuild.md)|Volitelný element.<br /><br /> Obsahuje sadu uživatelem definovaných elementů [Vlastnosti.](../msbuild/property-element-msbuild.md) V prvku může `PropertyGroup` být nula `Otherwise` nebo více prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Pomocí volby](../msbuild/choose-element-msbuild.md)|Vyhodnotí podřízené prvky a vybere jednu část kódu, kterou chcete spustit.|

## <a name="remarks"></a>Poznámky

 Může být pouze `Otherwise` jeden `Choose` prvek v prvku a musí být poslední prvek.

 `Choose`Prvky `When`, `Otherwise` a jsou používány společně poskytnout způsob, jak vybrat jednu část kódu spustit z několika možných alternativ. Další informace naleznete [v tématu Podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Příklad

 Následující projekt používá `Choose` prvek k výběru, která `When` sada hodnot vlastností v prvcích, které chcete nastavit. Pokud `Condition` atributy obou `When` prvků `false`vyhodnotit , hodnoty `Otherwise` vlastností v elementu jsou nastaveny.

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
- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
