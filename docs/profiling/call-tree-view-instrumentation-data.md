---
title: Zobrazení stromu volání – data instrumentace | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7497f455ad3868f53758555aa28d305b6068e30d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773508"
---
# <a name="call-tree-view---instrumentation-data"></a>Zobrazení stromu volání – data instrumentace
Hodnoty funkce ve stromu volání označují čas pro instance funkce, které byly volány nadřazenou funkcí ve stromu volání. Procentuální hodnoty jsou vypočteny porovnáním hodnoty instancí funkce s celkovým uplynulým časem včetně všech funkcí v profilování spustit.

## <a name="general"></a>Obecné
 Obecné sloupce identifikují funkci v řádku zobrazení.

|Sloupec|Popis|
|------------|-----------------|
|**Název funkce**|Název funkce.|
|**Adresa funkce**|Adresa funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Number of Calls**|Celkový počet volání, které byly provedeny do této funkce.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název, který je přiřazen k procesu.|
|**Režie výhradní sondy času**|Čas režie pro tuto funkci, která byla způsobena instrumentace. Režie sondy byla odečtena od všech výhradních časů.|
|**Režie sondy včetně času**|Čas režie pro tuto funkci a její podřízené funkce, která byla způsobena instrumentace. Režie sondy byla odečtena od all inclusive časů.|
|**Úroveň**|Hloubka funkce ve stromu volání. Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|

## <a name="elapsed-inclusive-values"></a>Uplynulé včetně hodnot
 Uplynulé včetně hodnoty označují čas na zásobníku volání těchto instancí funkce, které byly volány nadřazené funkce ve stromu volání. Čas zahrnuje čas strávený v podřízených funkcích, které byly volány funkcí a voláním operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý včetně času**|Celkový uplynulý včetně čas všech volání této funkce v tomto kontextu.|
|**Uplynulý včetně času %**|Procento celkového uplynulého včetně času profilování, který byl vyčerpán v celkovém uplynulém včetně času této funkce v tomto kontextu.|
|**Avg Uplynulý včetně čas**|Průměrná uplynulá včetně čas volání této funkce v tomto kontextu.|
|**Maximální uplynulý včetně času**|Maximální uplynulý včetně čas volání této funkce v tomto kontextu.|
|**Min uplynulý včetně času**|Minimální uplynulý včetně čas volání této funkce v tomto kontextu.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé výhradní hodnoty označují čas, po který tyto instance funkce, které byly volány nadřazenou funkcí ve stromu volání, prováděly kód v těle funkce; to znamená, když byla funkce v horní části zásobníku volání. Čas zahrnuje čas ve volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu. Čas však nezahrnuje čas strávený v podřízených funkcích, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý exkluzivní čas**|Celkový uplynulý výhradní čas všech volání této funkce v tomto kontextu.|
|**Uplynulý výhradní čas %**|Procento celkového uplynulého výhradního času spuštění profilování, který byl vyčerpán v celkovém uplynulém výhradním čase této funkce v tomto kontextu.|
|**Avg uplynulý exkluzivní čas**|Průměrná uplynulá výhradní doba volání této funkce v tomto kontextu.|
|**Maximální uplynulý exkluzivní čas**|Maximální uplynulý výhradní čas volání této funkce v tomto kontextu.|
|**Min uplynulý exkluzivní čas**|Minimální uplynulý výhradní čas volání této funkce v tomto kontextu.|

## <a name="application-inclusive-values"></a>Včetně hodnot aplikace
 Hodnoty zahrnující aplikaci označují čas, kdy instance funkce, které byly volány nadřazenou funkcí ve stromu volání, byly v zásobníku volání. Čas nezahrnuje čas, který byl stráven volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, čas však zahrnuje čas, který byl stráven v podřízených funkcích, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Včetně aplikace**|Celková aplikace včetně času všech volání této funkce v tomto kontextu.|
|**Včetně aplikace Čas %**|Procento celkového uplynulého včetně času spuštění profilování, který byl vynaložen v celkové aplikaci včetně času této funkce v tomto kontextu.|
|**Avg Aplikace včetně času**|Průměrná doba aplikace včetně volání této funkce v tomto kontextu.|
|**Maximální čas včetně aplikace**|Maximální doba aplikace včetně volání této funkce v tomto kontextu.|
|**Min aplikace včetně času**|Minimální doba aplikace včetně volání této funkce v tomto kontextu.|

## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace
 Výhradní hodnoty aplikace označují čas, kdy tyto instance funkce, které byly volány nadřazenou funkcí ve stromu volání, přímo prováděly kód v těle funkce; to znamená, když byla funkce v horní části zásobníku volání. Čas nezahrnuje čas strávený při volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu. Také nezahrnuje čas, který byl strávený v podřízené funkce, které byly volány funkce.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní čas aplikace**|Celkový výhradní čas aplikace všech volání této funkce v tomto kontextu.|
|**Výhradní čas aplikace %**|Procento celkového uplynulého výhradního času spuštění profilování, který byl vyčerpán v celkovém výhradním čase aplikace této funkce v tomto kontextu.|
|**Exkluzivní čas aplikace AVG**|Průměrná aplikace výhradní čas volání této funkce v tomto kontextu.|
|**Maximální exkluzivní čas aplikace**|Maximální výhradní čas aplikace volání této funkce v tomto kontextu.|
|**Min aplikace Exkluzivní čas**|Minimální výhradní čas aplikace volání této funkce v tomto kontextu.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)
- [Zobrazení stromu volání - instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení stromu volání – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
