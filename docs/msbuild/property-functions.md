---
title: Funkce vlastnictví | Dokumenty společnosti Microsoft
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb4c44b4e642ff1137df7f0afe02502224060a64
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302908"
---
# <a name="property-functions"></a>Funkce vlastností

Funkce vlastností jsou volání metod rozhraní .NET Framework, které se zobrazují v definicích vlastností MSBuild. Na rozdíl od úkolů funkce vlastností lze použít mimo cíle a jsou vyhodnoceny před spuštěním libovolného cíle.

Bez použití úloh MSBuild můžete číst systémový čas, porovnávat řetězce, odpovídat regulárním výrazům a provádět další akce ve skriptu sestavení. MSBuild se pokusí převést řetězec na číslo a číslo na řetězec a provést další převody podle potřeby.

Hodnoty řetězce vrácené z vlastností mají [uvozené speciální znaky.](msbuild-special-characters.md) Pokud chcete, aby hodnota byla zpracována, jako by byla `$([MSBuild]::Unescape())` vložena přímo do souboru projektu, použijte k unescape speciální znaky.

Funkce vlastností jsou k dispozici s rozhraním .NET Framework 4 a novějším.

## <a name="property-function-syntax"></a>Syntaxe funkce vlastnosti

Jedná se o tři druhy funkcí vlastností; každá funkce má jinou syntaxi:

- Funkce vlastností String (instance)
- Statické vlastnosti funkce
- Funkce vlastností MSBuild

### <a name="string-property-functions"></a>Funkce vlastností řetězce

Všechny hodnoty vlastností sestavení jsou pouze řetězcové hodnoty. Metody string (instance) můžete použít k provozu s libovolnou hodnotou vlastnosti. Můžete například extrahovat název jednotky (první tři znaky) z vlastnosti sestavení, která představuje úplnou cestu pomocí tohoto kódu:

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Statické vlastnosti funkce

Ve skriptu sestavení můžete přistupovat ke statickým vlastnostem a metodám mnoha systémových tříd. Chcete-li získat hodnotu statické vlastnosti, \<použijte následující syntaxi, kde \<class> je název systémové třídy a vlastnost> je název vlastnosti.

```
$([Class]::Property)
```

Můžete například použít následující kód k nastavení vlastnosti sestavení na aktuální datum a čas.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Chcete-li volat statickou metodu, \<použijte následující syntaxi, kde \<třída> je název systémové\<třídy, Metoda> je název metody a ( Parametry>) je seznam parametrů pro metodu:

```
$([Class]::Method(Parameters))
```

Chcete-li například nastavit vlastnost sestavení na nový identifikátor GUID, můžete použít tento skript:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

Ve statických vlastnostech můžete použít libovolnou statickou metodu nebo vlastnost těchto tříd systému:

- Systém.Bajt
- System.Char
- Systém.Převést
- System.datetime
- Systém.Desetinné místo
- Systém.Double
- System.Výčet
- System.Guid
- Systém.Int16
- Systém.Int32
- Systém.Int64
- Cesta System.IO.
- System.Math
- System.Runtime.InteropServices.OSPlatform
- System.Runtime.InteropServices.RuntimeInformace
- Systém.UInt16
- Systém.UInt32
- Systém.UInt64
- System.SByte
- System.Single
- System.string
- System.StringComparer
- System.TimeSpan
- System.Text.RegularExpressions.Regex
- System.UriBuilder
- System.Version
- Microsoft.Build.Utilities.ToolLocationHelper

Kromě toho můžete použít následující statické metody a vlastnosti:

- System.Environment::Příkazová čára
- System.Environment::ExpandEnvironmentVariables
- System.Environment::GetEnvironmentVariable
- System.Environment::Proměnné prostředí GetEnvironment
- System.Environment::GetFolderPath
- System.Environment::GetLogicalDrives
- System.IO.Directory::GetDirectories
- System.io.Directory::GetFiles
- System.io.Directory::GetLastAccessTime
- System.io.directory::GetLastWriteTime
- System.io.Directory::GetParent
- System.IO.File::Existuje
- System.io.File::GetCreationTime
- System.IO.File::Atributy GetAttributes
- System.io.File::GetLastAccessTime
- System.io.Soubor::GetLastWriteTime
- System.io.File::Čteníalltextu

### <a name="calling-instance-methods-on-static-properties"></a>Metody volání instance pro statické vlastnosti

Pokud přistupujete ke statické vlastnosti, která vrací instanci objektu, můžete vyvolat metody instance tohoto objektu. Chcete-li vyvolat metodu instance, \<použijte následující syntaxi, kde \<třída> je název systémové \<třídy, Vlastnost> je\<název vlastnosti, Metoda> je název metody a ( Parametry>) je seznam parametrů pro metodu:

