---
title: Pomocné spoje sady SDK pro ladění | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9edb7c508fdea6736a71c0f70c0d2ff305d4a399
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713653"
---
# <a name="sdk-helpers-for-debugging"></a>Pomocníci sad SDK pro ladění
Tyto funkce a deklarace jsou globální pomocné funkce pro implementaci ladicích modulů, vyhodnocení výrazů a zprostředkovatelů symbolů v jazyce C++.

> [!NOTE]
> V současné době neexistují žádné spravované verze těchto funkcí a deklarací.

## <a name="overview"></a>Přehled
 Aby byly ladicí moduly, vyhodnocení výrazů a zprostředkovatelé symbolů používáni visual studio, musí být registrovány. To se provádí nastavením podklíčů registru a položek, jinak označovaných jako "nastavení metriky." Následující globální funkce jsou navrženy tak, aby usnadnily proces aktualizace těchto metrik. V části Umístění registru naleznete rozložení každého podklíče registru, který je těmito funkcemi aktualizován.

## <a name="general-metric-functions"></a>Obecné metrické funkce
 Jedná se o obecné funkce používané ladicími moduly. Specializované funkce pro vyhodnocení výrazů a zprostředkovatele symbolů jsou podrobně popsány později.

### <a name="getmetric-method"></a>Metoda GetMetric
 Načte hodnotu metriky z registru.

```cpp
HRESULT GetMetric(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   DWORD * pdwValue,
   LPCWSTR pszAltRoot
);
```

|Parametr|Popis|
|---------------|-----------------|
|pszMachine|[v] Název případně vzdáleného počítače, jehož`NULL` registr bude zapsán (znamená místní počítač).|
|pszTyp|[v] Jeden z typů metrik.|
|guidSekce|[v] IDENTIFIKÁTOR GUID konkrétního motoru, hodnotitele, výjimky atd. To určuje pododdíl pod typem metriky pro určitý prvek.|
|pszMetrická|[v] Metrika, která má být získána. To odpovídá názvu konkrétní hodnoty.|
|pdwValue|[v] Umístění úložiště hodnoty z metriky. Existuje několik variant GetMetric, které můžete vrátit DWORD (jako v tomto příkladu), BSTR, GUID nebo pole IDENTIFIKÁTORŮ GUID.|
|pszAltRoot|[v] Alternativní kořen registru, který chcete použít. Nastavte `NULL` na použití výchozího nastavení.|

### <a name="setmetric-method"></a>Metoda SetMetric
 Nastaví zadanou hodnotu metriky v registru.

```cpp
HRESULT SetMetric(
         LPCWSTR pszType,
         REFGUID guidSection,
         LPCWSTR pszMetric,
   const DWORD   dwValue,
         bool    fUserSpecific,
         LPCWSTR pszAltRoot
);
```

|Parametr|Popis|
|---------------|-----------------|
|pszTyp|[v] Jeden z typů metrik.|
|guidSekce|[v] IDENTIFIKÁTOR GUID konkrétního motoru, hodnotitele, výjimky atd. To určuje pododdíl pod typem metriky pro určitý prvek.|
|pszMetrická|[v] Metrika, která má být získána. To odpovídá názvu konkrétní hodnoty.|
|dwValue|[v] Umístění úložiště hodnoty v metriky. Existuje několik variant SetMetric, které můžete uložit DWORD (v tomto příkladu), BSTR, GUID nebo pole GUID.|
|fUserSpecific|[v] TRUE, pokud je metrika specifická pro uživatele a zda má být zapsána do podregistru uživatele namísto podregistru místního počítače.|
|pszAltRoot|[v] Alternativní kořen registru, který chcete použít. Nastavte `NULL` na použití výchozího nastavení.|

### <a name="removemetric-method"></a>Metoda RemoveMetric
 Odebere zadanou metriku z registru.

```cpp
HRESULT RemoveMetric(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   LPCWSTR pszAltRoot
);
```

