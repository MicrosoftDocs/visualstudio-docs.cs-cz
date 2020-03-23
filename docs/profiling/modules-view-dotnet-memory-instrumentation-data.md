---
title: Zobrazení modulů - data instrumentace paměti .NET | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 521c884a0a25d7fa975a4039e6ec3e36ff4dc020
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778541"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Zobrazení modulů - data paměťových přístrojů .NET
Zobrazení modulů dat přidělení paměti .NET shromážděných pomocí metody instrumentace seskupuje data paměti a časování moduly, které byly provedeny při spuštění profilování. Profilovací data pro funkce modulu jsou uvedena pod uzlovým modulem.

## <a name="general"></a>Obecné

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

## <a name="net-memory-values"></a>Hodnoty paměti .NET
 Včetně hodnoty paměti .NET funkce označují počet (přidělení) a velikost (bajty) objektů, které byly vytvořeny funkce a její podřízené funkce.

 Výhradní hodnoty paměti označují počet a velikost objektů, které byly vytvořeny funkce a nikoli jeho podřízené funkce.

 Včetně a výhradní paměti hodnoty modulu jsou součtem včetně a výhradní paměti hodnoty funkcí v modulu.

|Sloupec|Popis|
|------------|-----------------|
|**Inkluzivní přidělení**|- Pro funkci celkový počet objektů, které byly vytvořeny funkce. Toto číslo zahrnuje objekty, které byly vytvořeny funkcemi, které byly volány funkcí.<br />- Pro modul počet objektů v profilování spustit, které byly přiděleny při provádění alespoň jednu funkci z modulu. Toto číslo zahrnuje objekty, které byly přiděleny ve funkcích, které byly generovány volání z funkcí modulu.|
|**Včetně přidělení %**|Procento všech objektů, které byly přiděleny v profilování spustit, které byly včetně přidělení modulu nebo funkce.|
|**Výhradní přidělení**|- Pro funkci počet objektů, které byly vytvořeny při spuštění funkce kódu v těle funkce (to znamená, když funkce byla v horní části zásobníku volání). Toto číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány funkcí.<br />- Pro modul, součet výhradní přidělení funkcí v modulu.|
|**Výhradní přidělení %**|Procento všech objektů, které byly přiděleny v profilování spustit, které byly výhradní přidělení modulu nebo funkce.|
|**Exkluzivní bajty**|- Pro funkci celkový počet bajtů paměti, které byly přiděleny při spuštění funkce kódu v těle funkce (to znamená, když funkce byla v horní části zásobníku volání). Toto číslo nezahrnuje bajty, které byly přiděleny ve funkcích, které byly volány funkcí.<br />- Pro modul součet výhradních bajtů, které byly přiděleny funkcemi v modulu.|
|**Výhradní bajty %**|Procento všech bajtů, které byly přiděleny v profilování spustit, které byly výhradní bajty modulu, funkce, řádku nebo instrukce.|
|**Včetně bajtů**|- Pro funkci počet bajtů, které byly přiděleny funkce. Toto číslo zahrnuje bajty, které byly přiděleny ve funkcích, které byly volány funkcí.<br />- Pro modul počet bajtů, které byly přiděleny v profilování spustit, které byly přiděleny při provádění alespoň jednu funkci z modulu. Toto číslo zahrnuje objekty, které byly vytvořeny ve všech funkcích, které byly volány funkce modulu.|
|**Včetně bajtů %**|Procento všech bajtů, které byly přiděleny v profilování spustit, které byly včetně bajtů modulu nebo funkce.|

## <a name="elapsed-inclusive-values"></a>Uplynulé včetně hodnot
 Uplynulé včetně hodnoty označují čas, který byla funkce v zásobníku volání. Čas zahrnuje čas strávený v podřízených funkcích a volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý včetně času**|- Pro funkci, čas, který byl strávený ve funkci. To zahrnuje čas strávený v podřízených funkcí a volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br />- Pro modul, doba, ve které alespoň jedna funkce v modulu byl na zásobníku volání.|
