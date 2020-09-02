---
title: Přizpůsobení sestavovacího systému
description: Tento článek je stručný úvod do systému sestavení MSBuild, který používá Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 0c511c448136210038f1034321a2828e5153add1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "71128392"
---
# <a name="customizing-the-build-system"></a>Přizpůsobení systému sestavení

Microsoft Build Engine je platforma pro vytváření aplikací. Modul, který je taky známý jako MSBuild, byl vyvinutý Microsoftem a umožňuje sestavovat aplikace .NET. Rozhraní mono má také svou vlastní implementaci modulu sestavení společnosti Microsoft s názvem **xbuild**. V tuto chvíli se ale xbuild vyvolala za použití nástroje MSBuild na všech operačních systémech.

Nástroj **MSBuild** slouží jako systém sestavení pro projekty v Visual Studio pro Mac a funguje tak, že převezme sadu vstupů, například zdrojové soubory, a transformuje je na výstupy, jako jsou spustitelné soubory. Tento výstup dosahuje vyvoláním nástrojů, jako je například kompilátor.

## <a name="msbuild-file"></a>Soubor MSBuild

Nástroj MSBuild používá soubor XML, který se označuje jako soubor projektu, který definuje *položky* , které jsou součástí projektu (například prostředky obrázku), a *vlastnosti* potřebné k sestavení projektu. V tomto souboru projektu bude vždy Přípona souboru `proj` , například `.csproj` pro projekty v jazyce C#.

### <a name="viewing-the-msbuild-file"></a>Zobrazení souboru MSBuild

Vyhledejte soubor MSBuild kliknutím pravým tlačítkem myši na název projektu a výběrem možnosti **Zobrazit ve Finderu**. V okně Finder se zobrazí všechny soubory a složky související s vaším projektem, včetně `.csproj` souboru, jak je znázorněno na následujícím obrázku:

![umístění csproj ve Finderu](media/customizing-build-system-image1.png)

Chcete-li zobrazit na `.csproj` nové kartě v Visual Studio pro Mac, klikněte pravým tlačítkem myši na název projektu a přejděte do části **nástroje > upravit soubor**:

![otevření csproj v editoru zdrojového kódu](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Složení souboru MSBuild

Všechny soubory MSBuild obsahují povinný kořenový `Project` element, například takto:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Projekt obvykle také naimportuje `.targets` soubor. Tento soubor obsahuje mnoho pravidel, která popisují postup zpracování a sestavení různých souborů. Import obvykle se zobrazí v dolní části `proj` souboru a projekty jazyka C# vypadají přibližně takto:

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Soubor cílů je jiný soubor MSBuild. Tento soubor obsahuje kód MSBuild, který je možné použít více projekty. Například `Microsoft.CSharp.targets` soubor, který je nalezen v adresáři reprezentovaný `MSBuildBinPath` vlastností (nebo proměnná), obsahuje logiku pro sestavování sestavení v jazyce c# ze zdrojových souborů c#.

### <a name="items-and-properties"></a>Položky a vlastnosti

V nástroji MSBuild existují dva základní datové typy: *položky* a *vlastnosti*, které jsou podrobněji vysvětleny v následujících oddílech.

#### <a name="properties"></a>Vlastnosti

Vlastnosti jsou páry klíč/hodnota, které se používají k ukládání nastavení, která ovlivňují kompilaci, jako jsou například možnosti kompilátoru.

Jsou nastaveny pomocí skupiny vlastností a mohou obsahovat libovolný počet PropertiesGroups, který může obsahovat libovolný počet vlastností.

Například vlastnost pro jednoduchou konzolovou aplikaci může vypadat jako v následujícím kódu XML:

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

Vlastnosti mohou být odkazovány z výrazů pomocí `$()` syntaxe. Například `$(Foo)` bude vyhodnocen jako hodnota `Foo` Vlastnosti. Pokud vlastnost nebyla nastavena, vyhodnotí se jako prázdný řetězec bez jakékoli chyby.

#### <a name="items"></a>Položky

Položky poskytují způsob, jak řešit vstupy do systému sestavení jako seznamy nebo sady a obvykle představují soubory. Každá položka má *typ*položky, *specifikaci*položky a volitelná libovolná *metadata*. Všimněte si, že nástroj MSBuild nefunguje na jednotlivých položkách, přebírá všechny položky daného typu označované jako *sada* položek.

Položky jsou vytvořeny deklarací `ItemGroup` . Může existovat libovolný počet ItemGroups, který může obsahovat libovolný počet položek.

Například následující fragment kódu vytvoří obrazovky pro spuštění iOS. Spouštěcí obrazovky mají typ sestavení `BundleResource` s specifikací jako cestu k imagi:

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

 Na sady položek lze pomocí syntaxe odkazovat z výrazů `@()` . Například `@(BundleResource)` se vyhodnotí jako BundleResource sada položek, což znamená všechny položky BundleResource. Pokud žádné položky tohoto typu neexistují, bude prázdná bez jakékoli chyby.

## <a name="resources-for-learning-msbuild"></a>Materiály k nástrojům MSBuild pro učení

Následující prostředky lze použít pro další informace o nástroji MSBuild podrobněji:

* [Přehled nástroje MSBuild](/visualstudio/msbuild/msbuild)
* [Koncepty nástroje MSBuild](/visualstudio/msbuild/msbuild-concepts)
