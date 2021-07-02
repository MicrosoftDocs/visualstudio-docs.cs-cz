---
title: Funkce vlastností | Microsoft Docs
description: Naučte se používat funkce vlastností, což jsou volání metod .NET Framework, které se zobrazují v MSBuild definicích vlastností.
ms.custom: SEO-VS-2020
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a47ff76c98c5788fdfca3d633c87664b6802de70
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222951"
---
# <a name="property-functions"></a>Funkce vlastností

Funkce vlastností jsou volání .NET Framework metody, které se zobrazují MSBuild definicích vlastností. Na rozdíl od úloh lze funkce vlastností použít mimo cíle a vyhodnocují se před libovolným cílovým spuštěním.

Bez použití MSBuild můžete číst systémový čas, porovnávat řetězce, porovnávat regulární výrazy a provádět další akce ve skriptu sestavení. MSBuild se pokusí převést řetězec na číslo a číslo na řetězec a podle potřeby provést další převody.

Řetězcové hodnoty vrácené funkcemi vlastností mají [speciální znaky uvozené.](msbuild-special-characters.md) Pokud chcete, aby se s hodnotou zacházelo, jako by byla přímo vložila do souboru projektu, použijte ke zrušení `$([MSBuild]::Unescape())` speciálních znaků.

Funkce vlastností jsou dostupné v .NET Framework 4 a novějších verzích.

## <a name="property-function-syntax"></a>Syntaxe funkce vlastností

Toto jsou tři druhy funkcí vlastností. Každá funkce má jinou syntaxi:

- Funkce vlastností string (instance)
- Funkce statických vlastností
- MSBuild vlastností

### <a name="string-property-functions"></a>Funkce vlastností řetězce

Všechny hodnoty vlastností sestavení jsou jen řetězcové hodnoty. Metody řetězce (instance) můžete použít k použití s libovolnou hodnotou vlastnosti. Pomocí tohoto kódu můžete například extrahovat název jednotky (první tři znaky) z vlastnosti sestavení, která představuje úplnou cestu:

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Funkce statických vlastností

Ve skriptu sestavení máte přístup ke statickým vlastnostem a metodám mnoha systémových tříd. Pokud chcete získat hodnotu statické vlastnosti, použijte následující syntaxi, kde je název systémové třídy a je \<Class> \<Property> název vlastnosti.

```
$([Class]::Property)
```

Například následující kód můžete použít k nastavení vlastnosti sestavení na aktuální datum a čas.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Pokud chcete volat statickou metodu, použijte následující syntaxi, kde je název systémové třídy, je název metody a ( ) je seznam parametrů \<Class> \<Method> pro \<Parameters> metodu:

```
$([Class]::Method(Parameters))
```

Pokud například chcete nastavit vlastnost sestavení na nový identifikátor GUID, můžete použít tento skript:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

Ve funkcích statických vlastností můžete použít libovolnou statickou metodu nebo vlastnost těchto systémových tříd:

- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.Char?displayProperty=nameWithType>
- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Enum?displayProperty=nameWithType>
- <xref:System.Guid?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.IO.Path?displayProperty=nameWithType>
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.OSPlatform?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- <xref:System.TimeSpan?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- <xref:System.UriBuilder?displayProperty=nameWithType>
- <xref:System.Version?displayProperty=nameWithType>
- <xref:Microsoft.Build.Utilities.ToolLocationHelper?displayProperty=nameWithType>

Kromě toho můžete použít následující statické metody a vlastnosti:

- [System.Environment::CommandLine](xref:System.Environment.CommandLine*)
- [System.Environment::ExpandEnvironmentVariables](xref:System.Environment.ExpandEnvironmentVariables*)
- [System.Environment::GetEnvironmentVariable](xref:System.Environment.GetEnvironmentVariable*)
- [System.Environment::GetEnvironmentVariables](xref:System.Environment.GetEnvironmentVariables*)
- [System.Environment::GetFolderPath](xref:System.Environment.GetFolderPath*)
- [System.Environment::GetLogicalDrives](xref:System.Environment.GetLogicalDrives*)
- [System.IO.Directory::GetDirectories](xref:System.IO.Directory.GetDirectories*)
- [System.IO.Directory::GetFiles](xref:System.IO.Directory.GetFiles*)
- [System.IO.Directory::GetLastAccessTime](xref:System.IO.Directory.GetLastAccessTime*)
- [System.IO.Directory::GetLastWriteTime](xref:System.IO.Directory.GetLastWriteTime*)
- [System.IO.Directory::GetParent](xref:System.IO.Directory.GetParent*)
- [System.IO.File::Exists](xref:System.IO.File.Exists*)
- [System.IO.File::GetCreationTime](xref:System.IO.File.GetCreationTime*)
- [System.IO.File::GetAttributes](xref:System.IO.File.GetAttributes*)
- [System.IO.File::GetLastAccessTime](xref:System.IO.File.GetLastAccessTime*)
- [System.IO.File::GetLastWriteTime](xref:System.IO.File.GetLastWriteTime*)
- [System.IO.File::ReadAllText](xref:System.IO.File.ReadAllText*)