|**Uplynulý včetně času %**|Procento celkového uplynulého včetně času spuštění profilování, který byl vynaložen v celkovém uplynulém včetně času tohoto modulu nebo funkce.|
|**Avg Uplynulý včetně čas**|- Pro funkci, průměrná uplynulá včetně čas volání této funkce.<br />- Pro modul, průměrná uplynulá včetně čas všech volání funkcí v modulu.|
|**Maximální uplynulý včetně času**|- Pro funkci, maximální uplynulý včetně čas volání této funkce.<br />- Pro modul, maximální uplynulý včetně času všech volání funkcí v modulu.|
|**Min uplynulý včetně času**|- Pro funkci, minimální uplynulý včetně čas volání tohoto modulu nebo funkce.<br />- Pro modul, minimální uplynulý včetně času všech volání funkcí v modulu.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé výhradní hodnoty označují čas, který byla funkce přímo spuštěna v horní části zásobníku volání. Čas zahrnuje čas volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale nezahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý exkluzivní čas**|- Pro funkci, čas, který byl strávený v modulu nebo funkce. To zahrnuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale vylučuje čas strávený v podřízených funkcích.<br />- Pro modul, součet uplynulých exkluzivních časů funkcí v modulu.|
|**Uplynulý výhradní čas %**|Procento celkového uplynulého výhradního času profilování, který byl stráven v celkovém uplynulém výhradním čase tohoto modulu nebo funkce.|
|**Avg uplynulý exkluzivní čas**|- Pro funkci, průměrná uplynulá výhradní čas volání této funkce.<br />- Pro modul, průměrná uplynulá výhradní čas všech volání funkcí v modulu.|
|**Maximální uplynulý exkluzivní čas**|- Pro funkci maximální uplynulý výhradní čas volání této funkce.<br />- Pro modul, maximální uplynulý exkluzivní čas všech volání funkcí v modulu.|
|**Min uplynulý exkluzivní čas**|- Pro funkci minimální uplynulý výhradní čas volání tohoto modulu nebo funkce.<br />- Pro modul, minimální uplynulý exkluzivní čas všech volání funkcí v modulu.|

## <a name="application-inclusive-values"></a>Včetně hodnot aplikace
 Hodnoty zahrnující aplikaci označují čas, kdy byla funkce v zásobníku volání. Čas nezahrnuje čas strávený při volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale zahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Včetně aplikace**|- Pro funkci, čas, který byl vynaložen na volání funkce. To zahrnuje čas strávený v podřízených funkcích, ale vylučuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br />- Pro modul, doba, ve které alespoň jedna funkce v modulu byl na zásobníku volání, s výjimkou času, který byl vynaložen na volání do operačního systému.|
|**Včetně aplikace Čas %**|Procento celkového uplynulého včetně času spuštění profilování, který byl vynaložen v aplikaci včetně času tohoto modulu nebo funkce.|
|**Avg Aplikace včetně času**|- Pro funkci, průměrná aplikace včetně čas volání této funkce.<br />- Pro modul, průměrná aplikace včetně času všech volání funkcí v modulu.|
|**Maximální čas včetně aplikace**|- Pro funkci, maximální aplikace včetně času volání této funkce.<br />- Pro modul, maximální aplikace včetně času všech volání funkcí v modulu.|
|**Min aplikace včetně času**|- Pro funkci, minimální aplikace včetně času volání tohoto modulu nebo funkce.<br />- Pro modul, minimální aplikace včetně času všech volání funkcí v modulu.|

## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace
 Výhradní hodnoty aplikace označují čas strávený v modulu nebo funkci, s výjimkou času stráveného v podřízených funkcích. Uvedený čas také vylučuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní čas aplikace**|- Pro funkci, celkový výhradní čas aplikace volání této funkce.<br />- Pro modul, celkový výhradní čas aplikace všech volání funkcí v modulu.|
|**Výhradní čas aplikace %**|Procento celkového uplynulého výhradního času spuštění profilování, který byl stráven v aplikaci výhradní čas tohoto modulu nebo funkce.|
|**Exkluzivní čas aplikace AVG**|- Pro funkci, průměrná aplikace výhradní čas volání této funkce.<br />- Pro modul, průměrná aplikace exkluzivní čas všech volání funkcí v modulu.|
|**Maximální exkluzivní čas aplikace**|- Pro funkci, maximální aplikace výhradní čas volání této funkce.<br />- Pro modul, maximální aplikace exkluzivní čas všech volání funkcí v modulu.|
|**Min aplikace Exkluzivní čas**|- Pro funkci, minimální aplikace výhradní čas volání tohoto modulu nebo funkce.<br />- Pro modul, minimální aplikace exkluzivní čas všech volání funkcí v modulu.|

## <a name="see-also"></a>Viz také
- [Zobrazení modulů - odběr vzorků](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)
- [Zobrazení modulů](../profiling/modules-view-sampling-data.md)
