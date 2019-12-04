---
title: Zobrazení modulů – data instrumentace paměti .NET | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778541"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Zobrazení modulů – data instrumentace paměti .NET
Moduly zobrazení dat přidělení paměti .NET shromážděných pomocí metody instrumentace seskupují data paměti a časování moduly, které byly spuštěny při spuštění profilace. Data profilování pro funkce modulu jsou uvedena pod uzlem modulu.

## <a name="general"></a>Obecné

|Sloupec|Popis|
|------------|-----------------|
|**Jméno**|Název funkce nebo modulu.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Počet volání**|Celkový počet volání, která byla provedena v této funkci nebo modulu.|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu, ve kterém byl spuštěn modul nebo funkce.|
|**Výhradní čas režie testu**|Časová režie této funkce nebo modulu z důvodu instrumentace.|
|**Čas celkové režie testu**|Časová režie této funkce nebo modulu a jejích podřízených funkcí z důvodu instrumentace.|

## <a name="net-memory-values"></a>Hodnoty paměti .NET
 Celkové hodnoty paměti .NET funkce označují počet (přidělení) a velikost objektů (v bajtech), které byly vytvořeny funkcí a jejími podřízenými funkcemi.

 Hodnoty exkluzivní paměti označují počet a velikost objektů, které byly vytvořeny funkcí a nikoli jejími podřízenými funkcemi.

 Celkové a exkluzivní hodnoty paměti modulu jsou součtem hodnot celkových hodnot paměti, které jsou v modulu obsažené a exkluzivní.

|Sloupec|Popis|
|------------|-----------------|
|**Celkové alokace**|– Pro funkci celkový počet objektů, které byly vytvořeny funkcí. Toto číslo zahrnuje objekty, které byly vytvořeny funkcemi, které byly volány funkcí.<br />– Pro modul je počet objektů v běhu profilace, které byly přiděleny při provádění alespoň jedné funkce z modulu. Toto číslo zahrnuje objekty, které byly přiděleny ve funkcích, které byly vygenerovány prostřednictvím volání funkcí modulu.|
|**% Celkových přidělení**|Procentuální podíl všech objektů, které byly přiděleny při spuštění profilace, které byly zahrnuty do přidělení modulu nebo funkce.|
|**Exkluzivní přidělení**|– Pro funkci počet objektů, které byly vytvořeny, když funkce prováděla kód v těle funkce (to znamená, když funkce byla v horní části zásobníku volání). Toto číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány funkcí.<br />– Pro modul součet exkluzivního přidělení funkcí v modulu.|
|**% Exkluzivní alokace**|Procento všech objektů, které byly přiděleny při spuštění profilace, které byly exkluzivním přidělením modulu nebo funkce.|
|**Exkluzivní počet bajtů**|– Pro funkci celkový počet bajtů paměti, které byly přiděleny, když funkce prováděla kód v těle funkce (to znamená, když funkce byla v horní části zásobníku volání). Toto číslo nezahrnuje bajty, které byly přiděleny ve funkcích, které byly volány funkcí.<br />– Pro modul součet exkluzivních bajtů, které byly přiděleny funkcemi v modulu.|
|**% Exkluzivních bajtů**|Procento všech bajtů, které byly přiděleny při spuštění profilace, které byly výhradně bajty modulu, funkce, řádku nebo instrukce.|
|**Včetně bajtů**|– Pro funkci počet bajtů, které byly přiděleny funkcí. Toto číslo zahrnuje bajty přidělené ve funkcích, které byly volány funkcí.<br />– Pro modul počet bajtů, které byly přiděleny při spuštění profilace, které byly přiděleny při provádění alespoň jedné funkce z modulu. Toto číslo zahrnuje objekty, které byly vytvořeny ve všech funkcích, které byly volány funkcemi modulu.|
|**% Celkových bajtů**|Procento všech bajtů, které byly přiděleny při spuštění profilace, včetně bajtů modulu nebo funkce.|

## <a name="elapsed-inclusive-values"></a>Uplynulé celkové hodnoty
 Uplynulé celkové hodnoty udávají čas, kdy byla funkce v zásobníku volání. Čas zahrnuje čas strávený v podřízených funkcích a v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý celkový čas**|– Pro funkci, čas strávený ve funkci. To zahrnuje čas strávený v podřízených funkcích a v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br />– Pro modul je časový interval, ve kterém byla alespoň jedna funkce v modulu v zásobníku volání.|
