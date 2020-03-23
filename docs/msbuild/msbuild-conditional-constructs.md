---
title: MSBuild podmíněné konstrukce | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633379"
---
# <a name="msbuild-conditional-constructs"></a>Podmíněné konstrukce MSBuild

MSBuild poskytuje mechanismus pro buď nebo zpracování s [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md)a [Otherwise](../msbuild/otherwise-element-msbuild.md) prvky.

## <a name="use-the-choose-element"></a>Použití prvku Choose

 Prvek `Choose` obsahuje řadu `When` prvků `Condition` s atributy, které jsou testovány v pořadí `true`od shora dolů, dokud jeden vyhodnotí na . Pokud více `When` než jeden `true`prvek vyhodnotí , pouze první z nich se používá. Prvek, `Otherwise` pokud je přítomen, bude vyhodnocen, pokud žádná podmínka pro prvek vyhodnotí `When` `true`.

 `Choose`prvky lze použít jako `Project` `When` podřízené prvky , a `Otherwise` prvky. `When`a `Otherwise` prvky `ItemGroup` `PropertyGroup`mohou `Choose` mít , , nebo podřízené prvky.

## <a name="example"></a>Příklad

 Následující příklad používá `Choose` `When` a prvky pro nebo zpracování. Vlastnosti a položky pro projekt jsou nastaveny v závislosti na hodnotě vlastnosti. `Configuration`

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

- [Vybrat prvek (MSBuild)](../msbuild/choose-element-msbuild.md)
- [Když element (MSBuild)](../msbuild/when-element-msbuild.md)
- [Jinak prvek (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
