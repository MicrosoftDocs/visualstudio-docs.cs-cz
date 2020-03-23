---
title: Principy datových hodnot instrumentace | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3dace7b13816c63664ccb4dabfed52d1c5fb7523
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778073"
---
# <a name="understand-instrumentation-data-values"></a>Principy hodnot dat instrumentace

Metoda *instrumentace* profilování Visual Studio zaznamenává podrobné informace o časování pro volání funkce, linky a pokyny v profilované aplikaci

Instrumentace metoda vloží kód na začátku a na konci cílové funkce v profilované binární a před a po každém volání těchto funkcí do jiných funkcí. Vložený kód zaznamenává následující informace:

- Interval mezi touto událostí kolekce a předchozí.

- Zda operační systém provedl operaci během intervalu. Operační systém může například číst nebo zapisovat na disk nebo přepínat mezi cílovým vláknem a jiným vláknem v jiném procesu.

Pro každý interval analýza profileru rekonstruuje zásobník volání, který byl přítomen na konci intervalu. Zásobník volání je seznam funkcí, které jsou aktivní na procesoru v určitém okamžiku. Pouze jedna funkce (aktuální funkce) je provádění kódu; další funkce jsou řetěz volání funkce, které vyústily v volání aktuální funkce (zásobník volání).

Pro každou funkci v zásobníku volání při zaznamenání intervalu přidá analýza profileru interval k jedné nebo více ze čtyř datových hodnot pro funkci. Analýza přidá interval k hodnotě dat pro funkci na základě dvou kritérií:

- Zda k intervalu došlo v kódu funkce nebo v *podřízené funkci* (funkce, která byla volána funkcí).

- Zda došlo k události operačního systému v intervalu.

Hodnoty dat pro interval funkce nebo oblasti dat jsou *pojmenovány Uplynulý včetně*, *Uplynulý výhradní*, *Včetně aplikace*a *Výhradní aplikace*:

- Všechny intervaly funkce jsou přidány do hodnoty dat Uplynulý včetně.

- Pokud došlo k intervalu v kódu funkce a není v podřízené funkce, interval je přidán do elapsed Výhradní data hodnotu funkce.

- Pokud událost operačního systému nedošlo v intervalu, interval je přidán do value Application Inclusive data.

- Pokud událost operačního systému nedošlo v intervalu a interval došlo v přímém spuštění kódu funkce (to znamená, že nedošlo v podřízené funkce), interval je přidán do výhradní hodnota aplikace data.

Profilování Nástroje sestavy agregovat celkové hodnoty funkcí v relaci profilování sám a procesy, vlákna a binární soubory relace.

## <a name="elapsed-inclusive-values"></a>Uplynulé včetně hodnoty

Celkový čas, který byl stráven provádění funkce a její podřízené funkce.

Uplynulé včetně hodnoty zahrnují intervaly, které byly vynaloženy přímo provádění kódu funkce a intervaly, které byly vynaloženy provádění podřízených funkcí cílové funkce. Intervaly funkce nebo její podřízené funkce, které zahrnují čekání na operační systém jsou také zahrnuty v uplynulý včetně hodnoty.

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty

Čas strávený prováděním funkce, s výjimkou času stráveného v podřízených funkcích.

Uplynulé výhradní hodnoty zahrnují intervaly, které byly vynaloženy přímo provádění kódu funkce, bez ohledu na to, zda došlo k události operačního systému v intervalu. Všechny intervaly strávené v podřízených funkcích, které byly volány cílovou funkcí, nejsou zahrnuty v hodnotách Elapsed Exclusive.

## <a name="application-inclusive-values"></a>Včetně aplikace hodnoty

Čas, který byl stráven provádění funkce a její podřízené funkce, s výjimkou času stráveného v událostech operačního systému.

Hodnoty Včetně aplikace nezahrnují intervaly, které obsahují události operačního systému. Hodnoty Application Inclusive zahrnují všechny ostatní intervaly, které byly vynaloženy na provádění funkce, bez ohledu na to, zda byl interval vyčerpán přímo při provádění kódu funkce nebo byl vyčerpán v podřízených funkcích cílové funkce.

## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace

Čas strávený prováděním funkce, s výjimkou času stráveného v podřízených funkcích a času stráveného v událostech operačního systému.

Výhradní hodnoty aplikace nezahrnují intervaly, které obsahují události operačního systému nebo intervaly, které byly vynaloženy provádění funkcí, které byly volány funkce. Výhradní hodnoty aplikace zahrnují pouze intervaly, které byly vynaloženy přímo prováděním kódu funkce a které neobsahovaly událost operačního systému.

## <a name="elapsed-inclusive-percent"></a>Uplynulá včetně procenta

Procento celkových hodnot Uplynulý včetně relace profilování, které byly hodnoty Uplynulý včetně funkce, modulu, vlákna nebo procesu.

100 * Funkce uplynula včetně / Relace uplynula včetně

## <a name="elapsed-exclusive-percent"></a>Uplynulá výhradní procenta

Procento celkových hodnot Uplynulý včetně relace profilování, které byly uplynulými výhradními hodnotami funkce, modulu, vlákna nebo procesu.

100 * Funkce uplynula Exclusive / Relace uplynulo včetně

## <a name="application-inclusive-percent"></a>Včetně procenta aplikace

Procento z celkového počtu aplikačnívčetně hodnoty profilování relace, které byly Application Inclusive hodnoty funkce, modulu, vlákna nebo procesu.

100 * Aplikace funkcí včetně / Relace aplikace včetně

## <a name="application-exclusive-percent"></a>Výhradní procento aplikace

Procento celkových hodnot Včetně aplikace v relaci profilování, které byly výhradními intervaly aplikace funkce, modulu, vlákna nebo procesu.

100 * Funkce aplikace Exclusive / Session Aplikace včetně

## <a name="see-also"></a>Viz také

[Analýza dat](../profiling/analyzing-performance-tools-data.md)
nástrojů výkonu[Postup: Zvolte metody sběru](../profiling/how-to-choose-collection-methods.md)
