---
title: '&lt;InstallChecks&gt; – Element (zaváděcí nástroj) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8004ccdcbd320479bcc1e343443ebdb017ee77f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896689"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt; – element (zaváděcí nástroj)
`InstallChecks` Element podporuje spouštění různých testy proti místnímu počítači, abyste měli jistotu, že byly nainstalovány všechny příslušné požadavky pro aplikaci.  

## <a name="syntax"></a>Syntaxe  

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
 Tento element je volitelný podřízený prvek `InstallChecks`. Pro každou instanci `AssemblyCheck`, zaváděcí nástroj budete mít jistotu, že sestavení identifikované elementem existuje v globální mezipaměti sestavení (GAC). Neobsahuje žádné elementy a má následující atributy.  

|Atribut|Popis|  
|---------------|-----------------|  
|`Property`|Požadováno. Název vlastnosti, která se uloží výsledek. Tato vlastnost může odkazovat z testu pod `InstallConditions` element, který je podřízeným prvkem z `Command` elementu. Další informace najdete v tématu [ \<příkazy > Element](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Požadováno. Plně kvalifikovaný název sestavení ke kontrole.|  
|`PublicKeyToken`|Požadováno. Zkrácené formě veřejný klíč přidružený k tomuto silný název sestavení. Všechna sestavení, které jsou uložené v mezipaměti GAC musí mít název, verzi a veřejný klíč.|  
|`Version`|Požadováno. Verze sestavení.<br /><br /> Číslo verze má formát \< *hlavní verze*>.\< *podverze*>.\< *verze buildu*>.\< *verze revize*>.|  
|`Language`|Volitelné. Jazyk lokalizované sestavení. Výchozí hodnota je `neutral`.|  
|`ProcessorArchitecture`|Volitelné. Procesor počítače, který je cílem této instalace. Výchozí hodnota je `msil`.|  

## <a name="externalcheck"></a>ExternalCheck  
 Tento element je volitelný podřízený prvek `InstallChecks`. Pro každou instanci `ExternalCheck`, zaváděcí nástroj spustit externí program s názvem v samostatném procesu a uložit jeho ukončovací kód ve vlastnosti indikován `Property`. `ExternalCheck` je užitečné pro provádění kontrol složitých závislostí, nebo pokud je jediný způsob, jak kontrolovat přítomnost součásti vytvořit její instanci.  

 `ExternalCheck` neobsahuje žádné elementy a má následující atributy.  

|Atribut|Popis|  
|---------------|-----------------|  
|`Property`|Požadováno. Název vlastnosti, která se uloží výsledek. Tato vlastnost může odkazovat z testu pod `InstallConditions` element, který je podřízeným prvkem z `Command` elementu. Další informace najdete v tématu [ \<příkazy > Element](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Požadováno. Externí program spustí. Program musí být součástí instalačního balíčku pro distribuci.|  
|`Arguments`|Volitelné. Zadává argumenty příkazového řádku pro spustitelný soubor s názvem podle `PackageFile`.|  

## <a name="filecheck"></a>FileCheck  
 Tento element je volitelný podřízený prvek `InstallChecks`. Pro každou instanci `FileCheck`, zaváděcí nástroj určí, zda existuje uvedeného souboru a vrátí číslo verze souboru. Pokud soubor neobsahuje číslo verze, zaváděcí nástroj nastaví vlastnost s názvem podle `Property` na hodnotu 0. Pokud soubor neexistuje, `Property` není nastavená na libovolnou hodnotu.  

 `FileCheck` neobsahuje žádné elementy a má následující atributy.  


| Atribut | Popis |
|-----------------| - |
| `Property` | Požadováno. Název vlastnosti, která se uloží výsledek. Tato vlastnost může odkazovat z testu pod `InstallConditions` element, který je podřízeným prvkem z `Command` elementu. Další informace najdete v tématu [ \<příkazy > Element](../deployment/commands-element-bootstrapper.md). |
| `FileName` | Požadováno. Název souboru, který má najít. |
| `SearchPath` | Požadováno. Disk nebo složku, do které má soubor hledat. Pokud to musí být relativní cesta `SpecialFolder` je přiřazena; v opačném případě musí být absolutní cesta. |
| `SpecialFolder` | Volitelné. Složka, která má zvláštní význam pro Windows nebo na [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Výchozí hodnota je k interpretaci `SearchPath` jako absolutní cesta. Platné hodnoty patří:<br /><br /> `AppDataFolder`. Složku application data pro to [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace; specifické pro aktuálního uživatele.<br /><br /> `CommonAppDataFolder`. Složce data aplikací všech uživatelů.<br /><br /> `CommonFilesFolder`. Složka Common Files pro aktuálního uživatele.<br /><br /> `LocalDataAppFolder`. Složka dat nepřenosných aplikací.<br /><br /> `ProgramFilesFolder`. Standardní složka Program Files pro 32bitové aplikace.<br /><br /> `StartUpFolder`. Tato složka obsahuje všechny aplikace, které jsou spuštěny při spuštění systému.<br /><br /> `SystemFolder`. Tato složka obsahuje 32bitové systémové knihovny DLL.<br /><br /> `WindowsFolder`. Tato složka obsahuje instalace systému Windows.<br /><br /> `WindowsVolume`. Disk nebo oddíl, který obsahuje instalace systému Windows. |
| `SearchDepth` | Volitelné. Hloubka, na který chcete vyhledat podsložky s názvem souboru. Hledání je hloubka první. Výchozí hodnota je 0, což omezuje vyhledávání na složku nejvyšší úrovně, určené `SpecialFolder` a **SearchPath**. |

## <a name="msiproductcheck"></a>MsiProductCheck  
 Tento element je volitelný podřízený prvek `InstallChecks`. Pro každou instanci `MsiProductCheck`, zaváděcí nástroj zkontroluje, zda zadané instalace Instalační služby systému Windows bylo spuštěno dokud se nedokončí. Hodnota vlastnosti je nastavena v závislosti na stavu nainstalovaného produktu. Kladná hodnota označuje, že je nainstalován produkt, 0 nebo -1 znamená, nenainstaluje se. (Podrobnosti najdete na funkci SDK Instalační služby systému Windows MsiQueryFeatureState Další informace.) . Pokud na počítači, není nainstalovaná Instalační služby systému Windows `Property` není nastaven.  

 `MsiProductCheck` neobsahuje žádné elementy a má následující atributy.  

|Atribut|Popis|  
|---------------|-----------------|  
|`Property`|Požadováno. Název vlastnosti, která se uloží výsledek. Tato vlastnost může odkazovat z testu pod `InstallConditions` element, který je podřízeným prvkem z `Command` elementu. Další informace najdete v tématu [ \<příkazy > Element](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Požadováno. Identifikátor GUID pro u nainstalovaného produktu.|  
|`Feature`|Volitelné. Identifikátor GUID pro konkrétní funkci nainstalované aplikace.|  

## <a name="registrycheck"></a>RegistryCheck  
 Tento element je volitelný podřízený prvek `InstallChecks`. Pro každou instanci `RegistryCheck`, zaváděcí nástroj zkontroluje, zda daný klíč registru existuje, nebo zda má uvedenou hodnotu.  

 `RegistryCheck` neobsahuje žádné elementy a má následující atributy.  

|Atribut|Popis|  
|---------------|-----------------|  
|`Property`|Požadováno. Název vlastnosti, která se uloží výsledek. Tato vlastnost může odkazovat z testu pod `InstallConditions` element, který je podřízeným prvkem z `Command` elementu. Další informace najdete v tématu [ \<příkazy > Element](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Požadováno. Název klíče registru.|  
|`Value`|Volitelné. Název hodnoty registru pro načtení. Ve výchozím nastavení je návratový text výchozí hodnotu. `Value` musí být řetězec nebo hodnota DWORD.|  

## <a name="registryfilecheck"></a>RegistryFileCheck  
 Tento element je volitelný podřízený prvek `InstallChecks`. Pro každou instanci `RegistryFileCheck`, zaváděcí nástroj načte verzi zadaného souboru, nejprve se pokouší načíst cestu k souboru ze zadaný klíč registru. To je zvlášť užitečné, pokud chcete vyhledat soubor v adresáři zadaném jako hodnota v registru.  

 `RegistryFileCheck` neobsahuje žádné elementy a má následující atributy.  

|Atribut|Popis|  
|---------------|-----------------|  
|`Property`|Požadováno. Název vlastnosti, která se uloží výsledek. Tato vlastnost může odkazovat z testu pod `InstallConditions` element, který je podřízeným prvkem z `Command` elementu. Další informace najdete v tématu [ \<příkazy > Element](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Požadováno. Název klíče registru. Jeho hodnota interpretována jako cesta k souboru, pokud `File` atribut je nastaven. Pokud tento klíč neexistuje, `Property` není nastaven.|  
|`Value`|Volitelné. Název hodnoty registru pro načtení. Ve výchozím nastavení je návratový text výchozí hodnotu. `Value` musí být řetězec.|  
|`FileName`|Volitelné. Název souboru. Je-li zadána, hodnota získaná z klíče registru se předpokládá se, že cestu k adresáři a tento název se připojí k němu. Pokud není zadán, předpokládá se, že hodnota vrácená z registru se být úplná cesta k souboru.|  
|`SearchDepth`|Volitelné. Hloubka, na který chcete vyhledat podsložky s názvem souboru. Hledání je hloubka první. Výchozí hodnota je 0, což omezuje vyhledávání na složku nejvyšší úrovně, určené hodnoty klíče registru.|  

## <a name="remarks"></a>Poznámky  
 Zatímco prvky pod `InstallChecks` definovat testy ke spuštění, se nemůžou provést. Chcete-li spustit testy, musíte vytvořit `Command` prvky pod `Commands` elementu.  

## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, `InstallChecks` element, protože se používá v souboru produktu pro [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  

```xml  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  

## <a name="installconditions"></a>InstallConditions  
 Když `InstallChecks` jsou vyhodnoceny, vytvářejí vlastnosti. Vlastnosti jsou pak používány `InstallConditions` k určení, zda by měla nainstalovat balíček, obejít nebo selhání. Následující tabulce jsou uvedeny `InstallConditions`:  

|||  
|-|-|  
|`FailIf`|Pokud existuje `FailIf` podmínka vyhodnotí jako true, balíček se nezdaří. Zbývající část podmínek nevyhodnotí se.|  
|`BypassIf`|Pokud existuje `BypassIf` podmínka vyhodnotí jako true, balíček bude možné obejít. Zbývající část podmínek nevyhodnotí se.|  

## <a name="predefined-properties"></a>Předdefinované vlastnosti  
 Následující tabulce jsou uvedeny `BypassIf` a `FailIf` prvky:  

|Vlastnost|Poznámky|Možné hodnoty|  
|--------------|-----------|---------------------|  
|`Version9X`|Číslo verze operačního systému Windows 9 X.|4.10 = Windows 98|  
|`VersionNT`|Číslo verze operačního systému Windows NT.|Major.Minor.ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|  
|`VersionNT64`|Číslo verze 64bitová verze systému Windows NT operační systém.|Stejné jako výše uvedené.|  
|`VersionMsi`|Číslo verze služby Windows Installer.|2.0 = Instalační služby systému Windows 2.0|  
|`AdminUser`|Určuje, zda má uživatel oprávnění správce na operačního systému Windows NT.|0 = žádná oprávnění správce<br /><br /> 1 = oprávnění správce|  

 Například pokud chcete zablokovat instalaci na počítač se systémem Windows 95, můžete použijte například následující kód:  

```xml  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  

## <a name="see-also"></a>Viz také:  
 [\<Příkazy > – element](../deployment/commands-element-bootstrapper.md)   
 [Referenční dokumentace schématu produktů a balíčků](../deployment/product-and-package-schema-reference.md)