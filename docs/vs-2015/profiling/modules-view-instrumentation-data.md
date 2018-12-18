---
title: Zobrazení modulů – Data instrumentace | Dokumentace Microsoftu
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
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55a01dab80d15bcd7356bc059db2be6d10f504a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808522"
---
# <a name="modules-view---instrumentation-data"></a>Zobrazení modulů – data instrumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Moduly zobrazení ukazuje údaje o výkonu, který je seskupené podle modulů, které byly v dat profilování. Funkce modulu jsou uvedeny pod uzlem modulu.  
  
## <a name="general"></a>Obecné  
 Obecné sloupce rozpoznat funkci zobrazení řádku.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název funkce nebo modulu.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Počet volání**|Celkový počet volání, které byly provedeny této funkce nebo modulu.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje funkci.|  
|**ID procesu**|ID procesu (PID) běhu profilování.|  
|**Název procesu**|Název procesu, ve kterém byla spuštěna modulu nebo funkce.|  
|**Výhradní čas režie**|Časová náročnost této funkce nebo modulu kvůli instrumentace.|  
|**Celkový čas režie**|Časová náročnost této funkce nebo modulu a její podřízené funkce z důvodu instrumentace.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulý včetně hodnoty  
 Uplynulý včetně hodnoty označuje datum a čas, který funkce byla v zásobníku volání. Čas obsahuje čas, který byl stráven v podřízené funkce a volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý celkový čas**|-Pro funkci, čas, který byl vynaložen ve funkci. To zahrnuje čas, který byl stráven v podřízené funkce a volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.<br />-Pro modul, čas, ve kterém byla aspoň jedna funkce v modulu v zásobníku volání.|  
|**% Uplynulého celkového času**|Procento celkového uplynulý celkový čas, který běhu profilování se využilo na celkový uplynulý celkový čas tohoto modulu nebo funkce.|  
|**Průměrný uplynulý celkový čas**|-Pro určitou funkci průměr uplynulý celkový čas volání této funkce.<br />-Pro modul průměr uplynulý celkový čas všechna volání funkce v modulu.|  
|**Maximální uplynulý celkový čas**|-Pro určitou funkci maximální uplynulý celkový čas volání této funkce.<br />-Pro modul maximální uplynulý celkový čas všechna volání funkce v modulu.|  
|**Minimální uplynulý celkový čas**|-Pro určitou funkci minimální uplynulý celkový čas volání tohoto modulu nebo funkce.<br />-Pro modul minimální uplynulý celkový čas všechna volání funkce v modulu.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulý výhradní hodnoty  
 Uplynulý výhradní hodnoty označuje datum a čas, který funkce byla spuštěna přímo v horní části zásobníku volání. Čas zahrnuje čas, který byl stráven ve volání do operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace, ale nezahrnuje čas, který byl stráven v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý výhradní čas**|-Pro funkci, čas, který byl stráven v modulu nebo funkce. To zahrnuje volání do operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace, ale nezahrnuje čas, který byl stráven v podřízené funkce.<br />-Pro modul součet uplynulý výhradní čas funkce v modulu.|  
|**% Uplynulého výhradního času**|Procento celkového uplynulý výhradní čas, který běhu profilování se využilo na celkový uplynulý výhradní čas tohoto modulu nebo funkce.|  
|**Průměrný uplynulý výhradní čas**|-Pro určitou funkci průměr uplynulý výhradní čas volání této funkce.<br />-Pro modul průměr uplynulý výhradní čas všechna volání funkce v modulu.|  
|**Maximální uplynulý výhradní čas**|-Pro určitou funkci maximální uplynulý výhradní čas volání této funkce.<br />-Pro modul maximální uplynulý výhradní čas všechna volání funkce v modulu.|  
|**Minimální uplynulý výhradní čas**|-Pro určitou funkci minimální uplynulý výhradní čas volání tohoto modulu nebo funkce.<br />-Pro modul minimální uplynulý výhradní čas všechna volání funkce v modulu.|  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Aplikace (včetně) hodnot označuje datum a čas, který funkce byla v zásobníku volání. Čas nezahrnuje čas, který byl stráven ve volání do operačního systému, například vstupně výstupní operace a přepnutí kontextu. Čas však neobsahuje čas, který byl stráven v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celkový čas aplikace**|-Pro funkci, čas, který byl stráven voláními do funkce. Jedná se o čas, který se využilo na podřízené funkce, ale vynechá volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.<br />-Pro modul, čas, ve kterém byla aspoň jedna funkce v modulu v zásobníku volání. To nezahrnuje čas, který byl stráven voláními do operačního systému.|  
|**% Celkového času aplikace**|Procento celkového uplynulý celkový čas spuštění profilování, která se využilo na celkový čas aplikace tohoto modulu nebo funkce.|  
|**Průměrný celkový čas aplikace**|-Pro funkci, celkový čas průměrná aplikace volání této funkce.<br />-Pro modul, celkový čas průměrná aplikace ze všech volání funkce v modulu.|  
|**Maximální celkový čas aplikace**|-Pro funkci, celkový čas maximální aplikace volání této funkce.<br />-Pro modul, celkový čas maximální aplikace ze všech volání funkce v modulu.|  
|**Minimální celkový čas aplikace**|-Pro funkci, celkový čas minimální aplikace volání tohoto modulu nebo funkce.<br />-Pro modul, celkový čas minimální aplikace ze všech volání funkce v modulu.|  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Výhradní hodnoty, které aplikaci určit čas, který byl stráven v modulu nebo funkce. To nezahrnuje čas, který se využilo na podřízené funkce a také nezahrnuje volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní čas aplikace**|Výhradní čas aplikace celkový počet všech volání do tohoto modulu nebo funkce.|  
|**% Výhradního času aplikace**|Procentuální podíl celkového počtu uplynulý výhradní čas spuštění profilování, který byl stráven v výhradní čas aplikace tohoto modulu nebo funkce.|  
|**Průměrný výhradní čas aplikace**|-Pro funkci v jazyce aplikace průměrný výhradní čas volání této funkce.<br />-Pro modul, průměrná aplikace výhradní čas všechna volání funkce v modulu.|  
|**Maximální výhradní čas aplikace**|-Pro funkci v jazyce aplikace maximální výhradní čas volání této funkce.<br />-Pro modul, výhradní čas aplikace maximální všechna volání funkce v modulu.|  
|**Minimální výhradní čas aplikace**|-Pro funkci v jazyce aplikace minimální výhradní čas volání tohoto modulu nebo funkce.<br />-Pro modul, výhradní čas minimální aplikace ze všech volání funkce v modulu.|  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení modulů](../profiling/modules-view-sampling-data.md)   
 [Zobrazení modulů – instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení modulů – Vzorkování](../profiling/modules-view-dotnet-memory-sampling-data.md)



