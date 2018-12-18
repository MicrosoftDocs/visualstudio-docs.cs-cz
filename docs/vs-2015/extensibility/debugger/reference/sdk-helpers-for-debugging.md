---
title: Pomocníci sad SDK pro ladění | Dokumentace Microsoftu
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
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 904ac14433bf6b7b839a4fe634175a7f583e27ab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772180"
---
# <a name="sdk-helpers-for-debugging"></a>Pomocníci sad SDK pro ladění
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tyto funkce a deklarace jsou globální pomocných funkcí pro provádění ladicími stroji vyhodnocovače výrazů a poskytovatelé symbol v jazyce C++.  
  
> [!NOTE]
>  V tuto chvíli neexistují žádné spravované verze těchto funkcí a deklarace.  
  
## <a name="overview"></a>Přehled  
 Aby ladicí stroj, vyhodnocovače výrazů a symbol zprostředkovatele pro Visual Studio musí být zaregistrovaný. To se provádí nastavením podklíče a položky, jinak známé jako "nastavení metriky." Následující globální funkce jsou navrženy k usnadnění procesu aktualizace tyto metriky. V části na umístění registru a zjistěte, rozložení podklíč registru, který se aktualizuje pomocí těchto funkcí.  
  
## <a name="general-metric-functions"></a>Obecné funkce metriky  
 Toto jsou obecné funkce používané v ladicí stroj. Specializované funkce pro vyhodnocovače výrazů a symbol poskytovatelé jsou podrobně popsané.  
  
### <a name="getmetric-method"></a>GetMetric – metoda  
 Načte hodnotu metriky z registru.  
  
```cpp#  
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
|pszMachine|[in] Název může být vzdáleného počítače, jejichž registr, se zapíšou (`NULL` znamená, že místní počítač).|  
|pszType|[in] Jeden z typů metriky.|  
|guidSection|[in] Identifikátor GUID konkrétní modul, Chyba při vyhodnocování, výjimky, atd. Toto nastavení určuje podčásti typ metriky pro konkrétní elementu.|  
|pszMetric|[in] Metrika získána. To odpovídá názvu konkrétní hodnotu.|  
|pdwValue|[in] Umístění úložiště maximum možnosti metriku. Existuje několik typů GetMetric, která vrací DWORD (jako v následujícím příkladu), BSTR, identifikátor GUID nebo pole identifikátorů GUID.|  
|pszAltRoot|[in] Použití s kořenovým alternativního registru. Nastavte na `NULL` chcete použít výchozí.|  
  
### <a name="setmetric-method"></a>SetMetric – metoda  
 Nastaví hodnotu zadané metriky v registru.  
  
```cpp#  
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
|pszType|[in] Jeden z typů metriky.|  
|guidSection|[in] Identifikátor GUID konkrétní modul, Chyba při vyhodnocování, výjimky, atd. Toto nastavení určuje podčásti typ metriky pro konkrétní elementu.|  
|pszMetric|[in] Metrika získána. To odpovídá názvu konkrétní hodnotu.|  
|dwValue|[in] Umístění úložiště hodnotu v metrice. Existuje několik typů SetMetric, která může ukládat DWORD (v tomto příkladu), BSTR, identifikátor GUID nebo pole identifikátorů GUID.|  
|fUserSpecific|[in] Hodnota TRUE, pokud metrika je specifické pro uživatele a pokud by měl být zadaný pro hive uživatele místo hive místního počítače.|  
|pszAltRoot|[in] Použití s kořenovým alternativního registru. Nastavte na `NULL` chcete použít výchozí.|  
  
### <a name="removemetric-method"></a>RemoveMetric – metoda  
 Odebere zadané metriky z registru.  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametr|Popis|  
|---------------|-----------------|  
|pszType|[in] Jeden z typů metriky.|  
|guidSection|[in] Identifikátor GUID konkrétní modul, Chyba při vyhodnocování, výjimky, atd. Toto nastavení určuje podčásti typ metriky pro konkrétní elementu.|  
|pszMetric|[in] Metrika má být odebrán. To odpovídá názvu konkrétní hodnotu.|  
|pszAltRoot|[in] Použití s kořenovým alternativního registru. Nastavte na `NULL` chcete použít výchozí.|  
  
