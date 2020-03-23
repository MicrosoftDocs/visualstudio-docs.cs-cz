---
title: Zobrazení funkcí - data instrumentace paměti .NET | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: eba1f0d1434d253aaca698d3ae582e3c507c2d23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779230"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>Zobrazení funkcí - data přístrojové paměti .NET
Zobrazení Funkce profilování profilování paměti .NET, která byla shromážděna pomocí metody instrumentace, uvádí funkce, které přidělili paměť během spuštění profilování. Řádek funkce hlásí velikost a počet přidělení a časovací data pro funkci.

## <a name="general"></a>Obecné

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
|**Režie výhradní sondy času**|Čas režie pro tuto funkci z důvodu instrumentace. Režie sondy byla odečtena od všech výhradních časů.|
|**Režie sondy včetně času**|Čas režie pro tuto funkci a její podřízené funkce z důvodu instrumentace. Režie sondy byla odečtena od all inclusive časů.|

## <a name="net-memory-values"></a>Hodnoty paměti .NET
 Včetně hodnoty paměti .NET funkce označují počet (přidělení) a velikost (bajty) objektů, které byly vytvořeny funkce a její podřízené funkce.

 Výhradní hodnoty paměti označují počet a velikost objektů, které byly vytvořeny funkce a nikoli jeho podřízené funkce.

|Sloupec|Popis|
|------------|-----------------|
|**Inkluzivní přidělení**|Celkový počet objektů, které byly vytvořeny v této funkci a ve funkcích, které byly volány touto funkcí.|
|**Včetně přidělení %**|Procento všech objektů, které byly přiděleny v profilování spustit, které byly včetně přidělení této funkce.|
|**Výhradní přidělení**|Celkový počet objektů, které byly vytvořeny při spuštění funkce kódu v těle funkce. Toto číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány touto funkcí.|
|**Výhradní přidělení %**|Procento všech objektů, které byly vytvořeny v profilování spustit, které byly výhradní přidělení této funkce.|
|**Včetně bajtů**|Počet bajtů paměti, které byly přiděleny v této funkci a ve funkcích, které byly volány touto funkcí.|
|**Včetně bajtů %**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly včetně bajtů této funkce.|
|**Exkluzivní bajty**|Počet bajtů paměti, které byly přiděleny touto funkcí, ale ne funkcemi, které byly volány touto funkcí.|
|**Výhradní bajty %**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly výhradní bajty této funkce.|

## <a name="elapsed-inclusive-values"></a>Uplynulé včetně hodnot
 Uplynulé včetně hodnoty označují čas, který byla funkce v zásobníku volání. Čas zahrnuje čas strávený v podřízených funkcích a volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý včetně času**|Celkový uplynulý včetně času všech volání této funkce.|
|**Uplynulý včetně času %**|Procento celkového uplynulého včetně času profilování, který byl stráven v uplynulém včetně času této funkce.|
|**Avg Uplynulý včetně čas**|Průměrná uplynulá doba volání této funkce.|
|**Maximální uplynulý včetně času**|Maximální uplynulý včetně čas volání této funkce.|
|**Min uplynulý včetně času**|Minimální uplynulý včetně čas volání této funkce.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé výhradní hodnoty označují čas, který byla funkce přímo spuštěna v horní části zásobníku volání. Čas zahrnuje čas ve volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale nezahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý exkluzivní čas**|Celkový uplynulý výhradní čas všech volání této funkce.|
|**Uplynulý výhradní čas %**|Procento celkového uplynulého výhradního času profilování, který byl stráven v celkovém uplynulém výhradním čase této funkce.|
|**Avg uplynulý exkluzivní čas**|Průměrná uplynulá výhradní doba volání této funkce.|
|**Maximální uplynulý exkluzivní čas**|Maximální uplynulý výhradní čas volání této funkce.|
|**Min uplynulý exkluzivní čas**|Minimální uplynulý výhradní čas volání této funkce.|

## <a name="application-inclusive-values"></a>Včetně hodnot aplikace
 Hodnoty zahrnující aplikaci označují čas, kdy byla funkce v zásobníku volání. Čas nezahrnuje čas strávený při volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale zahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Včetně aplikace**|Celkový čas aplikace včetně všech volání této funkce.|
|**Včetně aplikace Čas %**|Procento celkového uplynulého včetně času spuštění profilování, který byl vynaložen v celkové aplikaci včetně času této funkce.|
|**Avg Aplikace včetně času**|Průměrná doba aplikace včetně volání této funkce.|
|**Maximální čas včetně aplikace**|Maximální doba aplikace včetně volání této funkce.|
|**Min aplikace včetně času**|Minimální doba aplikace včetně volání této funkce.|

## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace
 Výhradní hodnoty aplikace označují čas, kdy byla funkce přímo spuštěna v horní části zásobníku volání. Čas nezahrnuje čas strávený při volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ani nezahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní čas aplikace**|Celkový výhradní čas aplikace všech volání této funkce.|
|**Výhradní čas aplikace %**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo vynaloženo v celkovém výhradním čase aplikace této funkce.|
|**Exkluzivní čas aplikace AVG**|Průměrná aplikace výhradní čas volání této funkce.|
|**Maximální exkluzivní čas aplikace**|Maximální výhradní čas aplikace volání této funkce.|
|**Min aplikace Exkluzivní čas**|Minimální výhradní čas aplikace volání této funkce.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení funkcí - vzorkování](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Zobrazení funkcí](../profiling/functions-view-instrumentation-data.md)
- [Zobrazení funkcí](../profiling/functions-view-sampling-data.md)
