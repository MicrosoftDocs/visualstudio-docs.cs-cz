---
title: Zobrazení funkcí – Data instrumentace paměti .NET | Dokumentace Microsoftu
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
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8bacc61ec9c254ce662854a08fe6a508977a72e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730190"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Zobrazení funkcí – data instrumentace paměti .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení funkcí .NET profilování data o přidělování paměti, která byla shromážděna pomocí metody instrumentace seznam funkcí, které přidělené paměti během spuštění profilování. Řádek funkce sestav, velikost a počet přidělení a dat časování pro funkci.  
  
## <a name="general"></a>Obecné  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název funkce**|Název funkce.|  
|**Adresa funkce**|Adresa funkce.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Počet volání**|Celkový počet volání provedených touto funkcí.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje funkci.|  
|**ID procesu**|ID procesu (PID) běhu profilování.|  
|**Název procesu**|Název procesu.|  
|**Výhradní čas režie**|Časová náročnost této funkce z důvodu instrumentace. Režie byla odečtena od vylučuje všechny časy.|  
|**Celkový čas režie**|Časová náročnost této funkce a její podřízené funkce z důvodu instrumentace. Test zatížení byla odečtena od fiskálního (včetně).|  
  
## <a name="net-memory-values"></a>Hodnoty paměti .NET  
 (Včetně) hodnot paměti .NET funkce označují číslo (přidělení) a velikost (bajty) objektů, které byly vytvořeny tak, že funkce a její podřízené funkce.  
  
 Výhradní paměti hodnoty označují, počtu a velikosti objektů, které byly vytvořeny, funkce a ne její podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celkově přidělení**|Celkový počet objektů, které byly vytvořeny v této funkci a funkce, které byly volány touto funkcí.|  
|**% Celkových přidělení**|Procento všech objektů, které byly přiděleny v profilování, která se celkově přidělení této funkce.|  
|**Výhradní přidělení**|Celkový počet objektů, které byly vytvořeny při provádění kódu funkce v těle funkce. Toto číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány touto funkcí.|  
|**% Výhradních přidělení**|Procento všech objektů, které byly vytvořeny v profilování, které byly výhradních přidělení této funkce.|  
|**Celkově bajtů**|Počet bajtů paměti, které byly přiděleny v této funkci a funkce, které byly volány touto funkcí.|  
|**% Celkových bajtů**|Procento bajtů paměti, které byly přiděleny v profilování, která se celkově bajtů této funkce.|  
|**Výhradní bajty**|Počet bajtů paměti, které byly přiděleny touto funkcí, ale ne pomocí funkcí, které byly volány touto funkcí.|  
|**% Výhradních bajtů**|Procento všech počet bajtů paměti, které byly přiděleny v profilování, které byly výhradních bajtů této funkce.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulý včetně hodnoty  
 Uplynulý včetně hodnoty označuje datum a čas, který funkce byla v zásobníku volání. Čas obsahuje čas, který byl stráven v podřízené funkce a volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý celkový čas**|Celkový uplynulý celkový čas všechna volání této funkce.|  
|**% Uplynulého celkového času**|Procento celkového uplynulý celkový čas, který byl stráven v uplynulý celkový čas této funkce spuštění profilování.|  
|**Průměrný uplynulý celkový čas**|Průměr uplynulý celkový čas volání této funkce.|  
|**Maximální uplynulý celkový čas**|Maximální uplynulý celkový čas volání této funkce.|  
|**Minimální uplynulý celkový čas**|Minimální uplynulý celkový čas volání této funkce.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulý výhradní hodnoty  
 Uplynulý výhradní hodnoty označuje datum a čas, který funkce byla spuštěna přímo v horní části zásobníku volání. Čas zahrnuje čas ve volání do operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace, ale nezahrnuje čas, který byl stráven v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý výhradní čas**|Celkový uplynulý výhradní čas všechna volání této funkce.|  
|**% Uplynulého výhradního času**|Procentuální podíl celkového počtu uplynulý výhradní čas spuštění profilování, která se využilo na celkový uplynulý výhradní čas této funkce.|  
|**Průměrný uplynulý výhradní čas**|Průměr uplynulý výhradní čas volání této funkce.|  
|**Maximální uplynulý výhradní čas**|Maximální uplynulý výhradní čas volání této funkce.|  
|**Minimální uplynulý výhradní čas**|Minimální uplynulý výhradní čas volání této funkce.|  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Aplikace (včetně) hodnot označuje datum a čas, který funkce byla v zásobníku volání. Čas nezahrnuje čas, který byl stráven ve volání do operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace, ale neobsahuje čas, který byl stráven v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celkový čas aplikace**|Celkový čas aplikace celkový počet všech volání této funkce.|  
|**% Celkového času aplikace**|Procento celkového uplynulý celkový čas, který byl stráven v celkový čas celkový aplikace této funkce spuštění profilování.|  
|**Průměrný celkový čas aplikace**|Celkový čas průměrná aplikace volání této funkce.|  
|**Maximální celkový čas aplikace**|Celkový čas aplikace maximální volání této funkce.|  
|**Minimální celkový čas aplikace**|Celkový čas aplikace minimální volání této funkce.|  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Výhradní hodnoty, které aplikaci označuje datum a čas, který funkce byla spuštěna přímo v horní části zásobníku volání. Čas nezahrnuje čas, který byl stráven ve volání do operačního systému, například vstupně výstupní operace a přepnutí kontextu ani obsahuje čas, který byl stráven v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní čas aplikace**|Výhradní čas aplikace celkový počet všech volání této funkce.|  
|**% Výhradního času aplikace**|Procentuální podíl celkového počtu uplynulý výhradní čas spuštění profilování, který byl stráven v výhradní čas aplikace celkový této funkce.|  
|**Průměrný výhradní čas aplikace**|Výhradní čas aplikace průměrné volání této funkce.|  
|**Maximální výhradní čas aplikace**|Výhradní čas aplikace maximální volání této funkce.|  
|**Minimální výhradní čas aplikace**|Výhradní čas aplikace minimální volání této funkce.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení funkcí – vzorkování](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Zobrazení funkcí](../profiling/functions-view-instrumentation-data.md)   
 [Zobrazení funkcí](../profiling/functions-view-sampling-data.md)