### <a name="enummetricsections-method"></a>EnumMetricSections – metoda  
 Provede výčet různých metrik oddílů v registru.  
  
```cpp#  
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
|pszMachine|[in] Název může být vzdáleného počítače, jejichž registr, se zapíšou (`NULL` znamená, že místní počítač).|  
|pszType|[in] Jeden z typů metriky.|  
|rgguidSections|[out v] Předběžně přidělené pole identifikátorů GUID pro vyplnění.|  
|pdwSize|[in] Maximální počet identifikátorů GUID, které mohou být uloženy v `rgguidSections` pole.|  
|pszAltRoot|[in] Použití s kořenovým alternativního registru. Nastavte na `NULL` chcete použít výchozí.|  
  
## <a name="expression-evaluator-functions"></a>Chyba při vyhodnocování funkce výraz  
  
|Funkce|Popis|  
|--------------|-----------------|  
|GetEEMetric|Načte hodnotu metriky z registru.|  
|SetEEMetric|Nastaví hodnotu zadané metriky v registru.|  
|RemoveEEMetric|Odebere zadané metriky z registru.|  
|GetEEMetricFile|Získá název souboru ze zadané metriky a načte, vrátí obsah souboru jako řetězec.|  
  
## <a name="exception-functions"></a>Výjimka funkce  
  
|Funkce|Popis|  
|--------------|-----------------|  
|GetExceptionMetric|Načte hodnotu metriky z registru.|  
|SetExceptionMetric|Nastaví hodnotu zadané metriky v registru.|  
|RemoveExceptionMetric|Odebere zadané metriky z registru.|  
|RemoveAllExceptionMetrics|Odebere všechny metriky výjimky z registru.|  
  
## <a name="symbol-provider-functions"></a>Funkce poskytovatele symbolů  
  
|Funkce|Popis|  
|--------------|-----------------|  
|GetSPMetric|Načte hodnotu metriky z registru.|  
|SetSPMetric|Nastaví hodnotu zadané metriky v registru.|  
|RemoveSPMetric|Odebere zadané metriky z registru.|  
  
## <a name="enumeration-functions"></a>Funkce výčtu  
  
|Funkce|Popis|  
|--------------|-----------------|  
|EnumMetricSections|Vytvoří výčet všech metrik pro zadaný typ metriky.|  
|EnumDebugEngine|Vytvoří výčet registrované ladicí stroj.|  
|EnumEEs|Vytvoří výčet vyhodnocovače výrazů registrovaný.|  
|EnumExceptionMetrics|Vytvoří výčet všech výjimek metrik.|  
  
## <a name="metric-definitions"></a>Definice metrik  
 Tyto definice můžete použít pro názvy předdefinovaných metrik. Názvy odpovídají různé klíče registru a názvy hodnot a jsou definované jako řetězce širokého znaku: například `extern LPCWSTR metrictypeEngine`.  
  
|Předdefinované typy metriky|Popis: Základní klíč pro...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Všechny metriky modul ladění.|  
|metrictypePortSupplier|Všechny metriky dodavatele portu.|  
|metrictypeException|Všechny výjimky metriky.|  
|metricttypeEEExtension|Všechna rozšíření Chyba při vyhodnocování výrazu.|  
  
|Vlastnosti modulu ladění|Popis|  
|-----------------------------|-----------------|  
|metricAddressBP|Nastavte na nenulovou hodnotu označující podporu pro zarážky adres.|  
|metricAlwaysLoadLocal|Nastavte na nenulovou hodnotu, aby bylo možné vždy načíst ladicí stroj místně.|  
|metricLoadInDebuggeeSession|NEPOUŽITO|  
|metricLoadedByDebuggee|Nastavte na nenulovou hodnotu označující, že ladicí stroj vždy se načtou s nebo program, který se právě ladí.|  
|metricAttach|Nastavte na nenulovou hodnotu označující podporu pro připojení k existující programy.|  
|metricCallStackBP|Nastavte na nenulovou hodnotu označující podporu pro zarážky zásobníku volání.|  
|metricConditionalBP|Nastavte na nenulovou hodnotu označující podporu pro nastavení podmíněné zarážky.|  
|metricDataBP|Nastavte na nenulovou hodnotu označující podporu pro nastavení zarážky na změny v datech.|  
|metricDisassembly|Nastavte na nenulovou hodnotu označující podporu pro produkční prostředí výpisu zpětný překlad.|  
|metricDumpWriting|Nastavte na nenulovou hodnotu označující podporu pro zápis (výpis paměti na výstupní zařízení) s výpisem paměti.|  
|metricENC|Nastavte na nenulovou hodnotu označující podpora pro funkce upravit a pokračovat. **Poznámka:** vlastního ladicího stroje nikdy nesmíte nastavit to nebo by měla vždy nastavte na hodnotu 0.|  
|metricExceptions|Nastavte na nenulovou hodnotu označující podporu pro výjimky.|  
|metricFunctionBP|Nastavte na nenulovou hodnotu označující podpora pro pojmenované zarážky (zarážky, které přerušit, když se některé název funkce je volána).|  
|metricHitCountBP|Nastavte na nenulovou hodnotu označující podporu pro nastavení zarážky "Zasáhněte bodu" (zarážky, které se aktivují až poté, co se dosažení určitého počtu pokusů o).|  
|metricJITDebug|Nastavte na nenulovou hodnotu označující podporu ladění just-in-time (ladicí program se spustí, když dojde k výjimce v spuštěný proces).|  
|metricMemory|NEPOUŽITO|  
|metricPortSupplier|Tuto možnost nastavte na identifikátor CLSID dodavatele portu jeden je implementováno.|  
|metricRegisters|NEPOUŽITO|  
|metricSetNextStatement|Nastavte na nenulovou hodnotu označující podporu pro nastavení dalšího příkazu (který přeskočí provádění zprostředkující příkazů).|  
|metricSuspendThread|Nastavte na nenulovou hodnotu označující podporu pro pozastavení provádění vlákna.|  
|metricWarnIfNoSymbols|Nastavte na nenulovou hodnotu označující, že uživatel by měl být vás upozorní, když neexistují žádné symboly.|  
|metricProgramProvider|Nastavte na identifikátor CLSID program zprostředkovatele.|  
|metricAlwaysLoadProgramProviderLocal|Nastavte tuto vlastnost na nenulovou hodnotu označující, že poskytovatel program by měla být vždy načteno místně.|  
|metricEngineCanWatchProcess|Nastavte na nenulovou hodnotu označující, že bude sledovat ladicí stroj pro zpracování událostí místo poskytovatele programu.|  
|metricRemoteDebugging|Nastavte na nenulovou hodnotu označující podpory vzdáleného ladění.|  
|metricEncUseNativeBuilder|Nastavte tuto vlastnost na nenulovou hodnotu označující, že upravit a pokračovat správce používejte encbuild.dll ladicí stroj pro sestavení pro úpravy a pokračování. **Poznámka:** vlastního ladicího stroje nikdy nesmíte nastavit to nebo by měla vždy nastavte na hodnotu 0.|  
|metricLoadUnderWOW64|Nastavte na nenulovou hodnotu označující, že ladicí stroj by měly být načteny v laděném procesu pod WOW, při ladění procesu 64-bit; ladicí stroj v opačném případě bude načten v procesu sady Visual Studio (která je spuštěna v modulu WOW64).|  
|metricLoadProgramProviderUnderWOW64|Nastavte na nenulovou hodnotu označující, že poskytovatel program by měl být načteny v laděném procesu, při ladění 64bitového procesu pod WOW; v opačném případě bude být načten v procesu sady Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Nastavte na nenulovou hodnotu označující, že pokud dojde k neošetřené výjimce přes hranice spravovaného a nespravovaného kódu by se měla zastavit proces.|  
|metricAutoSelectPriority|Nastavte prioritu pro automatický výběr ladicího stroje (vyšší hodnoty rovná vyšší prioritou).|  
|metricAutoSelectIncompatibleList|Klíč registru obsahující položky, které určují identifikátory GUID pro ladicí stroj neberou v automatický výběr. Tyto položky jsou čísla (0, 1, 2 a tak dále) s identifikátorem GUID vyjádřené jako řetězec.|  
|metricIncompatibleList|Klíč registru, který obsahuje položky, které určují identifikátory GUID pro ladicí moduly, které jsou kompatibilní s Tento ladicí stroj.|  
|metricDisableJITOptimization|Nastavte na nenulovou hodnotu označující, že během ladění by mělo být zakázáno optimalizace just-in-time (pro spravovaný kód).|  
  
|Chyba při vyhodnocování výrazu – vlastnosti|Popis|  
|-------------------------------------|-----------------|  
|metricEngine|To obsahuje počet ladicími stroji, které podporují Chyba při vyhodnocování zadaným výrazem.|  
|metricPreloadModules|Nastavte na nenulovou hodnotu označující, že by měl být moduly zavedené při spuštění vyhodnocovače výrazů proti programu.|  
|metricThisObjectName|Nastavte na "Tento" název objektu.|  
  
|Chyba při vyhodnocování výrazu – vlastnosti rozšíření|Popis|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|Název knihovny DLL, která podporuje toto rozšíření.|  
|metricExtensionRegistersSupported|Seznam registrů nepodporuje.|  
|metricExtensionRegistersEntryPoint|Vstupní bod pro přístup k registrů.|  
|metricExtensionTypesSupported|Seznam typů, které jsou podporovány.|  
|metricExtensionTypesEntryPoint|Vstupní bod pro přístup k typy.|  
  
|Vlastnosti dodavatele portu|Popis|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|Identifikátor CLSID výběr portu (a porty vyberte a přidejte porty pro ladění můžete použít dialogové okno uživatele).|  
|metricDisallowUserEnteredPorts|Nenulové, pokud uživatel zadal porty nelze přidat do dodavatele portu (díky tomu dialogové okno Výběr portu v podstatě jen pro čtení).|  
|metricPidBase|ID základní procesu používané dodavatele portu při přidělování ID procesů.|  
  
|Předdefinované typy Store SP|Popis|  
|-------------------------------|-----------------|  
|storetypeFile|Symboly se ukládají v samostatném souboru.|  
|storetypeMetadata|Symboly se ukládají jako metadata do sestavení.|  
  
|Různé vlastnosti|Popis|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Nastavte na nenulovou hodnotu, chcete-li zobrazit kód nonuser.|  
|metricJustMyCodeStepping|Nastavte na nenulovou hodnotu označující, že krokování může dojít pouze v uživatelském kódu.|  
|metricCLSID|Identifikátor CLSID pro objekt typu konkrétní metriky.|  
|metricName|Popisný název pro objekt typu konkrétní metriky.|  
|metricLanguage|Název jazyka.|  
  
## <a name="registry-locations"></a>Umístění registru  
 Metriky se čtou a zapisují do registru, konkrétně v `VisualStudio` podklíči.  
  
> [!NOTE]
>  Ve většině případů, metriky, se zapíšou do klíče HKEY_LOCAL_MACHINE. Někdy ale HKEY_CURRENT_USER být cílový klíč. Dbgmetric.lib zpracovává oba klíče. Při získávání metriku, vyhledá HKEY_CURRENT_USER první pak HKEY_LOCAL_MACHINE. Při nastavení metriky parametr určuje, které klíč nejvyšší úrovně se má použít.  
  
 *[klíč registru]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[kořenové verze]*\  
  
 *[metriky kořenové]*\  
  
 *[typu metrika.]*\  
  
 *[metrika] = [hodnota metriky]*  
  
 *[metrika] = [hodnota metriky]*  
  
 *[metrika] = [hodnota metriky]*  
  
|Zástupný text|Popis|  
|-----------------|-----------------|  
|*[klíč registru]*|`HKEY_CURRENT_USER` nebo `HKEY_LOCAL_MACHINE`.|  
|*[kořenové verze]*|Verze sady Visual Studio (například `7.0`, `7.1`, nebo `8.0`). Ale tohoto kořenového adresáře lze také změnit pomocí **/rootsuffix** přepnout na **devenv.exe**. Pro VSIP, je obvykle tento modifikátor **Exp**, takže kořenové verze bude, například 8.0Exp.|  
|*[metriky kořenové]*|Je to `AD7Metrics` nebo `AD7Metrics(Debug)`, v závislosti na tom, jestli se používá ladicí verzi dbgmetric.lib. **Poznámka:** zda dbgmetric.lib se používá, tyto zásady vytváření názvů by měl být nedodržuje Pokud máte rozdíly mezi debug a release verze, které se musí projevit v registru.|  
|*[typu metrika.]*|Typ metriky k zapsání: `Engine`, `ExpressionEvaluator`, `SymbolProvider`atd. Všechny jsou definované jako dbgmetric.h jako `metricTypeXXXX`, kde `XXXX` je název specifického typu.|  
|*[metrika]*|Název položky pro přiřazení hodnoty k nastavení metriky. Skutečné organizace metriky závisí na typu metrika.|  
|*[hodnota metriky]*|Hodnota přiřazená k metriku. Typ by měl mít (string, number, atd.) závisí na metriku.|  
  
> [!NOTE]
>  Všechny identifikátory GUID se ukládají ve formátu `{GUID}`. Například `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Ladicí stroje  
 Následuje uspořádání metrik ladicí moduly v registru. `Engine` je název typu metrika. ladicí stroj a odpovídá *[typ metriky]* ve výše uvedené podstromu registru.  
  
 `Engine`\  
  
 *[identifikátor guid modulu]*\  
  
 `CLSID` = *[identifikátor guid třídy]*  
  
 *[metrika] = [hodnota metriky]*  
  
 *[metrika] = [hodnota metriky]*  
  
 *[metrika] = [hodnota metriky]*  
  
 `PortSupplier`\  
  
 `0` = *[guid dodavatele portu]*  
  
 `1` = *[guid dodavatele portu]*  
  
