---
title: Zobrazení stromu volání – data instrumentace paměti .NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 2066959578987e358f8c1c91dcbda1eeb6f79f26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74773594"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Zobrazení stromu volání – data instrumentace paměti .NET
Zobrazení stromu volání dat profilace přidělení paměti .NET, která byla shromážděna pomocí metody instrumentace, zobrazuje cesty spuštění funkce, které byly provázány v profilované aplikaci. Kořen stromu je vstupní bod do aplikace nebo komponenty. Každý uzel funkce obsahuje seznam všech funkcí, které volal, a data o paměti a časování .NET pro funkci.

 Hodnoty ve stromovém zobrazení volání jsou pro instance funkcí, které byly volány nadřazenou funkcí ve stromu volání. Procentuální hodnoty se vypočtou porovnáním hodnoty instance funkce s celkovým počtem nebo velikostí přidělení při spuštění profilace.

## <a name="highlight-the-execution-hot-path"></a>Zvýraznit cestu k vykonání za běhu
 Zobrazení stromu volání může rozšiřovat a zvýrazňovat cestu spuštění procesu nebo funkce, která vytvořila největší nebo nejvíc objektů paměti. Chcete-li zobrazit nejvíce aktivních cest, klikněte pravým tlačítkem myši na proces nebo funkci a potom klikněte na **položku Rozbalit**kritickou cestu.

## <a name="set-the-call-tree-root-node"></a>Nastavit kořenový uzel stromu volání
 Každý proces v průběhu profilace se zobrazuje jako kořenový uzel. Můžete nastavit počáteční uzel zobrazení stromu volání kliknutím pravým tlačítkem myši na uzel, který chcete nastavit jako spouštěcí uzel, a následným výběrem možnosti **Nastavit kořen**.

 Když nastavíte kořenový uzel, eliminují se všechny ostatní záznamy z zobrazení kromě podstromu vybraného uzlu. Kořenový uzel můžete obnovit zpátky na uzel, který jste si prohlíželi. v okně zobrazení stromu volání klikněte pravým tlačítkem myši a vyberte **obnovit kořen**.

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
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název, který je přiřazen procesu.|
|**Výhradní čas režie testu**|Časová režie této funkce, která je způsobena instrumentací. Režie testu byla odečtena od všech výhradních časů.|
|**Čas celkové režie testu**|Časová režie této funkce a jejích podřízených funkcí, které jsou způsobeny instrumentací. Režie testu byla odečtena od všech celkových časů.|
|**Typ**|Kontext funkce:<br /><br /> -   **0** – aktuální funkce<br />-   **1** – funkce, která volá aktuální funkci<br />-   **2** – funkce, která je volána aktuální funkcí<br /><br /> Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|
|**Název kořenové funkce**|Název aktuální funkce Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|

## <a name="net-memory-values"></a>Hodnoty paměti .NET
 Celkové hodnoty paměti .NET funkce označují počet (přidělení) a velikost (v bajtech) objektů, které byly vytvořeny funkcí a funkcemi, které byly volány funkcí.

 Hodnoty exkluzivní paměti označují počet a velikost objektů, které byly vytvořeny kódem v těle funkce a nikoli funkcemi, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Celkové alokace**|Počet objektů, které byly přiděleny instancemi této funkce, které byly volány nadřazenou funkcí ve stromu volání. Toto číslo zahrnuje přidělení, která byla provedena pomocí podřízených funkcí.|
|**% Celkových přidělení**|Procentuální podíl všech objektů, které byly vytvořeny v rámci profilace, byly zahrnuty do přidělení instancí funkcí, které byly volány nadřazenou funkcí ve stromu volání.|
|**Exkluzivní přidělení**|Počet objektů, které byly přiděleny instancemi této funkce, které byly volány nadřazenou funkcí ve stromu volání. Toto číslo nezahrnuje přidělení, která byla provedena v podřízených funkcích.|
|**% Exkluzivní alokace**|Procentuální podíl všech objektů, které byly vytvořeny v rámci profilace, které byly exkluzivním přidělením instancí funkcí, které byly volány nadřazenou funkcí ve stromu volání.|