|Parametr|Popis|
|---------------|-----------------|
|pszTyp|[v] Jeden z typů metrik.|
|guidSekce|[v] IDENTIFIKÁTOR GUID konkrétního motoru, hodnotitele, výjimky atd. To určuje pododdíl pod typem metriky pro určitý prvek.|
|pszMetrická|[v] Metrika, která má být odebrána. To odpovídá názvu konkrétní hodnoty.|
|pszAltRoot|[v] Alternativní kořen registru, který chcete použít. Nastavte `NULL` na použití výchozího nastavení.|

### <a name="enummetricsections-method"></a>Metoda EnumMetricSections
 Vyjmenovává různé metrické oddíly v registru.

```cpp
HRESULT EnumMetricSections(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   GUID *  rgguidSections,
   DWORD * pdwSize,
   LPCWSTR pszAltRoot
);
```

|Parametr|Popis|
|---------------|-----------------|
|pszMachine|[v] Název případně vzdáleného počítače, jehož`NULL` registr bude zapsán (znamená místní počítač).|
|pszTyp|[v] Jeden z typů metrik.|
|rgguidSekce|[dovnitř, ven] Přededělitné pole identifikátorů GUID, které mají být vyplněny.|
|pdwVelikost|[v] Maximální počet identifikátorů GUID, které `rgguidSections` mohou být uloženy v poli.|
|pszAltRoot|[v] Alternativní kořen registru, který chcete použít. Nastavte `NULL` na použití výchozího nastavení.|

## <a name="expression-evaluator-functions"></a>Funkce vyhodnocení výrazu

|Funkce|Popis|
|--------------|-----------------|
|Geteemetrický|Načte hodnotu metriky z registru.|
|Seteemetrický|Nastaví zadanou hodnotu metriky v registru.|
|Odstraniteemetrický|Odebere zadanou metriku z registru.|
|GetEEMetricFile|Získá název souboru z zadané metriky a načte ji, vrácení obsahu souboru jako řetězec.|

## <a name="exception-functions"></a>Funkce výjimek

|Funkce|Popis|
|--------------|-----------------|
|GetExceptionMetric|Načte hodnotu metriky z registru.|
|Nastavitmetriku výjimky|Nastaví zadanou hodnotu metriky v registru.|
|Odebratmetriku výjimky|Odebere zadanou metriku z registru.|
|Odebratvšechny metriky exception|Odebere všechny metriky výjimek z registru.|

## <a name="symbol-provider-functions"></a>Funkce zprostředkovatele symbolů

|Funkce|Popis|
|--------------|-----------------|
|GetSPMetric|Načte hodnotu metriky z registru.|
|SetSPMetric|Nastaví zadanou hodnotu metriky v registru.|
|Odebrat metriku SPMetric|Odebere zadanou metriku z registru.|

## <a name="enumeration-functions"></a>Funkce výčtu

|Funkce|Popis|
|--------------|-----------------|
|EnumMetricSections|Zápoce vyjmenovává všechny metriky pro zadaný typ metriky.|
|EnumDebugEngine|Vyjmenovává registrované ladicí moduly.|
|EnumEEs|Vyjmenovává hodnotitele registrovaných výrazů.|
|EnumExceptionMetrics|Výčet všech metrik výjimek.|

## <a name="metric-definitions"></a>Definice metrik
 Tyto definice lze použít pro předdefinované názvy metrik. Názvy odpovídají různým klíčům registru a názvům hodnot a jsou `extern LPCWSTR metrictypeEngine`definovány jako řetězce širokých znaků: například .

|Předdefinované typy metrik|Popis: Základní klíč pro....|
|-----------------------------|---------------------------------------|
|metrictypeEngine|Všechny metriky ladicí modul.|
|metrictypePortDodavatel|Všechny metriky dodavatele portů.|
|exceptiona metrictypeException|Všechny metriky výjimek.|
|metricttypeEEExtension|Všechna rozšíření vyhodnocení výrazu.|