### <a name="calling-instance-methods-on-static-properties"></a>Volání metod instance u statických vlastností

Pokud máte přístup ke statické vlastnosti, která vrací instanci objektu, můžete vyvolat metody instance tohoto objektu. K vyvolání metody instance použijte následující syntaxi, kde je název systémové třídy, je název vlastnosti, je název metody a ( ) je seznam parametrů pro \<Class> \<Property> \<Method> \<Parameters> metodu:

```
$([Class]::Property.Method(Parameters))
```

Název třídy musí být plně kvalifikovaný s oborem názvů.

Například následující kód můžete použít k nastavení vlastnosti sestavení na aktuální datum dnes.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>MSBuild vlastností

K několika statickým metodám v sestavení je možné přistupovat za pomoci aritmetické, bitové logické a řídicí znakové podpory. K těmto metodám se přistupuje pomocí následující syntaxe, kde je název metody a ( ) je seznam \<Method> \<Parameters> parametrů pro metodu .

```
$([MSBuild]::Method(Parameters))
```

Pokud například chcete sečtet dvě vlastnosti, které mají číselné hodnoty, použijte následující kód.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Tady je seznam funkcí MSBuild vlastností:

|Signatura funkce|Description|
|------------------------|-----------------|
|double Add(double a, double b)|Přidejte dvě dvojité.|
|long Add(long a, long b)|Přidejte dvě dlouhé.|
|double Subtract(double a, double b)|Odečtěte dvě dvojité hodnoty.|
|long Subtract(long a, long b)|Odečtěte dvě dlouhé hodnoty.|
|double Multiply(double a, double b)|Vynásobte dvě dvojité.|
|long Multiply(long a, long b)|Vynásobte dvě dlouhé.|
|double Divide(double a, double b)|Vydělte dvě dvojité dělení.|
|long Divide(long a, long b)|Vydělí dvě dlouhé.|
|double Modulo(double a, double b)|Modulo two doubles|
|long Modulo(long a, long b)|Modulo dvě dlouhé.|
|string Escape(řetězec bez řídicího znaku)|Ukončte řetězec podle MSBuild řídicích znaků.|
|řetězec Unescape (uvozena řetězcem)|V závislosti na pravidlech ukončování MSBuild se řetězec vyjádřete.|
|int BitwiseOr(int first, int second)|Proveďte bitovou operaci u prvního a druhého `OR` (první &#124; sekundy).|
|int BitwiseAnd(int first, int second)|Proveďte bitovou operaci u prvního a druhého `AND` (první & sekundy).|
|int BitwiseXor(int first, int second)|Proveďte bitovou `XOR` operaci na prvním a druhém místě (první ^ sekunda).|
|int BitwiseNot(int first)|Proveďte bitový `NOT` (~první).|
|bool IsOsPlatform(string platformString)|Určete, jestli je aktuální platforma operačního systému `platformString` . `platformString` musí být členem <xref:System.Runtime.InteropServices.OSPlatform> .|
|bool IsOSUnixLike()|True, pokud je aktuální operační systém unixový systém.|
|string NormalizePath(params string[] path)|Získá kanonický úplnou cestu zadané cesty a zajistí, že obsahuje správné znaky oddělovače adresáře pro aktuální operační systém.|
|string NormalizeDirectory(params string[] path)|Získá kanonický úplnou cestu k zadanému adresáři a zajistí, že obsahuje správné znaky oddělovače adresáře pro aktuální operační systém a zároveň zajistí, aby měl koncové lomítko.|
|string EnsureTrailingSlash(cesta řetězce)|Pokud zadaná cesta nemá koncové lomítko, přidejte ho. Pokud je cesta prázdný řetězec, neupraví ji.|
|String GetPathOfFileAbove (soubor řetězce; String startingDirectory)|Vyhledá a vrátí úplnou cestu k souboru ve struktuře adresáře nad aktuálním umístěním souboru buildu nebo podle `startingDirectory` toho, jestli je zadaný.|
|GetDirectoryNameOfFileAbove (řetězec startingDirectory, název souboru String)|Vyhledejte a vraťte adresář se souborem buď v zadaném adresáři, nebo v umístění ve struktuře adresáře nad adresářem.|
|String MakeRelative (řetězec basePath, cesta k řetězci)|Vytváří `path` relativní vzhledem k `basePath` . `basePath` musí být absolutní adresář. Pokud `path` nejde provést relativní, vrátí se do stejného znění. Podobně jako `Uri.MakeRelativeUri` .|
|String ValueOrDefault (řetězec conditionValue, hodnota defaultValue řetězce)|Vrátí řetězec v parametru defaultValue pouze v případě, že parametr conditionValue je prázdný, v opačném případě vrátí hodnotu conditionValue.|

## <a name="nested-property-functions"></a>Vnořené funkce vlastností

Můžete zkombinovat funkce vlastností a vytvořit tak složitější funkce, jak ukazuje následující příklad.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Tento příklad vrátí hodnotu <xref:System.IO.FileAttributes> `Archive` bitu (32 nebo 0) souboru daného cestou `tempFile` . Všimněte si, že hodnoty výčtu dat nemohou být v rámci funkcí vlastností uvedeny podle názvu. Místo toho je třeba použít číselnou hodnotu (32).

Metadata se můžou objevit i ve funkcích vnořených vlastností. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

`DoesTaskHostExist`funkce property v MSBuild vrátí, zda je hostitel úlohy aktuálně nainstalován pro zadané hodnoty modulu runtime a architektury.

Tato funkce vlastnosti má následující syntaxi:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

`EnsureTrailingSlash`funkce property v MSBuild přidá koncové lomítko, pokud ještě neexistuje.

Tato funkce vlastnosti má následující syntaxi:

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

funkce MSBuild `GetDirectoryNameOfFileAbove` vlastností vyhledá soubor v adresářích nad aktuálním adresářem v cestě.

 Tato funkce vlastnosti má následující syntaxi:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Následující kód je příkladem této syntaxe.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

`GetPathOfFileAbove`funkce property v MSBuild vrátí cestu k zadanému souboru, pokud se nachází ve struktuře adresáře nad aktuálním adresářem. Je funkčně ekvivalentní volání

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Tato funkce vlastnosti má následující syntaxi:

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

funkce MSBuild `GetRegistryValue` vlastnost vrací hodnotu klíče registru. Tato funkce přijímá dva argumenty, název klíče a název hodnoty a vrací hodnotu z registru. Pokud nezadáte název hodnoty, vrátí se výchozí hodnota.

Následující příklady ukazují, jak se tato funkce používá:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

funkce MSBuild `GetRegistryValueFromView` vlastností získá data systémového registru podle klíče registru, hodnoty a jednoho nebo více seřazených zobrazení registru. Klíč a hodnota jsou prohledány v každém zobrazení registru v pořadí, dokud nebudou nalezeny.

Syntaxe pro tuto funkci vlastnosti je:

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

operační systém Windows 64 udržuje **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node** klíč registru, který představuje **HKEY_LOCAL_MACHINE\SOFTWARE** zobrazení registru pro 32 aplikace.

Ve výchozím nastavení 32 aplikace spuštěná v WOW64 přistupuje ke 32 zobrazení registru a aplikace 64-bit 64 přistupuje k zobrazení 16bitového registru.

K dispozici jsou následující zobrazení registru:

|Zobrazení registru|Definice|
|-------------------|----------------|
|Zadaná RegistryView. Registry32|Zobrazení registru pro 32 bitových aplikací.|
|Zadaná RegistryView. Registry64|Zobrazení registru pro 64 bitových aplikací.|
|Zadaná RegistryView. Default|Zobrazení registru, které odpovídá procesu, ve kterém je aplikace spuštěná.|

Následuje příklad.

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

Získá **SLRuntimeInstallPath** data **ReferenceAssemblies** klíče, hledá se nejprve v zobrazení registru 64 a potom v zobrazení registru 32.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

funkce MSBuild `MakeRelative` property vrátí relativní cestu druhé cesty vzhledem k první cestě. Každá cesta může být soubor nebo složka.

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

## <a name="msbuild-valueordefault"></a>MSBuild ValueOrDefault

funkce MSBuild `ValueOrDefault` vlastností vrátí první argument, pokud není null nebo prázdný. Pokud má první argument hodnotu null nebo je prázdný, funkce vrátí druhý argument.

Následující příklad ukazuje, jak je tato funkce použita.

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

<a name="TargetFramework"></a>

## <a name="msbuild-targetframework-and-targetplatform-functions"></a>MSBuild Funkce TargetFramework a TargetPlatform

MSBuild 16,7 a vyšší definují několik funkcí pro zpracování [vlastností TargetFramework a TargetPlatform](msbuild-target-framework-and-target-platform.md).

|Signatura funkce|Description|
|------------------------|-----------------|
|GetTargetFrameworkIdentifier (String targetFramework)|Analyzujte TargetFrameworkIdentifier z hodnoty TargetFramework.|
|GetTargetFrameworkVersion (String targetFramework)|Analyzujte TargetFrameworkVersion z hodnoty TargetFramework.|
|GetTargetPlatformIdentifier (String targetFramework)|Analyzujte TargetPlatformIdentifier z hodnoty TargetFramework.|
|GetTargetPlatformVersion (String targetFramework)|Analyzujte TargetPlatformVersion z hodnoty TargetFramework.|
|IsTargetFrameworkCompatible (String targetFrameworkTarget; String targetFrameworkCandidate)|Vrátí hodnotu true, pokud je cílový rámec kandidáta kompatibilní s touto cílovou architekturou a jinak false.|

Následující příklad ukazuje, jak jsou tyto funkce použity. 

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::GetTargetFrameworkIdentifier('net5.0-windows7.0'))</Value1>
        <Value2>$([MSBuild]::GetTargetFrameworkVersion('net5.0-windows7.0'))</Value2>
        <Value3>$([MSBuild]::GetTargetPlatformIdentifier('net5.0-windows7.0'))</Value3>
        <Value4>$([MSBuild]::GetTargetPlatformVersion('net5.0-windows7.0'))</Value4>
        <Value5>$([MSBuild]::IsTargetFrameworkCompatible('net5.0-windows', 'net5.0'))</Value5>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
        <Message Text="Value3 = $(Value3)" />
        <Message Text="Value4 = $(Value4)" />
        <Message Text="Value5 = $(Value5)" />
    </Target>
