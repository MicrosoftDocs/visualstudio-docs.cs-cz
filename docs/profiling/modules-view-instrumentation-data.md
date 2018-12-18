---
title: Zobrazení modulů – Data instrumentace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c849971da7681322b15365bc0d59ce8b3529f508
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256107"
---
# <a name="modules-view---instrumentation-data"></a>Zobrazení modulů – data instrumentace
Zobrazení modulů zobrazuje data výkonu, která se seskupují po moduly, které byly v profilaci data. Funkce modulu jsou uvedeny níže uzlu modulu.  
  
## <a name="general"></a>Obecné  
 Obecné sloupce rozpoznat funkci v řádku zobrazení.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název funkce nebo modul.|  
|**Číslo řádku – funkce**|Číslo řádku spuštění této funkce ve zdrojovém souboru.|  
|**Počet volání**|Celkový počet volání, které byly provedeny na tento modul nebo funkce.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta modul, který obsahuje funkce.|  
|**ID procesu**|ID procesu (PID) z profilace spustit.|  
|**Název procesu**|Název procesu, ve kterém se provádí modulu nebo funkce.|  
|**Režijní náklady na čas výhradní testu**|Čas zatížení pro tento modul z důvodu instrumentace nebo funkce.|  
|**Režijní náklady na čas včetně testu**|Čas režie pro tuto funkci nebo modul a jeho podřízené funkce z důvodu instrumentace.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulá (včetně) hodnot  
 Uplynulá (včetně) hodnot označuje datum a čas, který byl funkce v zásobníku volání. Čas zahrnuje času stráveného v podřízené funkce a volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý čas (včetně).**|-Pro funkce, času stráveného ve funkci. To zahrnuje času stráveného v podřízené funkce a volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.<br />-Pro modul, čas, ve kterém byl alespoň jednu funkci v modulu v zásobníku volání.|  
|**% Uplynulá doba (včetně).**|Procento uplynulé době celkový včetně profilace spuštění, který byl stráven v celková doba uplynulá včetně tohoto modulu nebo funkce.|  
|**Průměr uplynulý čas včetně čas**|-Pro funkci průměr uplynulý čas včetně volání této funkce.<br />-Průměr pro modul, uplynulý čas včetně všech volání funkcí v modulu.|  
|**Maximální uplynulá doba (včetně).**|-Pro funkci maximální uplynulý čas včetně volání této funkce.<br />-Pro modul maximální uplynulý čas včetně všech volání funkcí v modulu.|  
|**Min uplynulý čas včetně čas**|-Pro funkci minimální uplynulý čas včetně volání tohoto modulu nebo funkce.<br />-Pro modul minimální uplynulý čas včetně všech volání funkcí v modulu.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulá výhradní hodnoty  
 Uplynulá výhradní hodnoty označuje datum a čas, která funkce byla spuštěna přímo v horní části zásobníku volání. Čas zahrnuje času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně-výstupních operací, ale nezahrnuje času stráveného v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulá doba výhradní**|-Pro funkce, času stráveného v modulu nebo funkce. To zahrnuje volání operačního systému, jako jsou přepínače kontextu a vstupně-výstupních operací, ale nezahrnuje času stráveného v podřízené funkce.<br />-Pro modul uplynulý součet výhradní časy funkce v modulu.|  
|**Uplynulý čas výhradní %**|Procento uplynulé době celkový výhradní profilace spuštění, který byl stráven v celková doba uplynulá výhradní tohoto modulu nebo funkce.|  
|**Průměr uplynulý exkluzivní čas**|-Pro funkci uplynulý průměr výhradní čas volání této funkce.<br />-Pro modul průměr uplynulý čas výhradní všechna volání funkce v modulu.|  
|**Maximální uplynulá doba výhradní**|-Pro funkci maximální uplynulý výhradní čas volání této funkce.<br />-Pro modul maximální uplynulý výhradní čas všechna volání funkce v modulu.|  
|**Min uplynulý exkluzivní čas**|-Pro funkci uplynulý minimální výhradní čas volání tohoto modulu nebo funkce.<br />-Pro modul minimální uplynulý čas výhradní všechna volání funkce v modulu.|  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Aplikace (včetně) hodnot označuje datum a čas, který byl funkce v zásobníku volání. Čas nezahrnuje času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace. Čas však nezahrnuje času stráveného v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Doba aplikace (včetně).**|-Pro funkce, času stráveného při volání funkce. To zahrnuje dobu, po kterou byl stráven v podřízené funkce, ale nezahrnuje volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.<br />-Pro modul, čas, ve kterém byl alespoň jednu funkci v modulu v zásobníku volání. Nevztahuje se na času stráveného v volání operačního systému.|  
|**Aplikace % času (včetně).**|Procento celkového počtu uplynulý čas včetně času stráveného v čase aplikace včetně tohoto modulu nebo funkce spuštění profilování.|  
|**Prům. čas včetně aplikace**|-Pro funkce, včetně doba průměrná aplikace volání této funkce.<br />-Pro modul, průměrná aplikace včetně době všechna volání funkce v modulu.|  
|**Maximální doba včetně aplikace**|-Pro funkce, včetně doba maximální aplikace volání této funkce.<br />-Pro modul, doba maximální aplikace včetně všech volání funkce v modulu.|  
|**Doba včetně aplikace min.**|-Pro funkce, době minimální aplikace včetně volání tohoto modulu nebo funkce.<br />-Pro modul, doba minimální aplikace včetně všech volání funkce v modulu.|  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Aplikace hodnot, které označují času stráveného v modulu nebo funkce. Nevztahuje se na dobu, po kterou byl stráven podřízené funkcí a také vyloučí volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní doba aplikace**|Celkový počet aplikací čas výhradní všechna volání do tohoto modulu nebo funkce.|  
|**Aplikace % výhradní čas**|Procento celkového počtu uplynul výhradní času stráveného v čase výhradní aplikací tohoto modulu nebo funkce spuštění profilování.|  
|**Prům. čas výhradní aplikace**|-Pro funkce, době výhradní průměrná aplikace volání této funkce.<br />-Pro modul, průměrná aplikace výhradní době všechna volání funkce v modulu.|  
|**Maximální doba výhradní aplikace**|-Pro funkce, době výhradní maximální aplikace volání této funkce.<br />-Pro modul, doba výhradní maximální aplikace všechna volání funkce v modulu.|  
|**Doba výhradní aplikace min.**|-Pro funkce, době výhradní minimální aplikace volání tohoto modulu nebo funkce.<br />-Pro modul, doba výhradní minimální aplikace všechna volání funkce v modulu.|  
  
## <a name="see-also"></a>Viz také:  
 [Zobrazení modulů](../profiling/modules-view-sampling-data.md)   
 [Zobrazení modulů – instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Moduly zobrazení – vzorkování](../profiling/modules-view-dotnet-memory-sampling-data.md)