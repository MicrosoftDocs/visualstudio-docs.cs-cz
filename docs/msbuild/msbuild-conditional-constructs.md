---
title: Podmíněné konstrukce MSBuild | Microsoft Docs
description: Naučte se, jak MSBuild poskytuje mechanismus pro podmíněné zpracování pomocí prvků Choose, When a jinak.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 614a59771ea63637ee7c0576f67bf4798cb90c1f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046409"
---
# <a name="msbuild-conditional-constructs"></a>Podmíněné konstrukty nástroje MSBuild

Nástroj MSBuild poskytuje mechanismus pro nebo zpracování pomocí prvků [Choose](../msbuild/choose-element-msbuild.md), [when](../msbuild/when-element-msbuild.md)a [jinak](../msbuild/otherwise-element-msbuild.md) .

## <a name="use-the-choose-element"></a>Použití elementu Choose

 `Choose`Element obsahuje řadu `When` prvků s `Condition` atributy, které jsou testovány v pořadí shora dolů, dokud se jedna nevyhodnotí `true` . Pokud je více než jeden `When` prvek vyhodnocen `true` , je použita pouze první z nich. `Otherwise`Element, pokud je přítomen, bude vyhodnocen, pokud není podmínka na `When` element vyhodnocena jako `true` .

 `Choose` prvky lze použít jako podřízené prvky prvku `Project` `When` a `Otherwise` prvky. `When``Otherwise`prvky a mohou mít `ItemGroup` , `PropertyGroup` nebo `Choose` podřízené prvky.

## <a name="example"></a>Příklad

 V následujícím příkladu jsou použity `Choose` `When` prvky a pro zpracování nebo nebo. Vlastnosti a položky projektu jsou nastaveny v závislosti na hodnotě `Configuration` Vlastnosti.

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

V tomto příkladu je použita podmínka konstanty kompilátoru `DEFINED_CONSTANT` . Ty jsou obsaženy ve `DefinedConstants` Vlastnosti. Regulární výraz se používá pro shodu s přesnou konstantou v seznamu odděleném středníkem.

```xml
<Choose>
   <When Condition="$([System.Text.RegularExpressions.Regex]::IsMatch(
         $(DefineConstants), '^(.*;)*DEFINED_CONSTANT(;.*)*$'))">
      <!-- When DEFINED_CONSTANT is defined. -->
   </When>
   <!-- other conditions -->
</Choose>
```

## <a name="see-also"></a>Viz také

- [Choose – element (MSBuild)](../msbuild/choose-element-msbuild.md)
- [When – element (MSBuild)](../msbuild/when-element-msbuild.md)
- [Jinak – element (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
