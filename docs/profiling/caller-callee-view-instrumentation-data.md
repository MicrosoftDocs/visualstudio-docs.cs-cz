---
title: Zobrazení volajícího a volaní - Data instrumentace | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773293"
---
# <a name="callercallee-view---instrumentation-data"></a>Zobrazení volajícího/volaných - data instrumentace
Zobrazení Volající/Volaný zobrazuje informace o profilování vybrané funkce a jejích nadřazených a podřízených funkcí ve stromu volání. Zobrazení Volající/Volaný obsahuje tři mřížky.

 **Aktuální funkce** je zobrazena ve střední mřížce a zobrazuje informace o profilování vybrané funkce. Hodnoty zahrnují všechna volání funkce.

 **Funkce, které volaly aktuální funkci,** jsou zobrazeny v horní mřížce a zobrazují informace o profilování volající (nadřazené) funkce vybrané funkce. Hodnoty označují hodnotu hodnoty aktuální funkce, která byla generována voláním z této volající funkce.

 **Funkce, které byly volány aktuální funkcí,** jsou zobrazeny v dolní mřížce a zobrazují informace o profilování instancí volaných (podřízených) funkcí vybrané funkce. Hodnoty označují pouze čas, který byl vyčerpán v podřízené funkci, když byla volána aktuální funkcí.

## <a name="general"></a>Obecné
 Obecné sloupce identifikují funkci v řádku zobrazení.

|Sloupec|Popis|
|------------|-----------------|
|**Název funkce**|Název funkce.|
|**Adresa funkce**|Adresa funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Number of Calls**|Celkový počet volání této funkce.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Režie výhradní sondy času**|Čas režie pro tuto funkci, která byla způsobena instrumentace. Režie sondy byla odečtena od všech výhradních časů.|
|**Režie sondy včetně času**|Čas režie pro tuto funkci a její podřízené funkce, která byla způsobena instrumentace. Režie sondy byla odečtena od all inclusive časů.|
|**Typ**|Kontext funkce:<br /><br /> **0** - aktuální funkce<br /><br /> **1** - funkce, která volá aktuální funkci<br /><br /> **2** - funkce, která je volána aktuální funkcí<br /><br /> Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|
|**Název kořenové funkce**|Název aktuální funkce. Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|

## <a name="elapsed-inclusive-values"></a>Uplynulé včetně hodnot
 Uplynulé včetně hodnoty označují čas, který byla funkce v zásobníku volání. Čas zahrnuje čas strávený v podřízených funkcích a čas strávený voláním operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý včetně času**|- Pro aktuální funkci čas, který byl strávený ve funkci. Hodnota zahrnuje čas strávený v podřízených funkcí chod a volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br />- Pro volající funkce, množství uplynulý včetně čas aktuální funkce, která byla generována volání z této funkce volajícího.<br />- Pro volanou funkci čas, který byl stráven v instancích této funkce, které byly generovány voláníz aktuální funkce. Hodnota zahrnuje čas strávený v podřízených funkcích volaného a ve volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.|
