---
title: Zobrazení Caller-Callee – data instrumentace paměti sítě | Microsoft Docs
description: Projděte si zobrazení volající/volaný data profilace paměti .NET, které zobrazuje data přidělení a časování pro vybranou funkci a nadřazené a podřízené funkce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3fa4928f9da81b2141eec76e54bce7887f50a074
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148075"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Zobrazení Volající/Volaný – data instrumentace paměti .NET
Zobrazení volající/volaný pro data profilace paměti .NET, která byla shromážděna pomocí metody instrumentace, zobrazuje data přidělení a časování pro vybranou funkci a nadřazené a podřízené funkce této vybrané funkce. Zobrazení volající/volaný obsahuje tři mřížky.

 V prostřední mřížce se zobrazí **aktuální funkce** a zobrazí informace o profilaci paměti vybrané funkce. Hodnoty zahrnují všechna ukázková volání funkce.

 **Funkce, které se nazývají aktuální funkce** , se zobrazí v horní mřížce a zobrazuje množství hodnoty vybrané (aktuální) funkce, která byla vygenerována voláními z funkce volající (nadřazená).

 **Funkce, které byly volány aktuální funkcí** , se zobrazí v dolní mřížce a zobrazí data profilace paměti pro volané (podřízené) funkce vybrané funkce, pokud byla podřízená funkce volána aktuální funkcí.

 Dvojím kliknutím na řádek volajícího nebo volaného řádku můžete nastavit, aby byl řádek aktuální funkce.

## <a name="general"></a>Obecné

|Sloupec|Popis|
|------------|-----------------|
|**Název funkce**|Název funkce|
|**Adresa funkce**|Adresa funkce|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Number of Calls**|Celkový počet volání této funkce.|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu běhu profilace.|
|**Název procesu**|Název, který je přiřazen procesu.|
|**Výhradní čas režie testu**|Časová režie této funkce z důvodu instrumentace. Režie testu byla odečtena od všech výhradních časů.|
|**Čas celkové režie testu**|Časová režie této funkce a jejích podřízených funkcí z důvodu instrumentace. Režie testu byla odečtena od všech celkových časů.|
|**Typ**|Kontext funkce:<br /><br /> **0** – aktuální funkce<br /><br /> **1** – funkce, která volá aktuální funkci<br /><br /> **2** – funkce, která je volána aktuální funkcí<br /><br /> Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|
|**Název kořenové funkce**|Název aktuální funkce Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|

## <a name="net-memory-allocation-values"></a>Hodnoty alokace paměti .NET

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní přidělení**|– Pro aktuální funkci počet objektů, které byly vytvořeny v době, kdy funkce prováděla kód v těle funkce (to znamená, když funkce byla v horní části zásobníku volání). Počet nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány touto funkcí.<br />– Pro funkci volajícího se jedná o počet exkluzivních přidělení aktuální funkce, které byly vygenerovány voláními z této volající funkce.<br />– Pro funkci volaného je počet objektů, které byly vytvořeny instancemi této funkce, které byly volány aktuální funkcí. Toto číslo nezahrnuje objekty, které byly vytvořeny funkcemi, které byly volány funkcí volaný.|
|**% Exkluzivní alokace**|Procentuální podíl všech objektů, které byly vytvořeny v rámci profilace, které byly exkluzivním přidělením této funkce.|
|**Celkové alokace**|– Pro aktuální funkci počet objektů, které byly přiděleny funkcí při spuštění profilace. Číslo zahrnuje objekty, které byly vytvořeny ve funkcích volaný, které byly volány funkcí.<br />– Pro funkci volajícího je počet celkových přidělení aktuální funkce, které byly vygenerovány voláními z této volající funkce.<br />– Pro funkci volaného je počet objektů, které byly přiděleny instancemi této funkce vygenerované voláními z aktuální funkce. Číslo zahrnuje přidělení prováděné funkcemi, které byly volány touto funkcí volaný.|
|**% Celkových přidělení**|Procentuální podíl všech objektů, které byly vytvořeny v rámci profilace, které byly zahrnuty do přidělení této funkce.|
|**Exkluzivní počet bajtů**|– Pro aktuální funkci počet bajtů paměti, které byly přiděleny funkcí při spuštění profilace. Počet nezahrnuje paměť, která byla přidělena ve volání funkce volané funkcí.<br />– Pro funkci volajícího je počet exkluzivních bajtů aktuální funkce, které byly vygenerovány voláním této volající funkce.<br />– Pro funkci volaný počet bajtů, které byly přiděleny instancemi této funkce, které byly vygenerovány voláními z aktuální funkce. Počet nezahrnuje bajty, které byly přiděleny funkcemi, které byly volány funkcí volaný.|
|**% Exkluzivních bajtů**|Procento všech bajtů paměti, které byly přiděleny při spuštění profilace, které byly exkluzivním přidělením této funkce.|
|**Včetně bajtů**|– Pro aktuální funkci počet bajtů v paměti, které byly přiděleny funkcí při spuštění profilace. Číslo zahrnuje paměť, která byla přidělena voláním funkce volané funkce.<br />– Pro funkci volajícího je počet celkových bajtů instancí aktuální funkce, které byly vygenerovány voláními z této volající funkce.<br />– Pro funkci volaný počet bajtů, které byly přiděleny instancemi této funkce, které byly vygenerovány voláními z aktuální funkce. Toto číslo zahrnuje bajty, které byly přiděleny funkcemi, které byly volány touto funkcí volaný.|
|**% Celkových bajtů**|Procentuální podíl všech bajtů paměti, které byly přiděleny při spuštění profilace, včetně přidělení této funkce.|

