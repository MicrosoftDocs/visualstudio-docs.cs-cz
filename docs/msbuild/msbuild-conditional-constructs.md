---
title: Podmíněné konstrukce MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a06849c2aa0f4ec0203a7209ffc78be438dba9e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633379"
---
# <a name="msbuild-conditional-constructs"></a>Podmíněné konstrukty nástroje MSBuild

Nástroj MSBuild poskytuje mechanismus pro nebo zpracování pomocí prvků [Choose](../msbuild/choose-element-msbuild.md), [when](../msbuild/when-element-msbuild.md)a [jinak](../msbuild/otherwise-element-msbuild.md) .

## <a name="use-the-choose-element"></a>Použití elementu Choose

 Element `Choose` obsahuje řadu `When` prvků s `Condition` atributy, které jsou testovány v pořadí shora dolů, dokud se jedna nevyhodnotí jako `true`. Pokud je více než jeden prvek `When` vyhodnocen jako `true`, je použita pouze první z nich. `Otherwise` element, pokud je k dispozici, bude vyhodnocen, pokud není podmínka u `When`ho prvku vyhodnocena jako `true`.

 prvky `Choose` lze použít jako podřízené prvky `Project`, `When` a `Otherwise` elementy. prvky `When` a `Otherwise` mohou mít podřízené prvky `ItemGroup`, `PropertyGroup`nebo `Choose`.

## <a name="example"></a>Příklad

 Následující příklad používá prvky `Choose` a `When` pro zpracování/nebo. Vlastnosti a položky projektu jsou nastaveny v závislosti na hodnotě vlastnosti `Configuration`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='Debug' ">
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
    </Choose>
    <!-- Rest of Project -->
</Project>
```

## <a name="see-also"></a>Viz také

- [Choose – element (MSBuild)](../msbuild/choose-element-msbuild.md)
- [When – element (MSBuild)](../msbuild/when-element-msbuild.md)
- [Jinak – element (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
