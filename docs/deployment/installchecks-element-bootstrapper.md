---
title: '&lt;InstallChecks – &gt; element (zaváděcí nástroj) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7ba4da072a586bdc09993b77200a769be3940ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536302"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks – &gt; element (zaváděcí nástroj)
`InstallChecks`Prvek podporuje spuštění různých testů pro místní počítač, aby bylo zajištěno, že byly nainstalovány všechny odpovídající požadavky na aplikaci.

## <a name="syntax"></a>Syntax

```xml
<InstallChecks>
    <AssemblyCheck
        Property
        Name
        PublicKeyToken
        Version
        Language
        ProcessorArchitecture
    />
    <RegistryCheck
        Property
        Key
        Value
    />
    <ExternalCheck
        PackageFile
        Property
        Arguments
    />
    <FileCheck
        Property
        FileName
        SearchPath
        SpecialFolder
        SearchDepth
    />
    <MsiProductCheck
        Property
        Product
        Feature
    />
    <RegistryFileCheck
        Property
        Key
        Value
        FileName
        SearchDepth
    />
</InstallChecks>
```

## <a name="assemblycheck"></a>AssemblyCheck
 Tento prvek je volitelný podřízený prvek elementu `InstallChecks` . Pro každou instanci `AssemblyCheck` nástroje zaváděcí nástroj zajistí, aby sestavení identifikované prvkem existovalo v globální mezipaměti sestavení (GAC). Neobsahuje žádné elementy a má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`Property`|Povinná hodnota. Název vlastnosti, do které se má uložit výsledek Na tuto vlastnost lze odkazovat z testu pod `InstallConditions` prvkem, který je podřízeným `Command` prvkem elementu. Další informace naleznete v tématu [ \<Commands> element](../deployment/commands-element-bootstrapper.md).|
|`Name`|Povinná hodnota. Plně kvalifikovaný název sestavení, které má být zkontrolováno.|
|`PublicKeyToken`|Povinná hodnota. Zkrácený tvar veřejného klíče přidruženého k tomuto silně pojmenovanému sestavení. Všechna sestavení uložená v globální mezipaměti sestavení (GAC) musí mít název, verzi a veřejný klíč.|
|`Version`|Povinná hodnota. Verze sestavení<br /><br /> Číslo verze má formát \<*major version*> . \<*minor version*> . \<*build version*> . \<*revision version*> .|
|`Language`|Nepovinný parametr. Jazyk lokalizovaného sestavení. Výchozí je `neutral`.|
|`ProcessorArchitecture`|Nepovinný parametr. Procesor počítače, na který cílí Tato instalace Výchozí je `msil`.|

## <a name="externalcheck"></a>ExternalCheck
 Tento prvek je volitelný podřízený prvek elementu `InstallChecks` . Pro každou instanci `ExternalCheck` nástroje zaváděcí nástroj spustí pojmenovaný externí program v samostatném procesu a uloží jeho ukončovací kód do vlastnosti uvedené v `Property` . `ExternalCheck` je vhodný pro implementaci složitých kontrol závislosti nebo v případě, že jediný způsob kontroly existence součásti je vytvoření instance.

 `ExternalCheck` neobsahuje žádné elementy a má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`Property`|Povinná hodnota. Název vlastnosti, do které se má uložit výsledek Na tuto vlastnost lze odkazovat z testu pod `InstallConditions` prvkem, který je podřízeným `Command` prvkem elementu. Další informace naleznete v tématu [ \<Commands> element](../deployment/commands-element-bootstrapper.md).|
|`PackageFile`|Povinná hodnota. Externí program, který se má provést. Program musí být součástí distribučního balíčku instalace.|
|`Arguments`|Nepovinný parametr. Poskytuje argumenty příkazového řádku pro spustitelný soubor s názvem `PackageFile` .|

## <a name="filecheck"></a>Kontroler
 Tento prvek je volitelný podřízený prvek elementu `InstallChecks` . Pro každou instanci `FileCheck` nástroje zaváděcí nástroj určí, zda existuje pojmenovaný soubor, a vrátí číslo verze souboru. Pokud soubor nemá číslo verze, zaváděcí nástroj nastaví vlastnost s názvem `Property` na 0. Pokud soubor neexistuje, není `Property` nastaven na žádnou hodnotu.

 `FileCheck` neobsahuje žádné elementy a má následující atributy.