```
$([Class]::Property.Method(Parameters))
```

Název třídy musí být plně kvalifikovaný v oboru názvů.

Můžete například použít následující kód k nastavení vlastnosti sestavení na aktuální datum dnes.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>Funkce vlastností MSBuild

Několik statických metod v sestavení lze přistupovat k aritmetické, bitové logické a escape znak podporu. Přístup k těmto metodám pomocí \<následující syntaxe, kde metoda\<> je název metody a ( Parametry>) je seznam parametrů pro metodu.

```
$([MSBuild]::Method(Parameters))
```

Chcete-li například přidat dvě vlastnosti, které mají číselné hodnoty, použijte následující kód.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Zde je seznam funkcí vlastností MSBuild:

|Podpis funkce|Popis|
|------------------------|-----------------|
|double Add (dvojité a, dvojité b)|Přidejte dvě dvojhry.|
|dlouhé Add (dlouhé a, dlouhé b)|Přidejte dvě dlouhé.|
|double Subtract (dvojité a, dvojité b)|Odečtěte dvě dvojnásobky.|
|long Subtract (long a, long b)|Odečtěte dvě dlouhé.|
|double Multiply (dvojitá a, dvojitá b)|Vynásobte dvě dvojhry.|
|dlouhé Násobit (dlouhé a, dlouhé b)|Vynásobte dvě dlouhé.|
|dvojité dělení (dvojité a, dvojité b)|Rozdělte dvě čtyřhry.|
|dlouhé Dělení (dlouhé a, dlouhé b)|Rozdělte dvě dlouhé.|
|double Modulo (dvojité a, dvojité b)|Modulo dvě čtyřhry.|
|dlouhý Modulo (dlouhý a, dlouhý b)|Modulo dvě dlouhé.|
|řetězec Escape(řetězec bez řídicích lét)|Escape řetězec podle MSBuild uvození pravidel.|
|řetězec Unescape(řetězec uvozen)|Unescape řetězec podle MSBuild uvození pravidel.|
|int BitwiseOr (int první, int sekundy)|Proveďte bitově `OR` první a druhý (první &#124; sekundu).|
|int BitwiseAnd (int první, int druhý)|Proveďte bitově `AND` první a druhý (první & sekundu).|
|int BitwiseXor (int první, int druhý)|Proveďte bitově `XOR` na první a druhé (první ^ druhý).|
|int BitwiseNot (int první)|Proveďte bitové `NOT` (~první).|
|bool IsOsPlatform(string platformString)|Určete, zda je `platformString`aktuální platforma operačního operačního ého . `platformString`musí být členem <xref:System.Runtime.InteropServices.OSPlatform>.|
|bool IsOSUnixLike()|Pravda, pokud je aktuální Operační systém unixový systém.|
|string NormalizePath (params string[] cesta)|Získá kanonizovanou úplnou cestu k zadané cestě a zajistí, že obsahuje správné znaky oddělovače adresáře pro aktuální operační systém.|
|string NormalizeDirectory(params string[] cesta)|Získá kanonicalized úplnou cestu k zadanému adresáři a zajišťuje, že obsahuje správné znaky oddělovače adresáře pro aktuální operační systém a zároveň zajišťuje, že má koncové lomítko.|
|řetězec EnsureTrailingSlash(cesta řetězce)|Pokud daná cesta nemá koncové lomítko, přidejte ho. Pokud je cesta prázdný řetězec, nezmění ji.|
|řetězec GetPathOfFileabove(řetězec soubor, řetězec startingDirectory)|Vyhledá a vrátí úplnou cestu k souboru ve struktuře adresářů nad umístěním aktuálního souboru sestavení nebo na `startingDirectory`základě , pokud je zadán.|
|GetDirectoryNameOfFileabove(řetězec startingDirectory, řetězec fileName)|Vyhledejte a vraťte adresář souboru v zadaném adresáři nebo v umístění ve struktuře adresářů nad tímto adresářem.|
|řetězec MakeRelative(řetězec basePath, cesta řetězce)|Dělá `path` vzhledem k `basePath`. `basePath`musí být absolutní adresář. Pokud `path` nelze provést relativní, je vrácena doslovně. Podobně `Uri.MakeRelativeUri`jako .|
|řetězec ValueOrDefault(řetězec conditionValue, řetězec defaultValue)|Vrátí řetězec v parametru 'defaultValue' pouze v případě, že parametr 'conditionValue' je prázdný, jinak vrátí hodnotu conditionValue.|

## <a name="nested-property-functions"></a>Vnořené funkce vlastností

Můžete kombinovat funkce vlastností a vytvořit tak složitější funkce, jak ukazuje následující příklad.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Tento příklad vrátí hodnotu bitu <xref:System.IO.FileAttributes> `Archive` (32 nebo 0) `tempFile`souboru daného cestou . Všimněte si, že výčtové hodnoty dat se nemohou zobrazit podle názvu v rámci vlastností. Místo toho musí být použita číselná hodnota (32).

Metadata se mohou také zobrazit ve vnořených funkcích vlastností. Další informace naleznete v [tématu Batching](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

Funkce `DoesTaskHostExist` vlastnosti v msbuild vrátí, zda je hostitel úlohy aktuálně nainstalován pro zadané hodnoty runtime a architektury.

Tato funkce vlastnosti má následující syntaxi:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

Funkce `EnsureTrailingSlash` vlastnosti v MSBuild přidá koncové lomítko, pokud ještě neexistuje.

Tato funkce vlastnosti má následující syntaxi:

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileabovevýše

Funkce vlastnosti `GetDirectoryNameOfFileAbove` MSBuild hledá soubor v adresářích nad aktuálním adresářem v cestě.

 Tato funkce vlastnosti má následující syntaxi:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Následující kód je příkladem této syntaxe.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild getpathoffilenad

Funkce `GetPathOfFileAbove` vlastnosti v msbuild vrátí cestu k zadanému souboru, pokud je umístěn ve struktuře adresáře nad aktuálním adresářem. Je funkčně ekvivalentní volání

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Tato funkce vlastnosti má následující syntaxi:

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>Hodnota getregistry sestavení msbuild

Funkce vlastnosti `GetRegistryValue` MSBuild vrátí hodnotu klíče registru. Tato funkce má dva argumenty, název klíče a název hodnoty a vrátí hodnotu z registru. Pokud nezadáte název hodnoty, bude vrácena výchozí hodnota.

Následující příklady ukazují, jak se tato funkce používá:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

Funkce vlastnosti `GetRegistryValueFromView` MSBuild získá data systémového registru s klíčem registru, hodnotou a jedním nebo více seřazenými zobrazeními registru. Klíč a hodnota jsou prohledávány v každém zobrazení registru v pořadí, dokud nejsou nalezeny.

Syntaxe této funkce vlastnosti je:

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

64bitový operační systém windows udržuje klíč registru **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node,** který představuje zobrazení registru **HKEY_LOCAL_MACHINE\SOFTWARE** pro 32bitové aplikace.

Ve výchozím nastavení 32bitová aplikace spuštěná na wow64 přistupuje k 32bitovému zobrazení registru a 64bitová aplikace přistupuje k zobrazení 64bitového registru.

K dispozici jsou následující zobrazení registru:

|Zobrazení registru|Definice|
|-------------------|----------------|
|RegistryView.Registry32|32bitové zobrazení registru aplikace.|
|RegistryView.Registry64|Zobrazení registru 64bitových aplikací.|
|RegistryView.Default|Zobrazení registru, které odpovídá procesu, ve které je aplikace spuštěna.|

Následuje příklad.

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

získá data **SLRuntimeInstallPath** klíče **ReferenceAssemblies,** hledá nejprve v zobrazení 64bitového registru a potom v zobrazení 32bitového registru.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

Funkce vlastnosti `MakeRelative` MSBuild vrátí relativní cestu druhé cesty vzhledem k první cestě. Každá cesta může být soubor nebo složka.

Tato funkce vlastnosti má následující syntaxi:

```
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

Následující kód je příkladem této syntaxe.

```xml
<PropertyGroup>
    <Path1>c:\users\</Path1>
    <Path2>c:\users\username\</Path2>
</PropertyGroup>

<Target Name = "Go">
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />
</Target>

<!--
Output:
   username\
   ..\
-->
```

## <a name="msbuild-valueordefault"></a>Hodnota nebo výchozí hodnota msbuildu

Funkce vlastnosti `ValueOrDefault` MSBuild vrátí první argument, pokud není null nebo prázdný. Pokud je první argument null nebo prázdný, funkce vrátí druhý argument.

Následující příklad ukazuje, jak se tato funkce používá.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault('$(UndefinedValue)', 'a'))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault('b', '$(Value1)'))</Value2>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
    </Target>
</Project>

<!--
Output:
  Value1 = a
  Value2 = b
-->
```

## <a name="see-also"></a>Viz také

- [Vlastnosti MSBuild](../msbuild/msbuild-properties.md)

- [MSBuild – přehled](../msbuild/msbuild.md)
