---
title: Zobrazení modulů - Data instrumentace | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f6449ad30edf11d3d315532cc33db2a79c14f90b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778528"
---
# <a name="modules-view---instrumentation-data"></a>Zobrazení modulů - data instrumentace
Zobrazení Moduly zobrazuje údaje o výkonu, které jsou seskupeny podle modulů, které byly v datech profilování. Funkce modulu jsou uvedeny pod uzlničem modulu.

## <a name="general"></a>Obecné
 Obecné sloupce identifikují funkci v řádku zobrazení.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název funkce nebo modulu.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Number of Calls**|Celkový počet volání, které byly provedeny do této funkce nebo modulu.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu, ve kterém byl modul nebo funkce spuštěna.|
|**Režie výhradní sondy času**|Časrežie pro tuto funkci nebo modul z důvodu instrumentace.|
|**Režie sondy včetně času**|Čas režie pro tuto funkci nebo modul a jeho podřízené funkce z důvodu instrumentace.|

## <a name="elapsed-inclusive-values"></a>Uplynulé včetně hodnot
 Uplynulé včetně hodnoty označují čas, který byla funkce v zásobníku volání. Čas zahrnuje čas strávený v podřízených funkcích a volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý včetně času**|- Pro funkci, čas, který byl strávený ve funkci. To zahrnuje čas strávený v podřízených funkcí a volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br />- Pro modul, čas, ve kterém alespoň jedna funkce v modulu byl na zásobníku volání.|
|**Uplynulý včetně času %**|Procento celkového uplynulého včetně času spuštění profilování, který byl vynaložen v celkovém uplynulém včetně času tohoto modulu nebo funkce.|
|**Avg Uplynulý včetně čas**|- Pro funkci, průměrná uplynulá včetně čas volání této funkce.<br />- Pro modul, průměrná uplynulá včetně čas všech volání funkcí v modulu.|
|**Maximální uplynulý včetně času**|- Pro funkci, maximální uplynulý včetně čas volání této funkce.<br />- Pro modul, maximální uplynulý včetně času všech volání funkcí v modulu.|
|**Min uplynulý včetně času**|- Pro funkci, minimální uplynulý včetně čas volání tohoto modulu nebo funkce.<br />- Pro modul, minimální uplynulý včetně času všech volání funkcí v modulu.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé výhradní hodnoty označují čas, který byla funkce přímo spuštěna v horní části zásobníku volání. Čas zahrnuje čas strávený volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale nezahrnuje čas, který byl stráven v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý exkluzivní čas**|- Pro funkci, čas, který byl strávený v modulu nebo funkce. To zahrnuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale vylučuje čas strávený v podřízených funkcích.<br />- Pro modul, součet uplynulých exkluzivních časů funkcí v modulu.|
|**Uplynulý výhradní čas %**|Procento celkového uplynulého výhradního času profilování, který byl stráven v celkovém uplynulém výhradním čase tohoto modulu nebo funkce.|
|**Avg uplynulý exkluzivní čas**|- Pro funkci, průměrná uplynulá výhradní čas volání této funkce.<br />- Pro modul, průměrná uplynulá výhradní čas všech volání funkcí v modulu.|
|**Maximální uplynulý exkluzivní čas**|- Pro funkci maximální uplynulý výhradní čas volání této funkce.<br />- Pro modul, maximální uplynulý exkluzivní čas všech volání funkcí v modulu.|
|**Min uplynulý exkluzivní čas**|- Pro funkci minimální uplynulý výhradní čas volání tohoto modulu nebo funkce.<br />- Pro modul, minimální uplynulý exkluzivní čas všech volání funkcí v modulu.|

## <a name="application-inclusive-values"></a>Včetně hodnot aplikace
 Hodnoty zahrnující aplikaci označují čas, kdy byla funkce v zásobníku volání. Čas nezahrnuje čas strávený při volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu. Čas však zahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Včetně aplikace**|- Pro funkci, čas, který byl vynaložen na volání funkce. To zahrnuje čas strávený v podřízených funkcích, ale vylučuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br />- Pro modul, čas, ve kterém alespoň jedna funkce v modulu byl na zásobníku volání. To vylučuje čas strávený při volání operačního systému.|
|**Včetně aplikace Čas %**|Procento celkového uplynulého včetně času spuštění profilování, který byl vynaložen v aplikaci včetně času tohoto modulu nebo funkce.|
|**Avg Aplikace včetně času**|- Pro funkci, průměrná aplikace včetně čas volání této funkce.<br />- Pro modul, průměrná aplikace včetně času všech volání funkcí v modulu.|
|**Maximální čas včetně aplikace**|- Pro funkci, maximální aplikace včetně času volání této funkce.<br />- Pro modul, maximální aplikace včetně času všech volání funkcí v modulu.|
|**Min aplikace včetně času**|- Pro funkci, minimální aplikace včetně času volání tohoto modulu nebo funkce.<br />- Pro modul, minimální aplikace včetně času všech volání funkcí v modulu.|

## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace
 Výhradní hodnoty aplikace označují čas strávený v modulu nebo funkci. To vylučuje čas strávený v podřízených funkcích a také vylučuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní čas aplikace**|Celkový výhradní čas aplikace všech volání tohoto modulu nebo funkce.|
|**Výhradní čas aplikace %**|Procento celkového uplynulého výhradního času spuštění profilování, který byl stráven v aplikaci výhradní čas tohoto modulu nebo funkce.|
|**Exkluzivní čas aplikace AVG**|- Pro funkci, průměrná aplikace výhradní čas volání této funkce.<br />- Pro modul, průměrná aplikace exkluzivní čas všech volání funkcí v modulu.|
|**Maximální exkluzivní čas aplikace**|- Pro funkci, maximální aplikace výhradní čas volání této funkce.<br />- Pro modul, maximální aplikace exkluzivní čas všech volání funkcí v modulu.|
|**Min aplikace Exkluzivní čas**|- Pro funkci, minimální aplikace výhradní čas volání tohoto modulu nebo funkce.<br />- Pro modul, minimální aplikace exkluzivní čas všech volání funkcí v modulu.|

## <a name="see-also"></a>Viz také
- [Zobrazení modulů](../profiling/modules-view-sampling-data.md)
- [Pohled modulů - instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení modulů - odběr vzorků](../profiling/modules-view-dotnet-memory-sampling-data.md)
