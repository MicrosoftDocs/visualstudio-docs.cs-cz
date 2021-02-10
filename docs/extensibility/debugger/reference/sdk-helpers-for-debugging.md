---
title: Pomocníka sady SDK pro ladění | Microsoft Docs
description: Seznamte se s funkcemi a deklaracemi, které jsou globálními podpůrnými funkcemi pro implementaci modulů ladění, vyhodnocení výrazů a zprostředkovatelů symbolů v jazyce C++.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b98914d4e7fc2d63fd6cc9f79789c389e19b784
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935999"
---
# <a name="sdk-helpers-for-debugging"></a>Pomocníci sad SDK pro ladění
Tyto funkce a deklarace jsou globální pomocné funkce pro implementaci modulů ladění, vyhodnocení výrazů a poskytovatele symbolů v jazyce C++.

> [!NOTE]
> V tuto chvíli nejsou k dispozici žádné spravované verze těchto funkcí a deklarací.

## <a name="overview"></a>Přehled
 Aby moduly ladění, vyhodnocovací filtry výrazů a poskytovatelé symbolů používali aplikace Visual Studio, musí být zaregistrované. K tomu je potřeba nastavit podklíče a položky registru, jinak označované jako "nastavení metrik". Následující globální funkce jsou navrženy pro usnadnění procesu aktualizace těchto metrik. V části o umístěních registru najdete rozložení každého podklíče registru, který tyto funkce aktualizuje.

## <a name="general-metric-functions"></a>Obecné funkce metriky
 Jedná se o obecné funkce používané moduly ladění. Specializované funkce pro vyhodnocení výrazů a poskytovatele symbolů jsou popsány později.

### <a name="getmetric-method"></a>Getmetric – metoda
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
|pszMachine|pro Název možného vzdáleného počítače, jehož zápis bude napsán ( `NULL` znamená místní počítač).|
|pszType|pro Jeden z typů metriky.|
|guidSection|pro Identifikátor GUID konkrétního modulu, vyhodnocení, výjimka atd. Tím se určuje pododdíl v rámci typu metriky pro konkrétní element.|
|pszMetric|pro Metrika, která se má získat. To odpovídá konkrétnímu názvu hodnoty.|
|pdwValue|pro Umístění úložiště hodnoty z metriky. Existuje několik typů getmetriky, které mohou vracet DWORD (jako v tomto příkladu), BSTR, GUID nebo pole identifikátorů GUID.|
|pszAltRoot|pro Alternativní kořenový adresář registru, který se má použít. Nastavte na hodnotu `NULL` použít výchozí.|

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
|pszType|pro Jeden z typů metriky.|
|guidSection|pro Identifikátor GUID konkrétního modulu, vyhodnocení, výjimka atd. Tím se určuje pododdíl v rámci typu metriky pro konkrétní element.|
|pszMetric|pro Metrika, která se má získat. To odpovídá konkrétnímu názvu hodnoty.|
|dwValue|pro Umístění úložiště hodnoty v metrikě. Existuje několik typů SetMetric, které mohou ukládat DWORD (v tomto příkladu), BSTR, GUID nebo pole identifikátorů GUID.|
|fUserSpecific|pro TRUE, pokud je metrika specifická pro uživatele a v případě, že by měla být zapsána do podregistru uživatele místo podregistru místního počítače.|
|pszAltRoot|pro Alternativní kořenový adresář registru, který se má použít. Nastavte na hodnotu `NULL` použít výchozí.|

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
|pszType|pro Jeden z typů metriky.|
|guidSection|pro Identifikátor GUID konkrétního modulu, vyhodnocení, výjimka atd. Tím se určuje pododdíl v rámci typu metriky pro konkrétní element.|
|pszMetric|pro Metrika, která se má odebrat To odpovídá konkrétnímu názvu hodnoty.|
|pszAltRoot|pro Alternativní kořenový adresář registru, který se má použít. Nastavte na hodnotu `NULL` použít výchozí.|

