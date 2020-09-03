---
title: Zobrazení volaný volající – data instrumentace | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 551c183dd9c368b1af16c1fe52b36762f4e71504
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74773293"
---
# <a name="callercallee-view---instrumentation-data"></a>Zobrazení Volající/Volaný – data instrumentace
Zobrazení volající/volaný zobrazí informace o profilování vybrané funkce a jejích nadřazených a podřízených funkcí ve stromu volání. Zobrazení volající/volaný obsahuje tři mřížky.

 V prostřední mřížce se zobrazí **aktuální funkce** a zobrazí informace o profilování vybrané funkce. Hodnoty zahrnují všechna volání funkce.

 **Funkce, které se nazývají aktuální funkce** , se zobrazí v horní mřížce a zobrazují informace o profilování volajících (nadřazených) funkcí vybrané funkce. Hodnoty označují množství hodnoty aktuální funkce, která byla vygenerována voláním z této volající funkce.

 **Funkce, které byly volány aktuální funkcí** , jsou zobrazeny v dolní mřížce a zobrazují informace o profilech instancí volaných (podřízených) funkcí vybrané funkce. Hodnoty udávají pouze čas strávený v podřízené funkci při volání aktuální funkce.

## <a name="general"></a>Obecné
 Obecné sloupce identifikují funkci v řádku zobrazení.

|Sloupec|Popis|
|------------|-----------------|
|**Název funkce**|Název funkce|
|**Adresa funkce**|Adresa funkce|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Number of Calls**|Celkový počet volání této funkce.|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu|
|**Výhradní čas režie testu**|Časová režie této funkce, která byla způsobena instrumentací. Režie testu byla odečtena od všech výhradních časů.|
|**Čas celkové režie testu**|Časová režie této funkce a jejích podřízených funkcí, které byly způsobeny instrumentací. Režie testu byla odečtena od všech celkových časů.|
|**Typ**|Kontext funkce:<br /><br /> **0** – aktuální funkce<br /><br /> **1** – funkce, která volá aktuální funkci<br /><br /> **2** – funkce, která je volána aktuální funkcí<br /><br /> Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|
|**Název kořenové funkce**|Název aktuální funkce Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|

## <a name="elapsed-inclusive-values"></a>Uplynulé celkové hodnoty
 Uplynulé celkové hodnoty udávají čas, kdy byla funkce v zásobníku volání. Čas zahrnuje čas strávený v podřízených funkcích a čas strávený v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý celkový čas**|– Pro aktuální funkci čas strávený ve funkci. Hodnota zahrnuje čas strávený v podřízených funkcích a v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br />– Pro funkci volajícího je to množství uplynulého celkového času aktuální funkce, která byla vygenerována voláními z této volající funkce.<br />– Pro funkci volaný byl čas strávený v instancích této funkce vygenerovaný voláními z aktuální funkce. Hodnota zahrnuje čas strávený v podřízených funkcích volaného a v voláních operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.|
|**% Uplynulého celkového času**|Procento celkového uplynulého celkového času běhu profilace, které bylo v tomto kontextu stráveno v uplynulém čase této funkce.|
|**Průměrný uplynulý celkový čas**|Průměrný uplynulý celkový čas volání této funkce v tomto kontextu.|
|**Maximální uplynulý celkový čas**|Maximální uplynulý celková doba volání této funkce v tomto kontextu.|
|**Minimální uplynulý celkový čas**|Minimální uplynulý celkový čas volání této funkce v tomto kontextu.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé exkluzivní hodnoty označují čas, kdy byla funkce přímo spuštěna v horní části zásobníku volání. Čas zahrnuje čas strávený v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace, ale nezahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý výhradní čas**|– Pro aktuální funkci čas strávený v přímém provádění funkce. Hodnota zahrnuje čas strávený v podřízených funkcích a v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br />– Pro funkci volajícího je to množství uplynulého výhradního času aktuální funkce, která byla vygenerována voláními z této volající funkce.<br />– Pro funkci volaný byl čas strávený v instancích této funkce vygenerovaný voláními z aktuální funkce. Hodnota vylučuje čas, který byl vyčerpán v podřízených funkcích funkce volaný, ale obsahuje volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.|
|**% Uplynulého výhradního času**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo v tomto kontextu stráveno celkovým neúplným časem této funkce.|
|**Průměrný uplynulý výhradní čas**|Průměrný uplynulý výhradní čas volání této funkce v tomto kontextu.|
|**Maximální uplynulý výhradní čas**|Maximální uplynulý výhradní čas volání této funkce v tomto kontextu.|
|**Minimální uplynulý výhradní čas**|Minimální uplynulý výhradní čas volání této funkce v tomto kontextu.|