|Zástupný text|Popis|  
|-----------------|-----------------|  
|*[identifikátor guid modulu]*|Identifikátor GUID ladicího stroje.|  
|*[identifikátor guid třídy]*|Identifikátor GUID třídy, která implementuje tento ladicí stroj.|  
|*[guid dodavatele portu]*|Identifikátor GUID dodavatele portu, pokud existuje. Mnoho ladicími stroji použít výchozí dodavatele portu a proto není zadán vlastní dodavatele. V takovém případě podklíče `PortSupplier` budou chybět.|  
  
### <a name="port-suppliers"></a>Dodavatelé portů  
 Následuje uspořádání metrik dodavatele portu v registru. `PortSupplier` je název typu Metrika pro dodavatele portu a odpovídá *[typ metriky]*.  
  
 `PortSupplier`\  
  
 *[guid dodavatele portu]*\  
  
 `CLSID` = *[identifikátor guid třídy]*  
  
 *[metrika] = [hodnota metriky]*  
  
 *[metrika] = [hodnota metriky]*  
  
|Zástupný text|Popis|  
|-----------------|-----------------|  
|*[guid dodavatele portu]*|Identifikátor GUID dodavatele portu|  
|*[identifikátor guid třídy]*|Identifikátor GUID třídy, která implementuje tohoto dodavatele portu|  
  
