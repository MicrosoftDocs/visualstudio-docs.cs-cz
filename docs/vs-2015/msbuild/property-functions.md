---
title: Funkce vlastností | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4108e478e9e77a5ed5699b39dfae44884a6befd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67826179"
---
# <a name="property-functions"></a>Funkce vlastností
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V .NET Framework verzích 4 a 4,5 se funkce vlastností dají použít k vyhodnocení skriptů MSBuild. Funkce vlastností lze použít všude, kde se zobrazí vlastnosti. Na rozdíl od úloh lze funkce vlastností použít mimo cíle a jsou vyhodnocovány před jakýmkoli cílovým spuštěním.  
  
 Bez použití úloh nástroje MSBuild můžete přečíst systémový čas, porovnat řetězce, porovnat regulární výrazy a provádět další akce v rámci skriptu sestavení. Nástroj MSBuild se pokusí převést řetězec na číslo a číslo na řetězec a provést další převody podle požadavků.  
  
 **V tomto tématu:**  
  
- [Syntaxe funkce Property](#BKMK_Syntax)  
  
  - [Funkce řetězcových vlastností](#BKMK_String)  

  - [Funkce statických vlastností](#BKMK_Static)  

  - [Volání metod instancí ve statických vlastnostech](#BKMK_InstanceMethods)  

  - [Funkce vlastností MSBuild](#BKMK_PropertyFunctions)  
  
- [Vnořené funkce vlastností](#BKMK_Nested)  
  
- [DoesTaskHostExist nástroje MSBuild](#BKMK_DoesTaskHostExist)  
  
- [GetDirectoryNameOfFileAbove nástroje MSBuild](#BKMK_GetDirectoryNameOfFileAbove)  
  
- [GetRegistryValue nástroje MSBuild](#BKMK_GetRegistryValue)  
  
- [GetRegistryValueFromView nástroje MSBuild](#BKMK_GetRegistryValueFromView)  
  
- [MakeRelative nástroje MSBuild](#BKMK_MakeRelative)  
  
- [ValueOrDefault nástroje MSBuild](#BKMK_ValueOrDefault)  
  
## <a name="property-function-syntax"></a><a name="BKMK_Syntax"></a> Syntaxe funkce Property  
 Jedná se o tři druhy funkcí vlastností; Každá funkce má odlišnou syntaxi:  
  
- Funkce pro vlastnosti String (instance)  
  
- Funkce statických vlastností  
  
- Funkce vlastností MSBuild  
  
### <a name="string-property-functions"></a><a name="BKMK_String"></a> Funkce řetězcových vlastností  
 Všechny hodnoty vlastností buildu jsou jenom řetězcové hodnoty. Můžete použít metody řetězce (instance) k provozování libovolné hodnoty vlastnosti. Můžete například extrahovat název jednotky (první tři znaky) z vlastnosti Build, která představuje úplnou cestu pomocí tohoto kódu:  
  
 `$(ProjectOutputFolder.Substring(0,3))`  
  
### <a name="static-property-functions"></a><a name="BKMK_Static"></a> Funkce statických vlastností  
 Ve svém skriptu sestavení máte přístup ke statickým vlastnostem a metodám mnoha systémových tříd. Chcete-li získat hodnotu statické vlastnosti, použijte následující syntaxi, kde *Class* je název systémové třídy a *vlastnost* je název vlastnosti.  
  
 `$([Class]::Property)`  
  
 Například můžete použít následující kód k nastavení vlastnosti Build na aktuální datum a čas.  
  
 `<Today>$([System.DateTime]::Now)</Today>`  
  
 Chcete-li zavolat statickou metodu, použijte následující syntaxi, kde *Class* je název systémové třídy, *Metoda* je název metody a *(parametry)* je seznam parametrů pro metodu:  
  
 `$([Class]::Method(Parameters))`  
  
 Chcete-li například nastavit vlastnost Build na nový identifikátor GUID, můžete použít tento skript:  
  
 `<NewGuid>$([System.Guid]::NewGuid())</NewGuid>`  
  
 Ve funkcích statických vlastností můžete použít jakoukoli statickou metodu nebo vlastnost těchto systémových tříd:  
  
- System. Byte  
  
- System. Char  
  
- System. Convert  
  
- System. DateTime  
  
- System. Decimal  
  
- System. Double  
  
- System. Enum  
  
- System. GUID  
  
- System. Int16  
  
- System. Int32  
  
- System. Int64  
  
- System. IO. Path  
  
- System. Math  
  
- System. UInt16  
  
- System. UInt32  
  
- System. UInt64  
  
- System. SByte  
  
- System. Single  
  
- System. String  
  
- System. StringComparer  
  
- System. TimeSpan  
  
- System. text. RegularExpressions. Regex  
  
- Microsoft. Build. Utilities. ToolLocationHelper  
  
  Kromě toho můžete použít následující statické metody a vlastnosti:  
  
- System. Environment:: CommandLine  
  
- System. Environment:: ExpandEnvironmentVariables  
  
- System. Environment:: GetEnvironmentVariable  
  
- System. Environment:: GetEnvironmentVariables  
  
- System. Environment:: GetFolderPath  
  
- System. Environment:: GetLogicalDrives  
  
- System. IO. Directory:: getdirectors  
  
- System. IO. Directory:: GetFiles  
  
- System. IO. Directory:: GetLastAccessTime  
  
- System. IO. Directory:: GetLastWriteTime  
  
- System. IO. Directory:: GetParent  
  
- System. IO. File:: Exists  
  
- System. IO. File:: GetCreationTime  
  
- System. IO. File:: GetAttributes  
  
- System. IO. File:: GetLastAccessTime  
  
- System. IO. File:: GetLastWriteTime  
  
- System. IO. File:: ReadAllText  
  
### <a name="calling-instance-methods-on-static-properties"></a><a name="BKMK_InstanceMethods"></a> Volání metod instancí ve statických vlastnostech  
 Pokud přistupujete ke statické vlastnosti, která vrací instanci objektu, můžete vyvolat metody instance daného objektu. Chcete-li vyvolat metodu instance, použijte následující syntaxi, kde *Třída* je název systémové třídy, *vlastnost* je název vlastnosti, *Metoda* je název metody a *(parametry)* je seznam parametrů pro metodu:  
  
 `$([Class]::Property.Method(Parameters))`  
  
 Název třídy musí být plně kvalifikován pomocí oboru názvů.  
  
 Například můžete použít následující kód pro nastavení vlastnosti Build na aktuální datum v dnešní době.  
  
 `<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>`  
  
### <a name="msbuild-property-functions"></a><a name="BKMK_PropertyFunctions"></a> Funkce vlastností MSBuild  
 Několik statických metod v sestavení lze použít k zajištění aritmetické, bitové logické a řídicí znakové podpory. K těmto metodám přistupujete pomocí následující syntaxe, kde *Metoda* je název metody a *parametry* je seznam parametrů pro metodu.  
  
 `$([MSBuild]::Method(Parameters))`  
  
 Chcete-li například přidat dohromady dvě vlastnosti, které mají číselné hodnoty, použijte následující kód.  
  
 `$([MSBuild]::Add($(NumberOne), $(NumberTwo))`  
  
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
|Bitový operátor int (int First, int Second)|Proveďte bitovou kopii `OR` prvního a druhého (první &#124; sekundu).|  
|int BitwiseAnd (int First, int Second)|Proveďte bitovou kopii `AND` prvního a druhého (první & sekundu).|  
|int BitwiseXor (int First, int Second)|Proveďte bitovou kopii `XOR` prvního a druhého (prvních ^ sekund).|  
|int BitwiseNot (int First)|Proveďte bitovou `NOT` (~ First).|  
  
## <a name="nested-property-functions"></a><a name="BKMK_Nested"></a> Vnořené funkce vlastností  
 Můžete zkombinovat funkce vlastností a vytvořit tak složitější funkce, jak ukazuje následující příklad.  
  
 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`  
  
 Tento příklad vrátí hodnotu <xref:System.IO.FileAttributes> `Archive` bitu (32 nebo 0) souboru daného cestou `tempFile` . Všimněte si, že hodnoty výčtu dat nemohou být v rámci funkcí vlastností uvedeny podle názvu. Místo toho je třeba použít číselnou hodnotu (32).  
  
 Metadata se můžou objevit i ve funkcích vnořených vlastností. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).  
  
## <a name="msbuild-doestaskhostexist"></a><a name="BKMK_DoesTaskHostExist"></a> DoesTaskHostExist nástroje MSBuild  
 `DoesTaskHostExist`Funkce Property v nástroji MSBuild vrátí, zda je hostitel úlohy aktuálně nainstalován pro zadané hodnoty modulu runtime a architektury.  
  
 Tato funkce vlastnosti má následující syntaxi:  
  
```  
$[MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture)  
```  
  
## <a name="msbuild-getdirectorynameoffileabove"></a><a name="BKMK_GetDirectoryNameOfFileAbove"></a> GetDirectoryNameOfFileAbove nástroje MSBuild  
 Funkce MSBuild `GetDirectoryNameOfFileAbove` Property vyhledá soubor v adresářích nad aktuální adresář v cestě.  
  
 Tato funkce vlastnosti má následující syntaxi:  
  
```  
$[MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile)  
```  
  
 Následující kód je příkladem této syntaxe.  
  
```  
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />  
```  
  
## <a name="msbuild-getregistryvalue"></a><a name="BKMK_GetRegistryValue"></a> GetRegistryValue nástroje MSBuild  
 `GetRegistryValue`Funkce vlastnosti MSBuild vrací hodnotu klíče registru. Tato funkce přijímá dva argumenty, název klíče a název hodnoty a vrací hodnotu z registru. Pokud nezadáte název hodnoty, vrátí se výchozí hodnota.  
  
 Následující příklady ukazují, jak se tato funkce používá:  
  
```  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))  
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value  
  
```  
  
## <a name="msbuild-getregistryvaluefromview"></a><a name="BKMK_GetRegistryValueFromView"></a> GetRegistryValueFromView nástroje MSBuild  
 `GetRegistryValueFromView`Funkce vlastnosti MSBuild získá data systémového registru podle klíče registru, hodnoty a jednoho nebo více seřazených zobrazení registru. Klíč a hodnota jsou prohledány v každém zobrazení registru v pořadí, dokud nebudou nalezeny.  
  
 Syntaxe pro tuto funkci vlastnosti je:  
  
 [MSBuild \] :: GetRegistryValueFromView (řetězcové keynamey, řetězec valueName, objekt DefaultValue, objekt params [] zobrazení)  
  
 Operační systém Windows 64 udržuje klíč registru HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node, který nabízí zobrazení registru HKEY_LOCAL_MACHINE \SOFTWARE pro 32 aplikace.  
  
 Ve výchozím nastavení 32 aplikace spuštěná v WOW64 přistupuje ke 32 zobrazení registru a aplikace 64-bit 64 přistupuje k zobrazení 16bitového registru.  
  
 K dispozici jsou následující zobrazení registru:  
  
|Zobrazení registru|Definice|  
|-------------------|----------------|  
|Zadaná RegistryView. Registry32|Zobrazení registru pro 32 bitových aplikací.|  
|Zadaná RegistryView. Registry64|Zobrazení registru pro 64 bitových aplikací.|  
|Zadaná RegistryView. Default|Zobrazení registru, které odpovídá procesu, ve kterém je aplikace spuštěná.|  
  
 Následuje příklad.  
  
 `$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))`  
  
 Získá SLRuntimeInstallPath data ReferenceAssemblies klíče, hledá se nejprve v zobrazení registru 64 a potom v zobrazení registru 32.  
  
## <a name="msbuild-makerelative"></a><a name="BKMK_MakeRelative"></a> MakeRelative nástroje MSBuild  
 Funkce MSBuild `MakeRelative` Property vrátí relativní cestu druhé cesty vzhledem k první cestě. Každá cesta může být soubor nebo složka.  
  
 Tato funkce vlastnosti má následující syntaxi:  
  
```  
$[MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2))  
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
  
## <a name="msbuild-valueordefault"></a><a name="BKMK_ValueOrDefault"></a> ValueOrDefault nástroje MSBuild  
 Funkce MSBuild `ValueOrDefault` Property vrátí první argument, pokud není null nebo prázdný. Pokud má první argument hodnotu null nebo je prázdný, funkce vrátí druhý argument.  
  
 Následující příklad ukazuje, jak je tato funkce použita.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <Value1>$([MSBuild]::ValueOrDefault(`$(UndefinedValue)`, `a`))</Value1>  
        <Value2>$([MSBuild]::ValueOrDefault(`b`, `$(Value1)`))</Value2>  
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
[Vlastnosti nástroje MSBuild](msbuild-properties1.md)   
[Přehled nástroje MSBuild](msbuild.md)
