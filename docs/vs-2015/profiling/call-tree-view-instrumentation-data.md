---
title: Zobrazení stromu volání – Data instrumentace | Dokumentace Microsoftu
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
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 630f75468adf5995eb887ac5f73d82462bfe32a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786240"
---
# <a name="call-tree-view---instrumentation-data"></a>Zobrazení stromu volání – data instrumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hodnoty pro funkci ve stromu volání označuje datum a čas pro instance funkce, které byly volány nadřazené funkce ve stromu volání. Procentní hodnoty se počítá srovnáním hodnoty jsou funkce instance celkový uplynulý celkový čas všech funkcí během spuštění profilování.  
  
## <a name="general"></a>Obecné  
 Obecné sloupce rozpoznat funkci zobrazení řádku.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název funkce**|Název funkce.|  
|**Adresa funkce**|Adresa funkce.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Počet volání**|Celkový počet volání provedených touto funkcí.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje funkci.|  
|**ID procesu**|ID procesu (PID) běhu profilování.|  
|**Název procesu**|Název, který je přiřazen k procesu.|  
|**Výhradní čas režie**|Časová náročnost této funkce, která způsobila instrumentace. Režie byla odečtena od vylučuje všechny časy.|  
|**Celkový čas režie**|Časová náročnost této funkce a její podřízené funkce, která způsobila instrumentace. Test zatížení byla odečtena od fiskálního (včetně).|  
|**úroveň**|Hloubka funkce ve stromu volání. Pouze v [VSPerfReport](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulý včetně hodnoty  
 Uplynulý včetně hodnoty označuje datum a čas v zásobníku volání instance funkce, které byly volány nadřazené funkce ve stromu volání. Čas obsahuje čas, který byl stráven v podřízené funkce, které volal funkci a ve volání do operačního systému, například vstupně výstupní operace a přepnutí kontextu.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý celkový čas**|Celkový uplynulý celkový čas všechna volání této funkce v tomto kontextu.|  
|**% Uplynulého celkového času**|Procento celkového uplynulý celkový čas, který běhu profilování se využilo na celkový uplynulý celkový čas této funkce v tomto kontextu.|  
|**Průměrný uplynulý celkový čas**|Průměr uplynulý celkový čas volání této funkce v tomto kontextu.|  
|**Maximální uplynulý celkový čas**|Maximální uplynulý celkový čas volání této funkce v tomto kontextu.|  
|**Minimální uplynulý celkový čas**|Minimální uplynulý celkový čas volání této funkce v tomto kontextu.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulý výhradní hodnoty  
 Uplynulý výhradní hodnoty označuje datum a čas, že byly tyto instance funkce, které byly volány nadřazené funkce ve stromu volání spouštění kódu v těle funkce; To znamená, když funkce byla v horní části zásobníku volání. Čas zahrnuje čas ve volání do operačního systému, například vstupně výstupní operace a přepnutí kontextu. Čas, ale nezahrnuje čas, který byl stráven v podřízené funkce, které byly volány funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý výhradní čas**|Celkový uplynulý výhradní čas všechna volání této funkce v tomto kontextu.|  
|**% Uplynulého výhradního času**|Procento celkového uplynulý výhradní čas, který běhu profilování se využilo na celkový uplynulý výhradní čas této funkce v tomto kontextu.|  
|**Průměrný uplynulý výhradní čas**|Průměr uplynulý výhradní čas volání této funkce v tomto kontextu.|  
|**Maximální uplynulý výhradní čas**|Maximální uplynulý výhradní čas volání této funkce v tomto kontextu.|  
|**Minimální uplynulý výhradní čas**|Minimální uplynulý výhradní čas volání této funkce v tomto kontextu.|  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Aplikace (včetně) hodnot označuje datum a čas, které byly instancí funkce, které byly volány nadřazené funkce ve stromu volání zásobníku volání. Čas nezahrnuje čas, který byl stráven ve volání do operačního systému, například vstupně výstupní operace a přepnutí kontextu, čas však neobsahuje čas, který byl stráven v podřízené funkce, které byly volány funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celkový čas aplikace**|Celkový čas aplikace celkový počet všech volání této funkce v tomto kontextu.|  
|**% Celkového času aplikace**|Procento celkového uplynulý celkový čas, který běhu profilování se využilo na celkový čas celkový aplikace této funkce v tomto kontextu.|  
|**Průměrný celkový čas aplikace**|Celkový čas průměrná aplikace volání této funkce v tomto kontextu.|  
|**Maximální celkový čas aplikace**|Celkový čas aplikace maximální volání této funkce v tomto kontextu.|  
|**Minimální celkový čas aplikace**|Celkový čas aplikace minimální volání této funkce v tomto kontextu.|  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Výhradní hodnoty, které aplikaci označuje datum a čas, že tyto instance funkce, které byly volány nadřazené funkce ve stromu volání byly přímo spouštění kódu v těle funkce; To znamená, když funkce byla v horní části zásobníku volání. Čas nezahrnuje čas, který byl stráven ve volání do operačního systému, například vstupně výstupní operace a přepnutí kontextu. Také nezahrnuje čas, který byl stráven v podřízené funkce, které byly volány funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní čas aplikace**|Výhradní čas aplikace celkový počet všech volání této funkce v tomto kontextu.|  
|**% Výhradního času aplikace**|Procento celkového uplynulý výhradní čas, který běhu profilování se využilo na výhradní čas aplikace celkový této funkce v tomto kontextu.|  
|**Průměrný výhradní čas aplikace**|Výhradní čas aplikace průměrné volání této funkce v tomto kontextu.|  
|**Maximální výhradní čas aplikace**|Výhradní čas aplikace maximální volání této funkce v tomto kontextu.|  
|**Minimální výhradní čas aplikace**|Výhradní čas aplikace minimální volání této funkce v tomto kontextu.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)   
 [Zobrazení stromu volání – instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení stromu volání – Vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)