</Project>
```

```output
Value1 = .NETCoreApp
Value2 = 5.0
Value3 = windows
Value4 = 7.0
Value5 = True
```

## <a name="msbuild-version-comparison-functions"></a>MSBuild funkce pro porovnání verzí

MSBuild 16,5 a vyšší definují několik funkcí pro porovnávání řetězců, které reprezentují verze.

> [!Note]
> Operátory porovnání v podmínkách [mohou porovnat řetězce, které lze analyzovat jako `System.Version` objekty](msbuild-conditions.md#comparing-versions), ale porovnání mohou způsobit neočekávané výsledky. Preferovat funkce vlastností.

|Signatura funkce|Description|
|------------------------|-----------------|
|VersionEquals (String a; String b)|Vrátí, `true` zda `a` jsou verze a `b` jsou ekvivalentní podle níže uvedených pravidel.|
|VersionGreaterThan (String a; String b)|Vrátí `true` , pokud `a` je verze větší než `b` podle níže uvedených pravidel.|
|VersionGreaterThanOrEquals (String a; String b)|Vrátí, `true` Pokud `a` je verze větší než nebo rovna `b` podle následujících pravidel.|
|VersionLessThan (String a; String b)|Vrátí `true` , pokud `a` je verze nižší než `b` podle níže uvedených pravidel.|
|VersionLessThanOrEquals (String a; String b)|Vrátí, `true` Pokud `a` je verze menší nebo rovna `b` podle následujících pravidel.|
|VersionNotEquals (String a; String b)|Vrátí, `false` zda `a` jsou verze a `b` jsou ekvivalentní podle níže uvedených pravidel.|

V těchto metodách se verze analyzují jako <xref:System.Version?displayProperty=fullName> , s následujícími výjimkami:

* Úvodní `v` nebo `V` se ignoruje, což umožňuje porovnání `$(TargetFrameworkVersion)` .

* Vše od prvního '-' nebo ' + ' na konec řetězce verze je ignorováno. To umožňuje předávání v sémantických verzích (semver), ačkoliv pořadí není stejné jako semver. Místo toho nemají předběžné verze specifikátoru a metadata sestavení žádnou váhu řazení. To může být užitečné například k zapnutí funkce pro a jeho `>= x.y` zapnutí. `x.y.z-pre`

* Neurčené části jsou stejné jako části s nulovou hodnotou. (`x == x.0 == x.0.0 == x.0.0.0`).

* Prázdné znaky nejsou povolené v celočíselných komponentách.

* Jenom hlavní verze je platná ( `3` rovná se `3.0.0.0` )

* `+` není povoleno jako kladné znaménko v celočíselných komponentách (je považováno za metadata středníku a ignorováno).

> [!TIP]
> Porovnání [vlastností TargetFramework by](msbuild-target-framework-and-target-platform.md) obecně měla místo extrahování a porovnávání verzí používat [IsTargetFrameworkCompatible.](#TargetFramework) To umožňuje porovnávání `TargetFramework` hodnot, které se liší `TargetFrameworkIdentifier` v i ve verzi.

## <a name="msbuild-condition-functions"></a>MSBuild funkcí podmínky

Funkce a `Exists` `HasTrailingSlash` nejsou funkce vlastností. Jsou k dispozici pro použití s `Condition` atributem . Viz [MSBuild podmínky .](msbuild-conditions.md)

## <a name="see-also"></a>Viz také

- [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md)

- [MSBuild přehledu](../msbuild/msbuild.md)