## <a name="elapsed-inclusive-values"></a>Uplynulé celkové hodnoty
 Uplynulé celkové hodnoty udávají čas, kdy byla funkce v zásobníku volání. Čas zahrnuje čas strávený v podřízených funkcích a v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý celkový čas**|– Pro aktuální funkci čas strávený ve funkci. Hodnota zahrnuje čas strávený v podřízených funkcích a v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br />– Pro funkci volajícího je to množství uplynulého celkového času aktuální funkce, která byla vygenerována voláními z této volající funkce.<br />– Pro funkci volaného, čas strávený touto funkcí, který byl vygenerován voláními z aktuální funkce. Hodnota zahrnuje čas strávený v podřízených funkcích a v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.|
|**% Uplynulého celkového času**|Procento celkového uplynulého celkového času běhu profilace, které bylo v tomto kontextu stráveno v uplynulém čase této funkce.|
|**Průměrný uplynulý celkový čas**|Průměrný uplynulý celkový čas volání této funkce v tomto kontextu.|
|**Maximální uplynulý celkový čas**|Maximální uplynulý celková doba volání této funkce v tomto kontextu.|
|**Minimální uplynulý celkový čas**|Minimální uplynulý celkový čas volání této funkce v tomto kontextu.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé exkluzivní hodnoty označují čas, kdy byla funkce přímo spuštěna v horní části zásobníku volání. Čas zahrnuje čas volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace, ale nezahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý výhradní čas**|– Pro aktuální funkci čas, který byl stráven při provádění těla funkce. Hodnota vyloučí čas, který byl stráven v podřízených funkcích, ale obsahuje volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br />– Pro funkci volajícího je to množství uplynulého výhradního času aktuální funkce, která byla vygenerována voláními z této volající funkce.<br />– Pro funkci volaného, čas strávený touto funkcí, který byl vygenerován voláními z aktuální funkce. Hodnota vylučuje čas, který byl vyčerpán v podřízených funkcích funkce volaný, ale obsahuje volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.|
|**% Uplynulého výhradního času**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo v tomto kontextu stráveno celkovým neúplným časem této funkce.|
|**Průměrný uplynulý výhradní čas**|Průměrný uplynulý výhradní čas volání této funkce v tomto kontextu.|
|**Maximální uplynulý výhradní čas**|Maximální uplynulý výhradní čas volání této funkce v tomto kontextu.|
|**Minimální uplynulý výhradní čas**|Minimální uplynulý výhradní čas volání této funkce v tomto kontextu.|

## <a name="application-inclusive-values"></a>Hodnoty zahrnující aplikace
 Hodnoty pro všechny aplikace označují čas, kdy byla funkce v zásobníku volání. Čas neobsahuje čas strávený voláním operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace, ale obsahuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Celková doba aplikace**|– Pro aktuální funkci čas strávený ve funkci a jejích podřízených funkcích. Hodnota vylučuje čas, který byl stráven v voláních do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br />– Pro funkci volajícího je množství aplikace zahrnující čas aktuální funkce, která byla vygenerována voláním z této volající funkce.<br />– Pro funkci volaný byl čas strávený touto funkcí a jejími podřízenými funkcemi generovanými voláními z aktuální funkce. Tato hodnota neobsahuje čas strávený voláním operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.|
|**% Celkového času aplikace**|Procento celkového uplynulého celkového času běhu profilace, které bylo v tomto kontextu stráveno v celkovém čase aplikace této funkce.|
|**Průměrná doba aplikace (celková)**|Průměrná doba použití volání této funkce v tomto kontextu.|
|**Maximální celková doba aplikace**|Maximální doba volání této funkce v tomto kontextu (včetně celkového počtu aplikací).|
|**Minimální celková doba aplikace**|Minimální doba trvání volání této funkce v tomto kontextu (včetně celkového počtu aplikací).|

## <a name="application-exclusive-values"></a>Exkluzivní hodnoty aplikací
 Hodnoty exkluzivní pro aplikace označují čas strávený ve funkci bez času stráveného v podřízených funkcích. Uvedený čas také vyloučí čas, který byl stráven v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.

|Sloupec|Popis|
|------------|-----------------|
|**Výhradní čas aplikace**|– Pro aktuální funkci čas, který byl stráven při provádění těla funkce. Hodnota neobsahuje čas strávený v podřízených funkcích, ani nezahrnuje volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br />– Pro funkci volajícího se jedná o velikost výhradního času aplikace, která byla vygenerována voláním z této volající funkce.<br />– Pro funkci volaného, čas strávený touto funkcí, který byl vygenerován voláními z aktuální funkce. Hodnota neobsahuje čas, který byl vyčerpán v podřízených funkcích funkce volaný, ani nezahrnuje volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.|
|**% Výhradního času aplikace**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo v tomto kontextu stráveno v celkovém čase aplikace této funkce.|
|**Průměrný výhradní čas aplikace**|Průměrná doba použití pro volání této funkce v tomto kontextu.|
|**Maximální výhradní čas aplikace**|Maximální výhradní čas aplikace pro volání této funkce v tomto kontextu.|
|**Minimální výhradní čas aplikace**|Minimální výhradní čas aplikace pro volání této funkce v tomto kontextu.|

## <a name="see-also"></a>Viz také
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení Volající/Volaný – data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Zobrazení Volající/Volaný – data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)
- [Zobrazení Volající/Volaný – data vzorkování](../profiling/caller-callee-view-sampling-data.md)