### <a name="symbol-providers"></a>Poskytovatelé symbol  
 Následuje uspořádání metrik dodavatele symbolu v registru. `SymbolProvider` je název typu metrika. poskytovatel symbolů a odpovídá *[typ metriky]*.  
  
 `SymbolProvider`\  
  
 *[symbol identifikátor guid]*\  
  
 `file`\  
  
 `CLSID` = *[identifikátor guid třídy]*  
  
 *[metrika] = [hodnota metriky]*  
  
 *[metrika] = [hodnota metriky]*  
  
 `metadata`\  
  
 `CLSID` = *[identifikátor guid třídy]*  
  
 *[metrika] = [hodnota metriky]*  
  
 *[metrika] = [hodnota metriky]*  
  
|Zástupný text|Popis|  
|-----------------|-----------------|  
|*[symbol identifikátor guid]*|GUID poskytovatele symbolů|  
|*[identifikátor guid třídy]*|Identifikátor GUID třídy, která implementuje tento poskytovatel symbolů|  
  
### <a name="expression-evaluators"></a>Vyhodnocovače výrazů  
 Následuje uspořádání metrik Chyba při vyhodnocování výrazu v registru. `ExpressionEvaluator` je název typu Metrika pro vyhodnocovací filtr výrazů a odpovídá *[typ metriky]*.  
  
