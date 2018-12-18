---
title: Zobrazení volající volaný – Data instrumentace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8a24d19fabc3cb82dbb4004ec71b6fa00bc470c
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2018
ms.locfileid: "34336110"
---
# <a name="callercallee-view---instrumentation-data"></a>Zobrazení volající/volaný – data instrumentace
Zobrazení volající/volaný zobrazí profilování informace o vybrané funkce a její nadřazené a podřízené funkce ve stromové struktuře volání. Zobrazení volající/volaný obsahuje tři mřížky.  
  
 **Funkci Current** se zobrazí v prostředním mřížky a ukazuje profilace informace o vybrané funkce. Hodnoty zahrnují všechna volání funkce.  
  
 **Funkce, které volá funkci current** se zobrazí v horní mřížky a ukazuje profilace informace o funkcích volající (nadřazené) vybrané funkce. Hodnoty určují množství hodnotu aktuální funkce, který byl vygenerován volání z této funkce volajícího.  
  
 **Funkce, které byly volá funkci current** se zobrazí v mřížce dole a ukazuje profilace informace o instancích funkcí volaný (podřízená) vybrané funkce. Hodnoty znamenat pouze času stráveného ve funkci podřízené při volání funkcí aktuální.  
  
## <a name="general"></a>Obecné  
 Obecné sloupce rozpoznat funkci v řádku zobrazení.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název funkce**|Název funkce.|  
