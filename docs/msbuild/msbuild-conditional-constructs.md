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
ms.openlocfilehash: 26891fa67616b1796499722e03a764da2a8fd7d6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589263"
---
# <a name="msbuild-conditional-constructs"></a>Podmíněné konstrukty nástroje MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] poskytuje mechanismus pro nebo pro zpracování pomocí prvků [Choose](../msbuild/choose-element-msbuild.md), [when](../msbuild/when-element-msbuild.md)a [jinak](../msbuild/otherwise-element-msbuild.md) .

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

## <a name="see-also"></a>Viz také:
- [Choose – element (MSBuild)](../msbuild/choose-element-msbuild.md)
- [When – element (MSBuild)](../msbuild/when-element-msbuild.md)
- [Jinak – element (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