> [!NOTE]
>  Typ metriky pro `ExpressionEvaluator` není definovaný v dbgmetric.h, protože se předpokládá, že všechny metriky změny pro vyhodnocení výrazu půjdou přes metriky funkce Chyba při vyhodnocování výrazu odpovídající (rozložení `ExpressionEvaluator` podklíč je trochu složité, takže podrobné informace jsou skryty uvnitř dbgmetric.lib).  
  
 `ExpressionEvaluator`\  
  
 *[identifikátor guid jazyka]*\  
  
 *[identifikátor guid dodavatele]*\  
  
 `CLSID` = *[identifikátor guid třídy]*  
  
 *[metrika] = [hodnota metriky]*  
  
 *[metrika] = [hodnota metriky]*  
  
 `Engine`\  
  
 `0` = *[ladicí stroj guid]*  
  
 `1` = *[ladicí stroj guid]*  
  
|Zástupný text|Popis|  
|-----------------|-----------------|  
|*[identifikátor guid jazyka]*|Identifikátor GUID jazyka|  
|*[identifikátor guid dodavatele]*|Identifikátor GUID dodavatele|  
|*[identifikátor guid třídy]*|Identifikátor GUID třídy, které implementuje tato chyba při vyhodnocování výrazu|  
|*[ladicí stroj guid]*|Identifikátor GUID ladicího stroje, který tato chyba při vyhodnocování výrazu spolupracuje s|  
  
