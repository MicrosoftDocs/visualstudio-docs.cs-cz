---
title: Porozumění hodnotám dat instrumentace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
ms.assetid: 2cf94cf9-c317-4a52-bf00-670f1262165e
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 703d80da623c4fdb72328565513c6debe80447d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145477"
---
# <a name="understanding-instrumentation-data-values"></a>Porozumění hodnotám dat instrumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metoda profilace *instrumentace* [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] záznamů podrobné informace o časování pro volání funkce, řádky a pokyny v profilované aplikaci  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Metoda instrumentace vloží kód na začátek a konec cílových funkcí v profilované binární verzi a před a po každém volání těmito funkcemi do jiných funkcí. Vložený kód zaznamená následující:  
  
- Interval mezi touto událostí kolekce a předchozí.  
  
- Zda operační systém provedl během intervalu operaci. Operační systém může například číst nebo zapisovat na disk nebo přepínat mezi cílovým vláknem a jiným vláknem v jiném procesu.  
  
  **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Pro každý interval analyzuje Profiler zásobník volání, který byl přítomen na konci intervalu. Zásobník volání je seznam funkcí, které jsou aktivní v procesorech v určitém časovém okamžiku. Pouze jedna funkce (aktuální funkce) spouští kód; Ostatní funkce jsou řetězcem volání funkcí, jejichž výsledkem je volání aktuální funkce (zásobník volání).  
  
  Pro každou funkci v zásobníku volání, když byl interval zaznamenán, analyzuje Profiler interval do jedné nebo více čtyř hodnot dat pro funkci. Analýza přidá interval k hodnotě dat pro funkci na základě dvou kritérií:  
  
- Zda došlo k intervalu v kódu funkce nebo v *podřízené funkci* (funkce, která byla volána funkcí).  
  
- Určuje, zda došlo k události operačního systému v intervalu.  
  
  Hodnoty dat pro interval funkce nebo rozsahu dat se nazývají *uplynulé včetně*, *uplynulé: exkluzivní*, *aplikace včetně*a *exkluzivní aplikace*:  
  
- Všechny intervaly funkce jsou přidány do hodnoty uplynulá celková data.  
  
- Pokud k intervalu došlo v kódu funkce a nikoli v podřízené funkci, je interval přidán do hodnoty uplynulé exkluzivní datové hodnoty funkce.  
  
- Pokud se v intervalu nevyskytla událost operačního systému, přidá se do hodnoty Celková hodnota dat aplikace.  
  
- Pokud v intervalu nedošlo k události operačního systému a k intervalu, který byl proveden při přímém provádění kódu funkce (to znamená, že se nevyskytla v podřízené funkci), je interval přidán do hodnoty exkluzivní data aplikace.  
  
  Nástroje pro profilaci sestavy agreguje celkové hodnoty funkcí v samotné relaci profilace a procesy, vlákna a binární soubory relace.  
  
## <a name="elapsed-inclusive-values"></a>Uplynulé celkové hodnoty  
 Celkový čas strávený prováděním funkce a jejích podřízených funkcí.  
  
 Uplynulé zahrnuté hodnoty zahrnují intervaly, které strávily přímým spuštěním kódu funkce a intervaly strávené prováděním podřízených funkcí cílové funkce. Do uplynulých celkových hodnot patří i intervaly funkce nebo jejích podřízených funkcí, které zahrnují čekání na operační systém.  
  
## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty  
 Čas strávený prováděním funkce s výjimkou času stráveného v podřízených funkcích.  
  
 Uplynulé exkluzivní hodnoty zahrnují intervaly, které strávily přímým spuštěním kódu funkce bez ohledu na to, zda v intervalu došlo k události operačního systému. Všechny intervaly strávené podřízenými funkcemi, které byly volány cílovou funkcí, nejsou zahrnuty v uplynulých výhradních hodnotách.  
  
## <a name="application-inclusive-values"></a>Hodnoty zahrnující aplikace  
 Čas strávený prováděním funkce a jejích podřízených funkcí s výjimkou času stráveného událostmi operačního systému.  
  
 Hodnoty zahrnující aplikace neobsahují intervaly, které obsahují události operačního systému. Mezi zahrnuté hodnoty aplikací patří všechny ostatní intervaly, které strávily provádění funkce bez ohledu na to, zda byl interval stráven přímo spuštěným kódem funkce nebo byl vyčerpán v podřízených funkcích cílové funkce.  
  
## <a name="application-exclusive-values"></a>Exkluzivní hodnoty aplikací  
 Čas strávený spouštěním funkce s výjimkou času stráveného v podřízených funkcích a času stráveného v událostech operačního systému.  
  
 Hodnoty exkluzivní pro aplikace nezahrnují intervaly, které obsahují události a intervaly operačního systému, které strávily spouštění funkcí volaných funkcí. Hodnoty exkluzivní pro aplikace zahrnují pouze intervaly, které strávily přímým spuštěním kódu funkce a které neobsahovaly událost operačního systému.  
  
## <a name="elapsed-inclusive-percent"></a>Uplynulé celkové procento  
 Procentuální podíl celkového počtu uplynulých zahrnutých hodnot relace profilování, u nichž došlo k Uplynulosti, včetně hodnot funkce, modulu, vlákna nebo procesu.  
  
 100 * uplynulá celková hodnota funkce nebo uplynulá relace (včetně)  
  
## <a name="elapsed-exclusive-percent"></a>Uplynulé výhradní procento  
 Procentuální podíl celkového počtu uplynulých zahrnutých hodnot relace profilování, které uplynuly výhradně hodnoty funkce, modulu, vlákna nebo procesu.  
  
 100 * funkce uplynulá exkluzivní/relace uplynula (včetně)  
  
## <a name="application-inclusive-percent"></a>Celkové procento aplikací  
 Procentuální podíl celkových hodnot zahrnutých v rámci relace profilace, které byly hodnotami aplikace, modulu, vlákna nebo procesu.  
  
 100 * celková aplikace Functions (včetně) včetně aplikace v relaci  
  
## <a name="application-exclusive-percent"></a>Výhradní procento aplikace  
 Procentuální podíl celkových hodnot aplikace v relaci profilace, které byly výhradními intervaly aplikace, modulu, vlákna nebo procesu.  
  
 100 * aplikace Function exkluzivní/relace (včetně)  
  
## <a name="see-also"></a>Viz také  
 [Analýza dat nástrojů výkonu](../profiling/analyzing-performance-tools-data.md)   
 [Postupy: Výběr metod shromažďování](../profiling/how-to-choose-collection-methods.md)