|Vlastnosti ladicímodul|Popis|
|-----------------------------|-----------------|
|metricAddressBP|Nastavte nenulovou hodnotu, chcete-li označit podporu zarážek adres.|
|metricAlwaysLoadLocal|Nastavte nenulovou hodnotu, aby bylo možné vždy načíst ladicí modul místně.|
|metricLoadInDebuggeeSession|NEPOUŽÍVÁ SE|
|metrikaLoadedByDebuggee|Nastavte nenulovou hodnotu, která označuje, že ladicí modul bude vždy načten nebo programem, který je laděn.|
|metricAttach|Nastavte nenulovou hodnotu, která označuje podporu pro přílohu k existujícím programům.|
|metricCallStackBP|Nastavte na nenulovou hodnotu, která označuje podporu zarážek zásobníku volání.|
|metricConditionalBP|Nastavte nenulovou hodnotu, která označuje podporu pro nastavení podmíněných zarážek.|
|metricDataBP|Nastavte nenulovou hodnotu, která označuje podporu pro nastavení zarážek při změnách dat.|
|metricdisassembly|Nastavte nenulovou hodnotu, chcete-li označit podporu pro výrobu výpisu demontáže.|
|metricDumpWriting|Nastavte nenulovou hodnotu, která označuje podporu pro ukládání výpisu (ukládání paměti do výstupního zařízení).|
|metricENC|Nastavte nenulovou hodnotu, která označuje podporu pro úpravy a pokračování. **Poznámka:**  Vlastní ladicí modul by nikdy nastavit nebo by měl vždy nastavit na 0.|
|metricExceptions|Nastavte nenulovou hodnotu, chcete-li označit podporu výjimek.|
|metricFunctionBP|Nastavte nenulovou hodnotu, která označuje podporu pojmenovaných zarážek (zarážky, které se zalomí při volání určitého názvu funkce).|
|metricHitCountBP|Nastavte nenulovou hodnotu, která označuje podporu pro nastavení zarážek bodu zásahu (zarážky, které jsou spuštěny až po dosažení určitého počtu opakování).|
|metricJITDebug|Nastavte nenulovou hodnotu, která označuje podporu pro ladění za běhu (ladicí program je spuštěn, když dojde k výjimce v běžícím procesu).|
|metricMemory|NEPOUŽÍVÁ SE|
|metricPortDodavatel|Nastavte to clsid dodavatele portu, pokud je implementována.|
|metricRegisters|NEPOUŽÍVÁ SE|
|metricSetNextStatement|Nastavte nenulovou hodnotu, která označuje podporu pro nastavení dalšího příkazu (který přeskočí provádění zprostředkujících příkazů).|
|metricSuspendThread|Nastavte nenulovou hodnotu, která označuje podporu pro pozastavení provádění podprocesu.|
|metrikaWarnIfNoSymbols|Nastavte nenulovou hodnotu označující, že uživatel by měl být upozorněn, pokud neexistují žádné symboly.|
|metricProgramProvider|Nastavte to na CLSID poskytovatele programu.|
|metricAlwaysLoadProgramProviderLocal|Nastavte tuto hodnotu na nenulovou hodnotu označující, že zprostředkovatel programu by měl být vždy načten místně.|
|metricEngineCanWatchProcess|Nastavte tuto hodnotu na nenulovou hodnotu označující, že ladicí modul bude sledovat události procesu namísto zprostředkovatele programu.|
|metricRemoteDebugging|Nastavte tuto hodnotu na nenulovou hodnotu, chcete-li označit podporu pro vzdálené ladění.|
|metricEncUseNativeBuilder|Nastavte tuto hodnotu na nenulovou hodnotu označující, že Správce úprav a pokračování by měl použít soubor encbuild.dll ladicího stroje k sestavení pro úpravy a pokračování. **Poznámka:**  Vlastní ladicí modul by nikdy nastavit nebo by měl vždy nastavit na 0.|
|metrikaLoadUnderWOW64|Nastavte tuto hodnotu na nenulovou hodnotu označující, že ladicí modul by měl být načten v procesu ladění v rámci WOW při ladění 64bitového procesu; v opačném případě bude ladicí modul načten v procesu sady Visual Studio (který je spuštěn pod WOW64).|
|metricLoadProgramProviderUnderWOW64|Nastavte tuto hodnotu na nenulovou hodnotu označující, že zprostředkovatel programu by měl být načten v procesu ladění při ladění 64bitového procesu v rámci WOW; v opačném případě bude načten v procesu sady Visual Studio.|
|metricStopOnExceptionCrossingManagedBoundary|Nastavte tuto hodnotu na nenulovou hodnotu označující, že proces by měl zastavit, pokud je vyvolána neošetřená výjimka přes hranice spravovaného/nespravovaného kódu.|
|metricAutoSelectPriorit|Nastavte tuto prioritu pro automatický výběr ladicího modulu (vyšší hodnoty se rovnají vyšší prioritě).|
|metricAutoSelectIncompatibleList|Klíč registru obsahující položky, které určují identifikátory GUID pro ladění motorů, které mají být ignorovány v automatickém výběru. Tyto položky jsou číslo (0, 1, 2 a tak dále) s identifikátorem GUID vyjádřeným jako řetězec.|
|metricIncompatibleList|Klíč registru obsahující položky, které určují identifikátory GUID pro ladicí moduly, které nejsou kompatibilní s tímto ladicím strojem.|
|metricdisableJITOptimization|Nastavte tuto hodnotu na nenulovou hodnotu označující, že optimalizace just-in-time (pro spravovaný kód) by měly být během ladění zakázány.|