### <a name="enummetricsections-method"></a>Metoda EnumMetricSections
 Vytvoří výčet různých sekcí metrik v registru.

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
|pszMachine|pro Název možného vzdáleného počítače, jehož zápis bude napsán ( `NULL` znamená místní počítač).|
|pszType|pro Jeden z typů metriky.|
|rgguidSections|[in, out] Předběžně přidělené pole identifikátorů GUID, které se mají vyplnit.|
|pdwSize|pro Maximální počet identifikátorů GUID, které mohou být uloženy v `rgguidSections` poli.|
|pszAltRoot|pro Alternativní kořenový adresář registru, který se má použít. Nastavte na hodnotu `NULL` použít výchozí.|

## <a name="expression-evaluator-functions"></a>Funkce vyhodnocovacího filtru výrazů

|Funkce|Description|
|--------------|-----------------|
|GetEEMetric|Načte hodnotu metriky z registru.|
|SetEEMetric|Nastaví zadanou hodnotu metriky v registru.|
|RemoveEEMetric|Odebere zadanou metriku z registru.|
|GetEEMetricFile|Získá název souboru ze zadané metriky a načte ho a vrátí obsah souboru jako řetězec.|

## <a name="exception-functions"></a>Funkce výjimky

|Funkce|Description|
|--------------|-----------------|
|GetExceptionMetric|Načte hodnotu metriky z registru.|
|SetExceptionMetric|Nastaví zadanou hodnotu metriky v registru.|
|RemoveExceptionMetric|Odebere zadanou metriku z registru.|
|RemoveAllExceptionMetrics|Odebere všechny metriky výjimek z registru.|

## <a name="symbol-provider-functions"></a>Funkce poskytovatele symbolů

|Funkce|Description|
|--------------|-----------------|
|GetSPMetric|Načte hodnotu metriky z registru.|
|SetSPMetric|Nastaví zadanou hodnotu metriky v registru.|
|RemoveSPMetric|Odebere zadanou metriku z registru.|

## <a name="enumeration-functions"></a>Funkce výčtu

|Funkce|Description|
|--------------|-----------------|
|EnumMetricSections|Vytvoří výčet všech metrik pro zadaný typ metriky.|
|EnumDebugEngine|Vytvoří výčet registrovaných ladicích modulů.|
|EnumEEs|Vytvoří výčet vyhodnocení registrovaných výrazů.|
|EnumExceptionMetrics|Vytvoří výčet všech metrik výjimek.|

## <a name="metric-definitions"></a>Definice metrik
 Tyto definice lze použít pro předdefinované názvy metrik. Názvy odpovídají různým klíčům registru a názvům hodnot a jsou definovány jako řetězce s velkým znakem: například `extern LPCWSTR metrictypeEngine` .

|Předdefinované typy metrik|Popis: základní klíč pro....|
|-----------------------------|---------------------------------------|
|metrictypeEngine|Všechny metriky ladicího stroje.|
|metrictypePortSupplier|Všechny metriky dodavatelů portů.|
|metrictypeException|Všechny metriky výjimek.|
|metricttypeEEExtension|Všechna rozšíření vyhodnocovacího filtru výrazů.|