## <a name="application-inclusive-values"></a>Hodnoty zahrnující aplikace
 Hodnoty pro všechny aplikace označují čas, kdy byla funkce v zásobníku volání. Čas neobsahuje čas strávený voláním operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace, ale obsahuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Celková doba aplikace**|– Pro aktuální funkci čas strávený ve funkci a jejích podřízených funkcích. Hodnota vylučuje čas, který byl stráven v voláních do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br />– Pro funkci volajícího je množství aplikace zahrnující čas aktuální funkce, která byla vygenerována voláním z této volající funkce.<br />– Pro funkci volaný byl čas strávený v instancích této funkce vygenerovaný voláními z aktuální funkce. Hodnota zahrnuje čas strávený v podřízených funkcích volané funkce, ale nezahrnuje čas strávený voláním operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.|
|**% Celkového času aplikace**|Procento celkového uplynulého celkového času běhu profilace, které bylo v tomto kontextu stráveno v celkovém čase aplikace této funkce.|
|**Průměrná doba aplikace (celková)**|Průměrná doba použití volání této funkce v tomto kontextu.|
|**Maximální celková doba aplikace**|Maximální doba volání této funkce v tomto kontextu (včetně celkového počtu aplikací).|
|**Minimální celková doba aplikace**|Minimální doba trvání volání této funkce v tomto kontextu (včetně celkového počtu aplikací).|

## <a name="application-exclusive-values"></a>Exkluzivní hodnoty aplikací
 Hodnoty exkluzivní pro aplikace označují čas strávený ve funkci. To vylučuje čas strávený v podřízených funkcích a také vyloučí volání operačního systému, jako jsou přepínače kontextu a vstupně-výstupní operace.

|Sloupec|Popis|
|------------|-----------------|
|**Výhradní čas aplikace**|– Pro aktuální funkci čas strávený v přímém provádění funkce. Hodnota neobsahuje čas strávený v podřízených funkcích, ani nezahrnuje volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br />– Pro funkci volajícího se jedná o velikost výhradního času aplikace, která byla vygenerována voláním z této volající funkce.<br />– Pro funkci volaný byl čas strávený v instancích této funkce vygenerovaný voláními z aktuální funkce. Hodnota neobsahuje čas, který byl vyčerpán v podřízených funkcích funkce volaný, ani nezahrnuje volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.|
|**% Výhradního času aplikace**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo v tomto kontextu stráveno v celkovém čase aplikace této funkce.|
|**Průměrný výhradní čas aplikace**|Průměrná doba použití pro volání této funkce v tomto kontextu.|
|**Maximální výhradní čas aplikace**|Maximální výhradní čas aplikace pro volání této funkce v tomto kontextu.|
|**Minimální výhradní čas aplikace**|Minimální výhradní čas aplikace pro volání této funkce v tomto kontextu.|

## <a name="see-also"></a>Viz také
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení Volající/Volaný – data vzorkování](../profiling/caller-callee-view-sampling-data.md)
- [Zobrazení Volající/Volaný – data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Zobrazení Volající/Volaný – data instrumentace paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