|Vlastnosti vyhodnocení výrazu|Popis|
|-------------------------------------|-----------------|
|metricEngine|To obsahuje počet ladicích modulů, které podporují zadaný vyhodnocení výrazu.|
|metrické předpětíModuly|Nastavte tuto hodnotu na nenulovou hodnotu, která označuje, že moduly by měly být předinstalovány při spuštění vyhodnocení výrazu proti programu.|
|metricThisObjectName|Nastavte tento název objektu "this".|

|Vlastnosti rozšíření vyhodnocení výrazu|Popis|
| - |-----------------|
|metricExtensionDll|Název dll, který podporuje toto rozšíření.|
|metricExtensionRegistersPodporováno|Seznam podporovaných registrů.|
|metricExtensionRegistersEntryPoint|Vstupní bod pro přístup k registrům.|
|metricExtensionTypesSupported|Seznam podporovaných typů.|
|metricExtensionTypesEntryPoint|Vstupní bod pro přístup k typům.|

|Vlastnosti dodavatele portů|Popis|
|------------------------------|-----------------|
|metrikaPortPickerCLSID|CLSID výběru portů (dialogové okno, které může uživatel použít k výběru portů a přidání portů pro ladění).|
|metricDisallowUserEnteredPorts|Nenulová, pokud uživatelem zadané porty nelze přidat k dodavateli portu (to dělá dialogové okno pro výběr portu v podstatě jen pro čtení).|
|metricPidBase|ID základního procesu používané dodavatelem portu při přidělování ID procesu.|

|Předdefinované typy úložiště SP|Popis|
|-------------------------------|-----------------|
|soubor storetypeFile|Symboly jsou uloženy v samostatném souboru.|
|storetypeMetadata|Symboly jsou uloženy jako metadata v sestavení.|

|Různé vlastnosti|Popis|
|------------------------------|-----------------|
|metricShowNonUserCode|Nastavte tuto hodnotu na nenulovou, chcete-li zobrazit neuživatelský kód.|
|metricJustMyCodeStepping|Nastavte tuto hodnotu na nenulovou hodnotu označující, že krokování může dojít pouze v uživatelském kódu.|
|metricCLSID|CLSID pro objekt určitého typu metriky.|
|metricName|Uživatelsky přívětivý název objektu určitého typu metriky.|
|metricLanguage|Název jazyka.|

## <a name="registry-locations"></a>Umístění registru
 Metriky jsou čteny a zapsány do `VisualStudio` registru, konkrétně v podklíči.

> [!NOTE]
> Ve většině času budou metriky zapsány do HKEY_LOCAL_MACHINE klíče. Někdy však HKEY_CURRENT_USER bude cílový klíč. Dbgmetric.lib zpracovává oba klíče. Když metriku získává, nejprve vyhledá HKEY_CURRENT_USER a pak HKEY_LOCAL_MACHINE. Při nastavování metriky parametr určuje, který klíč nejvyšší úrovně se má použít.

 *[klíč registru]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[kořenová verze]*\

 *[kořenová metrika]*\

 *[typ metriky]*\

 *[metric] = [metrická hodnota]*

 *[metric] = [metrická hodnota]*

 *[metric] = [metrická hodnota]*

