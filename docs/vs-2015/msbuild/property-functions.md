---
title: Funkce vlastností | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0194de0a9f14186dc02b17564c77b1b2bc7441be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920171"
---
# <a name="property-functions"></a>Funkce vlastností
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
V rozhraní .NET Framework verze 4 a 4.5 lze použít funkce vlastností k vyhodnocení skriptů nástroje MSBuild. Funkce vlastností je možné bez ohledu na to vlastnosti se zobrazí. Na rozdíl od úloh funkce vlastností lze použít vně cíle a vyhodnocují před spuštěním jakékoli cílové.  
  
 Bez použití úkolů nástroje MSBuild, přečíst systémový čas, porovnat řetězce, porovnat regulární výrazy a provádět jiné akce v váš skript buildu. Nástroj MSBuild se pokusí převést řetězec na číslo a číslo na řetězec a ujistěte se, ostatní převody, podle potřeby.  
  
 **V tomto tématu:**  
  
-   [Syntaxe funkce vlastností](#BKMK_Syntax)  
  
    -   [Funkce vlastností řetězce](#BKMK_String)  
  
    -   [Funkce statických vlastností](#BKMK_Static)  
  
    -   [Volání metody Instance ve statické vlastnosti](#BKMK_InstanceMethods)  
  
    -   [Funkce vlastností MSBuild](#BKMK_PropertyFunctions)  
  
-   [Vnořené vlastnosti funkce](#BKMK_Nested)  
  
-   [MSBuild DoesTaskHostExist](#BKMK_DoesTaskHostExist)  
  
-   [MSBuild GetDirectoryNameOfFileAbove](#BKMK_GetDirectoryNameOfFileAbove)  
  
-   [MSBuild GetRegistryValue](#BKMK_GetRegistryValue)  
  
-   [MSBuild GetRegistryValueFromView](#BKMK_GetRegistryValueFromView)  
  
-   [MSBuild MakeRelative](#BKMK_MakeRelative)  
  
-   [MSBuild ValueOrDefault](#BKMK_ValueOrDefault)  
  
##  <a name="BKMK_Syntax"></a> Syntaxe funkce vlastností  
 Toto jsou tři druhy vlastnost funkce. Každá funkce má odlišnou syntaxi:  
  
-   Funkce vlastností řetězců (instance)  
  
-   Funkce statických vlastností  
  
-   Funkce vlastností MSBuild  
  
###  <a name="BKMK_String"></a> Funkce vlastností řetězce  
 Všechny hodnoty vlastností sestavení jsou jenom řetězcové hodnoty. Provozovat na jakoukoli hodnotu vlastnosti můžete použít metody řetězců (instance). Název jednotky (prvních tří znaků) může například extrahovat z vlastnosti sestavení, který představuje úplnou cestu pomocí tohoto kódu:  
  
 `$(ProjectOutputFolder.Substring(0,3))`  
  
###  <a name="BKMK_Static"></a> Funkce statických vlastností  
 Ve vašem skriptu sestavení můžete přistupovat statické vlastnosti a metody mnoha systémových tříd. Chcete-li získat hodnotu statická vlastnost, použijte následující syntaxi, kde *třídy* je název třídy systému a *vlastnost* je název vlastnosti.  
  
 `$([Class]::Property)`  
  
 Například můžete použít následující kód pro nastavení vlastnosti sestavení na aktuální datum a čas.  
  
 `<Today>$([System.DateTime]::Now)</Today>`  
  
 Zavolat statickou metodu, použijte následující syntaxi, kde *třídy* je název třídy systému *metoda* je název metody, a *(parametry)* je seznam parametrů pro metodu:  
  
 `$([Class]::Method(Parameters))`  
  
 Například pokud chcete nastavit vlastnost sestavení na nové GUID, můžete použít tento skript:  
  
 `<NewGuid>$([System.Guid]::NewGuid())</NewGuid>`  
  
 Statická vlastnost funkcí můžete použít všechny statické metody nebo vlastnosti z těchto tříd systému:  
  
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
  
- System.UInt16  
  
- System.UInt32  
  
- System.UInt64  
  
- System.SByte  
  
- System.Single  
  
- System.String  
  
- System.StringComparer  
  
- Hodnota System.TimeSpan  
  
- System.Text.RegularExpressions.Regex  
  
- Microsoft.Build.Utilities.ToolLocationHelper  
  
  Kromě toho můžete použít následující statické metody a vlastnosti:  
  
- System.Environment::CommandLine  
  
- System.Environment::ExpandEnvironmentVariables  
  
- System.Environment::GetEnvironmentVariable  
  
- System.Environment::GetEnvironmentVariables  
  
- System.Environment::GetFolderPath  
  
- System.Environment::GetLogicalDrives  
  
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
  
###  <a name="BKMK_InstanceMethods"></a> Volání metody Instance ve statické vlastnosti  
 Pokud přistupujete statickou vlastnost, která vrací instanci objektu, můžete vyvolat metody instance tohoto objektu. Chcete-li vyvolat metodu instance, použijte následující syntaxi, kde *třídy* je název třídy systému *vlastnost* je název vlastnosti, *– metoda* je název Metoda, a *(parametry)* je seznam parametrů pro metodu:  
  
 `$([Class]::Property.Method(Parameters))`  
  
 Název třídy musí být plně kvalifikovaný s oborem názvů.  
  
 Například můžete použít následující kód pro nastavení vlastnosti sestavení na aktuální datum ještě dnes.  
  
 `<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>`  
  
###  <a name="BKMK_PropertyFunctions"></a> Funkce vlastností MSBuild  
 Několik statických metod v sestavení je přístupná poskytnout aritmetický bitový logický a podporu řídicí znak. Tyto metody přistupujete pomocí následující syntaxe, kde *metoda* je název metody a *parametry* je seznam parametrů pro metodu.  
  
 `$([MSBuild]::Method(Parameters))`  
  
 Například pro sečtení dvou vlastností, které mají číselné hodnoty, použijte následující kód.  
  
 `$([MSBuild]::Add($(NumberOne), $(NumberTwo))`  
  
 Tady je seznam funkcí vlastností MSBuild:  
  
|Signatura funkce|Popis|  
|------------------------|-----------------|  
|Přidat Double (double a double b)|Přidejte dvě Double.|  
|dlouho přidáte (long, dlouhé b)|Přidejte dvě dlouhé.|  
|Double odečíst (double a double b)|Odečtení dvou hodnot datového typu Double.|  
|dlouho odečte (long, dlouhé b)|Odečtení dvou dlouhé.|  
|Double násobení (double a double b)|Vynásobí dvě Double.|  
|dlouho násobení (long, long b)|Vynásobí dvě dlouhé.|  
|Double rozdělte (double a double b)|Vydělí dvě Double.|  
|Rozdělte dlouhé (long, long b)|Vydělí dvě dlouhé.|  
|dvojité Modulo (double a double b)|Modulo dvě Double.|  
|dlouho Modulo (long, long b)|Modulo dvě dlouhé.|  
|řetězec Escape(string unescaped)|Řídicí řetězce podle pravidel útěku MSBuild.|  
|řetězec Unescape (uvozený řetězec)|Unescape – řetězce podle pravidel útěku MSBuild.|  
|int BitwiseOr (int první, int sekundu)|Provedení bitové operace `OR` prvního a druhého (první &#124; druhé).|  
|int BitwiseAnd (int první, int sekundu)|Provedení bitové operace `AND` prvního a druhého (první a druhé).|  
|int BitwiseXor (int první, int sekundu)|Provedení bitové operace `XOR` prvního a druhého (první ^ druhé).|  
|int BitwiseNot(int first)|Provedení bitové operace `NOT` (~ první).|  
  
##  <a name="BKMK_Nested"></a> Vnořené vlastnosti funkce  
 Můžete kombinovat funkce vlastností formuláře složitější funguje, jak ukazuje následující příklad.  
  
 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`  
  
 V tomto příkladu vrátí hodnotu <xref:System.IO.FileAttributes> `Archive` bit (32 nebo 0) soubor danou cestou `tempFile`. Všimněte si, že hodnoty výčtu dat nemůže být použit název v rámci funkce vlastností. Číselná hodnota (32) musíte použít místo toho.  
  
 Vnořené vlastnosti funkce může také zobrazit metadata. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).  
  
##  <a name="BKMK_DoesTaskHostExist"></a> MSBuild DoesTaskHostExist  
 `DoesTaskHostExist` Vlastnost funkce v nástroji MSBuild vrátí, zda je hostitel úloh aktuálně nainstalované pro zadané hodnoty modulu runtime a architektury.  
  
 Tato vlastnost funkce má následující syntaxi:  
  
```  
$[MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture)  
```  
  
##  <a name="BKMK_GetDirectoryNameOfFileAbove"></a> MSBuild GetDirectoryNameOfFileAbove  
 MSBuild `GetDirectoryNameOfFileAbove` vlastnost funkce hledá soubor v adresářích nad aktuálního adresáře v cestě.  
  
 Tato vlastnost funkce má následující syntaxi:  
  
```  
$[MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile)  
```  
  
 Následující kód je příkladem této syntaxe.  
  
```  
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />  
```  
  
##  <a name="BKMK_GetRegistryValue"></a> MSBuild GetRegistryValue  
 MSBuild `GetRegistryValue` vlastnost funkce vrací hodnotu klíče registru. Tato funkce přebírá dva argumenty, název klíče a název hodnoty a vrátí hodnotu z registru. Pokud nezadáte název hodnoty, vrátí se výchozí hodnota.  
  
 Následující příklady ukazují, jak tato funkce slouží:  
  
```  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))  
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value  
  
```  
  
##  <a name="BKMK_GetRegistryValueFromView"></a> MSBuild GetRegistryValueFromView  
 MSBuild `GetRegistryValueFromView` vlastnost funkce získá data registru systému daný klíč registru, hodnotu a jeden nebo více seřazené registru zobrazení. Klíče a hodnoty budou prohledány v každém zobrazení registru v pořadí, dokud se nenachází.  
  
 Syntaxe pro tuto funkci vlastnost je:  
  
 [Nástroj MSBuild\]:: GetRegistryValueFromView (keyName řetězec, valueName řetězec, objekt defaultValue, zobrazení params object [])  
  
 Operační systém Windows 64-bit uchovává HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node klíč registru, který představuje zobrazení HKEY_LOCAL_MACHINE\SOFTWARE registru pro 32bitové aplikace.  
  
 Ve výchozím nastavení 32bitové aplikace běžící v prostředí WOW64, má přístup k zobrazení 32bitového registru a 64bitové aplikace přistupuje k zobrazení 64bitovém registru.  
  
 K dispozici jsou následující zobrazení registru:  
  
|Zobrazení registru|Definice|  
|-------------------|----------------|  
|RegistryView.Registry32|Zobrazení registru 32bitovou aplikaci.|  
|RegistryView.Registry64|Zobrazení registru 64bitové aplikace.|  
|RegistryView.Default|Zobrazení registru, který odpovídá proces, na kterém aplikace běží na.|  
  
 Následuje příklad.  
  
 `$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))`  
  
 získá data SLRuntimeInstallPath ReferenceAssemblies klíče, nejprve v 64bitovém registru zobrazení a poté v zobrazení 32bitového registru.  
  
##  <a name="BKMK_MakeRelative"></a> MSBuild MakeRelative  
 MSBuild `MakeRelative` vlastnost funkce vrátí relativní cesta druhý cestu relativní vzhledem k první cesta. Každá cesta může být soubor nebo složku.  
  
 Tato vlastnost funkce má následující syntaxi:  
  
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
  
##  <a name="BKMK_ValueOrDefault"></a> MSBuild ValueOrDefault  
 MSBuild `ValueOrDefault` vlastnost funkce vrátí první argument, pokud má hodnotu null nebo prázdný. Pokud první argument je null nebo prázdný, funkce vrátí druhý argument.  
  
 Následující příklad ukazuje, jak tuto funkci použít.  
  
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


