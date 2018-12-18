---
title: Porozumění hodnotám dat instrumentace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 524f6f575725fed754c3873af8a9ff62a3c3686f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477545"
---
# <a name="understand-instrumentation-data-values"></a>Pochopení hodnotám dat instrumentace

*Instrumentace* metoda záznamy v sadě Visual Studio profilace podrobné informace o časování pro volání funkcí, řádky a pokyny v PROFILOVANÉHO aplikaci

Metoda instrumentace vloží kód na začátku a konci funkce cíl v PROFILOVANÉHO binárního souboru a před a po každém volání pomocí těchto funkcí dalších funkcí. Vložený kód zaznamenává následující informace:

- Interval mezi tato událost kolekce a předchozí.

- Operační systém, zda byla provedena operace během intervalu. Například může operační systém pro čtení nebo zápisu na disk nebo přepínač mezi vlákno cíl a jiné vlákno v jiném procesu.

V každém intervalu rekonstruuje analysis profileru zásobníku volání, který se nachází na konci tohoto intervalu. Zásobník volání je seznam funkcí, které jsou aktivní procesoru v bodě v čase. Jenom jednu funkci (funkci current) je provádění kódu; dalších funkcí jsou řetěz volání funkce, která je výsledkem volání funkce aktuální (zásobníku volání).

Pro jednotlivé funkce v zásobníku volání během intervalu zaznamenávání, analýzy profileru přidá intervalu k jedné nebo více hodnot čtyři dat pro funkci. Analýza přidá interval datové hodnoty pro funkci na základě dvou kritérií:

- Jestli interval došlo k chybě v kódu funkce nebo v *podřízené funkce* (funkci, která byla zavolána funkce).

- Jestli událost operačního systému došlo k chybě v intervalu.

Hodnoty dat pro časový interval, rozsahu funkce nebo data jsou pojmenované *uplynulý čas včetně*, *uplynulý výhradní*, *aplikace včetně*, a  *Exkluzivní aplikace*:

- Uplynulý čas včetně hodnotu data jsou přidány všechny intervaly funkce.

- Pokud interval došlo k chybě v kódu funkce a není ve funkci podřízené, interval se přidá do uplynutí výhradní hodnota dat funkce.

- Pokud událost operačního systému se nevyskytla v intervalu, interval se přidá do aplikace včetně hodnotu data.

- Pokud událost operačního systému se nevyskytla v intervalu a interval, došlo k chybě při přímé provádění kódu funkce (to znamená, že ho se nevyskytla ve funkci podřízené), interval se přidá do aplikace výhradní hodnotu data.

Nástroje pro profilaci sestavy agregovat celkové hodnoty funkcí v samotném relace profilování a procesy, vláken a binární soubory relace.

## <a name="elapsed-inclusive-values"></a>Uplynulá (včetně) hodnot

Celkový čas, která byla potřebná k provedení funkce a jeho podřízené funkce.

Uplynulá (včetně) hodnot zahrnují intervalech, které byly potřebná k provedení přímo kód funkce a intervalech, které byly potřebná k provedení funkce podřízené funkce cíl. Funkce nebo jeho podřízené funkce, které obsahují čeká na operační systém intervalů jsou také uvedené v uplynulý čas (včetně) hodnot.

## <a name="elapsed-exclusive-values"></a>Uplynulá výhradní hodnoty

Čas, kdy byla potřebná k provedení funkce, s výjimkou času stráveného v podřízené funkce.

Uplynulá hodnot, které zahrnují intervalech, které byly potřebná k provedení přímo kód funkce, bez ohledu na to, jestli operační systém události došlo k chybě v intervalu. Všechny intervaly věnovaný podřízené funkce, které byly volá funkci cíl nejsou součástí uplynulý výhradní hodnoty.

## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot

Čas, kdy byla potřebná k provedení funkce a jeho podřízené funkce, s výjimkou času stráveného v událostech operačního systému.

Aplikace (včetně) hodnot nezahrnují intervalech, které obsahují události v operačním systému. Aplikace (včetně) hodnot zahrnout všechny ostatní intervalech, které byly potřebná k provedení funkce, bez ohledu na to, jestli interval strávená přímo provádění kódu funkce nebo byl stráven podřízené funkce funkce cíl.

## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace

Čas, kdy byla potřebná k provedení funkce, s výjimkou času stráveného v podřízené funkce a času stráveného v událostech operačního systému.

Aplikace hodnot, které neobsahují intervalech, které obsahují události v operačním systému nebo intervalech, které byly potřebná k provedení funkce, které byly volá funkci. Aplikace hodnot, které zahrnují jenom intervalech, byly potřebná k provedení přímo kód funkce a který neobsahoval událost operačního systému.

## <a name="elapsed-inclusive-percent"></a>Uplynulá v procentech (včetně).

Procento celkové uplynulý čas (včetně) hodnot relace profilování které byly uplynulý čas včetně hodnoty funkce, modulu, vlákno nebo proces.

100 * funkce uplynulý čas včetně / uplynulé relace (včetně).

## <a name="elapsed-exclusive-percent"></a>Uplynulá výhradní procent

Procento celkové uplynulý čas (včetně) hodnot relace profilování které byly uplynulý výhradní hodnoty funkce, modulu, vlákno nebo proces.

100 * funkce uplynulá exkluzivní / uplynulé relace (včetně).

## <a name="application-inclusive-percent"></a>Aplikace v procentech (včetně).

Procento celkové aplikace včetně hodnoty relace profilování které byly aplikace včetně hodnoty funkce, modulu, vlákno nebo proces.

100 * funkce aplikace (včetně) nebo aplikace relace (včetně).

## <a name="application-exclusive-percent"></a>Výhradní procent aplikace

Procento celkové aplikace včetně hodnoty relace profilování které byly funkce, modulu, vlákno nebo proces aplikace výhradní intervalů.

100 * funkce exkluzivní aplikace nebo relace aplikace (včetně).

## <a name="see-also"></a>Viz také:

[Analýza dat nástrojů pro měření výkonu](../profiling/analyzing-performance-tools-data.md)  
[Postupy: Výběr metod shromažďování](../profiling/how-to-choose-collection-methods.md)