## <a name="elapsed-inclusive-values"></a>Uplynulé celkové hodnoty
 Uplynulé celkové hodnoty udávají čas, kdy byla funkce v zásobníku volání. Čas zahrnuje čas strávený ve funkcích, které byly volány funkcí a v volání operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý celkový čas**|Celkový uplynulý celková doba všech volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|
|**% Uplynulého celkového času**|Procento celkového uplynulého celkového času běhu profilování, které bylo stráveno v celkovém uplynulém časovém intervalu této funkce, pokud bylo voláno nadřazenou funkcí ve stromu volání.|
|**Průměrný uplynulý celkový čas**|Průměrně uplynulý celkový čas volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|
|**Maximální uplynulý celkový čas**|Maximální uplynulý celkový čas volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|
|**Minimální uplynulý celkový čas**|Minimální uplynulý celkový čas volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé exkluzivní hodnoty označují čas, kdy byla funkce přímo spuštěna v horní části zásobníku volání. Čas zahrnuje čas volání do operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace. Čas však neobsahuje čas strávený ve funkcích, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý výhradní čas**|Celkový uplynulý výhradní čas všech volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|
|**% Uplynulého výhradního času**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo stráveno celkovým výhradním časem této funkce, pokud bylo voláno nadřazenou funkcí ve stromu volání.|
|**Průměrný uplynulý výhradní čas**|Průměrný uplynulý výhradní čas volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|
|**Maximální uplynulý výhradní čas**|Maximální uplynulý výhradní čas volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|
|**Minimální uplynulý výhradní čas**|Minimální uplynulý výhradní čas volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|

## <a name="application-inclusive-values"></a>Hodnoty zahrnující aplikace
 Hodnoty pro všechny aplikace označují čas, kdy byla funkce v zásobníku volání. Čas neobsahuje čas strávený voláním operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace. Čas zahrnuje čas strávený v podřízených funkcích, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Celková doba aplikace**|Celková celková doba všech volání této funkce v aplikaci, která byla volána nadřazenou funkcí ve stromu volání.|
|**% Celkového času aplikace**|Procento celkového uplynulého celkového času běhu profilování, které bylo stráveno v celkovém čase aplikace této funkce, pokud bylo voláno nadřazenou funkcí ve stromu volání.|
|**Průměrná doba aplikace (celková)**|Průměrná doba aplikace při volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|
|**Maximální celková doba aplikace**|Maximální doba volání této funkce v aplikaci, která byla volána nadřazenou funkcí ve stromu volání.|
|**Minimální celková doba aplikace**|Minimální doba (včetně) aplikace při volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|

## <a name="application-exclusive-values"></a>Exkluzivní hodnoty aplikací
 Hodnoty exkluzivní pro aplikace označují čas strávený ve funkci bez času stráveného v podřízených funkcích, které byly volány funkcí. Čas také vyloučí volání do operačního systému, jako jsou přepínače kontextu a vstupně-výstupní operace.

|Sloupec|Popis|
|------------|-----------------|
|**Výhradní čas aplikace**|Celková aplikace exkluzivní dobu všech volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|
|**% Výhradního času aplikace**|Procento celkového uplynulého výhradního času spuštění profilování, které bylo stráveno v celkovém čase aplikace této funkce, pokud bylo voláno nadřazenou funkcí ve stromu volání.|
|**Průměrný výhradní čas aplikace**|Průměrná doba použití aplikace při volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|
|**Maximální výhradní čas aplikace**|Maximální výhradní čas aplikace pro volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|
|**Minimální výhradní čas aplikace**|Minimální výhradní čas aplikace pro volání této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|