|Vlastnosti ladicího stroje|Description|
|-----------------------------|-----------------|
|metricAddressBP|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu pro zarážky adres.|
|metricAlwaysLoadLocal|Nastavte na nenulovou hodnotu, chcete-li vždy načíst modul ladění místně.|
|metricLoadInDebuggeeSession|NEPOUŽÍVÁ SE|
|metricLoadedByDebuggee|Nastavte na nenulovou hodnotu, chcete-li označit, že ladicí stroj bude vždy načten pomocí nebo program, který je laděn.|
|metricAttach|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu pro přílohy k existujícím programům.|
|metricCallStackBP|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu zarážek zásobníku volání.|
|metricConditionalBP|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu pro nastavení podmíněných zarážek.|
|metricDataBP|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu nastavení zarážek při změnách v datech.|
|metricDisassembly|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu pro produkci zpětných seznamů.|
|metricDumpWriting|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu pro zápis do výpisu paměti (výpis paměti do výstupního zařízení).|
|metricENC|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu pro úpravy a pokračování. **Poznámka:**  Vlastní modul ladění by nikdy neměl nastavit, nebo by měl být vždy nastaven na hodnotu 0.|
|metricExceptions|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu pro výjimky.|
|metricFunctionBP|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu pojmenovaných zarážek (zarážky, které přeruší při volání určité funkce).|
|metricHitCountBP|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu pro nastavení "bod přístupů" (zarážky, které se aktivují až po určitém počtu opakování).|
|metricJITDebug|Nastavte na nenulovou hodnotu, pokud chcete označit podporu ladění za běhu (ladicí program se spustí, když dojde k výjimce ve spuštěném procesu).|
|metricMemory|NEPOUŽÍVÁ SE|
|metricPortSupplier|Tuto hodnotu nastavte na CLSID dodavatele portu, pokud je jeden implementovaný.|
|metricRegisters|NEPOUŽÍVÁ SE|
|metricSetNextStatement|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu pro nastavení dalšího příkazu (který přeskočí spuštění zprostředkujících příkazů).|
|metricSuspendThread|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu pro pozastavení provádění vlákna.|
|metricWarnIfNoSymbols|Nastavte na nenulovou hodnotu, pokud chcete, aby měl uživatel oznámení, pokud nejsou k dispozici žádné symboly.|
|metricProgramProvider|Nastavte na CLSID poskytovatele programu.|
|metricAlwaysLoadProgramProviderLocal|Nastavte na nenulovou hodnotu, chcete-li určit, že by měl být poskytovatel programu vždy načten místně.|
|metricEngineCanWatchProcess|Nastavte na nenulovou hodnotu, chcete-li označit, že ladicí stroj bude sledovat události procesu místo poskytovatele programu.|
|metricRemoteDebugging|Nastavte na nenulovou hodnotu, pokud chcete, aby označovala podporu pro vzdálené ladění.|
|metricEncUseNativeBuilder|Nastavte na nenulovou hodnotu, pokud chcete, aby měl správce úprav a pokračování k sestavení pro úpravu a pokračování použít encbuild.dll modulu ladění. **Poznámka:**  Vlastní modul ladění by nikdy neměl nastavit, nebo by měl být vždy nastaven na hodnotu 0.|
|metricLoadUnderWOW64|Nastavte na nenulovou hodnotu, chcete-li označit, že ladicí stroj by měl být načten v procesu laděného procesu v rámci WOW při ladění 64 procesu; v opačném případě se modul ladění načte do procesu sady Visual Studio (který běží pod WOW64).|
|metricLoadProgramProviderUnderWOW64|Nastavte na nenulovou hodnotu, pokud chcete, aby se zprostředkovatel programu načetl v procesu laděného procesu při ladění 64 procesu v WOW; v opačném případě bude načten do procesu sady Visual Studio.|
|metricStopOnExceptionCrossingManagedBoundary|Nastavte na nenulovou hodnotu, pokud chcete, aby se proces zastavil, pokud je vyvolána neošetřená výjimka přes hranice spravovaného a nespravovaného kódu.|
|metricAutoSelectPriority|Nastavte prioritu pro automatický výběr ladicího stroje (vyšší hodnoty se rovnají vyšší prioritě).|
|metricAutoSelectIncompatibleList|Klíč registru obsahující položky, které určují identifikátory GUID pro ladicí moduly, které se mají ignorovat při automatickém výběru. Tyto položky jsou číslo (0, 1, 2 atd.) s identifikátorem GUID vyjádřeným jako řetězec.|
|metricIncompatibleList|Klíč registru obsahující položky, které určují identifikátory GUID pro moduly ladění, které jsou nekompatibilní s tímto ladicím modulem.|
|metricDisableJITOptimization|Nastavte na nenulovou hodnotu, chcete-li určit, že při ladění by měly být zakázány optimalizace za běhu (pro spravovaný kód).|

