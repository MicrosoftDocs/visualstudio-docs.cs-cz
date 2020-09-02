---
title: Zobrazení funkcí – data instrumentace paměti .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 340a12bfb8dc9a26c4200682851bb0acc684dddf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62419907"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Zobrazení funkcí – data instrumentace paměti .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení funkcí dat profilování alokace paměti .NET, která byla shromážděna pomocí metody instrumentace, uvádí funkce, které přidělené paměti při spuštění profilace. Řádek funkce sestaví velikost a počet přidělení a data časování pro funkci.  
  
## <a name="general"></a>Obecné  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název funkce**|Název funkce|  
|**Adresa funkce**|Adresa funkce|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Number of Calls**|Celkový počet volání této funkce.|  
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|  
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|  
|**Název procesu**|Název procesu|  
|**Výhradní čas režie testu**|Časová režie této funkce z důvodu instrumentace. Režie testu byla odečtena od všech výhradních časů.|  
|**Čas celkové režie testu**|Časová režie této funkce a jejích podřízených funkcí z důvodu instrumentace. Režie testu byla odečtena od všech celkových časů.|  
  
## <a name="net-memory-values"></a>Hodnoty paměti .NET  
 Celkové hodnoty paměti .NET funkce označují počet (přidělení) a velikost objektů (v bajtech), které byly vytvořeny funkcí a jejími podřízenými funkcemi.  
  
 Hodnoty exkluzivní paměti označují počet a velikost objektů, které byly vytvořeny funkcí a nikoli jejími podřízenými funkcemi.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celkové alokace**|Celkový počet objektů, které byly vytvořeny touto funkcí a ve funkcích, které byly volány touto funkcí.|  
|**% Celkových přidělení**|Procentuální podíl všech objektů, které byly přiděleny při spuštění profilace, včetně přidělení této funkce.|  
|**Exkluzivní přidělení**|Celkový počet objektů, které byly vytvořeny při provádění kódu v těle funkce. Toto číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány touto funkcí.|  
|**% Exkluzivní alokace**|Procentuální podíl všech objektů, které byly vytvořeny v rámci profilace, které byly exkluzivním přidělením této funkce.|  
|**Včetně bajtů**|Počet bajtů paměti, které byly přiděleny touto funkcí a ve funkcích, které byly volány touto funkcí.|  
|**% Celkových bajtů**|Procento všech bajtů paměti, které byly přiděleny při spuštění profilace, včetně bajtů této funkce.|  
|**Exkluzivní počet bajtů**|Počet bajtů paměti, které byly přiděleny touto funkcí, ale nikoli funkcemi, které byly volány touto funkcí.|  
|**% Exkluzivních bajtů**|Procento všech bajtů paměti, které byly přiděleny při spuštění profilace, které byly výhradně bajty této funkce.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulé celkové hodnoty  
 Uplynulé celkové hodnoty udávají čas, kdy byla funkce v zásobníku volání. Čas zahrnuje čas strávený v podřízených funkcích a v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý celkový čas**|Celkový uplynulý celkový čas všech volání této funkce.|  
|**% Uplynulého celkového času**|Procento celkového uplynulého celkového času běhu profilace, které bylo stráveno v uplynulém celkovém čase této funkce.|  
|**Průměrný uplynulý celkový čas**|Průměrně uplynulý celková doba volání této funkce.|  
|**Maximální uplynulý celkový čas**|Maximální uplynulý celková doba volání této funkce.|  
|**Minimální uplynulý celkový čas**|Minimální uplynulý celkový čas volání této funkce.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty  
 Uplynulé exkluzivní hodnoty označují čas, kdy byla funkce přímo spuštěna v horní části zásobníku volání. Čas zahrnuje čas volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace, ale nezahrnuje čas strávený v podřízených funkcích.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý výhradní čas**|Celkový uplynulý výhradní čas všech volání této funkce.|  
|**% Uplynulého výhradního času**|Procento celkového uplynulého výhradního času pro spuštění profilování, které bylo stráveno celkovým uplynulým výhradním časem této funkce.|  
|**Průměrný uplynulý výhradní čas**|Průměrný uplynulý výhradní čas volání této funkce.|  
|**Maximální uplynulý výhradní čas**|Maximální uplynulý výhradní čas volání této funkce.|  
|**Minimální uplynulý výhradní čas**|Minimální uplynulý výhradní čas volání této funkce.|  
  
## <a name="application-inclusive-values"></a>Hodnoty zahrnující aplikace  
 Hodnoty pro všechny aplikace označují čas, kdy byla funkce v zásobníku volání. Čas neobsahuje čas strávený voláním operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace, ale obsahuje čas strávený v podřízených funkcích.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celková doba aplikace**|Celkový čas všech volání této funkce pro všechny aplikace.|  
|**% Celkového času aplikace**|Procento celkového uplynulého celkového času běhu profilace, které bylo stráveno v celkovém čase aplikace této funkce.|  
|**Průměrná doba aplikace (celková)**|Průměrná doba použití volání této funkce.|  
|**Maximální celková doba aplikace**|Maximální doba volání této funkce v rámci aplikace.|  
|**Minimální celková doba aplikace**|Minimální doba pro volání této funkce (včetně celkového počtu aplikací).|  
  
## <a name="application-exclusive-values"></a>Exkluzivní hodnoty aplikací  
 Hodnoty exkluzivní pro aplikace označují čas, kdy byla funkce přímo spuštěna v horní části zásobníku volání. Čas neobsahuje čas strávený voláním operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace, ani nezahrnuje čas strávený v podřízených funkcích.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní čas aplikace**|Celkový výhradní čas všech volání této funkce.|  
|**% Výhradního času aplikace**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo stráveno v celkovém čase aplikace, který je výhradně členem této funkce.|  
|**Průměrný výhradní čas aplikace**|Průměrná doba aplikace, která je výhradním časem pro volání této funkce.|  
|**Maximální výhradní čas aplikace**|Maximální doba výhradního volání této funkce pro aplikaci.|  
|**Minimální výhradní čas aplikace**|Minimální výhradní čas aplikace pro volání této funkce.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení funkcí – vzorkování](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Zobrazení funkcí](../profiling/functions-view-instrumentation-data.md)   
 [Zobrazení funkcí](../profiling/functions-view-sampling-data.md)