|Zástupný symbol|Popis|
|-----------------|-----------------|
|*[klíč registru]*|`HKEY_CURRENT_USER` nebo `HKEY_LOCAL_MACHINE`.|
|*[kořenová verze]*|Verze sady Visual Studio (například `7.0`, `7.1`, nebo `8.0`). Tento kořen však lze také upravit pomocí **přepínače /rootsuffix** na **devenv.exe**. Pro VSIP je tento modifikátor obvykle **Exp**, takže kořen verze by byl například 8.0Exp.|
|*[kořenová metrika]*|Toto `AD7Metrics` je `AD7Metrics(Debug)`buď nebo , v závislosti na tom, zda je použita ladicí verze dbgmetric.lib. **Poznámka:**  Zda je použit dbgmetric.lib, tato konvence pojmenování by měla být dodržena, pokud máte rozdíly mezi ladicí a vydané verze, které musí být zohledněny v registru.|
|*[typ metriky]*|Typ metriky, která `Engine`má `ExpressionEvaluator` `SymbolProvider`být zapsána: , , , atd. Všechny jsou definovány jako v souboru dbgmetric.h as `metricTypeXXXX`, kde `XXXX` je konkrétní název typu.|
|*[metrické]*|Název položky, které má být přiřazena hodnota pro nastavení metriky. Skutečná organizace metrik závisí na typu metriky.|
|*[metrická hodnota]*|Hodnota přiřazená metrice. Typ, který by měla hodnota mít (řetězec, číslo atd.), závisí na metrice.|

> [!NOTE]
> Všechny identifikátory GUID jsou `{GUID}`uloženy ve formátu . Například, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Ladicí moduly
 Následuje organizace metrikladové motory v registru. `Engine`je název typu metriky pro ladicí modul a odpovídá *[typ metriky]* ve výše uvedeném podstromu registru.

 `Engine`\

 *[motor guid]*\

 `CLSID` = *[třída guid]*

 *[metric] = [metrická hodnota]*

 *[metric] = [metrická hodnota]*

 *[metric] = [metrická hodnota]*

 `PortSupplier`\

 `0` = *[průvodce dodavatelem portu]*

 `1` = *[průvodce dodavatelem portu]*

|Zástupný symbol|Popis|
|-----------------|-----------------|
|*[motor guid]*|Identifikátor GUID ladicího modulu.|
|*[třída guid]*|Guid třídy, která implementuje tento ladicí modul.|
|*[průvodce dodavatelem portu]*|Guid dodavatele přístavu, pokud existuje. Mnoho ladicích modulů používá výchozího dodavatele portu, a proto nespecifikuje vlastního dodavatele. V takovém případě bude `PortSupplier` podklíč chybět.|

### <a name="port-suppliers"></a>Dodavatelé portů
 Následuje organizace metriky dodavatele portu v registru. `PortSupplier`je název typu metriky pro dodavatele portu a odpovídá *[typ metriky]*.

 `PortSupplier`\

 *[průvodce dodavatelem portu]*\

 `CLSID` = *[třída guid]*

 *[metric] = [metrická hodnota]*

 *[metric] = [metrická hodnota]*

|Zástupný symbol|Popis|
|-----------------|-----------------|
|*[průvodce dodavatelem portu]*|Identifikátor GUID dodavatele přístavu|
|*[třída guid]*|Identifikátor GUID třídy, která implementuje tohoto dodavatele portů|

### <a name="symbol-providers"></a>Zprostředkovatelé symbolů
 Následuje organizace metriky dodavatele symbolv registru. `SymbolProvider`je název typu metriky pro poskytovatele symbolů a odpovídá *[metrickému typu]*.

 `SymbolProvider`\

 *[identifikátor guid poskytovatele symbolů]*\

 `file`\

 `CLSID` = *[třída guid]*

 *[metric] = [metrická hodnota]*

 *[metric] = [metrická hodnota]*

 `metadata`\

 `CLSID` = *[třída guid]*

 *[metric] = [metrická hodnota]*

 *[metric] = [metrická hodnota]*