|Vlastnosti vyhodnocovacího filtru výrazů|Description|
|-------------------------------------|-----------------|
|metricEngine|Tím se udržuje počet ladicích modulů, které podporují vyhodnocení určeného výrazu.|
|metricPreloadModules|Nastavte na nenulovou hodnotu, pokud chcete, aby se moduly při spuštění vyhodnocovacího filtru výrazů pro program vyčetly předem.|
|metricThisObjectName|Nastavte na název objektu this.|

|Vlastnosti rozšíření vyhodnocovacího filtru výrazů|Description|
| - |-----------------|
|metricExtensionDll|Název knihovny DLL, která podporuje toto rozšíření.|
|metricExtensionRegistersSupported|Seznam podporovaných registrů.|
|metricExtensionRegistersEntryPoint|Vstupní bod pro přístup k registrům|
|metricExtensionTypesSupported|Seznam podporovaných typů.|
|metricExtensionTypesEntryPoint|Vstupní bod pro přístup k typům|

|Vlastnosti dodavatele portu|Description|
|------------------------------|-----------------|
|metricPortPickerCLSID|Identifikátor CLSID ovládacího prvku pro výběr portu (dialogové okno, které uživatel může použít k výběru portů a přidání portů pro ladění).|
|metricDisallowUserEnteredPorts|Nenulová, pokud uživatelem zadané porty nelze přidat k dodavateli portů (tím je dialogové okno pro výběr portu v podstatě jen pro čtení).|
|metricPidBase|Základní ID procesu používané dodavatelem portu při přidělování ID procesu.|

|Předdefinované typy úložiště SP|Description|
|-------------------------------|-----------------|
|storetypeFile|Symboly jsou uloženy v samostatném souboru.|
|storetypeMetadata|Symboly jsou uloženy jako metadata v sestavení.|

|Různé vlastnosti|Description|
|------------------------------|-----------------|
|metricShowNonUserCode|Nastavte na nenulovou hodnotu, chcete-li zobrazit neuživatelský kód.|
|metricJustMyCodeStepping|Nastavte na nenulovou hodnotu, chcete-li indikovat, že krokování může probíhat pouze v uživatelském kódu.|
|metricCLSID|Identifikátor CLSID pro objekt určitého typu metriky.|
|metricName|Uživatelsky přívětivý název pro objekt konkrétního typu metriky.|
|metricLanguage|Název jazyka.|

## <a name="registry-locations"></a>Umístění registru
 Metriky se čtou a zapisují do registru, konkrétně v `VisualStudio` podklíči.

> [!NOTE]
> Ve většině případů budou metriky zapsány do HKEY_LOCAL_MACHINEho klíče. Někdy ale HKEY_CURRENT_USER bude cílový klíč. Dbgmetric. lib zpracovává oba klíče. Při získávání metriky se nejprve vyhledá HKEY_CURRENT_USER a pak HKEY_LOCAL_MACHINE. Když je nastavená metrika, parametr určuje, který klíč nejvyšší úrovně se má použít.

 *[klíč registru]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[kořen verze]*\

 *[metrika-kořen]*\

 *[typ metriky]*\

 *[metrika] = [hodnota metriky]*

 *[metrika] = [hodnota metriky]*

 *[metrika] = [hodnota metriky]*

