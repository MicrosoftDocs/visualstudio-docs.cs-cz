---
title: Zobrazení modulů – data instrumentace | Microsoft Docs
description: Zjistěte, jak zobrazení modulů zobrazuje údaje o výkonu, které jsou seskupeny podle modulů, které byly v datech profilace.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 031068d159b7004b7cfe7fcf1c747c2eb582afc8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879771"
---
# <a name="modules-view---instrumentation-data"></a>Zobrazení modulů – data instrumentace
Zobrazení modulů zobrazuje údaje o výkonu, které jsou seskupeny podle modulů, které byly v datech profilace. Funkce modulu jsou uvedeny pod uzlem modulu.

## <a name="general"></a>Obecné
 Obecné sloupce identifikují funkci v řádku zobrazení.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název funkce nebo modulu.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Number of Calls**|Celkový počet volání, která byla provedena v této funkci nebo modulu.|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu, ve kterém byl spuštěn modul nebo funkce.|
|**Výhradní čas režie testu**|Časová režie této funkce nebo modulu z důvodu instrumentace.|
|**Čas celkové režie testu**|Časová režie této funkce nebo modulu a jejích podřízených funkcí z důvodu instrumentace.|

## <a name="elapsed-inclusive-values"></a>Uplynulé celkové hodnoty
 Uplynulé celkové hodnoty udávají čas, kdy byla funkce v zásobníku volání. Čas zahrnuje čas strávený v podřízených funkcích a v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý celkový čas**|– Pro funkci, čas strávený ve funkci. To zahrnuje čas strávený v podřízených funkcích a v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br />– Pro modul je čas, ve kterém byla alespoň jedna funkce v modulu v zásobníku volání.|
|**% Uplynulého celkového času**|Procento celkového uplynulého celkového času běhu profilace, které bylo stráveno v celkovém uplynulém časovém intervalu tohoto modulu nebo funkce.|
|**Průměrný uplynulý celkový čas**|– Pro funkci Průměrná uplynulá celková doba volání této funkce.<br />– Pro modul byl průměrný uplynulý celkový čas všech volání funkcí v modulu.|
|**Maximální uplynulý celkový čas**|– Pro funkci maximální uplynulý celkový čas volání této funkce.<br />– Pro modul, maximální uplynulý celkový čas všech volání funkcí v modulu.|
|**Minimální uplynulý celkový čas**|– Pro funkci, minimální uplynulý celkový čas volání tohoto modulu nebo funkce.<br />– Pro modul, minimální uplynulý celkový čas všech volání funkcí v modulu.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé exkluzivní hodnoty označují čas, kdy byla funkce přímo spuštěna v horní části zásobníku volání. Čas zahrnuje čas strávený v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace, ale nezahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý výhradní čas**|– Pro funkci, čas strávený modulem nebo funkcí. To zahrnuje volání do operačního systému, jako jsou přepínače kontextu a vstupně-výstupní operace, ale vyloučí čas strávený v podřízených funkcích.<br />– Pro modul součet uplynulých výhradních časů funkcí v modulu.|
|**% Uplynulého výhradního času**|Procento celkového uplynulého výhradního času pro spuštění profilování, které bylo stráveno celkovým uplynulým výhradním časem tohoto modulu nebo funkce.|
|**Průměrný uplynulý výhradní čas**|– Pro funkci průměrný uplynulý výhradní čas volání této funkce.<br />– Pro modul průměrný uplynulý výhradní čas všech volání funkcí v modulu.|
|**Maximální uplynulý výhradní čas**|– Pro funkci maximální uplynulý výhradní čas volání této funkce.<br />– Pro modul je maximální uplynulý výhradní čas všech volání funkcí v modulu.|
|**Minimální uplynulý výhradní čas**|– Pro funkci byl minimální uplynulý výhradní čas volání tohoto modulu nebo funkce.<br />– Pro modul byl minimální uplynulý výhradní čas všech volání funkcí v modulu.|

## <a name="application-inclusive-values"></a>Hodnoty zahrnující aplikace
 Hodnoty pro všechny aplikace označují čas, kdy byla funkce v zásobníku volání. Čas neobsahuje čas strávený voláním operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace. Nicméně čas obsahuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Celková doba aplikace**|– Pro funkci, čas strávený voláním funkce. To zahrnuje čas strávený v podřízených funkcích, ale vyloučí volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br />– Pro modul je čas, ve kterém byla alespoň jedna funkce v modulu v zásobníku volání. Tím se nevylučuje čas strávený voláním do operačního systému.|
|**% Celkového času aplikace**|Procento celkového uplynulého celkového času běhu profilace, které bylo stráveno v celkovém čase tohoto modulu nebo funkce.|
|**Průměrná doba aplikace (celková)**|– Pro funkci představuje Průměrná doba, jakou aplikace volá tuto funkci.<br />– Pro modul vypočítá Průměrná doba použití všech volání funkcí v modulu.|
|**Maximální celková doba aplikace**|– Pro funkci je to maximální doba volání této funkce (včetně).<br />– Pro modul je maximální doba všech volání funkcí v modulu (celková) aplikace.|
|**Minimální celková doba aplikace**|– Pro funkci je to minimální čas pro volání tohoto modulu nebo funkce.<br />– Pro modul, minimální dobu všech volání funkcí v modulu, což je celková doba aplikace.|

## <a name="application-exclusive-values"></a>Exkluzivní hodnoty aplikací
 Hodnoty exkluzivní pro aplikace udávají čas strávený modulem nebo funkcí. To vylučuje čas strávený v podřízených funkcích a také vyloučí volání operačního systému, jako jsou přepínače kontextu a vstupně-výstupní operace.

|Sloupec|Popis|
|------------|-----------------|
|**Výhradní čas aplikace**|Celková celková doba aplikace všech volání tohoto modulu nebo funkce.|
|**% Výhradního času aplikace**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo stráveno v exkluzivním čase aplikace tohoto modulu nebo funkce.|
|**Průměrný výhradní čas aplikace**|– Pro funkci představuje Průměrná doba aplikace výhradní čas volání této funkce.<br />– Pro modul vyhledá Průměrná doba aplikace výhradní čas všech volání funkcí v modulu.|
|**Maximální výhradní čas aplikace**|– Pro funkci je maximální doba aplikace při volání této funkce.<br />– Pro modul je maximální doba aplikace exkluzivní pro všechna volání funkcí v modulu.|
|**Minimální výhradní čas aplikace**|– Pro funkci minimální výhradní čas aplikace pro volání tohoto modulu nebo funkce.<br />– Pro modul, minimální výhradní čas aplikace pro všechna volání funkcí v modulu.|

## <a name="see-also"></a>Viz také
- [Zobrazení modulů](../profiling/modules-view-sampling-data.md)
- [Zobrazení modulů – instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení modulů – vzorkování](../profiling/modules-view-dotnet-memory-sampling-data.md)
