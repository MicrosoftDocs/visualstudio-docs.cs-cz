---
title: VSPerfReport | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 282bb801625429d639e625a0a5edb02a8fb4da25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777982"
---
# <a name="vsperfreport"></a>VSPerfReport
Nástroj příkazového řádku VSPerfReport se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] používá k vytváření sestav pomocí nástrojů profilování profilování datových souborů. Výchozí formát sestavy je . *csv.*

 VSPerfReport používá následující syntaxi:

```cmd
VSPerfReport [/U] vspfilename [/options]
```

 Všimněte `filename` si, že musí být platný . *vsp* nebo . *vsps.*

 Nástroj příkazového řádku VSPerfReport se také používá k porovnání . *vsp* nebo . *vsps* soubory. Chcete-li generovat sestavu rozdílu ("diff"), použijte následující syntaxi:

```cmd
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]
```

 `vspfilename1 and vspfilename2`musí být platný . *vsp* nebo . *vsps* soubory.

## <a name="symbol-files"></a>Soubory symbolů
 Chcete-li zobrazit informace o symbolu, jako jsou názvy funkcí a čísla řádků, vsPerfReport vyžaduje přístup k symbolu (. PDB) profilovaných součástí a souborů symbolů systému Windows. Další informace naleznete v [tématu Postup: Určení umístění souborů symbolů z příkazového řádku](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).

## <a name="general-report-options"></a>Možnosti obecné sestavy
 Následující tabulka popisuje obecné možnosti formátování sestavy a možnosti, které vybírají data, která mají být hlášena.

|Možnosti|Popis|
|-------------|-----------------|
|**U**|Výstup sestavy a přesměrovaný výstup konzoly jsou zapsány jako Unicode. Musí být zadána první možnost.|
|**Shrnutí:**[*typy*]|Vytvoří jeden nebo více typů sestav.<br /><br /> -   `All`- jsou generovány všechny typy sestav.<br />-   `CallerCallee`- vztahy mezi funkcemi nadřazený/podřízený.<br />-   `Function`- volané funkce.<br />-   `CallTree`- hierarchie volaných funkcí.<br />-   `Counter`- všechny značky spolu s hodnotami čítače výkonu systému Windows.<br />-   `Ip`- profilované instrukce.<br />-   `Life`- životnost přidělených objektů (k dispozici při shromažďování alokačních dat.)<br />-   `Line`data profilu řádku zdrojového kódu.<br />-   `Header`- sestava obsahuje informace záhlaví souboru.<br />-   `Mark`všechny značky.<br />-   `Module`- profilované moduly.<br />-   `Process`- profilované procesy.<br />-   `Thread`- profilované závity.<br />-   `Type`- přidělené typy.<br />-   `Contention`- tvrzení o zdrojích.<br />-   `RuleWarnings`- problémy s pravidly výkonu<br />-   `ETW`- všechny události trasování událostí pro Windows (ETW) události shromážděné v profilování spustit. Datový soubor .etl musí být v původním umístění nebo v adresáři obsahujícím soubor VSP nebo VSPS.|
|**Xml**|Výstupní sestava ve formátu XML.|
|**Volání**|Vytvoří seznam položek a výstupů funkce, událostí ETW a značek.|
|**ClearPackedSymboly**|Odstraní dříve vložené symboly z datového souboru profileru. Spusťte tento příkaz před spuštěním PackSymbols podruhé.|
|**Cesta symbolu:**`path`|Určuje jednu nebo více vyhledávacích cest nebo serverů symbolů, které obsahují symboly datového souboru profileru.|
|**LaděníSymPath**|Zobrazí seznam umístění, která jsou vyhledávána, a zda jsou nalezeny. Tato možnost je užitečná k vyřešení problémů s rozlišením symbolů.|
|**Symboly balení**|Uloží symboly do souboru dat profilování (.vsp) tak, aby tento symbol (.* pdb*) soubory nejsou vyžadovány pro analýzu.|
|**Výstup:** *cesta*&#124;*název souboru*|Určuje alternativní umístění generovaných souborů sestav. Ve výchozím nastavení jsou sestavy vytvářeny v aktuálním adresáři.|
|**Souhrnný soubor**|Analyzujte a ukládejte analyzované informace do souhrnného souboru .vsps.|
|**Tiskové značky**|Zobrazí názvy a časová razítka pro všechny značky v zadaném souboru sestavy.|
|**?**|Zobrazí informace o využití.|
|**NoLogo**|Skryje informace o verzi, když je sestava spuštěna.|
|**Adresář uživatelských pravidel**|Určuje adresář obsahující uživatelem definovaná pravidla výkonu [dosud nebyla implementována].|

## <a name="filter-options"></a>Možnosti filtru
 Následující tabulka popisuje možnosti filtrování dostupných dat.

|Možnosti|Popis|
|-------------|-----------------|
|**JustMyCode****:**[`caller`: [`callee`][, ]]|Zobrazit pouze volání funkce uživatelské aplikace; skrýt systémová volání.<br /><br /> - Žádné parametry - skrýt všechny systémové funkce.<br />-   `caller`- zobrazit jednu úroveň systémových funkcí, které volají funkce aplikace.<br />-   `callee`- zobrazit jednu úroveň systémových funkcí, které jsou volány uživatelskými aplikačními funkcemi.|
|**StartTime:**[*hodnota*]|Zobrazit pouze data shromážděná za hodnotou (v milisekundách.)|
|**Koncový čas:**[*hodnota*]|Zobrazit pouze data shromážděná před hodnotou (v milisekundách.)|
|**Soubor filtru:**`VSPFFile`|Určuje umístění souboru filtru, který byl vygenerován z okna Sestavy výkonu sady Visual Studio.|
|**MsFilter:**[*čas zahájení,doba trvání*]|Zobrazit pouze `starttime` data od `duration` až do délky (v milisekundách.)|
|**Proces:**[*pid*]|Zobrazit pouze data ze zadaného procesu.|
|**Závit:**[*threadid*]|Zobrazit pouze data ze zadaného vlákna.|
|**Závit:**[*threadid,processid*]|Zobrazit pouze data ze zadaného vlákna přidruženého k zadanému procesu.|

## <a name="difference-report-options"></a>Možnosti sestavy rozdílů
 Následující tabulka popisuje možnosti porovnání souborů sestav.

|Možnosti|Popis|
|-------------|-----------------|
|**Diff**  `vspfile1 vspfile2`|Porovnejte dva soubory sestavy (.* vsp* nebo . *vsps*) Soubory. Možnosti souhrnu budou ignorovány pomocí možnosti diff.|
|**Rozdíl:**[*hodnota*]|Pod touto prahovou hodnotou nebude rozdíl mezi dvěma hodnotami brán v úvahu. Nová data s hodnotami pod touto prahovou hodnotou se také nezobrazí.|
|**DiffTable:**[*název tabulky*]|Tato konkrétní tabulka slouží k porovnání souborů. Výchozí je tabulka funkcí.|
|**DiffColumn:**[*název sloupce*]|Použijte tento konkrétní sloupec porovnat hodnoty. Výchozí je sloupec procentuální chudinky výhradních vzorků.|
|**QueryDiffTables**|Seznam platných tabulek a sloupců pro dva soubory sestavy k dispozici.|

## <a name="see-also"></a>Viz také
- [Zobrazení sestavy výkonu](../profiling/performance-report-views.md)
