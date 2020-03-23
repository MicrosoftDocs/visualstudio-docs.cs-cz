---
title: Zobrazení volajícího a volaní - NET Memory Instrumentation Data | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 3c51f4bc1e823f565670bf1f6df77553ff4658d6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779724"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Zobrazení volajícího/volaných - data přístrojové instrumentace paměti .NET
Zobrazení volajícího a volaného dat profilování paměti .NET, která byla shromážděna pomocí metody instrumentace, zobrazuje data přidělení a časování pro vybranou funkci a nadřazené a podřízené funkce této vybrané funkce. Zobrazení Volající/Volaný obsahuje tři mřížky.

 **Aktuální funkce** je zobrazena ve střední mřížce a zobrazuje informace o profilování paměti o vybrané funkci. Hodnoty zahrnují všechny vzorkované volání funkce.

 **Funkce, které volaly aktuální funkci,** jsou zobrazeny v horní mřížce a zobrazují hodnotu vybrané (aktuální) funkce, která byla generována voláním z funkce volajícího (nadřazeného).

 **Funkce, které byly volány aktuální funkcí,** jsou zobrazeny v dolní mřížce a zobrazují data profilování paměti pro volané (podřízené) funkce vybrané funkce, když byla podřízená funkce volána aktuální funkcí.

 Poklepáním volajícího nebo volaný řádek funkce, aby tento řádek aktuální funkce.

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
|**ID procesu**|ID procesu profilování spustit.|
|**Název procesu**|Název, který je přiřazen k procesu.|
|**Režie výhradní sondy času**|Čas režie pro tuto funkci z důvodu instrumentace. Režie sondy byla odečtena od všech výhradních časů.|
|**Režie sondy včetně času**|Čas režie pro tuto funkci a její podřízené funkce z důvodu instrumentace. Režie sondy byla odečtena od all inclusive časů.|
|**Typ**|Kontext funkce:<br /><br /> **0** - aktuální funkce<br /><br /> **1** - funkce, která volá aktuální funkci<br /><br /> **2** - funkce, která je volána aktuální funkcí<br /><br /> Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|
|**Název kořenové funkce**|Název aktuální funkce. Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|

## <a name="net-memory-allocation-values"></a>Hodnoty přidělení paměti .NET

|Sloupec|Popis|
|------------|-----------------|
|**Výhradní přidělení**|- Pro aktuální funkci počet objektů, které byly vytvořeny při spuštění funkce kódu v těle funkce (to znamená, když byla funkce v horní části zásobníku volání). Číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány touto funkcí.<br />- Pro volající funkce číslo výhradní přidělení aktuální funkce, které byly generovány volání z této funkce volajícího.<br />- Pro volanou funkci počet objektů, které byly vytvořeny instancemi této funkce, které byly volány aktuální funkcí. Toto číslo nezahrnuje objekty, které byly vytvořeny funkcemi, které byly volány volanou funkcí.|
|**Výhradní přidělení %**|Procento všech objektů, které byly vytvořeny v profilování spustit, které byly výhradní přidělení této funkce.|
|**Inkluzivní přidělení**|- Pro aktuální funkce počet objektů, které byly přiděleny funkce v profilování spustit. Číslo zahrnuje objekty, které byly vytvořeny v volané funkce, které byly volány funkce.<br />- Pro volající funkce, číslo včetně přidělení aktuální funkce, které byly generovány volání z této funkce volajícího.<br />- Pro volanou funkci počet objektů, které byly přiděleny instancemi této funkce, které byly generovány voláníz aktuální funkce. Číslo zahrnuje přidělení provedené funkcemi, které byly volány touto volanou funkcí.|
|**Včetně přidělení %**|Procento všech objektů, které byly vytvořeny v profilování spustit, které byly včetně přidělení této funkce.|
|**Exkluzivní bajty**|- Pro aktuální funkce počet bajtů paměti, které byly přiděleny funkce v profilování spustit. Číslo nezahrnuje paměť, která byla přidělena v volaných funkcích, které byly volány funkcí.<br />- Pro volající funkce, číslo výhradní bajty aktuální funkce, které byly generovány z volání této funkce volajícího.<br />- Pro volanou funkci počet bajtů, které byly přiděleny instancemi této funkce, které byly generovány voláníz aktuální funkce. Číslo nezahrnuje bajty, které byly přiděleny funkcemi, které byly volány volanou funkcí.|
|**Výhradní bajty %**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly výhradní přidělení této funkce.|
|**Včetně bajtů**|- Pro aktuální funkce počet bajtů v paměti, které byly přiděleny funkce v profilování spustit. Číslo zahrnuje paměť, která byla přidělena v volaných funkcích, které byly volány funkcí.<br />- Pro volající funkce, počet včetně bajtů instance aktuální funkce, které byly generovány volání z této funkce volajícího.<br />- Pro volanou funkci počet bajtů, které byly přiděleny instancemi této funkce, které byly generovány voláníz aktuální funkce. Číslo zahrnuje bajty, které byly přiděleny funkcemi, které byly volány touto volanou funkcí.|
|**Včetně bajtů %**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly včetně přidělení této funkce.|

