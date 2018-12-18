---
title: Zobrazení funkcí – Data instrumentace paměti .NET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: d48393a2d160e3691069a4b5f86dd814b63d935d
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237679"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Zobrazení funkcí – data instrumentace paměti .NET
Zobrazení funkcí rozhraní .NET paměti přidělení profilování dat, která nebyla shromážděna pomocí metody instrumentace obsahuje seznam funkcí, které přidělené paměti při spuštění profilování. Řádek funkce sestav, velikost a počet přidělování a dat časování pro funkci.  
  
## <a name="general"></a>Obecné  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název funkce**|Název funkce.|  
|**Adresa funkce**|Adresa funkce.|  
|**Číslo řádku – funkce**|Číslo řádku spuštění této funkce ve zdrojovém souboru.|  
|**Počet volání**|Celkový počet volání této funkce.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta modul, který obsahuje funkce.|  
|**ID procesu**|ID procesu (PID) z profilace spustit.|  
|**Název procesu**|Název procesu.|  
|**Režijní náklady na čas výhradní testu**|Čas režie pro tuto funkci z důvodu instrumentace. Režijní náklady na test odečtení od sebe výhradní.|  
|**Režijní náklady na čas včetně testu**|Čas režie pro tuto funkci a jeho podřízené funkce z důvodu instrumentace. Test režie odečtení od sebe (včetně).|  
  
## <a name="net-memory-values"></a>Hodnoty paměti .NET  
 (Včetně) hodnot paměti .NET funkce znamenat počet (přidělení) a velikost (bajty) objektů, které byly vytvořeny tak, že funkce a jeho podřízené funkce.  
  
 Hodnoty výhradní paměti označují, počtu a velikosti objektů, které byly vytvořeny, funkce a ne její podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Přidělení (včetně).**|Celkový počet objektů, které byly vytvořeny v tato funkce a funkce, které byly volat pomocí této funkce.|  
|**% Přidělení (včetně).**|Procento všech objektů, které byly přiděleny v profilaci spuštění, které byly včetně přidělení této funkce.|  
|**Výhradní přidělení**|Celkový počet objektů, které byly vytvořeny při funkce provádění kódu v těle funkce. Toto číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volat pomocí této funkce.|  
|**Výhradní přidělení %**|Procento všech objektů, které byly vytvořeny v profilaci spuštění, které byly výhradní přidělení této funkce.|  
|**Bajtů (včetně).**|Počet bajtů paměti, které byly přiděleny v tato funkce a funkce, které byly volat pomocí této funkce.|  
|**% Bajtů (včetně).**|Procento všech bajtů paměti, které byly přiděleny v profilaci spuštění, které byly včetně bajtů této funkce.|  
|**Výhradní bajtů**|Počet bajtů paměti, které byly přiděleny pomocí této funkce, ale není podle funkce, která se nazývá pomocí této funkce.|  
|**% Výhradní bajtů**|Procento všech bajtů paměti, které byly přiděleny v profilaci spuštění, které byly výhradní bajtů této funkce.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulá (včetně) hodnot  
 Uplynulá (včetně) hodnot označuje datum a čas, který byl funkce v zásobníku volání. Čas zahrnuje času stráveného v podřízené funkce a volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý čas (včetně).**|Celkový počet uplynulý čas včetně všechna volání této funkce.|  
|**% Uplynulá doba (včetně).**|Procento celkového počtu uplynulý čas včetně čas spuštění profilování stráveného při uplynulá doba včetně této funkce.|  
|**Průměr uplynulý čas včetně čas**|Průměr uplynulý čas včetně volání této funkce.|  
|**Maximální uplynulá doba (včetně).**|Maximální uplynulý čas včetně volání této funkce.|  
|**Min uplynulý čas včetně čas**|Minimální uplynulý čas včetně volání této funkce.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulá výhradní hodnoty  
 Uplynulá výhradní hodnoty označuje datum a čas, která funkce byla spuštěna přímo v horní části zásobníku volání. Čas zahrnuje čas ve voláních operačního systému, jako jsou přepínače kontextu a vstupně-výstupních operací, ale nezahrnuje času stráveného v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulá doba výhradní**|Celkový počet uplynulý čas výhradní všechna volání této funkce.|  
|**Uplynulý čas výhradní %**|Procento celkového počtu uplynul výhradní času stráveného při celková doba uplynulá výhradní této funkce spuštění profilování.|  
|**Průměr uplynulý exkluzivní čas**|Průměr uplynulý čas výhradní volání této funkce.|  
|**Maximální uplynulá doba výhradní**|Maximální uplynulý čas výhradní volání této funkce.|  
|**Min uplynulý exkluzivní čas**|Minimální uplynulý čas výhradní volání této funkce.|  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Aplikace (včetně) hodnot označuje datum a čas, který byl funkce v zásobníku volání. Čas nezahrnuje času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně-výstupních operací, ale nezahrnuje času stráveného v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Doba aplikace (včetně).**|Celkový počet aplikací čas včetně všechna volání této funkce.|  
|**Aplikace % času (včetně).**|Procento celkového počtu uplynulý čas včetně čas spuštění profilování stráveného v čase (včetně). Celkový počet aplikací této funkce.|  
|**Prům. čas včetně aplikace**|Průměrná aplikace čas včetně volání této funkce.|  
|**Maximální doba včetně aplikace**|Čas (včetně). maximální aplikace volání této funkce.|  
|**Doba včetně aplikace min.**|Čas včetně minimální aplikace volání této funkce.|  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Aplikace hodnot, které označuje datum a čas, která funkce byla spuštěna přímo v horní části zásobníku volání. Čas nezahrnuje času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně-výstupních operací, ani jej nezahrnuje času stráveného v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní doba aplikace**|Celkový počet aplikací čas výhradní všechna volání této funkce.|  
|**Aplikace % výhradní čas**|Procento celkového počtu uplynul výhradní času stráveného při výhradní doba celkový aplikace této funkce spuštění profilování.|  
|**Prům. čas výhradní aplikace**|Průměrná aplikace čas výhradní volání této funkce.|  
|**Maximální doba výhradní aplikace**|Čas výhradní maximální aplikace volání této funkce.|  
|**Doba výhradní aplikace min.**|Čas výhradní minimální aplikace volání této funkce.|  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení funkcí – vzorkování](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Zobrazení funkcí](../profiling/functions-view-instrumentation-data.md)   
 [Zobrazení funkcí](../profiling/functions-view-sampling-data.md)