---
title: Zobrazení stromu volání – Data instrumentace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b42cce6c9134a668d5096150d986e950ed8a8e7
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262228"
---
# <a name="call-tree-view---instrumentation-data"></a>Zobrazení stromu volání – data instrumentace
Hodnoty pro funkci ve stromové struktuře volání označuje datum a čas pro instance funkce, které byly volá funkci nadřazené ve stromové struktuře volání. Procentní hodnoty se počítá srovnáním hodnotu instance funkce celkovou dobu uplynulá včetně všechny funkce v profilaci spustit.  
  
## <a name="general"></a>Obecné  
 Obecné sloupce rozpoznat funkci v řádku zobrazení.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název funkce**|Název funkce.|  
|**Adresa funkce**|Adresa funkce.|  
|**Číslo řádku – funkce**|Číslo řádku spuštění této funkce ve zdrojovém souboru.|  
|**Počet volání**|Celkový počet volání, které byly provedeny na tuto funkci.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta modul, který obsahuje funkce.|  
|**ID procesu**|ID procesu (PID) z profilace spustit.|  
|**Název procesu**|Název, který je přiřazen k procesu.|  
|**Režijní náklady na čas výhradní testu**|Čas režie pro tuto funkci byl příčinou instrumentace. Režijní náklady na test odečtení od sebe výhradní.|  
|**Režijní náklady na čas včetně testu**|Čas režie pro tuto funkci a jeho podřízené funkce, bylo způsobeno instrumentace. Test režie odečtení od sebe (včetně).|  
|**úroveň**|Hloubka funkce ve stromové struktuře volání. Pouze v [vsperfreport –](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulá (včetně) hodnot  
 Uplynulá (včetně) hodnot označuje datum a čas v zásobníku volání instancí funkce, které byly volá funkci nadřazené ve stromové struktuře volání. Čas zahrnuje času stráveného v podřízené funkce, které byly volá funkce a volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý čas (včetně).**|Celkový počet uplynulý čas včetně všechna volání této funkce v tomto kontextu.|  
|**% Uplynulá doba (včetně).**|Procento uplynulé době celkový včetně profilace spuštění, který byl stráven v celková doba uplynulá (včetně). Tato funkce v tomto kontextu.|  
|**Průměr uplynulý čas včetně čas**|Průměr uplynulý čas včetně volání této funkce v tomto kontextu.|  
|**Maximální uplynulá doba (včetně).**|Maximální uplynulý čas včetně volání této funkce v tomto kontextu.|  
|**Min uplynulý čas včetně čas**|Minimální uplynulý čas včetně volání této funkce v tomto kontextu.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulá výhradní hodnoty  
 Uplynulá výhradní hodnoty označuje datum a čas, že instance funkce, které byly volá funkci nadřazené ve stromové struktuře volání měla spuštěním kódu v těle funkce; To znamená, když funkce byla v horní části zásobníku volání. Čas zahrnuje čas v volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace. Čas však nezahrnuje času stráveného v podřízené funkce, které byly volá funkci.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulá doba výhradní**|Celkový počet uplynulý čas výhradní všechna volání této funkce v tomto kontextu.|  
|**Uplynulý čas výhradní %**|Procento uplynulé době celkový výhradní profilace spuštění, který byl stráven v celková doba uplynulá výhradní této funkce v tomto kontextu.|  
|**Průměr uplynulý exkluzivní čas**|Průměr uplynulý čas výhradní volání této funkce v tomto kontextu.|  
|**Maximální uplynulá doba výhradní**|Maximální uplynulý čas výhradní volání této funkce v tomto kontextu.|  
|**Min uplynulý exkluzivní čas**|Minimální uplynulý čas výhradní volání této funkce v tomto kontextu.|  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Aplikace (včetně) hodnot označuje datum a čas, které byly instance funkce, které byly volá funkci nadřazené ve stromové struktuře volání v zásobníku volání. Čas nezahrnuje času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně-výstupních operací, ale čas nezahrnuje času stráveného v podřízené funkce, které byly volá funkci.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Doba aplikace (včetně).**|Celkový počet aplikací čas včetně všechna volání této funkce v tomto kontextu.|  
|**Aplikace % času (včetně).**|Procento uplynulé době celkový včetně profilace spuštění, který byl stráven v čase celkový aplikace (včetně). Tato funkce v tomto kontextu.|  
|**Prům. čas včetně aplikace**|Průměrná aplikace čas včetně volání této funkce v tomto kontextu.|  
|**Maximální doba včetně aplikace**|Čas (včetně). maximální aplikace volání této funkce v tomto kontextu.|  
|**Doba včetně aplikace min.**|Čas včetně minimální aplikace volání této funkce v tomto kontextu.|  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Aplikace hodnot, které označuje datum a čas, že instance funkce, které byly volá funkci nadřazené ve stromové struktuře volání byly přímo spuštěním kódu v těle funkce; To znamená, když funkce byla v horní části zásobníku volání. Čas nezahrnuje času stráveného v volání operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace. Také neobsahoval času stráveného v podřízené funkce, které byly volá funkci.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní doba aplikace**|Celkový počet aplikací čas výhradní všechna volání této funkce v tomto kontextu.|  
|**Aplikace % výhradní čas**|Procento uplynulé době celkový výhradní profilace spuštění, který byl stráven výhradní včas celkový aplikace této funkce v tomto kontextu.|  
|**Prům. čas výhradní aplikace**|Průměrná aplikace čas výhradní volání této funkce v tomto kontextu.|  
|**Maximální doba výhradní aplikace**|Čas výhradní maximální aplikace volání této funkce v tomto kontextu.|  
|**Doba výhradní aplikace min.**|Čas výhradní minimální aplikace volání této funkce v tomto kontextu.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)   
 [Zobrazení stromu volání – instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Volání stromové zobrazení – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)