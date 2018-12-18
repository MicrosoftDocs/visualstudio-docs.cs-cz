---
title: Zobrazení volající / volaný – Data instrumentace paměti .NET | Dokumentace Microsoftu
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
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf809747bff2146c6a45afd49768dbda69ae7d91
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782281"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Zobrazení volající/volaný – Data instrumentace paměti .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení volající/volaný – data profilace, která byla shromážděna pomocí metody instrumentace paměti .NET zobrazí přidělení a dat časování pro vybranou funkci a funkce nadřazené a podřízené vybrané funkce. Zobrazení volající/volaný obsahuje tři mřížky.  
  
 **Aktuální funkce** se zobrazí v mřížce střední a zobrazuje informace o vybrané funkce profilace sledováním využívání paměti. Hodnoty zahrnují všechny vzorky volání funkce.  
  
 **Funkce, které volaly aktuální funkcí** se zobrazí v hlavní mřížky, a zobrazuje množství hodnota vybranou funkci (aktuální), který byl vygenerován ve volání funkce volajícího (nadřazené).  
  
 **Funkce, které byly volány aktuální funkcí** se zobrazí v mřížce dolů a zobrazuje paměti data profilování pro volaných (podřízený) funkcí z vybrané funkce při podřízené funkce byla volána aktuální funkce.  
  
 Klikněte dvakrát na volající nebo volaný funkce řádku provádět, který řádek aktuální funkce.  
  
