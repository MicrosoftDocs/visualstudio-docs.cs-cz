---
title: Otherwise – Element (MSBuild) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a84284c1378ba5fd2cd4cf953a6d7e15b4f207e8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266354"
---
# <a name="otherwise-element-msbuild"></a>Otherwise – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Určuje blok kódu budou spuštěny, pokud a pouze tehdy, pokud podmínky všech `When` prvky vyhodnotit `false`.  
  
 \<Project>  
 \<Zvolte >  
 \<Když >  
 \<Zvolte >  
 ...  
 \<V opačném případě >  
 \<Zvolte >  
 ...  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Zvolte](../msbuild/choose-element-msbuild.md)|Volitelný element.<br /><br /> Vyhodnotí jako podřízené prvky a vyberte jednu část kódu ke spuštění. Může být nula nebo více `Choose` prvky `Otherwise` elementu.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Volitelný element.<br /><br /> Obsahuje sadu uživatelem definované [položky](../msbuild/item-element-msbuild.md) elementy. Může být nula nebo více `ItemGroup` prvky `Otherwise` elementu.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Volitelný element.<br /><br /> Obsahuje sadu uživatelem definované [vlastnost](../msbuild/property-element-msbuild.md) elementy. Může být nula nebo více `PropertyGroup` prvky `Otherwise` elementu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Zvolte](../msbuild/choose-element-msbuild.md)|Vyhodnotí jako podřízené prvky a vyberte jednu část kódu ke spuštění.|  
  
## <a name="remarks"></a>Poznámky  
 Může existovat pouze jeden `Otherwise` prvek `Choose` element a musí být posledním prvkem.  
  
 `Choose`, `When`, A `Otherwise` elementy se používají společně poskytují způsob, jak vybrat jednu část kódu k provedení počet možných alternativy. Další informace najdete v tématu [podmíněné konstrukce](../msbuild/msbuild-conditional-constructs.md).  
  
## <a name="example"></a>Příklad  
 Následující projekt používá `Choose` které sadu hodnot vlastností v vybrat element `When` prvky pro nastavení. Pokud `Condition` atributy obou `When` prvky vyhodnotit `false`, vlastnost hodnoty v `Otherwise` element jsou nastavené.  
  
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