### <a name="expression-evaluator-extensions"></a>Rozšíření Chyba při vyhodnocování výrazu  
 Následuje uspořádání metrik rozšíření Chyba při vyhodnocování výrazu v registru. `EEExtensions` je název metriky typu výrazu chyba při vyhodnocování rozšíření a odpovídá *[typ metriky]*.  
  
 `EEExtensions`\  
  
 *[identifikátor guid rozšíření]*\  
  
 *[metrika] = [hodnota metriky]*  
  
 *[metrika] = [hodnota metriky]*  
  
|Zástupný text|Popis|  
|-----------------|-----------------|  
|*[identifikátor guid rozšíření]*|Identifikátor GUID rozšíření Chyba při vyhodnocování výrazu|  
  
### <a name="exceptions"></a>Výjimky  
 Následuje uspořádání metrik výjimky v registru. `Exception` je název typu Metrika pro výjimky a odpovídá *[typ metriky]*.  
  
 `Exception`\  
  
 *[ladicí stroj guid]*\  
  
 *[typy výjimek]*\  
  
 *[výjimka]*\  
  
 *[metrika] = [hodnota metriky]*  
  
 *[metrika] = [hodnota metriky]*  
  
 *[výjimka]*\  
  
 *[metrika] = [hodnota metriky]*  
  
 *[metrika] = [hodnota metriky]*  
  
|Zástupný text|Popis|  
|-----------------|-----------------|  
|*[ladicí stroj guid]*|Identifikátor GUID ladicího stroje, který podporuje výjimky.|  
|*[typy výjimek]*|Obecný název podklíče identifikující třídu výjimky, které mohou být zpracovány. Typické názvy jsou **výjimky jazyka C++**, **výjimky Win32**, **výjimky modulu Common Language Runtime**, a **nativních kontrol za běhu**. Tyto názvy se také používají k identifikaci konkrétní třídu výjimky na uživatele.|  
|*[výjimka]*|Název pro výjimku: například **_com_error** nebo **Ctrl + Break**. Tyto názvy se také používají k identifikaci konkrétní výjimky na uživatele.|  
  
## <a name="requirements"></a>Požadavky  
 Tyto soubory jsou umístěny v [!INCLUDE[vs_dev10_ext](../../../includes/vs-dev10-ext-md.md)] adresáře instalace sady SDK (ve výchozím nastavení, *[jednotka]* \Program Files\Microsoft Visual Studio 2010 SDK\\).  
  
 Záhlaví: includes\dbgmetric.h  
  
 Knihovna: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace ke knihovně API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)