## <a name="elapsed-inclusive-values"></a>Uplynulé včetně hodnot
 Uplynulé včetně hodnoty označují čas, který byla funkce v zásobníku volání. Čas zahrnuje čas strávený v podřízených funkcích a volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý včetně času**|- Pro aktuální funkci čas, který byl strávený ve funkci. Hodnota zahrnuje čas strávený v podřízených funkcí chod a volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br />- Pro volající funkce, množství uplynulý včetně čas aktuální funkce, která byla generována volání z této funkce volajícího.<br />- Pro volanou funkci čas, který byl vyčerpán v této funkci, která byla generována volání z aktuální funkce. Hodnota zahrnuje čas strávený v podřízených funkcí chod a volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.|
|**Uplynulý včetně času %**|Procento celkového uplynulého včetně času profilování, který byl vyčerpán v uplynulém včetně času této funkce v tomto kontextu.|
|**Avg Uplynulý včetně čas**|Průměrná uplynulá včetně čas volání této funkce v tomto kontextu.|
|**Maximální uplynulý včetně času**|Maximální uplynulý včetně čas volání této funkce v tomto kontextu.|
|**Min uplynulý včetně času**|Minimální uplynulý včetně čas volání této funkce v tomto kontextu.|

## <a name="elapsed-exclusive-values"></a>Uplynulé výhradní hodnoty
 Uplynulé výhradní hodnoty označují čas, který byla funkce přímo spuštěna v horní části zásobníku volání. Čas zahrnuje čas ve volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale nezahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Uplynulý exkluzivní čas**|- Pro aktuální funkci čas, který byl vynaložen na provádění těla funkce. Hodnota vylučuje čas strávený v podřízených funkcích, ale zahrnuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br />- Pro volající funkce, množství uplynulý výhradní čas aktuální funkce, která byla generována volání z této funkce volajícího.<br />- Pro volanou funkci čas, který byl vyčerpán v této funkci, která byla generována volání z aktuální funkce. Hodnota vylučuje čas, který byl stráven v podřízených funkcích volané funkce, ale zahrnuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.|
|**Uplynulý výhradní čas %**|Procento celkového uplynulého výhradního času spuštění profilování, který byl vyčerpán v celkovém uplynulém výhradním čase této funkce v tomto kontextu.|
|**Avg uplynulý exkluzivní čas**|Průměrná uplynulá výhradní doba volání této funkce v tomto kontextu.|
|**Maximální uplynulý exkluzivní čas**|Maximální uplynulý výhradní čas volání této funkce v tomto kontextu.|
|**Min uplynulý exkluzivní čas**|Minimální uplynulý výhradní čas volání této funkce v tomto kontextu.|

## <a name="application-inclusive-values"></a>Včetně hodnot aplikace
 Hodnoty zahrnující aplikaci označují čas, kdy byla funkce v zásobníku volání. Čas nezahrnuje čas strávený při volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu, ale zahrnuje čas strávený v podřízených funkcích.

|Sloupec|Popis|
|------------|-----------------|
|**Včetně aplikace**|- Pro aktuální funkci, čas, který byl vynaložen ve funkci a její podřízené funkce. Hodnota vylučuje čas, který byl vynaložen na volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br />- Pro volající funkce, množství aplikace včetně času aktuální funkce, která byla generována volání z této funkce volajícího.<br />- Pro volanou funkci čas, který byl vyčerpán v této funkci a jeho podřízené funkce, které byly generovány volání z aktuální funkce. Hodnota nezahrnuje čas, který byl vynaložen na volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.|
|**Včetně aplikace Čas %**|Procento celkového uplynulého včetně času spuštění profilování, který byl vynaložen v celkové aplikaci včetně času této funkce v tomto kontextu.|
|**Avg Aplikace včetně času**|Průměrná doba aplikace včetně volání této funkce v tomto kontextu.|
|**Maximální čas včetně aplikace**|Maximální doba aplikace včetně volání této funkce v tomto kontextu.|
|**Min aplikace včetně času**|Minimální doba aplikace včetně volání této funkce v tomto kontextu.|

## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace
 Výhradní hodnoty aplikace označují čas, který byl strávený ve funkci, s výjimkou času stráveného v podřízených funkcích. Uvedený čas také vylučuje čas, který byl vynaložen volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní čas aplikace**|- Pro aktuální funkci čas, který byl vynaložen na provádění těla funkce. Hodnota nezahrnuje čas strávený v podřízených funkcích, ani volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br />- Pro volající funkce, množství aplikace výhradní čas aktuální funkce, která byla generována volání z této funkce volajícího.<br />- Pro volanou funkci čas, který byl vyčerpán v této funkci, která byla generována volání z aktuální funkce. Hodnota nezahrnuje čas strávený v podřízených funkcích volané funkce, ani nezahrnuje volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.|
|**Výhradní čas aplikace %**|Procento celkového uplynulého výhradního času spuštění profilování, který byl vyčerpán v celkovém výhradním čase aplikace této funkce v tomto kontextu.|
|**Exkluzivní čas aplikace AVG**|Průměrná aplikace výhradní čas volání této funkce v tomto kontextu.|
|**Maximální exkluzivní čas aplikace**|Maximální výhradní čas aplikace volání této funkce v tomto kontextu.|
|**Min aplikace Exkluzivní čas**|Minimální výhradní čas aplikace volání této funkce v tomto kontextu.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení volajícího/volaných – vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Zobrazení volajícího/volaných - data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)
- [Zobrazení volajícího/volaných - vzorkovací data](../profiling/caller-callee-view-sampling-data.md)
