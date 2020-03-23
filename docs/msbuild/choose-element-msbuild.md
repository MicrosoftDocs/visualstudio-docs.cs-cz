---
title: Zvolit prvek (MSBuild) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634471"
---
# <a name="choose-element-msbuild"></a>Vybrat prvek (MSBuild)

Vyhodnotí podřízené prvky `ItemGroup` pro výběr `PropertyGroup` jedné sady prvků nebo prvků, které mají být vyhodnoceny.

 \<> \<projektu \<Zvolte \<>, když> vybrat> ... \<V \<opačném případě> zvolte> ...

## <a name="syntax"></a>Syntaxe

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

 Žádné.

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Jinak](../msbuild/otherwise-element-msbuild.md)|Volitelný element.<br /><br /> Určuje `PropertyGroup` blok kódu a `ItemGroup` prvky, které mají `When` být `false`vyhodnoceny, pokud jsou podmínky všech prvků vyhodnoceny . V prvku může `Otherwise` být nula `Choose` nebo jeden prvek a musí být poslední prvek.|
|[Kdy](../msbuild/when-element-msbuild.md)|Požadovaný element.<br /><br /> Určuje možný blok kódu pro `Choose` prvek, který chcete vybrat. Může být jeden `When` nebo více `Choose` prvků v prvku.|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Jinak](../msbuild/otherwise-element-msbuild.md) | Určuje blok kódu, který má být `When` spuštěn, `false`pokud jsou podmínky všech prvků vyhodnoceny . |
| [Projektu](../msbuild/project-element-msbuild.md) | Požadovaný kořenový prvek souboru projektu MSBuild. |
| [Kdy](../msbuild/when-element-msbuild.md) | Určuje možný blok kódu pro `Choose` prvek, který chcete vybrat. |

## <a name="remarks"></a>Poznámky

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