|**% Uplynulého celkového času**|Procento celkového uplynulého celkového času běhu profilace, které bylo stráveno v celkovém uplynulém časovém intervalu tohoto modulu nebo funkce.|
|**Průměrný uplynulý celkový čas**|– Pro funkci Průměrná uplynulá celková doba volání této funkce.<br />– Pro modul byl průměrný uplynulý celkový čas všech volání funkcí v modulu.|
|**Maximální uplynulý celkový čas**|– Pro funkci maximální uplynulý celkový čas volání této funkce.<br />– Pro modul, maximální uplynulý celkový čas všech volání funkcí v modulu.|
|**Minimální uplynulý celkový čas**|– Pro funkci, minimální uplynulý celkový čas volání tohoto modulu nebo funkce.<br />– Pro modul, minimální uplynulý celkový čas všech volání funkcí v modulu.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé exkluzivní hodnoty označují čas, kdy byla funkce přímo spuštěna v horní části zásobníku volání. Čas zahrnuje čas volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace, ale nezahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý výhradní čas**|– Pro funkci, čas strávený modulem nebo funkcí. To zahrnuje volání do operačního systému, jako jsou přepínače kontextu a vstupně-výstupní operace, ale vyloučí čas strávený v podřízených funkcích.<br />– Pro modul součet uplynulých výhradních časů funkcí v modulu.|
|**% Uplynulého výhradního času**|Procento celkového uplynulého výhradního času pro spuštění profilování, které bylo stráveno celkovým uplynulým výhradním časem tohoto modulu nebo funkce.|
|**Průměrný uplynulý výhradní čas**|– Pro funkci průměrný uplynulý výhradní čas volání této funkce.<br />– Pro modul průměrný uplynulý výhradní čas všech volání funkcí v modulu.|
|**Maximální uplynulý výhradní čas**|– Pro funkci maximální uplynulý výhradní čas volání této funkce.<br />– Pro modul je maximální uplynulý výhradní čas všech volání funkcí v modulu.|
|**Minimální uplynulý výhradní čas**|– Pro funkci byl minimální uplynulý výhradní čas volání tohoto modulu nebo funkce.<br />– Pro modul byl minimální uplynulý výhradní čas všech volání funkcí v modulu.|

## <a name="application-inclusive-values"></a>Hodnoty zahrnující aplikace
 Hodnoty pro všechny aplikace označují čas, kdy byla funkce v zásobníku volání. Čas neobsahuje čas strávený voláním operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace, ale obsahuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Celková doba aplikace**|– Pro funkci, čas strávený voláním funkce. To zahrnuje čas strávený v podřízených funkcích, ale vyloučí volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br />– Pro modul, časové období, ve kterém byla alespoň jedna funkce v modulu v zásobníku volání, kromě času stráveného voláním do operačního systému.|
|**% Celkového času aplikace**|Procento celkového uplynulého celkového času běhu profilace, které bylo stráveno v celkovém čase tohoto modulu nebo funkce.|
|**Průměrná doba aplikace (celková)**|– Pro funkci představuje Průměrná doba, jakou aplikace volá tuto funkci.<br />– Pro modul vypočítá Průměrná doba použití všech volání funkcí v modulu.|
|**Maximální celková doba aplikace**|– Pro funkci je to maximální doba volání této funkce (včetně).<br />– Pro modul je maximální doba všech volání funkcí v modulu (celková) aplikace.|
|**Minimální celková doba aplikace**|– Pro funkci je to minimální čas pro volání tohoto modulu nebo funkce.<br />– Pro modul, minimální dobu všech volání funkcí v modulu, což je celková doba aplikace.|

## <a name="application-exclusive-values"></a>Exkluzivní hodnoty aplikací
 Hodnoty exkluzivní pro aplikace udávají čas strávený modulem nebo funkcí s výjimkou času stráveného v podřízených funkcích. Uvedený čas také vyloučí volání do operačního systému, jako jsou přepínače kontextu a vstupně-výstupní operace.

|Sloupec|Popis|
|------------|-----------------|
|**Výhradní čas aplikace**|– Pro funkci celková aplikace exkluzivní dobu volání této funkce.<br />– Pro modul celková aplikace exkluzivní dobu všech volání funkcí v modulu.|
|**% Výhradního času aplikace**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo stráveno v exkluzivním čase aplikace tohoto modulu nebo funkce.|
|**Průměrný výhradní čas aplikace**|– Pro funkci představuje Průměrná doba aplikace výhradní čas volání této funkce.<br />– Pro modul vyhledá Průměrná doba aplikace výhradní čas všech volání funkcí v modulu.|
|**Maximální výhradní čas aplikace**|– Pro funkci je maximální doba aplikace při volání této funkce.<br />– Pro modul je maximální doba aplikace exkluzivní pro všechna volání funkcí v modulu.|
|**Minimální výhradní čas aplikace**|– Pro funkci minimální výhradní čas aplikace pro volání tohoto modulu nebo funkce.<br />– Pro modul, minimální výhradní čas aplikace pro všechna volání funkcí v modulu.|

## <a name="see-also"></a>Viz také:
- [Zobrazení modulů – vzorkování](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)
- [Zobrazení modulů](../profiling/modules-view-sampling-data.md)
