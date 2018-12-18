---
title: Porozumění hodnotám dat instrumentace | Dokumentace Microsoftu
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
- Profiling Tools,instrumentation
- instrumentation profiling method
ms.assetid: 2cf94cf9-c317-4a52-bf00-670f1262165e
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aaa94700c22858be5b6a739034715d1bc926eaf9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787936"
---
# <a name="understanding-instrumentation-data-values"></a>Porozumění hodnotám dat instrumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Instrumentace* metodu profilace [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zaznamenává podrobné informace o časování pro volání funkce, řádky a podle pokynů v profilované aplikace  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Metoda instrumentace vkládá kód na začátek a konec cílového funkcí v profilované binární soubor a před a po každé volání těmito funkcemi dalších funkcí. Vložený kód zaznamenává následující:  
  
- Interval mezi předchozí a tato událost kolekce.  
  
- Určuje, zda operační systém byla provedena operace během intervalu. Například operačního systému může číst nebo zapsat na disk nebo přepínače mezi cílovým vláknem a jiné vlákno v jiném procesu.  
  
  **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  V každém intervalu rekonstruuje analýzy profiler zásobníku volání, která byla k dispozici na konci interval. Zásobník volání je seznam funkcí, které jsou aktivní na procesoru v bodě v čase. Jenom jednu funkci (aktuální funkci) spouští kód; ostatní funkce jsou řetěz volání funkce, jejichž výsledkem volání na aktuální funkci (zásobník volání).  
  
  Pro každou funkci v zásobníku volání během intervalu zaznamenávání, profiler analýzy přidá interval do jedné nebo více hodnot čtyři dat pro funkci. Analýza přidá interval na hodnotu data pro funkce na základě dvou kritérií:  
  
- Určuje, zda došlo k v kódu funkce nebo v intervalu *podřízené funkce* (funkce, která byla volána funkce).  
  
- Určuje, zda událost operačního systému došlo k chybě v intervalu.  
  
  Hodnoty dat pro interval rozsah funkce nebo data jsou s názvem *uplynulý včetně*, *uplynulý výhradní*, *aplikace včetně*, a  *Výhradní čas aplikace*:  
  
- Uplynulý včetně hodnotu data jsou přidány všechny intervaly funkce.  
  
- Pokud interval došlo k chybě v kódu funkce a není ve funkci podřízené, interval je přidána do uplynulý výhradní datový typ funkce.  
  
- Pokud nedošlo k události operačního systému v intervalu, interval je přidána do aplikace včetně hodnotu data.  
  
- Pokud událost operačního systému nedošlo k v intervalu a intervalu došlo k přímé provádění kódu funkce (to znamená, ho nedošlo k ve funkci podřízené), interval se přidá do aplikace výhradní hodnoty data.  
  
  Nástroje pro profilaci sestavy shrnují celkové hodnoty funkcí v relaci profilování a procesy, vlákna a binární soubory z relace.  
  
## <a name="elapsed-inclusive-values"></a>Uplynulý včetně hodnoty  
 Celkový čas, který byl stráven spouštěním funkce a její podřízené funkce.  
  
 Uplynulý včetně hodnoty zahrnují intervalů, které se spotřebovávají přímo provádění kódu funkce a intervaly, které byly stráven spouštěním funkce podřízené cílová funkce. Uplynulý včetně hodnoty jsou taky součástí intervalech funkci nebo její podřízené funkce, které zahrnují časový limit na operační systém.  
  
## <a name="elapsed-exclusive-values"></a>Uplynulý výhradní hodnoty  
 Čas, který byl stráven spouštěním funkce, s výjimkou čas, který byl stráven v podřízené funkce.  
  
 Uplynulý výhradní hodnoty zahrnují intervalů, které se spotřebovávají přímo provádění kódu funkce bez ohledu na to, zda došlo k události operačního systému v intervalu. Všechny intervaly stráveného podřízené funkce, které byly volány cílová funkce nejsou součástí uplynulý výhradní hodnoty.  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Čas, který byl stráven spouštěním funkce a její podřízené funkce, s výjimkou čas, který byl stráven v událostí operačního systému.  
  
 Aplikace (včetně) hodnot nezahrnují intervalech, které obsahují událostí operačního systému. Aplikace (včetně) hodnot zahrnout všechny intervaly, které byly stráven spouštěním funkce, bez ohledu na to, zda interval utratilo přímo provádění kódu funkce nebo byl vynaložen na podřízené funkce cílová funkce.  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Čas, který byl stráven spouštěním funkce, s výjimkou čas, který se využilo na podřízené funkce a čas, který byl stráven v událostí operačního systému.  
  
 Výhradní hodnoty, které aplikaci nezahrnují intervalech, které obsahují událostí operačního systému nebo intervaly, které byly strávený spouštěním funkcí, které byly volány funkce. Výhradní hodnoty aplikace zahrnují pouze intervaly, které byly strávený přímo provádění kódu funkce a, která neobsahovala událost operačního systému.  
  
## <a name="elapsed-inclusive-percent"></a>Uplynulý včetně procent  
 Procento z celkového uplynulý včetně hodnot relace profilování, které byly uplynulý včetně hodnoty funkce, modulu, vlákna nebo procesu.  
  
 100 * funkce uplynulý celkový / uplynulý celkový relace  
  
## <a name="elapsed-exclusive-percent"></a>Uplynulý výhradní procent  
 Procento z celkového uplynulý včetně hodnot relace profilování, které byly uplynulý výhradní hodnoty funkce, modulu, vlákna nebo procesu.  
  
 100 * funkce uplynulý výhradní čas / uplynulý celkový relace  
  
## <a name="application-inclusive-percent"></a>Celkové procento aplikace  
 Procento z celkové aplikace (včetně) hodnot relace profilování, které byly aplikace včetně hodnoty funkce, modulu, vlákna nebo procesu.  
  
 100 * funkce aplikace, včetně / relace aplikace (včetně)  
  
## <a name="application-exclusive-percent"></a>Výhradní procent aplikace  
 Procento z celkové aplikace včetně hodnot relace profilování, které byly aplikace exkluzivní intervalech funkce, modulu, vlákna nebo procesu.  
  
 100 * funkce výhradní čas aplikace / aplikace relace (včetně)  
  
## <a name="see-also"></a>Viz také  
 [Analýza výkonu nástrojů pro Data](../profiling/analyzing-performance-tools-data.md)   
 [Postupy: Výběr metod shromažďování](../profiling/how-to-choose-collection-methods.md)



