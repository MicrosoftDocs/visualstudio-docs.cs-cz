---
title: Zobrazení modulů – Data instrumentace paměti .NET | Dokumentace Microsoftu
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
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85024296eff4fb4d26b3a588217a1e6fe5221d3e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755394"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Zobrazení modulů – data instrumentace paměti .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Moduly přehled shromážděných pomocí metody instrumentace data přidělení paměti .NET seskupí podle moduly, které byly spuštěny během spuštění profilování paměti a data časování. Data profilování pro funkce v modulu je uvedena pod uzel modulu.  
  
## <a name="general"></a>Obecné  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název funkce nebo modulu.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Počet volání**|Celkový počet volání, které byly provedeny této funkce nebo modulu.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje funkci.|  
|**ID procesu**|ID procesu (PID) běhu profilování.|  
|**Název procesu**|Název procesu, ve kterém byla spuštěna modulu nebo funkce.|  
|**Výhradní čas režie**|Časová náročnost této funkce nebo modulu kvůli instrumentace.|  
|**Celkový čas režie**|Časová náročnost této funkce nebo modulu a její podřízené funkce z důvodu instrumentace.|  
  
## <a name="net-memory-values"></a>Hodnoty paměti .NET  
 (Včetně) hodnot paměti .NET funkce označují číslo (přidělení) a velikost (bajty) objektů, které byly vytvořeny tak, že funkce a její podřízené funkce.  
  
 Výhradní paměti hodnoty označují, počtu a velikosti objektů, které byly vytvořeny, funkce a ne její podřízené funkce.  
  
 Paměť zahrnuté a výhradní hodnoty modulu jsou součet celkové a výhradní paměti hodnoty funkce v modulu.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celkově přidělení**|-Pro funkci, celkový počet objektů, které se vytvořily ve funkci. Toto číslo zahrnuje objekty, které byly vytvořeny pomocí funkcí, které byly volány funkce.<br />-Pro modul počet objektů v profilování, které byly přiděleny při provádění funkce alespoň jeden z modulu. Toto číslo zahrnuje objekty, které byly přiděleny ve funkcích, které byly vytvořeny podle volání z funkce modulu.|  
|**% Celkových přidělení**|Procento všech objektů, které byly přiděleny v profilování, která se celkově přidělení modulu nebo funkce.|  
|**Výhradní přidělení**|-Pro určitou funkci, počet objektů, které se vytvořily při provádění kódu funkce v těle funkce (to znamená, když funkce byla v horní části zásobníku volání). Toto číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány funkce.<br />-Pro modul, součet výhradních přidělení funkce v modulu.|  
|**% Výhradních přidělení**|Procento všech objektů, které byly přiděleny v profilování, které byly výhradních přidělení modulu nebo funkce.|  
|**Výhradní bajty**|-Pro určitou funkci celkový počet bajtů paměti, které byly přiděleny při provádění funkce kód ve funkci textu (to znamená, když funkce byla v horní části zásobníku volání). Toto číslo nezahrnuje bajtů, které byly přiděleny ve funkcích, které byly volány funkce.<br />-Pro modul, součet výhradních bajtů, které byly přiděleny pomocí funkcí v modulu.|  
|**% Výhradních bajtů**|Procento všech bajtů, které byly přiděleny v profilování, které byly výhradních bajtů modulu, funkce, řádek nebo instrukci.|  
|**Celkově bajtů**|-Pro funkci, počet bajtů, které byly přiděleny funkcí. Toto číslo zahrnuje bajtů, které byly přiděleny ve funkcích, které byly volány funkce.<br />-Pro modul počet bajtů, které byly přiděleny v profilování, které byly přiděleny při provádění funkce alespoň jeden z modulu. Toto číslo zahrnuje objekty, které byly vytvořeny ve všech funkcí, které byly volány funkce modulu.|  
|**% Celkových bajtů**|Procento všech bajtů, které byly přiděleny v profilování, která se celkově bajtů modulu nebo funkce.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulý včetně hodnoty  
 Uplynulý včetně hodnoty označuje datum a čas, který funkce byla v zásobníku volání. Čas obsahuje čas, který byl stráven v podřízené funkce a volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý celkový čas**|-Pro funkci, čas, který byl vynaložen ve funkci. To zahrnuje čas, který byl stráven v podřízené funkce a volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.<br />-Pro modul, doba, ve kterém byla aspoň jedna funkce v modulu v zásobníku volání.|  
