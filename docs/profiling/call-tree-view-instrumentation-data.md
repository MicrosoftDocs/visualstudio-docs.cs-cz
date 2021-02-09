---
title: Zobrazení stromu volání – data instrumentace | Microsoft Docs
description: Přečtěte si, jak zobrazení stromu volání zobrazuje informace o instrumentaci ve stromu volání v Prohlížeč výkonu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 815c6c0fc3eec3678f878e081d76c95cb7e8fc78
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860838"
---
# <a name="call-tree-view---instrumentation-data"></a>Zobrazení stromu volání – data instrumentace
Hodnoty pro funkci ve stromu volání označují čas pro instance funkce, které byly volány nadřazenou funkcí ve stromu volání. Procentuální hodnoty se vypočtou porovnáním hodnoty instancí funkcí s celkovým celkovým počtem uplynulých úplných funkcí v průběhu profilace.

## <a name="general"></a>Obecné
 Obecné sloupce identifikují funkci v řádku zobrazení.

|Sloupec|Popis|
|------------|-----------------|
|**Název funkce**|Název funkce|
|**Adresa funkce**|Adresa funkce|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Number of Calls**|Celkový počet volání, která byla provedena u této funkce.|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název, který je přiřazen procesu.|
|**Výhradní čas režie testu**|Časová režie této funkce, která byla způsobena instrumentací. Režie testu byla odečtena od všech výhradních časů.|
|**Čas celkové režie testu**|Časová režie této funkce a jejích podřízených funkcí, které byly způsobeny instrumentací. Režie testu byla odečtena od všech celkových časů.|
|**Obsah**|Hloubka funkce ve stromu volání. Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|

## <a name="elapsed-inclusive-values"></a>Uplynulé celkové hodnoty
 Uplynulé celkové hodnoty udávají čas v zásobníku volání těch instancí funkce, které byly volány nadřazenou funkcí ve stromu volání. Čas zahrnuje čas strávený v podřízených funkcích, které byly volány funkcí a v voláních do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý celkový čas**|Celkový uplynulý celkový čas všech volání této funkce v tomto kontextu.|
|**% Uplynulého celkového času**|Procento celkového uplynulého celkového času běhu profilace, které bylo v tomto kontextu stráveno celkovým uplynulým časem této funkce.|
|**Průměrný uplynulý celkový čas**|Průměrný uplynulý celkový čas volání této funkce v tomto kontextu.|
|**Maximální uplynulý celkový čas**|Maximální uplynulý celková doba volání této funkce v tomto kontextu.|
|**Minimální uplynulý celkový čas**|Minimální uplynulý celkový čas volání této funkce v tomto kontextu.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé exkluzivní hodnoty označují čas, kdy tyto instance funkce, které byly volány nadřazenou funkcí ve stromu volání, prováděly kód v těle funkce; To znamená, že pokud byla funkce v horní části zásobníku volání. Čas zahrnuje čas volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace. Čas však neobsahuje čas, který byl stráven v podřízených funkcích, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý výhradní čas**|Celkový uplynulý výhradní čas všech volání této funkce v tomto kontextu.|
|**% Uplynulého výhradního času**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo v tomto kontextu stráveno celkovým neúplným časem této funkce.|
|**Průměrný uplynulý výhradní čas**|Průměrný uplynulý výhradní čas volání této funkce v tomto kontextu.|
|**Maximální uplynulý výhradní čas**|Maximální uplynulý výhradní čas volání této funkce v tomto kontextu.|
|**Minimální uplynulý výhradní čas**|Minimální uplynulý výhradní čas volání této funkce v tomto kontextu.|

## <a name="application-inclusive-values"></a>Hodnoty zahrnující aplikace
 Hodnoty zahrnující aplikace označují čas, kdy instance funkce, které byly volány nadřazenou funkcí ve stromu volání, byly v zásobníku volání. Čas nezahrnuje čas strávený voláním operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace, ale čas zahrnuje čas strávený v podřízených funkcích, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Celková doba aplikace**|Celková celková doba všech volání této funkce v tomto kontextu aplikace|
|**% Celkového času aplikace**|Procento celkového uplynulého celkového času běhu profilace, které bylo v tomto kontextu stráveno v celkovém čase aplikace této funkce.|
|**Průměrná doba aplikace (celková)**|Průměrná doba použití volání této funkce v tomto kontextu.|
|**Maximální celková doba aplikace**|Maximální doba volání této funkce v tomto kontextu (včetně celkového počtu aplikací).|
|**Minimální celková doba aplikace**|Minimální doba trvání volání této funkce v tomto kontextu (včetně celkového počtu aplikací).|

## <a name="application-exclusive-values"></a>Exkluzivní hodnoty aplikací
 Hodnoty exkluzivní pro aplikace označují dobu, po kterou tyto instance funkce, které byly volány nadřazenou funkcí ve stromu volání, přímo spouštějí kód v těle funkce; To znamená, že pokud byla funkce v horní části zásobníku volání. Čas neobsahuje čas strávený voláním operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace. Nezahrnuje také čas strávený v podřízených funkcích, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Výhradní čas aplikace**|Celková celková doba aplikace pro všechna volání této funkce v tomto kontextu.|
|**% Výhradního času aplikace**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo v tomto kontextu stráveno v celkovém čase aplikace této funkce.|
|**Průměrný výhradní čas aplikace**|Průměrná doba použití pro volání této funkce v tomto kontextu.|
|**Maximální výhradní čas aplikace**|Maximální výhradní čas aplikace pro volání této funkce v tomto kontextu.|
|**Minimální výhradní čas aplikace**|Minimální výhradní čas aplikace pro volání této funkce v tomto kontextu.|

## <a name="see-also"></a>Viz také
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)
- [Zobrazení stromu volání – instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení stromu volání – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
