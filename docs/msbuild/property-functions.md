---
title: Funkce vlastností | Microsoft Docs
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
ms.openlocfilehash: b0551162a00437b01c7357dfdac16462aad8f2fc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597383"
---
# <a name="property-functions"></a>Funkce vlastností

V .NET Framework verzích 4 a 4,5 se funkce vlastností dají použít k vyhodnocení skriptů MSBuild. Funkce vlastností lze použít všude, kde se zobrazí vlastnosti. Na rozdíl od úloh lze funkce vlastností použít mimo cíle a jsou vyhodnocovány před jakýmkoli cílovým spuštěním.

 Bez použití úloh nástroje MSBuild můžete přečíst systémový čas, porovnat řetězce, porovnat regulární výrazy a provádět další akce v rámci skriptu sestavení. Nástroj MSBuild se pokusí převést řetězec na číslo a číslo na řetězec a provést další převody podle požadavků.
 
Řetězcové hodnoty vrácené z funkcí vlastnosti mají řídicí [znaky speciální](msbuild-special-characters.md) . Pokud chcete, aby byla hodnota zpracována, jako by byla vložena přímo do souboru projektu, použijte `$([MSBuild]::Unescape())` pro zrušení Escape speciálních znaků.

## <a name="property-function-syntax"></a>Syntaxe funkce Property

Jedná se o tři druhy funkcí vlastností; Každá funkce má odlišnou syntaxi:

- Funkce pro vlastnosti String (instance)
- Funkce statických vlastností
- Funkce vlastností MSBuild

### <a name="string-property-functions"></a>Funkce řetězcových vlastností

Všechny hodnoty vlastností buildu jsou jenom řetězcové hodnoty. Můžete použít metody řetězce (instance) k provozování libovolné hodnoty vlastnosti. Můžete například extrahovat název jednotky (první tři znaky) z vlastnosti Build, která představuje úplnou cestu pomocí tohoto kódu:

```fundamental
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Funkce statických vlastností

Ve svém skriptu sestavení máte přístup ke statickým vlastnostem a metodám mnoha systémových tříd. Chcete-li získat hodnotu statické vlastnosti, použijte následující syntaxi, kde \<třídy > je název třídy System a \<Property > je název vlastnosti.

```fundamental
$([Class]::Property)
```

Například můžete použít následující kód k nastavení vlastnosti Build na aktuální datum a čas.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Chcete-li zavolat statickou metodu, použijte následující syntaxi, kde \<třídy > je název třídy systému, \<metoda > je název metody a (\<Parameters >) je seznam parametrů pro metodu:

```fundamental
$([Class]::Method(Parameters))
```

Chcete-li například nastavit vlastnost Build na nový identifikátor GUID, můžete použít tento skript:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

Ve funkcích statických vlastností můžete použít jakoukoli statickou metodu nebo vlastnost těchto systémových tříd:

- System.Byte
- System.Char
- System.Convert
- System.DateTime
- System.Decimal
- System.Double
- System.Enum
- System.Guid
- System.Int16
- System.Int32
- System.Int64
- System.IO.Path
- System.Math
- System.Runtime.InteropServices.OSPlatform
- System.Runtime.InteropServices.RuntimeInformation
- System.UInt16
- System.UInt32
- System.UInt64
- System.SByte
- System. Single
- System. String
- System.StringComparer
- System. TimeSpan
- System.Text.RegularExpressions.Regex
- System.UriBuilder
- System.Version
- Microsoft.Build.Utilities.ToolLocationHelper

Kromě toho můžete použít následující statické metody a vlastnosti:

- System. Environment:: CommandLine
- System.Environment::ExpandEnvironmentVariables
- System.Environment::GetEnvironmentVariable
- System. Environment:: GetEnvironmentVariables
- System.Environment::GetFolderPath
- System. Environment:: GetLogicalDrives
- System.IO.Directory::GetDirectories
- System.IO.Directory::GetFiles
- System.IO.Directory::GetLastAccessTime
- System.IO.Directory::GetLastWriteTime
- System.IO.Directory::GetParent
- System.IO.File::Exists
- System.IO.File::GetCreationTime
- System.IO.File::GetAttributes
- System.IO.File::GetLastAccessTime
- System.IO.File::GetLastWriteTime
- System.IO.File::ReadAllText

### <a name="calling-instance-methods-on-static-properties"></a>Volání metod instancí ve statických vlastnostech

Pokud přistupujete ke statické vlastnosti, která vrací instanci objektu, můžete vyvolat metody instance daného objektu. Chcete-li vyvolat metodu instance, použijte následující syntaxi, kde \<třídy > je název třídy systému, \<Property > je název vlastnosti, \<metoda > je název metody a (\<Parameters >) je seznam parametrů pro metodu:

```fundamental
$([Class]::Property.Method(Parameters))
```

Název třídy musí být plně kvalifikován pomocí oboru názvů.

Například můžete použít následující kód pro nastavení vlastnosti Build na aktuální datum v dnešní době.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>Funkce vlastností MSBuild

Několik statických metod v sestavení lze použít k zajištění aritmetické, bitové logické a řídicí znakové podpory. K těmto metodám přistupujete pomocí následující syntaxe, kde \<metoda > je název metody a (\<Parameters >) je seznam parametrů pro metodu.

```fundamental
$([MSBuild]::Method(Parameters))
```

Chcete-li například přidat dohromady dvě vlastnosti, které mají číselné hodnoty, použijte následující kód.

```fundamental
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Tady je seznam funkcí MSBuild vlastností:

