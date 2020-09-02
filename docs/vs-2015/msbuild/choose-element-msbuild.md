---
title: Choose – element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 642a4996b9b7cb24ead5b58e8f3f98b8abf7657c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187003"
---
# <a name="choose-element-msbuild"></a>Choose – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vyhodnotí podřízené prvky a vybere jednu sadu `ItemGroup` prvků a/nebo `PropertyGroup` prvků k vyhodnocení.  
  
 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  
  
## <a name="syntax"></a>Syntax  
  
```  
<Choose>  
    <When Condition="'StringA'=='StringB'">... </When>  
    <Otherwise>... </Otherwise>  
</Choose>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Případech](../msbuild/otherwise-element-msbuild.md)|Volitelný element.<br /><br /> Určuje blok kódu `PropertyGroup` a `ItemGroup` prvků, které mají být vyhodnoceny, pokud jsou podmínky všech `When` elementů vyhodnocovány `false` . V prvku může být nula nebo jeden `Otherwise` element `Choose` a musí se jednat o poslední prvek.|  
|[Když](../msbuild/when-element-msbuild.md)|Požadovaný element.<br /><br /> Určuje možný blok kódu pro `Choose` prvek, který chcete vybrat. Element může obsahovat jeden nebo více `When` prvků `Choose` .|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Případech](../msbuild/otherwise-element-msbuild.md)|Určuje blok kódu, který se má provést, pokud jsou podmínky všech `When` prvků vyhodnoceny jako `false` .|  
|[Projekt](../msbuild/project-element-msbuild.md)|Požadovaný kořenový prvek [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu.|  
|[Když](../msbuild/when-element-msbuild.md)|Určuje možný blok kódu pro `Choose` prvek, který chcete vybrat.|  
  
## <a name="remarks"></a>Poznámky  
 `Choose`Prvky, `When` a `Otherwise` jsou společně k dispozici k tomu, aby bylo možné vybrat jeden oddíl kódu, který se má vykonat z několika možných alternativ. Další informace naleznete v tématu [podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md).  
  
## <a name="example"></a>Příklad  
 Následující projekt používá `Choose` prvek k výběru sady hodnot vlastností v prvcích, které `When` mají být nastaveny. Pokud `Condition` jsou atributy obou `When` prvků vyhodnocovány na `false` , jsou nastaveny hodnoty vlastností v `Otherwise` prvku.  
  
```  
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
 [Podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
