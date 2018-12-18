---
title: Přizpůsobení procesu sestavení
description: Tento článek je stručný úvod do MSBuild sestavovací systém používá sada Visual Studio pro Mac
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 7fbd275e3e946461559db41668a749cd6631ba09
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296304"
---
# <a name="customizing-the-build-system"></a>Přizpůsobení procesu sestavení

Nástroj MSbuild je modul sestavení s vyvinutý microsoftem, který umožňuje vytváření primárně aplikací .NET. Mono framework obsahuje také vlastní implementace společnosti Microsoft Build Engine, volá **xbuild**. Ale xbuild byla ukončena používat MSBuild na všechny operační systémy.

**Nástroj MSbuild** slouží především pro jako systém sestavení pro projekty v sadě Visual Studio pro Mac.

Nástroj MSBuild funguje tak, že trvá sadu vstupů, jako je například zdrojové soubory a přemění je na výstupů, jako je například spustitelné soubory. Tento výstup dosahuje vyvoláním nástrojů, jako je kompilátor.

## <a name="msbuild-file"></a>Soubor MSBuild

Nástroj MSBuild používá soubor XML s názvem souboru projektu, který definuje *položky* , které jsou součástí vašeho projektu (například obrázek prostředky) a *vlastnosti* potřebné k sestavení projektu. Tento soubor projektu bude mít vždy příponu souboru končí na `proj`, jako například `.csproj` pro projekty jazyka C#.

### <a name="viewing-the-msbuild-file"></a>V souboru nástroje MSBuild

Vyhledejte soubor MSBuild tak, že kliknete pravým tlačítkem na název projektu a vyberete **zobrazit ve Finderu**. V okně hledání se zobrazí všechny soubory a složky, které jsou spojené s projektem, včetně `.csproj` souboru, jak je znázorněno na následujícím obrázku:

![umístění souboru csproj ve Finderu.](media/customizing-build-system-image1.png)

Chcete-li zobrazit `.csproj` na nové kartě v sadě Visual Studio pro Mac, klikněte pravým tlačítkem na název vašeho projektu a přejděte do **nástroje > Upravit soubor**:

![otevření v editoru zdrojového kódu csproj](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Složení soubor MSBuild

Všechny soubory MSBuild obsahují vyžadovaný kořenový `Project` prvek, například takto:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Obvykle se také importovat projekt `.targets` souboru. Tento soubor obsahuje celou řadu pravidla, která popisují, jak zpracovat a různé soubory sestavení. Import se obvykle zobrazují směrem k dolní části vašeho `proj` souborů a pro projekty jazyka C# vypadat přibližně takto:

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Soubor cílů je jiný soubor MSBuild. Tento soubor obsahuje kód MSBuild, který je opakovaně použitelné ve více projektů. Například `Microsoft.CSharp.targets` soubor, který se nachází v adresáři reprezentována `MSBuildBinPath` vlastnost (nebo proměnné), obsahuje logiku pro tvorbu sestavení C# od zdrojové soubory jazyka C#.

### <a name="items-and-properties"></a>Položky a vlastnosti

Existují dva základní datové typy v nástroji MSBuild: *položky* a *vlastnosti*, které jsou vysvětlené podrobněji v následujících částech.

#### <a name="properties"></a>Vlastnosti

Vlastnosti jsou páry klíč/hodnota, které se používají k ukládání nastavení, která ovlivňují kompilace, jako jsou možnosti kompilátoru.

Jsou nastavené pomocí PropertyGroup a může obsahovat libovolný počet PropertiesGroups, který může obsahovat libovolný počet vlastností.

PropertyGroup pro jednoduchou konzolovou aplikaci může například vypadat jako následující kód XML:

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

Vlastnosti lze odkazovat z výrazů pomocí `$()` syntaxe. Například `$(Foo)` se vyhodnotí jako hodnotu `Foo` vlastnost. Pokud nebyla nastavena vlastnost, se vyhodnotí jako prázdný řetězec, bez jakékoli chyby.

#### <a name="items"></a>Položky

Položky poskytují způsob řešení problémů s vstupy do systému sestavení, jako jsou uvedeny nebo nastaví a obvykle představují soubory. Každá položka má položku *typ*, položku *specifikace*a volitelné libovolného *metadat*. Všimněte si, že nástroj MSBuild nepracuje na jednotlivé položky trvá u všech položek zadaný typ označuje položku *nastavení*

Položky jsou vytvořeny prohlášením `ItemGroup`. Může existovat libovolný počet ItemGroups, který může obsahovat libovolný počet položek.

Například následující fragment kódu vytvoří spuštění obrazovky pro iOS. Spusťte obrazovky obsahují typ sestavení `BundleResource`, s specifikace jako cestu k bitové kopii:

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

 Položku sady lze odkazovat z výrazů pomocí `@()` syntaxe. Například `@(BundleResource)` se vyhodnotí jako sada BundleResource položky, což znamená, že všechny položky BundleResource. Pokud neexistují žádné položky tohoto typu, bude prázdný, bez jakékoli chyby.

## <a name="resources-for-learning-msbuild"></a>Zdroje informací nástroje MSBuild

Další informace o nástroji MSBuild podrobněji lze použít v následujících zdrojích:

* [Přehled nástroje MSBuild](/visualstudio/msbuild/msbuild)
* [Koncepty nástroje MSBuild](/visualstudio/msbuild/msbuild-concepts)
