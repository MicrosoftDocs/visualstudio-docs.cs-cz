---
title: Choose – element (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4f699b4ffc9372af0c803d094390544932d652b
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634471"
---
# <a name="choose-element-msbuild"></a>Choose – element (MSBuild)

Vyhodnotí podřízené prvky a vybere jednu sadu `ItemGroup` prvků a/nebo `PropertyGroup` prvky k vyhodnocení.

 \<projektu \<> vyberte možnost > \<, když > \<vyberte >... \<jinak > \<zvolit >...

## <a name="syntax"></a>Syntaxe

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

 Žádné.

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|[Případech](../msbuild/otherwise-element-msbuild.md)|Volitelný element.<br /><br /> Určuje blok kódu `PropertyGroup` a `ItemGroup` prvky pro vyhodnocení, zda jsou podmínky všech `When` prvků vyhodnoceny na `false`. V elementu `Choose` může být nula nebo jeden `Otherwise` elementů a musí se jednat o poslední prvek.|
|[Kdy](../msbuild/when-element-msbuild.md)|Požadovaný element.<br /><br /> Určuje možný blok kódu pro `Choose` prvek, který chcete vybrat. V elementu `Choose` může být jeden nebo více `When` prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| - | - |
| [Případech](../msbuild/otherwise-element-msbuild.md) | Určuje blok kódu, který se má provést, pokud jsou podmínky všech `When`ch prvků vyhodnoceny jako `false`. |
| [Projektem](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu MSBuild. |
| [Kdy](../msbuild/when-element-msbuild.md) | Určuje možný blok kódu pro `Choose` prvek, který chcete vybrat. |

## <a name="remarks"></a>Poznámky

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
