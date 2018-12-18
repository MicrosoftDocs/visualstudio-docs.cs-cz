---
title: Podmíněné konstrukty nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ade8344b5f4189e9588fc8e75ef88fa5cf8f8c5
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080194"
---
# <a name="msbuild-conditional-constructs"></a>Podmíněné konstrukty nástroje MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] poskytuje mechanismus pro buď / nebo zpracování s [zvolit](../msbuild/choose-element-msbuild.md), [při](../msbuild/when-element-msbuild.md), a [jinak](../msbuild/otherwise-element-msbuild.md) elementy.  
  
## <a name="use-the-choose-element"></a>Použití elementu zvolte  
 `Choose` Element obsahuje posloupnost `When` prvky s `Condition` atributy, které jsou testovány v pořadí od shora dolů, dokud nebude vyhodnocen jako jeden `true`. Pokud více než jeden `When` vyhodnotí jako element `true`, je použita pouze první z nich. `Otherwise` Element, pokud jsou k dispozici, budou vyhodnoceny, pokud žádná podmínka na `When` vyhodnotí jako element `true`.  
  
 `Choose` prvky lze použít jako podřízené prvky `Project`, `When` a `Otherwise` elementy. `When` a `Otherwise` prvky mohou mít `ItemGroup`, `PropertyGroup`, nebo `Choose` podřízené prvky.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Choose` a `When` prvky pro buď / nebo zpracování. Nastavení vlastnosti a položky projektu závisí na hodnotě `Configuration` vlastnost.  
  
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
 [Choose – element (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [Když – element (MSBuild)](../msbuild/when-element-msbuild.md)   
 [Otherwise – element (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)