## <a name="general"></a>Obecné  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název funkce**|Název funkce.|  
|**Adresa funkce**|Adresa funkce.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Počet volání**|Celkový počet volání provedených touto funkcí.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje funkci.|  
|**ID procesu**|ID procesu spuštění profilování.|  
|**Název procesu**|Název, který je přiřazen k procesu.|  
|**Výhradní čas režie**|Časová náročnost této funkce z důvodu instrumentace. Režie byla odečtena od vylučuje všechny časy.|  
|**Celkový čas režie**|Časová náročnost této funkce a její podřízené funkce z důvodu instrumentace. Test zatížení byla odečtena od fiskálního (včetně).|  
|**Typ**|Kontext funkce:<br /><br /> **0** -aktuální funkce<br /><br /> **1** – funkce, která volá aktuální funkci<br /><br /> **2** – funkce, která volá aktuální funkci<br /><br /> Pouze v [VSPerfReport](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**Název kořenové funkce**|Název aktuální funkce. Pouze v [VSPerfReport](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
  
## <a name="net-memory-allocation-values"></a>Hodnotami přidělení paměti .NET  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní přidělení**|-Pro funkci aktuální počet objektů, které se vytvořily při provádění kódu funkce v těle funkce (to znamená, když funkce byla v horní části zásobníku volání). Číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány touto funkcí.<br />-Pro volající funkci, počet výhradních přidělení aktuální funkce, které byly vytvořeny voláním z této funkce volajícího.<br />-Pro volaných funkce počet objektů, které byly vytvořeny podle instance této funkce, které byly volány aktuální funkcí. Toto číslo nezahrnuje objekty, které byly vytvořeny pomocí funkcí, které byly volány volaných funkcí.|  
|**% Výhradních přidělení**|Procento všech objektů, které byly vytvořeny v profilování, které byly výhradních přidělení této funkce.|  
|**Celkově přidělení**|-Pro aktuální funkci Počet objektů, které byly přiděleny podle funkce při spuštění profilace. Číslo obsahuje objekty, které byly vytvořeny ve volaných funkcí, které byly volány funkce.<br />-Pro volající funkci, počet celkových přidělení aktuální funkce, které byly vytvořeny voláním z této funkce volajícího.<br />-Pro volaných funkce počet objektů, které byly přiděleny instancí této funkce, které byly vytvořeny voláním z aktuální funkce. Obsahuje počet přidělení provedených pomocí funkcí, které byly volány touto funkcí volaných.|  
|**% Celkových přidělení**|Procento všech objektů, které byly vytvořeny v profilování, která se celkově přidělení této funkce.|  
|**Výhradní bajty**|-Pro aktuální funkci Počet bajtů paměti, které byly přiděleny podle funkce při spuštění profilace. Číslo nezahrnuje paměti, který se v volaných funkcí, které byly volány funkce.<br />-Pro volající funkci Počet výhradních bajtů, které byly generovány z aktuální funkce volání touto funkcí volajícího.<br />-Pro volaných funkcí počet bajtů, které byly přiděleny instancí této funkce, které byly vytvořeny voláním z aktuální funkce. Počet bajtů, které byly přiděleny pomocí funkcí, které byly volány funkcí volaných neobsahuje.|  
|**% Výhradních bajtů**|Procento všech počet bajtů paměti, které byly přiděleny v profilování, které byly výhradních přidělení této funkce.|  
|**Celkově bajtů**|-Pro aktuální funkci Počet bajtů v paměti, které byly přiděleny podle funkce při spuštění profilace. Číslo obsahuje paměti, který se ve volaných funkcí, které byly volány funkce.<br />-Pro volající funkci, počet celkových bajtů instance aktuální funkce, které byly vytvořeny podle volání z této funkce volajícího.<br />-Pro volaných funkcí počet bajtů, které byly přiděleny instancí této funkce, které byly vytvořeny voláním z aktuální funkce. Obsahuje počet bajtů, které byly přiděleny pomocí funkcí, které byly volány touto funkcí volaných.|  
|**% Celkových bajtů**|Procento bajtů paměti, které byly přiděleny v profilování, která se celkově přidělení této funkce.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulý včetně hodnoty  
 Uplynulý včetně hodnoty označuje datum a čas, který funkce byla v zásobníku volání. Čas obsahuje čas, který byl stráven v podřízené funkce a volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý celkový čas**|-Pro aktuální funkci čas, který byl vynaložen ve funkci. Hodnota zahrnuje čas, který byl stráven v podřízené funkce a volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.<br />-Pro volající funkce množství uplynulý celkový čas aktuální funkci, která byla vygenerována volání z této funkce volajícího.<br />– Pro volaných funkce doba strávená na této funkci, která byla vygenerována volá aktuální funkci. Hodnota zahrnuje čas, který byl stráven v podřízené funkce a volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.|  
|**% Uplynulého celkového času**|Procento celkového uplynulý celkový čas, který byl stráven v uplynulý celkový čas této funkce v tomto kontextu spuštění profilování.|  
|**Průměrný uplynulý celkový čas**|Průměr uplynulý celkový čas volání této funkce v tomto kontextu.|  
|**Maximální uplynulý celkový čas**|Maximální uplynulý celkový čas volání této funkce v tomto kontextu.|  
|**Minimální uplynulý celkový čas**|Minimální uplynulý celkový čas volání této funkce v tomto kontextu.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulý výhradní hodnoty  
 Uplynulý výhradní hodnoty označuje datum a čas, který funkce byla spuštěna přímo v horní části zásobníku volání. Čas zahrnuje čas ve volání do operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace, ale nezahrnuje čas, který byl stráven v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý výhradní čas**|-Pro aktuální funkci čas, který byl stráven v provádění těla funkce. Hodnota nezahrnuje čas, který se využilo na podřízené funkce, ale obsahuje volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.<br />-Pro volající funkce množství uplynulý výhradní čas aktuální funkci, která byla vygenerována volání z této funkce volajícího.<br />– Pro volaných funkce doba strávená na této funkci, která byla vygenerována volá aktuální funkci. Hodnota nezahrnuje čas, který se využilo na podřízené funkcí volaných funkcí, ale obsahuje volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.|  
|**% Uplynulého výhradního času**|Procento celkového uplynulý výhradní čas, který běhu profilování se využilo na celkový uplynulý výhradní čas této funkce v tomto kontextu.|  
|**Průměrný uplynulý výhradní čas**|Průměr uplynulý výhradní čas volání této funkce v tomto kontextu.|  
|**Maximální uplynulý výhradní čas**|Maximální uplynulý výhradní čas volání této funkce v tomto kontextu.|  
|**Minimální uplynulý výhradní čas**|Minimální uplynulý výhradní čas volání této funkce v tomto kontextu.|  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Aplikace (včetně) hodnot označuje datum a čas, který funkce byla v zásobníku volání. Čas nezahrnuje čas, který byl stráven ve volání do operačního systému, jako jsou přepínače kontextu a vstupně výstupní operace, ale neobsahuje čas, který byl stráven v podřízené funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celkový čas aplikace**|-Pro aktuální funkci čas, který se využilo na funkci a její podřízené funkce. Hodnota nezahrnuje čas, který byl stráven voláními do operačního systému, například vstupně výstupní operace a přepnutí kontextu.<br />-Pro volající funkce množství celkový čas aplikace aktuální funkce, která byla vygenerována volání z této funkce volajícího.<br />-Pro volaných funkce čas, který byl stráven v této funkci a její podřízené funkce, která byla vygenerována volání z aktuální funkce. Hodnota nezahrnuje čas, který byl stráven ve volání do operačního systému, například vstupně výstupní operace a přepnutí kontextu.|  
|**% Celkového času aplikace**|Procento celkového uplynulý celkový čas, který běhu profilování se využilo na celkový čas celkový aplikace této funkce v tomto kontextu.|  
|**Průměrný celkový čas aplikace**|Celkový čas průměrná aplikace volání této funkce v tomto kontextu.|  
|**Maximální celkový čas aplikace**|Celkový čas aplikace maximální volání této funkce v tomto kontextu.|  
|**Minimální celkový čas aplikace**|Celkový čas aplikace minimální volání této funkce v tomto kontextu.|  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Výhradní hodnoty, které aplikaci označuje čas, který byl vynaložen ve funkci, s výjimkou čas, který byl stráven v podřízené funkce. Stanovený čas také nezahrnuje čas, která byla vydaná incalls do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní čas aplikace**|-Pro aktuální funkci čas, který byl stráven v provádění těla funkce. Hodnota nezahrnuje čas, který byl stráven v podřízené funkce ani obsahuje volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.<br />-Pro volající funkce množství výhradní čas aplikace aktuální funkce, která byla vygenerována volání z této funkce volajícího.<br />– Pro volaných funkce doba strávená na této funkci, která byla vygenerována volá aktuální funkci. Hodnota nezahrnuje čas, který byl stráven v podřízené funkcí volaných funkcí ani obsahuje volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.|  
|**% Výhradního času aplikace**|Procento celkového uplynulý výhradní čas, který běhu profilování se využilo na výhradní čas aplikace celkový této funkce v tomto kontextu.|  
|**Průměrný výhradní čas aplikace**|Výhradní čas aplikace průměrné volání této funkce v tomto kontextu.|  
|**Maximální výhradní čas aplikace**|Výhradní čas aplikace maximální volání této funkce v tomto kontextu.|  
|**Minimální výhradní čas aplikace**|Výhradní čas aplikace minimální volání této funkce v tomto kontextu.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení volající/volaný – Data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Zobrazení volající/volaný – Data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)   
 [Volající / volaný zobrazení – vzorkování dat](../profiling/caller-callee-view-sampling-data.md)