|Zástupný symbol|Description|
|-----------------|-----------------|
|*[klíč registru]*|`HKEY_CURRENT_USER` nebo `HKEY_LOCAL_MACHINE`:|
|*[kořen verze]*|Verze sady Visual Studio (například, `7.0` `7.1` nebo `8.0` ). Tuto kořenovou složku ale můžete také změnit pomocí přepínače **/rootsuffix** na **devenv.exe**. V případě VSIP je tento modifikátor obvykle **exp**, takže kořen verze by byl například 8.0 EXP.|
|*[metrika-kořen]*|To je buď `AD7Metrics` nebo `AD7Metrics(Debug)` , v závislosti na tom, zda je použita ladicí verze dbgmetric. lib. **Poznámka:**  Bez ohledu na to, jestli se používá dbgmetric. lib, by se tato konvence vytváření názvů měla dodržovat, pokud máte rozdíly mezi verzemi ladění a vydání, které se musí v registru projevit.|
|*[typ metriky]*|Typ metriky, která se má zapsat: `Engine` , `ExpressionEvaluator` , `SymbolProvider` atd. Jsou všechny definovány jako v dbgmetric. h jako `metricTypeXXXX` , kde `XXXX` je specifický název typu.|
|*metriky*|Název položky, pro kterou má být přiřazena hodnota, aby bylo možné metriku nastavit. Skutečná organizace metrik závisí na typu metriky.|
|*[metrika hodnota]*|Hodnota přiřazená ke metrikě Typ, který má být hodnota (řetězec, číslo atd.), závisí na metrikě.|

> [!NOTE]
> Všechny identifikátory GUID jsou uloženy ve formátu `{GUID}` . Například, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Moduly ladění
 Níže je organizace metriky modulů ladění v registru. `Engine` je název typu metriky pro ladicí stroj a odpovídá *[typ metriky]* ve výše uvedeném podstromu registru.

 `Engine`\

 *[GUID modulu]*\

 `CLSID` = *[GUID třídy]*

 *[metrika] = [hodnota metriky]*

 *[metrika] = [hodnota metriky]*

 *[metrika] = [hodnota metriky]*

 `PortSupplier`\

 `0` = *[GUID dodavatele portu]*

 `1` = *[GUID dodavatele portu]*

|Zástupný symbol|Description|
|-----------------|-----------------|
|*[GUID modulu]*|Identifikátor GUID ladicího stroje.|
|*[GUID třídy]*|Identifikátor GUID třídy, která implementuje tento ladicí stroj.|
|*[GUID dodavatele portu]*|Identifikátor GUID dodavatele portu, pokud existuje. Řada ladicích modulů používá výchozího dodavatele portu, proto nespecifikuje svého dodavatele. V takovém případě podklíč `PortSupplier` nebude přítomen.|

### <a name="port-suppliers"></a>Dodavatelé portů
 Níže je organizace metriky dodavatelů portů v registru. `PortSupplier` je název typu metriky pro dodavatele portu a odpovídá *[typ metriky]*.

 `PortSupplier`\

 *[GUID dodavatele portu]*\

 `CLSID` = *[GUID třídy]*

 *[metrika] = [hodnota metriky]*

 *[metrika] = [hodnota metriky]*

|Zástupný symbol|Description|
|-----------------|-----------------|
|*[GUID dodavatele portu]*|Identifikátor GUID dodavatele portu|
|*[GUID třídy]*|Identifikátor GUID třídy, která implementuje tohoto dodavatele portu|

### <a name="symbol-providers"></a>Poskytovatelé symbolů
 Následuje organizace metrik dodavatelů symbolů v registru. `SymbolProvider` je název typu metriky pro poskytovatele symbolů a odpovídá *[typ metriky]*.

 `SymbolProvider`\

 *[identifikátor GUID poskytovatele symbolů]*\

 `file`\

 `CLSID` = *[GUID třídy]*

 *[metrika] = [hodnota metriky]*

 *[metrika] = [hodnota metriky]*

 `metadata`\

 `CLSID` = *[GUID třídy]*

 *[metrika] = [hodnota metriky]*

 *[metrika] = [hodnota metriky]*

|Zástupný symbol|Description|
|-----------------|-----------------|
|*[identifikátor GUID poskytovatele symbolů]*|Identifikátor GUID poskytovatele symbolů|
|*[GUID třídy]*|Identifikátor GUID třídy, která implementuje tohoto poskytovatele symbolů|

