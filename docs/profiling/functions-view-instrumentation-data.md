---
title: Zobrazení funkcí - Data instrumentace | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 423b6d61af93c37e6fa83549ed3fa5d422128165
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779217"
---
# <a name="functions-view---instrumentation-data"></a>Zobrazení funkcí - data instrumentace
Sestava Funkce obsahuje seznam dat profilování podle názvu funkce.

## <a name="general"></a>Obecné
 Obecné sloupce identifikují funkci v řádku zobrazení.

|Sloupec|Popis|
|------------|-----------------|
|**Název funkce**|Název funkce.|
|**Adresa funkce**|Adresa funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Number of Calls**|Celkový počet volání, které jsou provedeny do této funkce.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Režie výhradní sondy času**|Čas režie pro tuto funkci, která je způsobena instrumentace. Nezahrnuje režii ve funkcích, které byly volány funkcí. Režie sondy byla odečtena od všech výhradních časů.|
|**Režie sondy včetně času**|Čas režie pro tuto funkci a její podřízené funkce, která je způsobena instrumentace. Zahrnuje režii ve funkcích, které byly volány funkcí. Režie sondy byla odečtena od all inclusive časů.|

## <a name="elapsed-inclusive-values"></a>Uplynulé včetně hodnot
 Uplynulé včetně hodnoty označují čas, který byla funkce v zásobníku volání. Čas zahrnuje čas strávený ve funkcích, které byly volány funkcí a čas, který byl stráven voláním operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý včetně času**|Celkový uplynulý včetně času všech volání této funkce.|
|**Uplynulý včetně času %**|Procento celkového uplynulého včetně času profilování, který byl stráven v uplynulém včetně času této funkce.|
|**Avg Uplynulý včetně čas**|Průměrná uplynulá doba volání této funkce.|
|**Maximální uplynulý včetně času**|Maximální uplynulý včetně čas volání této funkce.|
|**Min uplynulý včetně času**|Minimální uplynulý včetně čas volání této funkce.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé výhradní hodnoty označují čas, kdy funkce prováděla kód v těle funkce, tj. Čas zahrnuje čas strávený volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale nezahrnuje čas strávený ve funkcích, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý exkluzivní čas**|Celkový uplynulý výhradní čas všech volání této funkce.|
|**Uplynulý výhradní čas %**|Procento celkového uplynulého výhradního času profilování, který byl stráven v celkovém uplynulém výhradním čase této funkce.|
|**Avg uplynulý exkluzivní čas**|Průměrná uplynulá výhradní doba volání této funkce.|
|**Maximální uplynulý exkluzivní čas**|Maximální uplynulý výhradní čas volání této funkce.|
|**Min uplynulý exkluzivní čas**|Minimální uplynulý výhradní čas volání této funkce.|

## <a name="application-inclusive-values"></a>Včetně hodnot aplikace
 Hodnoty zahrnující aplikaci označují čas, kdy byla funkce v zásobníku volání. Čas nezahrnuje čas strávený voláníoperačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale zahrnuje čas strávený ve funkcích, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Včetně aplikace**|Celkový čas aplikace včetně všech volání této funkce.|
|**Včetně aplikace Čas %**|Procento celkového uplynulého včetně času spuštění profilování, který byl vynaložen v celkové aplikaci včetně času této funkce.|
|**Avg Aplikace včetně času**|Průměrná doba aplikace včetně volání této funkce.|
|**Maximální čas včetně aplikace**|Maximální doba aplikace včetně volání této funkce.|
|**Min aplikace včetně času**|Minimální doba aplikace včetně volání této funkce.|

## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace
 Výhradní hodnoty aplikace označují čas, kdy byla funkce přímo spuštěna v horní části zásobníku volání. Čas nezahrnuje čas strávený voláníoperačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu a nezahrnuje čas strávený ve funkcích, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní čas aplikace**|Celkový výhradní čas aplikace všech volání této funkce.|
|**Výhradní čas aplikace %**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo vynaloženo v celkovém výhradním čase aplikace této funkce.|
|**Exkluzivní čas aplikace AVG**|Průměrná aplikace výhradní čas volání této funkce.|
|**Maximální exkluzivní čas aplikace**|Maximální výhradní čas aplikace volání této funkce.|
|**Min aplikace Exkluzivní čas**|Minimální výhradní čas aplikace volání této funkce.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení funkcí](../profiling/functions-view-sampling-data.md)
- [Zobrazení funkcí - vzorkování](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Zobrazení funkcí - instrumentace](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
