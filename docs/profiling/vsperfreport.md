---
title: VSPerfReport | Microsoft Docs
description: Přečtěte si, že nástroj příkazového řádku VSPerfReport slouží k vytváření sestav pomocí souborů dat profilování sady Visual Studio Nástroje pro profilaci.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 507ea5a90aa17ba252a95714f488f5ea22dff4f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911498"
---
# <a name="vsperfreport"></a>VSPerfReport
Nástroj příkazového řádku VSPerfReport slouží k vytváření sestav pomocí  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci datových souborů profilování. Výchozí formát sestavy je. soubor *CSV* .

 VSPerfReport používá následující syntaxi:

```cmd
VSPerfReport [/U] vspfilename [/options]
```

 Všimněte si, že `filename` musí být platná.*VSP* nebo. soubor *vsps*

 Nástroj příkazového řádku VSPerfReport se používá také k porovnání. *VSP* nebo. soubory *vsps* . Pokud chcete vygenerovat sestavu rozdílů (rozdílové), použijte tuto syntaxi:

```cmd
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]
```

 `vspfilename1 and vspfilename2` musí být platný. *VSP* nebo. soubory *vsps* .

## <a name="symbol-files"></a>Soubory symbolů
 Chcete-li zobrazit informace o symbolech, jako jsou názvy funkcí a čísla řádků, VSPerfReport vyžaduje přístup k symbolu (. PDB) soubory profilované součásti a soubory symbolů systému Windows. Další informace naleznete v tématu [How to: určení umístění souborů symbolů z příkazového řádku](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).

## <a name="general-report-options"></a>Obecné možnosti sestavy
 Následující tabulka popisuje obecné možnosti formátování sestavy a možnosti, které vyberou data k nahlášení.

|Možnosti|Description|
|-------------|-----------------|
|**H**|Výstup sestavy a přesměrované výstupy konzoly jsou zapsané jako Unicode. Musí se jednat o první zadanou možnost.|
|**Shrnutí:**[*typy*]|Vytvoří jeden nebo více typů sestav.<br /><br /> -   `All` -jsou generovány všechny typy sestav.<br />-   `CallerCallee` – Vztahy nadřazenosti a podřízenosti mezi funkcemi.<br />-   `Function` -funkce, které jsou volány.<br />-   `CallTree` -hierarchie volání funkcí.<br />-   `Counter` – všechny značky společně s hodnotami čítače výkonu systému Windows.<br />-   `Ip` – pokyny profilování.<br />-   `Life` – doba života přidělených objektů (k dispozici, když se shromažďují data přidělení)<br />-   `Line` data profilu čáry zdrojového kódu.<br />-   `Header` -Sestava obsahuje informace o záhlaví souboru.<br />-   `Mark` všechny značky.<br />-   `Module` -moduly profilované.<br />-   `Process` -procesy profilace.<br />-   `Thread` – vlákna profilace.<br />-   `Type` -přidělené typy.<br />-   `Contention` – spory prostředků.<br />-   `RuleWarnings` – problémy s pravidlem výkonu<br />-   `ETW` – všechny události trasování událostí pro Windows (ETW) shromážděné při spuštění profilace. Datový soubor. ETL musí být v původním umístění nebo v adresáři, který obsahuje soubor. vsp nebo. vsps.|
|**XML**|Výstupní sestava ve formátu XML.|
|**CallTrace**|Vytvoří seznam vstupů a výstupů funkcí, událostí ETW a značek.|
|**ClearPackedSymbols**|Odebere dříve vložené symboly z datového souboru profileru. Spusťte tento příkaz před dalším spuštěním PackSymbols.|
|**SymbolPath:**`path`|Určuje jednu nebo více cest hledání nebo serverů symbolů, které obsahují symboly pro datový soubor profileru.|
|**DebugSymPath**|Vypíše umístění, ve kterých jsou vyhledávány symboly a zda jsou nalezeny. Tato možnost je užitečná pro řešení problémů s překladem symbolů.|
|**PackSymbols**|Uloží symboly do souboru dat profilování (. vsp), takže symbol (.*soubory PDB* nejsou pro analýzu požadovány.|
|**Výstup:** *cesta*&#124;*název_souboru*|Určuje alternativní umístění pro vygenerované soubory sestav. Ve výchozím nastavení se sestavy vytvářejí v aktuálním adresáři.|
|**SummaryFile**|Analyzujte a uložte analyzované informace v souboru souhrnu. vsps.|
|**PrintMarks**|Zobrazí názvy a časová razítka pro všechny značky v zadaném souboru sestavy.|
|**?**|Zobrazí informace o použití.|
|**NoLogo**|Po spuštění sestavy skryje informace o verzi.|
|**UserRulesDirectory**|Určuje adresář obsahující uživatelsky definovaná pravidla výkonu [dosud neimplementováno].|

## <a name="filter-options"></a>Možnosti filtru
 Následující tabulka popisuje možnosti, jak filtrovat data, která jsou k dispozici.

|Možnosti|Description|
|-------------|-----------------|
|**JustMyCode**[**:**[ `caller` ] [] `callee` ]|Zobrazit pouze volání funkcí aplikace uživatele; Skryjte systémová volání.<br /><br /> -Žádné parametry – skryje všechny systémové funkce.<br />-   `caller` -Zobrazí jednu úroveň systémových funkcí, které volají funkce aplikace.<br />-   `callee` -Zobrazit jednu úroveň systémových funkcí, které jsou volány funkcemi uživatelské aplikace.|
|**Čas_spuštění:**[*hodnota*]|Zobrazit pouze data shromážděná po hodnotě (v milisekundách)|
|**Čas_ukončení:**[*hodnota*]|Zobrazit pouze data shromážděná před hodnotou (v milisekundách)|
|**FilterFile:**`VSPFFile`|Určuje umístění souboru filtru, který byl vygenerován z okna Sestava výkonu sady Visual Studio.|
|**MsFilter:**[*čas_spuštění, Duration*]|Zobrazit pouze data z `starttime` až do délky `duration` (v milisekundách)|
|**Proces:**[*PID*]|Zobrazit pouze data ze zadaného procesu.|
|**Vlákno:**[*IDvlákna*]|Zobrazit pouze data ze zadaného vlákna.|
|**Vlákno:**[*IDvlákna, ProcessID*]|Zobrazit pouze data ze zadaného vlákna přidruženého k zadanému procesu.|

## <a name="difference-report-options"></a>Rozdíly – možnosti sestavy
 Následující tabulka popisuje možnosti pro porovnávání souborů sestav.

|Možnosti|Description|
|-------------|-----------------|
|**Diff**  `vspfile1 vspfile2`|Porovnejte dva soubory sestav (.*VSP* nebo. *vsps*) spis. Možnosti souhrnu budou ignorovány pomocí možnosti diff.|
|**Rozdíl:**[*hodnota*]|Pod touto prahovou hodnotou se bude ignorovat rozdíl mezi dvěma hodnotami. Také se nezobrazí nová data s hodnotami pod touto prahovou hodnotou.|
|**Diff:**[*TableName*]|Tato konkrétní tabulka slouží k porovnání souborů. Výchozím nastavením je tabulka Functions (funkce).|
|**DiffColumn:**[*ColumnName*]|Použijte tento konkrétní sloupec hodnoty porovnání. Ve výchozím nastavení je ve sloupci výhradní vzorky procento.|
|**QueryDiffTables**|Vypíše platné tabulky a sloupce pro dva zadané soubory sestavy.|

## <a name="see-also"></a>Viz také
- [Zobrazení sestav výkonu](../profiling/performance-report-views.md)