| Atribut | Popis |
|-----------------| - |
| `Property` | Povinná hodnota. Název vlastnosti, do které se má uložit výsledek Na tuto vlastnost lze odkazovat z testu pod `InstallConditions` prvkem, který je podřízeným `Command` prvkem elementu. Další informace naleznete v tématu [ \<Commands> element](../deployment/commands-element-bootstrapper.md). |
| `FileName` | Povinná hodnota. Název souboru, který se má najít |
| `SearchPath` | Povinná hodnota. Disk nebo složka, ve které chcete soubor vyhledat. Pokud je přiřazena, musí se jednat o relativní cestu `SpecialFolder` . v opačném případě musí být absolutní cesta. |
| `SpecialFolder` | Nepovinný parametr. Složka, která má zvláštní význam buď pro systém Windows, nebo na [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Výchozí hodnota je interpretována `SearchPath` jako absolutní cesta. Platné hodnoty jsou následující:<br /><br /> `AppDataFolder`. Složka Application data pro tuto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci, která je specifická pro aktuálního uživatele.<br /><br /> `CommonAppDataFolder`. Složka Application data použitá všemi uživateli<br /><br /> `CommonFilesFolder`. Složka Common Files pro aktuálního uživatele<br /><br /> `LocalDataAppFolder`. Složka dat pro neroamingové aplikace<br /><br /> `ProgramFilesFolder`. Složka standardního programu Program Files pro 32-bitové aplikace.<br /><br /> `StartUpFolder`. Složka, která obsahuje všechny aplikace spuštěné při spuštění systému.<br /><br /> `SystemFolder`. Složka, která 32 obsahuje 32bitové systémové knihovny DLL.<br /><br /> `WindowsFolder`. Složka, která obsahuje instalaci systému Windows.<br /><br /> `WindowsVolume`. Jednotka nebo oddíl, který obsahuje instalaci systému Windows. |
| `SearchDepth` | Nepovinný parametr. Hloubka, na které se mají hledat podsložky v podsložkách pro pojmenovaný soubor Hledání má první hloubku. Výchozí hodnota je 0, což omezuje hledání do složky na nejvyšší úrovni určené pomocí `SpecialFolder` a **SearchPath**. |

## <a name="msiproductcheck"></a>MsiProductCheck
 Tento prvek je volitelný podřízený prvek elementu `InstallChecks` . Pro každou instanci `MsiProductCheck` nástroje zaváděcí nástroj kontroluje, zda byla zadaná instalace aplikace Microsoft instalační služba systému Windows spuštěna až do dokončení. Hodnota vlastnosti je nastavena v závislosti na stavu nainstalovaného produktu. Kladná hodnota znamená, že je produkt nainstalovaný, 0 nebo-1 znamená, že není nainstalovaný. (Další informace najdete v MsiQueryFeatureState funkce sady SDK pro Instalační služba systému Windows.) . Pokud Instalační služba systému Windows není v počítači nainstalován, `Property` není nastavena.

 `MsiProductCheck` neobsahuje žádné elementy a má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`Property`|Povinná hodnota. Název vlastnosti, do které se má uložit výsledek Na tuto vlastnost lze odkazovat z testu pod `InstallConditions` prvkem, který je podřízeným `Command` prvkem elementu. Další informace naleznete v tématu [ \<Commands> element](../deployment/commands-element-bootstrapper.md).|
|`Product`|Povinná hodnota. Identifikátor GUID nainstalovaného produktu.|
|`Feature`|Nepovinný parametr. Identifikátor GUID konkrétní funkce nainstalované aplikace.|

## <a name="registrycheck"></a>RegistryCheck
 Tento prvek je volitelný podřízený prvek elementu `InstallChecks` . Pro každou instanci `RegistryCheck` nástroje zaváděcí nástroj zkontroluje, zda zadaný klíč registru existuje nebo zda má určenou hodnotu.

 `RegistryCheck` neobsahuje žádné elementy a má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`Property`|Povinná hodnota. Název vlastnosti, do které se má uložit výsledek Na tuto vlastnost lze odkazovat z testu pod `InstallConditions` prvkem, který je podřízeným `Command` prvkem elementu. Další informace naleznete v tématu [ \<Commands> element](../deployment/commands-element-bootstrapper.md).|
|`Key`|Povinná hodnota. Název klíče registru.|
|`Value`|Nepovinný parametr. Název hodnoty registru, která se má načíst. Ve výchozím nastavení se vrátí text výchozí hodnoty. `Value` musí být buď řetězec, nebo hodnota DWORD.|

## <a name="registryfilecheck"></a>RegistryFileCheck
 Tento prvek je volitelný podřízený prvek elementu `InstallChecks` . Pro každou instanci `RegistryFileCheck` nástroje zaváděcí nástroj načte verzi zadaného souboru, nejprve se pokusí načíst cestu k souboru ze zadaného klíče registru. To je užitečné hlavně v případě, že chcete vyhledat soubor v adresáři zadaném jako hodnota v registru.

 `RegistryFileCheck` neobsahuje žádné elementy a má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`Property`|Povinná hodnota. Název vlastnosti, do které se má uložit výsledek Na tuto vlastnost lze odkazovat z testu pod `InstallConditions` prvkem, který je podřízeným `Command` prvkem elementu. Další informace naleznete v tématu [ \<Commands> element](../deployment/commands-element-bootstrapper.md).|
|`Key`|Povinná hodnota. Název klíče registru. Jeho hodnota je interpretována jako cesta k souboru, pokud `File` atribut není nastaven. Pokud tento klíč neexistuje, `Property` není nastaven.|
|`Value`|Nepovinný parametr. Název hodnoty registru, která se má načíst. Ve výchozím nastavení se vrátí text výchozí hodnoty. `Value` musí být řetězec.|
|`FileName`|Nepovinný parametr. Název souboru. Je-li tento parametr zadán, bude hodnota získaná z klíče registru považována za cestu k adresáři a tento název je připojen k tomuto názvu. Pokud není zadaný, předpokládá se hodnota vrácená z registru jako úplná cesta k souboru.|
|`SearchDepth`|Nepovinný parametr. Hloubka, na které se mají hledat podsložky v podsložkách pro pojmenovaný soubor Hledání má první hloubku. Výchozí hodnota je 0, což omezuje hledání na složku nejvyšší úrovně určenou hodnotou klíče registru.|

## <a name="remarks"></a>Poznámky
 Zatímco prvky pod `InstallChecks` definují testy, které mají být spuštěny, nejsou spuštěny. Chcete-li provést testy, je nutné vytvořit `Command` prvky pod `Commands` prvkem.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `InstallChecks` prvek, který je použit v souboru produktu pro .NET Framework.

```xml
<InstallChecks>
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
</InstallChecks>
```

## <a name="installconditions"></a>InstallConditions
 Když `InstallChecks` jsou vyhodnocovány, vyvolávají vlastnosti. Vlastnosti se pak používají `InstallConditions` k určení, jestli se má balíček nainstalovat, vynechat nebo selhat. Následující tabulka uvádí `InstallConditions` :

|Stav|Popis|
|-|-|
|`FailIf`|Pokud se nějaká `FailIf` Podmínka vyhodnotí jako true, balíček se nepodaří. Zbývající podmínky nebudou vyhodnoceny.|
|`BypassIf`|Pokud se kterákoli `BypassIf` Podmínka vyhodnotí jako true, balíček se obejít. Zbývající podmínky nebudou vyhodnoceny.|

## <a name="predefined-properties"></a>Předdefinované vlastnosti
 V následující tabulce jsou uvedeny `BypassIf` `FailIf` prvky a:

|Vlastnost|Poznámky|Možné hodnoty|
|--------------|-----------|---------------------|
|`Version9X`|Číslo verze operačního systému Windows 9X.|4,10 = Windows 98|
|`VersionNT`|Číslo verze operačního systému založeného na systému Windows NT.|Hlavní_verze. podverze. ServicePack<br /><br /> 5,0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|
|`VersionNT64`|Číslo verze 64 operačního systému Windows NT.|Stejné, jak bylo zmíněno dříve.|
|`VersionMsi`|Číslo verze služby Instalační služba systému Windows.|2,0 = Instalační služba systému Windows 2,0|
|`AdminUser`|Určuje, jestli má uživatel oprávnění správce v operačním systému Windows NT.|0 = žádná oprávnění správce<br /><br /> 1 = oprávnění správce|

 Chcete-li například zablokovat instalaci na počítači se systémem Windows 95, použijte následující kód:

```xml
<!-- Block install on Windows 95 -->
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>
```

## <a name="see-also"></a>Viz také
- [\<Commands> objekt](../deployment/commands-element-bootstrapper.md)
- [Odkaz na schéma produktu a balíčku](../deployment/product-and-package-schema-reference.md)