|**Uplynulý včetně času %**|Procento celkového uplynulého včetně času profilování, který byl vyčerpán v uplynulém včetně času této funkce v tomto kontextu.|
|**Avg Uplynulý včetně čas**|Průměrná uplynulá včetně čas volání této funkce v tomto kontextu.|
|**Maximální uplynulý včetně času**|Maximální uplynulý včetně čas volání této funkce v tomto kontextu.|
|**Min uplynulý včetně času**|Minimální uplynulý včetně čas volání této funkce v tomto kontextu.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé výhradní hodnoty označují čas, který byla funkce přímo spuštěna v horní části zásobníku volání. Čas zahrnuje čas strávený volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale nezahrnuje čas, který byl stráven v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý exkluzivní čas**|- Pro aktuální funkci čas, který byl vynaložen v přímém provádění funkce. Hodnota zahrnuje čas strávený v podřízených funkcí chod a volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br />- Pro volající funkce, množství uplynulý výhradní čas aktuální funkce, která byla generována volání z této funkce volajícího.<br />- Pro volanou funkci čas, který byl stráven v instancích této funkce, které byly generovány voláníz aktuální funkce. Hodnota vylučuje čas, který byl stráven v podřízených funkcích volané funkce, ale zahrnuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.|
|**Uplynulý výhradní čas %**|Procento celkového uplynulého výhradního času spuštění profilování, který byl vyčerpán v celkovém uplynulém výhradním čase této funkce v tomto kontextu.|
|**Avg uplynulý exkluzivní čas**|Průměrná uplynulá výhradní doba volání této funkce v tomto kontextu.|
|**Maximální uplynulý exkluzivní čas**|Maximální uplynulý výhradní čas volání této funkce v tomto kontextu.|
|**Min uplynulý exkluzivní čas**|Minimální uplynulý výhradní čas volání této funkce v tomto kontextu.|

## <a name="application-inclusive-values"></a>Včetně hodnot aplikace
 Hodnoty zahrnující aplikaci označují čas, kdy byla funkce v zásobníku volání. Čas nezahrnuje čas strávený při volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale zahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Včetně aplikace**|- Pro aktuální funkci, čas, který byl vynaložen ve funkci a její podřízené funkce. Hodnota vylučuje čas, který byl vynaložen na volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br />- Pro volající funkce, množství aplikace včetně času aktuální funkce, která byla generována volání z této funkce volajícího.<br />- Pro volanou funkci čas, který byl stráven v instancích této funkce, které byly generovány voláníz aktuální funkce. Hodnota zahrnuje čas strávený v podřízených funkcích volané funkce, ale nezahrnuje čas, který byl stráven volání operačního systému, jako jsou například přepnutí kontextu a operace vstup a výstup.|
|**Včetně aplikace Čas %**|Procento celkového uplynulého včetně času spuštění profilování, který byl vynaložen v celkové aplikaci včetně času této funkce v tomto kontextu.|
|**Avg Aplikace včetně času**|Průměrná doba aplikace včetně volání této funkce v tomto kontextu.|
|**Maximální čas včetně aplikace**|Maximální doba aplikace včetně volání této funkce v tomto kontextu.|
|**Min aplikace včetně času**|Minimální doba aplikace včetně volání této funkce v tomto kontextu.|

## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace
 Výhradní hodnoty aplikace označují čas strávený ve funkci. To vylučuje čas strávený v podřízených funkcích a také vylučuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní čas aplikace**|- Pro aktuální funkci čas, který byl vynaložen v přímém provádění funkce. Hodnota nezahrnuje čas strávený v podřízených funkcích, ani volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br />- Pro volající funkce, množství aplikace výhradní čas aktuální funkce, která byla generována volání z této funkce volajícího.<br />- Pro volanou funkci čas, který byl stráven v instancích této funkce, které byly generovány voláníz aktuální funkce. Hodnota nezahrnuje čas strávený v podřízených funkcích volané funkce, ani nezahrnuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.|
|**Výhradní čas aplikace %**|Procento celkového uplynulého výhradního času spuštění profilování, který byl vyčerpán v celkovém výhradním čase aplikace této funkce v tomto kontextu.|
|**Exkluzivní čas aplikace AVG**|Průměrná aplikace výhradní čas volání této funkce v tomto kontextu.|
|**Maximální exkluzivní čas aplikace**|Maximální výhradní čas aplikace volání této funkce v tomto kontextu.|
|**Min aplikace Exkluzivní čas**|Minimální výhradní čas aplikace volání této funkce v tomto kontextu.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení volajícího/volaných - vzorkovací data](../profiling/caller-callee-view-sampling-data.md)
- [Zobrazení volajícího/volaných – vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Zobrazení volajícího/volaných - data přístrojové paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