### <a name="expression-evaluators"></a>Vyhodnocovací filtry výrazů
 Následuje uspořádání metrik vyhodnocení výrazu v registru. `ExpressionEvaluator` je název typu metriky pro vyhodnocovací filtr výrazů a odpovídá *[typ metriky]*.

> [!NOTE]
> Typ metriky pro `ExpressionEvaluator` není definovaný v dbgmetric. h, protože se předpokládá, že všechny změny metrik pro vyhodnocovací filtry výrazů procházejí odpovídajícími funkcemi metriky vyhodnocení výrazu (rozložení `ExpressionEvaluator` podklíče je trochu složité, takže podrobnosti jsou skryté v dbgmetric. lib).

 `ExpressionEvaluator`\

 *[Language GUID]*\

 *[GUID dodavatele]*\

 `CLSID` = *[GUID třídy]*

 *[metrika] = [hodnota metriky]*

 *[metrika] = [hodnota metriky]*

 `Engine`\

 `0` = *[GUID modulu ladění]*

 `1` = *[GUID modulu ladění]*

|Zástupný symbol|Description|
|-----------------|-----------------|
|*[Language GUID]*|Identifikátor GUID jazyka|
|*[GUID dodavatele]*|Identifikátor GUID dodavatele|
|*[GUID třídy]*|Identifikátor GUID třídy, která implementuje tento vyhodnocovací filtr výrazů|
|*[GUID modulu ladění]*|Identifikátor GUID ladicího stroje, se kterým tento filtr výrazů pracuje|

### <a name="expression-evaluator-extensions"></a>Rozšíření vyhodnocovacího filtru výrazů
 Níže je organizace metriky rozšíření vyhodnocení výrazu v registru. `EEExtensions` je název typu metriky pro rozšíření vyhodnocovacího filtru výrazů a odpovídá *[typ metriky]*.

 `EEExtensions`\

 *[identifikátor GUID rozšíření]*\

 *[metrika] = [hodnota metriky]*

 *[metrika] = [hodnota metriky]*

|Zástupný symbol|Description|
|-----------------|-----------------|
|*[identifikátor GUID rozšíření]*|Identifikátor GUID rozšíření vyhodnocovacího filtru výrazů|

### <a name="exceptions"></a>Výjimky
 Níže je organizace metrik výjimek v registru. `Exception` je název typu metriky pro výjimky a odpovídá *[typ metriky]*.

 `Exception`\

 *[GUID modulu ladění]*\

 *[typy výjimek]*\

 *jímka*\

 *[metrika] = [hodnota metriky]*

 *[metrika] = [hodnota metriky]*

 *jímka*\

 *[metrika] = [hodnota metriky]*

 *[metrika] = [hodnota metriky]*

|Zástupný symbol|Description|
|-----------------|-----------------|
|*[GUID modulu ladění]*|Identifikátor GUID ladicího stroje, který podporuje výjimky.|
|*[typy výjimek]*|Obecný název podklíče identifikující třídu výjimek, které lze zpracovat. Typickými názvy jsou **výjimky jazyka C++**, výjimky **Win32**, **výjimky modulu CLR (Common Language Runtime)** a **Kontrola nativního Run-Time**. Tyto názvy slouží také k identifikaci konkrétní třídy výjimky pro uživatele.|
|*jímka*|Název pro výjimku: například **_com_error** nebo **Control-break**. Tyto názvy slouží také k identifikaci konkrétní výjimky pro uživatele.|

## <a name="requirements"></a>Požadavky
 Tyto soubory jsou umístěny v [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] instalačním adresáři sady SDK (ve výchozím nastavení je to *[jednotka]* \Program Files\Microsoft Visual Studio 2010 SDK \\ ).

 Záhlaví: includes\dbgmetric.h

 Knihovna: libs\ad2de.lib, libs\dbgmetric.lib

## <a name="see-also"></a>Viz také
- [Referenční informace k rozhraním API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
