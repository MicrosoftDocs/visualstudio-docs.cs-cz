---
title: VSPerfReport | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12b76923a0687125643f95228397d3051cb08c5b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806825"
---
# <a name="vsperfreport"></a>VSPerfReport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vsperfreport – nástroj příkazového řádku se používá k vytvoření sestavy, které používají [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů pro profilaci sady souborů dat profilování. Výchozí formát sestavy je soubor .csv.  
  
 VSPerfReport používá následující syntaxi:  
  
```  
VSPerfReport [/U] vspfilename [/options]  
```  
  
 Všimněte si, že `filename` musí být platný soubor .vsp nebo .vsps.  
  
 Vsperfreport – nástroj příkazového řádku se také používá pro porovnání souborů .vsp nebo .vsps. Aby se vygenerovala sestava rozdíl ("diff"), použijte následující syntaxi:  
  
```  
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]  
```  
  
 `vspfilename1 and vspfilename2` musí být platný soubor .vsp nebo .vsps soubory.  
  
## <a name="symbol-files"></a>Soubory symbolů  
 Chcete-li zobrazit informace o symbolech, jako jsou názvy funkcí a čísla řádků, VSPerfReport vyžaduje přístup k symbolu (. Soubory symbolů soubory PDB) PROFILOVANÉHO komponent a Windows. Další informace najdete v tématu [postupy: určení umístění souboru se symboly z příkazového řádku](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
  
## <a name="general-report-options"></a>Obecná sestava možnosti  
 Následující tabulka popisuje obecnou zprávu formátování možnosti a možnosti, které vyberte data, která mají být uvedeny.  
  
|Možnosti|Popis|  
|-------------|-----------------|  
|**U**|Výstup sestavy a přesměrovaný výstup konzoly je zapsán jako Unicode. První možnost je povinná.|  
|**Shrnutí:**[*typy*]|Vytvoří jeden nebo více typů sestav.<br /><br /> -   `All` -jsou generovány všechny typy sestav.<br />-   `CallerCallee` -nadřazené a podřízené vztahy mezi funkcemi.<br />-   `Function` -volané funkce.<br />-   `CallTree` -hierarchii volané funkce.<br />-   `Counter` -všechny značky společně s Windows performance hodnoty čítačů.<br />-   `Ip` -pokyny profilována.<br />-   `Life` -dobu životnosti přidělených objektů (k dispozici, když jsou shromážděná data o přidělování.)<br />-   `Line` data profilu řádku zdrojového kódu.<br />-   `Header` -Sestava obsahuje informace o souboru záhlaví.<br />-   `Mark` všechny značky.<br />-   `Module` -Profilované moduly.<br />-   `Process` -Profilovat procesy.<br />-   `Thread` -vlákna profilována.<br />-   `Type` -přidělené typy.<br />-   `Contention` -Sporty prostředků.<br />-   `RuleWarnings` -problémy pravidla výkonu<br />-   `ETW` -všechny události trasování událostí pro Windows (ETW) shromážděné při spuštění profilace. Datový soubor ETL musí být v původním umístění nebo do adresáře, který obsahuje soubor .vsp nebo .vsps.|  
|**Xml**|Výstup sestavy ve formátu XML.|  
|**CallTrace**|Vytvoří seznam vstupu funkce a ukončí, událostí trasování událostí pro Windows a značky.|  
|**ClearPackedSymbols**|Odebere dříve vložený symboly z datového souboru profilování. Tento příkaz spustit před spuštěním PackSymbols a druhý čas.|  
|**SymbolPath:** `path`|Určuje cesty pro hledání nebo serverů symbolů, které obsahují symboly pro datového souboru profilování.|  
|**DebugSymPath**|Seznam umístění, která jsou prohledány na symboly a určuje, zda jsou dostupné. Tato možnost je užitečná při řešení problémů rozlišení symbolů.|  
|**PackSymbols**|Uloží symboly do souboru dat profilování (.vsp) tak, aby se nevyžadují pro analýzu soubory symbolů (PDB).|  
|**Výstup:** *cesta*&#124;*název souboru*|Určuje alternativní umístění pro soubory generované sestavě. Ve výchozím nastavení jsou sestavy vytvoří v aktuálním adresáři.|  
|**SummaryFile**|Analyzovat a uložit analyzované informace v souboru souhrnu .vsps.|  
|**PrintMarks**|Zobrazte názvy a časová razítka pro všechny značky v souboru zadané sestavy.|  
|**?**|Zobrazí informace o použití.|  
|**NoLogo**|Informace o verzi skryje, když je sestava spuštěna.|  
|**UserRulesDirectory**|Určuje adresář obsahující uživatelsky definovaným výkonem pravidla [ještě nebyla implementována].|  
  
## <a name="filter-options"></a>Možnosti filtrování  
 Následující tabulka popisuje možnosti filtrovat dostupná data.  
  
|Možnosti|Popis|  
|-------------|-----------------|  
|**JustMyCode**[**:**[`caller`] [,`callee`]]|Zobrazit pouze uživatele volání funkcí aplikace; Skryjte systémových volání.<br /><br /> -Žádné parametry - skrýt všechny systémové funkce.<br />-   `caller` -Zobrazit jednu úroveň funkce systému, které volají funkce aplikace.<br />-   `callee` -Zobrazit jednu úroveň funkce systému, které jsou volány pomocí funkcí aplikace uživatele.|  
|**StartTime:**[*hodnotu*]|Zobrazit pouze data shromážděná za hodnotou (v milisekundách).|  
|**EndTime:**[*hodnotu*]|Zobrazit pouze data shromážděná před hodnotou (v milisekundách).|  
|**FilterFile:** `VSPFFile`|Určuje umístění souboru filtru, která byla vygenerována z okna sestavy výkonu Visual Studio.|  
|**MsFilter:**[*časzahájeni, trvání*]|Zobrazit pouze data od `starttime` až do délky `duration` (v milisekundách).|  
|**Proces:**[*pid*]|Zobrazit pouze data ze zadaného procesu.|  
|**Vlákna:**[*idvlákna*]|Zobrazit pouze data ze zadaného vlákna.|  
|**Vlákna:**[*idvlákna, idprocesu*]|Zobrazit pouze data ze zadaného vlákna přidruženého se zadaným procesem.|  
  
## <a name="difference-report-options"></a>Možnosti sestavy rozdíl  
 Následující tabulka popisuje možnosti pro porovnávání souborů sestav.  
  
|Možnosti|Popis|  
|-------------|-----------------|  
|**Diff**  `vspfile1 vspfile2`|Porovnejte dva soubory (.vsp nebo .vsps) souborů sestav. Možnosti souhrnu budou ignorovány pomocí možnosti rozdílů.|  
|**Diff:**[*hodnotu*]|Nižší než tato prahová hodnota bude ignorována rozdíl mezi dvěma hodnotami. Také se nezobrazí nová data s hodnotami pod tuto mezní hodnotu.|  
|**DiffTable:**[*tablename*]|Použijte tuto konkrétní tabulku pro porovnání souborů. Výchozí hodnota je tabulka funkcí.|  
|**DiffColumn:**[*názevsloupce*]|Pomocí tohoto konkrétního sloupce porovnání hodnot. Výchozí hodnota je sloupec procent výhradních vzorků.|  
|**QueryDiffTables**|Vypsat platné tabulky a sloupce příslušné dva soubory sestav, které jsou k dispozici.|  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení sestav výkonu](../profiling/performance-report-views.md)



