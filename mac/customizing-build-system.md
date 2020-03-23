---
title: Přizpůsobení sestavovacího systému
description: Tento článek je stručný úvod do systému sestavení MSBuild používané visual studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 0c511c448136210038f1034321a2828e5153add1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128392"
---
# <a name="customizing-the-build-system"></a>Přizpůsobení systému sestavení

Microsoft Build Engine je platforma pro vytváření aplikací. Modul, který je také známý jako MSBuild, byl vyvinut společností Microsoft a umožňuje vytváření aplikací .NET. Mono framework má také vlastní implementaci modulu sestavení společnosti Microsoft, nazvaný **xbuild**. V tomto okamžiku však xbuild byl vyřazen ve prospěch použití MSBuild ve všech operačních systémech.

**MSBuild** se používá jako systém sestavení pro projekty v sadě Visual Studio pro Mac a funguje tak, že sadu vstupů, jako jsou zdrojové soubory a transformuje je na výstupy, jako jsou spustitelné soubory. Dosahuje tohoto výstupu vyvoláním nástrojů, jako je například kompilátor.

## <a name="msbuild-file"></a>Soubor MSBuild

MSBuild používá soubor XML, nazývaný soubor projektu, který definuje *položky,* které jsou součástí projektu (například obrazové prostředky), a *vlastnosti* potřebné k vytvoření projektu. Tento soubor projektu bude mít vždy `proj`příponu souboru končící na , například `.csproj` pro projekty Jazyka C#.

### <a name="viewing-the-msbuild-file"></a>Zobrazení souboru MSBuild

Vyhledejte soubor MSBuild tak, že kliknete pravým tlačítkem myši na název projektu a vyberete **možnost Odhalit ve Finderu**. V okně hledáníse zobrazí všechny soubory a složky související s projektem, včetně souboru, `.csproj` jak je znázorněno na následujícím obrázku:

![csproj umístění ve Finderu](media/customizing-build-system-image1.png)

Pokud chcete `.csproj` v Visual Studiu for Mac zobrazit novou kartu, klikněte pravým tlačítkem myši na název projektu a přejděte na **Nástroje > upravit soubor**:

![otevření csproj ve zdrojovém editoru](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Složení souboru MSBuild

Všechny soubory MSBuild obsahují `Project` povinný kořenový prvek, například takto:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Projekt obvykle také importuje `.targets` soubor. Tento soubor obsahuje mnoho pravidel, která popisují, jak zpracovat a sestavit různé soubory. Import se obvykle zobrazí v `proj` dolní části souboru a pro projekty jazyka C# vypadají přibližně takto:

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Soubor cílů je jiný soubor MSBuild. Tento soubor obsahuje kód MSBuild, který je opakovaně použitelný pro více projektů. Například `Microsoft.CSharp.targets` soubor, který se nachází v adresáři `MSBuildBinPath` reprezentovaném vlastností (nebo proměnnou), obsahuje logiku pro vytváření sestavení C# ze zdrojových souborů Jazyka C#.

### <a name="items-and-properties"></a>Položky a vlastnosti

Existují dva základní datové typy v MSBuild: *položky* a *vlastnosti*, které jsou podrobněji vysvětleny v následujících částech.

#### <a name="properties"></a>Vlastnosti

Vlastnosti jsou dvojice klíč/hodnota, které se používají k ukládání nastavení, které ovlivňují kompilaci, jako jsou například možnosti kompilátoru.

Jsou nastaveny pomocí PropertyGroup a může obsahovat libovolný počet PropertiesGroups, které mohou obsahovat libovolný počet vlastností.

Například PropertyGroup pro jednoduchou konzolovou aplikaci může vypadat jako následující XML:

```xml
<PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
    <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
    <OutputType>Exe</OutputType>
    <RootNamespace>refactoring</RootNamespace>
    <AssemblyName>refactoring</AssemblyName>
    <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
</PropertyGroup>
```

Vlastnosti lze odkazovat z `$()` výrazů pomocí syntaxe. Například `$(Foo)` budou vyhodnoceny jako `Foo` hodnota vlastnosti. Pokud vlastnost nebyla nastavena, bude vyhodnocena jako prázdný řetězec bez chyby.

#### <a name="items"></a>Items

Položky poskytují způsob, jak nakládat se vstupy do systému sestavení jako seznamy nebo sady a obvykle představují soubory. Každá položka má *typ*položky , *specifikaci*položky a volitelná libovolná *metadata*. Všimněte si, že MSBuild nefunguje na jednotlivé položky, trvá na všechny položky daného typu volal *sadu* položek

Položky jsou vytvořeny `ItemGroup`deklarováním . Může existovat libovolný počet ItemGroups, které mohou obsahovat libovolný počet položek.

Například následující fragment kódu vytvoří obrazovky spuštění iOS. Spouštěcí obrazovky mají typ `BundleResource`sestavení , přičemž specifikace je cesta k obrázku:

```xml
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```

 Sady položek lze odkazovat z `@()` výrazů pomocí syntaxe. Například `@(BundleResource)` budou vyhodnoceny jako sada položek BundleResource, což znamená všechny položky BundleResource. Pokud neexistují žádné položky tohoto typu, bude prázdný, bez chyby.

## <a name="resources-for-learning-msbuild"></a>Zdroje informací pro výuku MSBuild

Následující zdroje informací lze podrobněji získat k informacím o msbuildu:

* [Přehled msbuildu](/visualstudio/msbuild/msbuild)
* [Koncepty nástroje MSBuild](/visualstudio/msbuild/msbuild-concepts)