|Zástupný symbol|Popis|
|-----------------|-----------------|
|*[identifikátor guid poskytovatele symbolů]*|Identifikátor GUID poskytovatele symbolů|
|*[třída guid]*|Identifikátor GUID třídy, která implementuje tohoto zprostředkovatele symbolů|

### <a name="expression-evaluators"></a>Vyhodnocení výrazů
 Následuje organizace metriky vyhodnocení výrazu v registru. `ExpressionEvaluator`je název typu metriky pro vyhodnocení výrazu a odpovídá *[typ metriky]*.

> [!NOTE]
> Typ metriky `ExpressionEvaluator` pro není definován v dbgmetric.h, protože se předpokládá, že všechny změny metriky pro vyhodnocení výrazů `ExpressionEvaluator` budou procházet příslušné funkce metriky vyhodnocení výrazu (rozložení podklíče je poněkud složité, takže podrobnosti jsou skryté uvnitř dbgmetric.lib).

 `ExpressionEvaluator`\

 *[jazyk oválný]*\

 *[průvodce dodavatelem]*\

 `CLSID` = *[třída guid]*

 *[metric] = [metrická hodnota]*

 *[metric] = [metrická hodnota]*

 `Engine`\

 `0` = *[ladění motoru guid]*

 `1` = *[ladění motoru guid]*

|Zástupný symbol|Popis|
|-----------------|-----------------|
|*[jazyk oválný]*|Identifikátor GUID jazyka|
|*[průvodce dodavatelem]*|Identifikátor GUID dodavatele|
|*[třída guid]*|Identifikátor GUID třídy, která implementuje tento vyhodnocení výrazu|
|*[ladění motoru guid]*|Identifikátor GUID ladicího modulu, se kterým tento vyhodnocení výrazu pracuje|

### <a name="expression-evaluator-extensions"></a>Rozšíření vyhodnocení výrazu
 Následuje organizace metrikrozšíření vyhodnocení výrazu v registru. `EEExtensions`je název typu metriky pro rozšíření vyhodnocení výrazu a odpovídá *[typ metriky]*.

 `EEExtensions`\

 *[rozšíření guid]*\

 *[metric] = [metrická hodnota]*

 *[metric] = [metrická hodnota]*

|Zástupný symbol|Popis|
|-----------------|-----------------|
|*[rozšíření guid]*|Identifikátor GUID rozšíření vyhodnocení výrazu|

### <a name="exceptions"></a>Výjimky
 Následuje organizace výjimek metriky v registru. `Exception`je název typu metriky pro výjimky a odpovídá *[typ metriky]*.

 `Exception`\

 *[ladění motoru guid]*\

 *[typy výjimek]*\

 *[výjimka]*\

 *[metric] = [metrická hodnota]*

 *[metric] = [metrická hodnota]*

 *[výjimka]*\

 *[metric] = [metrická hodnota]*

 *[metric] = [metrická hodnota]*

|Zástupný symbol|Popis|
|-----------------|-----------------|
|*[ladění motoru guid]*|Identifikátor GUID ladicího modulu, který podporuje výjimky.|
|*[typy výjimek]*|Obecný název podklíče identifikující třídu výjimek, které lze zpracovat. Typickými **názvy jsou výjimky jazyka C++**, **výjimky win32**, **výjimky běžného jazykového běhu**a **nativní kontroly za běhu**. Tyto názvy se také používají k identifikaci určité třídy výjimky pro uživatele.|
|*[výjimka]*|Název výjimky: například **_com_error** nebo **Control-Break**. Tyto názvy se také používají k identifikaci konkrétní výjimku pro uživatele.|

## <a name="requirements"></a>Požadavky
 Tyto soubory jsou [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] umístěny v instalačním adresáři sady SDK (ve výchozím nastavení *[jednotka]* \Program Files\Microsoft Visual Studio 2010 SDK\\).

 Záhlaví: includes\dbgmetric.h

 Knihovna: libs\ad2de.lib, libs\dbgmetric.lib

## <a name="see-also"></a>Viz také
- [Referenční informace k rozhraním API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