|**% Uplynulého celkového času**|Procento celkového uplynulý celkový čas, který běhu profilování se využilo na celkový uplynulý celkový čas tohoto modulu nebo funkce.|  
|**Průměrný uplynulý celkový čas**|-Pro určitou funkci průměr uplynulý celkový čas volání této funkce.<br />-Pro modul průměr uplynulý celkový čas všechna volání funkce v modulu.|  
|**Maximální uplynulý celkový čas**|-Pro určitou funkci maximální uplynulý celkový čas volání této funkce.<br />-Pro modul maximální uplynulý celkový čas všechna volání funkce v modulu.|  
|**Minimální uplynulý celkový čas**|-Pro určitou funkci minimální uplynulý celkový čas volání tohoto modulu nebo funkce.<br />-Pro modul minimální uplynulý celkový čas všechna volání funkce v modulu.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulý výhradní hodnoty  
 Uplynulý výhradní hodnoty označuje datum a čas, který funkce byla spuštěna přímo v horní části zásobníku volání. Čas zahrnuje čas ve volání do operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace, ale nezahrnuje čas, který byl stráven v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý výhradní čas**|-Pro funkci, čas, který byl stráven v modulu nebo funkce. To zahrnuje volání do operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace, ale nezahrnuje čas, který byl stráven v podřízené funkce.<br />-Pro modul součet uplynulý výhradní čas funkce v modulu.|  
|**% Uplynulého výhradního času**|Procento celkového uplynulý výhradní čas, který běhu profilování se využilo na celkový uplynulý výhradní čas tohoto modulu nebo funkce.|  
|**Průměrný uplynulý výhradní čas**|-Pro určitou funkci průměr uplynulý výhradní čas volání této funkce.<br />-Pro modul průměr uplynulý výhradní čas všechna volání funkce v modulu.|  
|**Maximální uplynulý výhradní čas**|-Pro určitou funkci maximální uplynulý výhradní čas volání této funkce.<br />-Pro modul maximální uplynulý výhradní čas všechna volání funkce v modulu.|  
|**Minimální uplynulý výhradní čas**|-Pro určitou funkci minimální uplynulý výhradní čas volání tohoto modulu nebo funkce.<br />-Pro modul minimální uplynulý výhradní čas všechna volání funkce v modulu.|  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Aplikace (včetně) hodnot označuje datum a čas, který funkce byla v zásobníku volání. Čas nezahrnuje čas, který byl stráven ve volání do operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace, ale neobsahuje čas, který byl stráven v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celkový čas aplikace**|-Pro funkci, čas, který byl stráven voláními do funkce. Jedná se o čas, který se využilo na podřízené funkce, ale vynechá volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.<br />-Pro modul, doba, ve kterém byla aspoň jedna funkce v modulu v zásobníku volání, kromě času, který byl stráven voláními do operačního systému.|  
|**% Celkového času aplikace**|Procento celkového uplynulý celkový čas spuštění profilování, která se využilo na celkový čas aplikace tohoto modulu nebo funkce.|  
|**Průměrný celkový čas aplikace**|-Pro funkci, celkový čas průměrná aplikace volání této funkce.<br />-Pro modul, celkový čas průměrná aplikace ze všech volání funkce v modulu.|  
|**Maximální celkový čas aplikace**|-Pro funkci, celkový čas maximální aplikace volání této funkce.<br />-Pro modul, celkový čas maximální aplikace ze všech volání funkce v modulu.|  
|**Minimální celkový čas aplikace**|-Pro funkci, celkový čas minimální aplikace volání tohoto modulu nebo funkce.<br />-Pro modul, celkový čas minimální aplikace ze všech volání funkce v modulu.|  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Výhradní hodnoty, které aplikaci označuje čas, který byl stráven v modulu nebo funkce, s výjimkou čas, který byl stráven v podřízené funkce. Volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu vylučuje stanovený čas.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní čas aplikace**|-Pro funkci, výhradní čas aplikace celkový počet volání této funkce.<br />-Pro modul, výhradní čas aplikace celkový počet všech volání funkce v modulu.|  
|**% Výhradního času aplikace**|Procentuální podíl celkového počtu uplynulý výhradní čas spuštění profilování, který byl stráven v výhradní čas aplikace tohoto modulu nebo funkce.|  
|**Průměrný výhradní čas aplikace**|-Pro funkci v jazyce aplikace průměrný výhradní čas volání této funkce.<br />-Pro modul, průměrná aplikace výhradní čas všechna volání funkce v modulu.|  
|**Maximální výhradní čas aplikace**|-Pro funkci v jazyce aplikace maximální výhradní čas volání této funkce.<br />-Pro modul, výhradní čas aplikace maximální všechna volání funkce v modulu.|  
|**Minimální výhradní čas aplikace**|-Pro funkci v jazyce aplikace minimální výhradní čas volání tohoto modulu nebo funkce.<br />-Pro modul, výhradní čas minimální aplikace ze všech volání funkce v modulu.|  
  
## <a name="see-also"></a>Viz také  
 [Moduly zobrazení – vzorkování](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)   
 [Zobrazení modulů](../profiling/modules-view-sampling-data.md)



