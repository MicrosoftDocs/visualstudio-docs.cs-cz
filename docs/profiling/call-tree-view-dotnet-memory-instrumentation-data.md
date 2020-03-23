---
title: Zobrazení stromu volání – data instrumentace paměti .NET | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773594"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Zobrazení stromu volání – data instrumentace paměti .NET
Strom volání zobrazení dat profilování přidělení paměti .NET, která byla shromážděna pomocí metody instrumentace, zobrazí cesty spuštění funkce, které byly provázány v profilované aplikaci. Kořen stromu je vstupníbod do aplikace nebo součásti. Každý uzel funkce obsahuje seznam všech funkcí, které volal, a data paměti .NET a časování pro funkci.

 Hodnoty v zobrazení Strom volání jsou pro instance funkcí, které byly volány nadřazenou funkcí ve stromu volání. Procentuální hodnoty se vypočítají porovnáním hodnoty instance funkce s celkovým počtem nebo velikostí přidělení v systému profilování.

## <a name="highlight-the-execution-hot-path"></a>Zvýrazněte cestu spuštění hot
 Strom volání zobrazení můžete rozbalit a zvýraznit cestu spuštění procesu nebo funkce, která vytvořila největší nebo nejvíce objektů paměti. Chcete-li zobrazit nejaktivnější cestu, klepněte pravým tlačítkem myši na proces nebo funkci a potom klepněte na příkaz **Rozbalit aktivní cestu**.

## <a name="set-the-call-tree-root-node"></a>Nastavení kořenového uzlu kořenového stromu volání
 Každý proces v profilování spustit je zobrazen jako kořenový uzel. Počáteční uzel zobrazení Strom volání můžete nastavit tak, že kliknete pravým tlačítkem myši na uzel, který chcete nastavit jako počáteční uzel, a pak vyberete **nastavit kořenový adresář**.

 Když nastavíte kořenový uzel, odstraníte všechny ostatní položky ze zobrazení kromě podstromu vybraného uzlu. Kořenový uzel můžete obnovit zpět na uzel, který jste si prohlíželi; klepněte pravým tlačítkem myši v okně Zobrazení stromu volání a vyberte **příkaz Obnovit kořenový adresář**.

## <a name="general"></a>Obecné

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
|**Název procesu**|Název, který je přiřazen k procesu.|
|**Režie výhradní sondy času**|Čas režie pro tuto funkci, která je způsobena instrumentace. Režie sondy byla odečtena od všech výhradních časů.|
|**Režie sondy včetně času**|Čas režie pro tuto funkci a její podřízené funkce, která je způsobena instrumentace. Režie sondy byla odečtena od all inclusive časů.|
|**Typ**|Kontext funkce:<br /><br /> -   **0** - aktuální funkce<br />-   **1** - funkce, která volá aktuální funkci<br />-   **2** - funkce, která je volána aktuální funkcí<br /><br /> Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|
|**Název kořenové funkce**|Název aktuální funkce. Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|

## <a name="net-memory-values"></a>Hodnoty paměti .NET
 Včetně hodnoty paměti .NET funkce označují počet (přidělení) a velikost (bajty) objektů, které byly vytvořeny funkcí a funkcemi, které byly volány funkcí.

 Výhradní hodnoty paměti označují počet a velikost objektů, které byly vytvořeny kódem v těle funkce a nikoli funkcemi, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Inkluzivní přidělení**|Počet objektů, které byly přiděleny instance této funkce, které byly volány nadřazenou funkcí ve stromu volání. Toto číslo zahrnuje přidělení, které byly provedeny podřízené funkce.|
|**Včetně přidělení %**|Procento všech objektů, které byly vytvořeny v profilování spustit, které byly včetně přidělení instance funkce, které byly volány nadřazené funkce ve stromu volání.|
|**Výhradní přidělení**|Počet objektů, které byly přiděleny instance této funkce, které byly volány nadřazenou funkcí ve stromu volání. Toto číslo nezahrnuje přidělení, které byly provedeny podřízené funkce.|
|**Výhradní přidělení %**|Procento všech objektů, které byly vytvořeny v profilování spustit, které byly výhradní přidělení instance funkce, které byly volány nadřazené funkce ve stromu volání.|

## <a name="elapsed-inclusive-values"></a>Uplynulé včetně hodnot
 Uplynulé včetně hodnoty označují čas, který byla funkce v zásobníku volání. Čas zahrnuje čas strávený ve funkcích, které byly volány funkcí a voláním operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý včetně času**|Celkový uplynulý včetně čas všech volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Uplynulý včetně času %**|Procento celkového uplynulého včetně času spuštění profilování, který byl vynaložen v celkovém uplynulý včetně času této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Avg Uplynulý včetně čas**|Průměrná uplynulá doba volání této funkce, kdy byla volána nadřazenou funkcí ve stromu volání.|
|**Maximální uplynulý včetně času**|Maximální uplynulý včetně čas volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Min uplynulý včetně času**|Minimální uplynulý včetně čas volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé výhradní hodnoty označují čas, který byla funkce přímo spuštěna v horní části zásobníku volání. Čas zahrnuje čas ve volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu. Čas však nezahrnuje čas strávený ve funkcích, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý exkluzivní čas**|Celkový uplynulý výhradní čas všech volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Uplynulý výhradní čas %**|Procento celkového uplynulého výhradního času spuštění profilování, který byl stráven v celkovém uplynulém výhradním čase této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Avg uplynulý exkluzivní čas**|Průměrná uplynulá výhradní doba volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Maximální uplynulý exkluzivní čas**|Maximální uplynulý výhradní čas volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Min uplynulý exkluzivní čas**|Minimální uplynulý výhradní čas volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|

## <a name="application-inclusive-values"></a>Včetně hodnot aplikace
 Hodnoty zahrnující aplikaci označují čas, kdy byla funkce v zásobníku volání. Čas nezahrnuje čas strávený při volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu. Čas zahrnuje čas strávený v podřízených funkcích, které byly volány funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Včetně aplikace**|Celkový čas aplikace včetně všech volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Včetně aplikace Čas %**|Procento celkového uplynulého včetně času spuštění profilování, který byl vynaložen v celkové aplikaci včetně času této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Avg Aplikace včetně času**|Průměrná doba aplikace včetně volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Maximální čas včetně aplikace**|Maximální doba aplikace včetně volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Min aplikace včetně času**|Minimální doba aplikace včetně volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|

## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace
 Výhradní hodnoty aplikace označují čas, který byl strávený ve funkci, s výjimkou času stráveného v podřízených funkcích, které byly volány funkcí. Čas také vylučuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní čas aplikace**|Celkový výhradní čas aplikace všech volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Výhradní čas aplikace %**|Procento celkového uplynulého výhradního času spuštění profilování, který byl vynaložen v celkovém výhradním čase aplikace této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Exkluzivní čas aplikace AVG**|Průměrná výhradní doba aplikace volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Maximální exkluzivní čas aplikace**|Maximální výhradní čas aplikace volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Min aplikace Exkluzivní čas**|Minimální výhradní čas aplikace volání této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