|**Adresa funkce**|Adresa funkce.|  
|**Číslo řádku – funkce**|Číslo řádku spuštění této funkce ve zdrojovém souboru.|  
|**Počet volání**|Celkový počet volání této funkce.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta modul, který obsahuje funkce.|  
|**ID procesu**|ID procesu (PID) z profilace spustit.|  
|**Název procesu**|Název procesu.|  
|**Režijní náklady na čas výhradní testu**|Čas režie pro tuto funkci byl příčinou instrumentace. Režijní náklady na test odečtení od sebe výhradní.|  
|**Režijní náklady na čas včetně testu**|Čas režie pro tuto funkci a jeho podřízené funkce, bylo způsobeno instrumentace. Test režie odečtení od sebe (včetně).|  
|**Typ**|Kontext funkce:<br /><br /> **0** -aktuální funkce<br /><br /> **1** -funkci, která volá funkci current<br /><br /> **2** -funkci, která volá funkci current<br /><br /> Pouze v [vsperfreport –](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**Název kořenové – funkce**|Název aktuální funkce. Pouze v [vsperfreport –](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulá (včetně) hodnot  
 Uplynulá (včetně) hodnot označuje datum a čas, který byl funkce v zásobníku volání. Čas zahrnuje času stráveného v podřízené funkce a času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý čas (včetně).**|-Pro aktuální funkci času stráveného ve funkci. Hodnota obsahuje času stráveného v podřízené funkce a volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.<br />-Pro volající funkce časového intervalu uplynulá včetně aktuální funkce, který byl vygenerován volání z této funkce volajícího.<br />-Pro funkce volaný času stráveného v instancích této funkce, které byly vygenerovány volání z aktuální funkce. Hodnota obsahuje času stráveného v podřízené funkce volaného a volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.|  
|**% Uplynulá doba (včetně).**|Procento celkového počtu uplynulý čas včetně času stráveného v uplynulé době (včetně). Tato funkce v tomto kontextu spuštění profilování.|  
|**Průměr uplynulý čas včetně čas**|Průměr uplynulý čas včetně volání této funkce v tomto kontextu.|  
|**Maximální uplynulá doba (včetně).**|Maximální uplynulý čas včetně volání této funkce v tomto kontextu.|  
|**Min uplynulý čas včetně čas**|Minimální uplynulý čas včetně volání této funkce v tomto kontextu.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulá výhradní hodnoty  
 Uplynulá výhradní hodnoty označuje datum a čas, která funkce byla spuštěna přímo v horní části zásobníku volání. Čas zahrnuje času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně-výstupních operací, ale nezahrnuje času stráveného v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulá doba výhradní**|-Pro aktuální funkci času stráveného při přímé provádění funkce. Hodnota obsahuje času stráveného v podřízené funkce a volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.<br />-Pro volající funkce časového intervalu uplynulá výhradní aktuální funkce, který byl vygenerován volání z této funkce volajícího.<br />-Pro funkce volaný času stráveného v instancích této funkce, které byly vygenerovány volání z aktuální funkce. Hodnota vyloučí času stráveného v podřízené funkce volaný funkce, ale obsahuje volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.|  
|**Uplynulý čas výhradní %**|Procento uplynulé době celkový výhradní profilace spuštění, který byl stráven v celková doba uplynulá výhradní této funkce v tomto kontextu.|  
|**Průměr uplynulý exkluzivní čas**|Průměr uplynulý čas výhradní volání této funkce v tomto kontextu.|  
|**Maximální uplynulá doba výhradní**|Maximální uplynulý čas výhradní volání této funkce v tomto kontextu.|  
|**Min uplynulý exkluzivní čas**|Minimální uplynulý čas výhradní volání této funkce v tomto kontextu.|  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Aplikace (včetně) hodnot označuje datum a čas, který byl funkce v zásobníku volání. Čas nezahrnuje času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně-výstupních operací, ale nezahrnuje času stráveného v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Doba aplikace (včetně).**|-Pro aktuální funkci času stráveného v funkce a jeho podřízené funkce. Hodnota vyloučí času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.<br />-Pro volající funkce, včetně dobu aplikace aktuální funkce, který byl vygenerován volání z této funkce volajícího.<br />-Pro funkce volaný času stráveného v instancích této funkce, které byly vygenerovány volání z aktuální funkce. Hodnota obsahuje času stráveného v podřízené funkce volaný funkce, ale nezahrnuje času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.|  
|**Aplikace % času (včetně).**|Procento uplynulé době celkový včetně profilace spuštění, který byl stráven v čase celkový aplikace (včetně). Tato funkce v tomto kontextu.|  
|**Prům. čas včetně aplikace**|Průměrná aplikace čas včetně volání této funkce v tomto kontextu.|  
|**Maximální doba včetně aplikace**|Čas (včetně). maximální aplikace volání této funkce v tomto kontextu.|  
|**Doba včetně aplikace min.**|Čas včetně minimální aplikace volání této funkce v tomto kontextu.|  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Aplikace hodnot, které označují času stráveného ve funkci. Nevztahuje se na dobu, po kterou byl stráven podřízené funkcí a také vyloučí volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní doba aplikace**|-Pro aktuální funkci času stráveného při přímé provádění funkce. Hodnota nezahrnuje času stráveného v podřízené funkce ani nezahrnuje volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.<br />-Pro volající funkce množství času výhradní aplikace aktuální funkce, který byl vygenerován volání z této funkce volajícího.<br />-Pro funkce volaný času stráveného v instancích této funkce, které byly vygenerovány volání z aktuální funkce. Hodnota nezahrnuje času stráveného v podřízené funkce funkce volaný ani nezahrnuje volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.|  
|**Aplikace % výhradní čas**|Procento uplynulé době celkový výhradní profilace spuštění, který byl stráven výhradní včas celkový aplikace této funkce v tomto kontextu.|  
|**Prům. čas výhradní aplikace**|Průměrná aplikace čas výhradní volání této funkce v tomto kontextu.|  
|**Maximální doba výhradní aplikace**|Čas výhradní maximální aplikace volání této funkce v tomto kontextu.|  
|**Doba výhradní aplikace min.**|Čas výhradní minimální aplikace volání této funkce v tomto kontextu.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení volající/volaný – vzorkování dat](../profiling/caller-callee-view-sampling-data.md)   
 [Zobrazení volající/volaný – data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Zobrazení volající/volaný – data instrumentace paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)