|Signatura funkce|Popis|
|------------------------|-----------------|
|dvojité přidání (dvojitá a, dvojitá přesnost b)|Přidejte dvě dvojité.|
|dlouhé přidání (dlouhé a, dlouhé b)|Přidejte dvě dlouhé.|
|Dvojitý rozdíl (dvojitá a, dvojitá přesnost b)|Odečte dvě dvojice.|
|Long odečíst (Long a, Long b)|Odečte dvě dlouhé.|
|dvojité násobení (Double a, double b)|Vynásobení dvou dvojitých hodnot.|
|Long násobení (Long a, Long b)|Vynásobte dvě dlouhé.|
|dvojité dělení (dvojitá a, dvojitá přesnost b)|Vydělí dvě dvojitá čísla.|
|dlouhé rozdělení (Long a, Long b)|Rozdělte dvě dlouhé.|
|dvojité modulo (dvojitá a, dvojitá přesnost b)|Modulo dvě dvojitá přesnost.|
|dlouhé modulo (dlouhé a, dlouhé b)|Modulo dvě dlouhé.|
|Řídicí znak řetězce (řetězec bez řídicích znaků)|Vyřídí řetězec podle pravidel pro uvozovací znaky MSBuild.|
|řetězcové zrušení řídicího znaku (řetězcové řídicí znaky)|Odřídí řetězec podle pravidel pro uvozovací znaky MSBuild.|
|Bitový operátor int (int First, int Second)|Proveďte bitovou `OR` první a druhý (první &#124; sekunda).|
|int BitwiseAnd (int First, int Second)|Proveďte v prvním a druhém bitové `AND` (první & sekundy).|
|int BitwiseXor (int First, int Second)|Proveďte bitovou `XOR` první a druhý (prvních ^ sekund).|
|int BitwiseNot (int First)|Proveďte bitovou `NOT` (~ First).|
|bool IsOsPlatform (String platformString)|Určete, zda je aktuální platforma operačního systému `platformString`. `platformString` musí být členem <xref:System.Runtime.InteropServices.OSPlatform>.|
|bool IsOSUnixLike()|True, pokud je aktuální operační systém systémem UNIX.|
|String NormalizePath (cesta k parametrům řetězec [])|Získá kanonickou úplnou cestu k zadané cestě a zajistí, že obsahuje správné znaky oddělovače adresáře pro aktuální operační systém.|
|String NormalizeDirectory (cesta k parametrům řetězec [])|Získá kanonickou úplnou cestu k zadanému adresáři a zajistí, že obsahuje správné znaky oddělovačů adresářů pro aktuální operační systém a zároveň zajišťuje, že má koncové lomítko.|
|EnsureTrailingSlash řetězce (cesta k řetězci)|Pokud daná cesta nemá koncové lomítko, pak ji přidejte. Pokud je cesta prázdným řetězcem, neupraví ho.|
|String GetPathOfFileAbove (soubor řetězce; String startingDirectory)|Vyhledá soubor na základě umístění aktuálního souboru buildu nebo na základě `startingDirectory`, je-li tento parametr zadán.|
|GetDirectoryNameOfFileAbove (řetězec startingDirectory, název souboru String)|Vyhledejte soubor buď v zadaném adresáři, nebo v umístění ve struktuře adresářů nad adresářem.|
|String MakeRelative (řetězec basePath, cesta k řetězci)|Vytvoří `path` relativní ke `basePath`. `basePath` musí být absolutní adresář. Pokud `path` nelze nastavit jako relativní, vrátí se do stejného znění. Podobně jako `Uri.MakeRelativeUri`.|
|String ValueOrDefault (řetězec conditionValue, hodnota defaultValue řetězce)|Vrátí řetězec v parametru defaultValue pouze v případě, že parametr conditionValue je prázdný, v opačném případě vrátí hodnotu conditionValue.|

## <a name="nested-property-functions"></a>Vnořené funkce vlastností

Můžete zkombinovat funkce vlastností a vytvořit tak složitější funkce, jak ukazuje následující příklad.

```fundamental
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

V tomto příkladu se vrátí hodnota <xref:System.IO.FileAttributes>`Archive` bitu (32 nebo 0) souboru zadaného cestou `tempFile`. Všimněte si, že hodnoty výčtu dat nemohou být v rámci funkcí vlastností uvedeny podle názvu. Místo toho je třeba použít číselnou hodnotu (32).

Metadata se můžou objevit i ve funkcích vnořených vlastností. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

Funkce `DoesTaskHostExist` vlastnosti v nástroji MSBuild vrátí, zda je hostitel úlohy aktuálně nainstalován pro zadané hodnoty modulu runtime a architektury.

Tato funkce vlastnosti má následující syntaxi:

```fundamental
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>EnsureTrailingSlash nástroje MSBuild

Funkce `EnsureTrailingSlash` vlastnosti v MSBuild přidá koncové lomítko, pokud ještě neexistuje.

Tato funkce vlastnosti má následující syntaxi:

```fundamental
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

Funkce MSBuild `GetDirectoryNameOfFileAbove` Property vyhledá soubor v adresářích nad aktuální adresář v cestě.

 Tato funkce vlastnosti má následující syntaxi:

```fundamental
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Následující kód je příkladem této syntaxe.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>GetPathOfFileAbove nástroje MSBuild

Funkce `GetPathOfFileAbove` vlastnosti v nástroji MSBuild vrátí cestu k souboru bezprostředně před tímto souborem. Je funkčně ekvivalentní volání

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Tato funkce vlastnosti má následující syntaxi:

```fundamental
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>GetRegistryValue nástroje MSBuild

Funkce vlastnosti `GetRegistryValue` MSBuild vrací hodnotu klíče registru. Tato funkce přijímá dva argumenty, název klíče a název hodnoty a vrací hodnotu z registru. Pokud nezadáte název hodnoty, vrátí se výchozí hodnota.

Následující příklady ukazují, jak se tato funkce používá:

```fundamental
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>GetRegistryValueFromView nástroje MSBuild

Funkce vlastnosti `GetRegistryValueFromView` MSBuild získá data systémového registru podle klíče registru, hodnoty a jednoho nebo více seřazených zobrazení registru. Klíč a hodnota jsou prohledány v každém zobrazení registru v pořadí, dokud nebudou nalezeny.

Syntaxe pro tuto funkci vlastnosti je:

```fundamental
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Operační systém Windows 64 udržuje klíč registru **HKEY_LOCAL_MACHINE \software\wow6432node** , který nabízí zobrazení registru **HKEY_LOCAL_MACHINE \Software** pro 32 aplikace.

Ve výchozím nastavení 32 aplikace spuštěná v WOW64 přistupuje ke 32 zobrazení registru a aplikace 64-bit 64 přistupuje k zobrazení 16bitového registru.

K dispozici jsou následující zobrazení registru:

|Zobrazení registru|Definice|
|-------------------|----------------|
|Zadaná RegistryView. Registry32|Zobrazení registru pro 32 bitových aplikací.|
|Zadaná RegistryView. Registry64|Zobrazení registru pro 64 bitových aplikací.|
|Zadaná RegistryView. Default|Zobrazení registru, které odpovídá procesu, ve kterém je aplikace spuštěná.|

Například:

 ```fundamental
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

Získá **SLRuntimeInstallPath** data **ReferenceAssemblies** klíče, hledá se nejprve v zobrazení registru 64 a potom v zobrazení registru 32.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

Funkce MSBuild `MakeRelative` Property vrátí relativní cestu druhé cesty vzhledem k první cestě. Každá cesta může být soubor nebo složka.

Tato funkce vlastnosti má následující syntaxi:

```fundamental
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

## <a name="msbuild-valueordefault"></a>ValueOrDefault nástroje MSBuild

Funkce vlastnosti MSBuild `ValueOrDefault` vrátí první argument, pokud nemá hodnotu null ani není prázdný. Pokud má první argument hodnotu null nebo je prázdný, funkce vrátí druhý argument.

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

## <a name="see-also"></a>Viz také:

- [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md)

- [Přehled nástroje MSBuild](../msbuild/msbuild.md)
