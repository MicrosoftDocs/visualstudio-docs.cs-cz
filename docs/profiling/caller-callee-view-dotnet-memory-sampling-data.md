---
title: Zobrazení volajícího a volaní – vzorkování paměti .NET | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 50e278e858ea086c83b29ef4eebf6b48ee8e477e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773306"
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Zobrazení volajícího/volaných – vzorkování paměti .NET
Zobrazení Volající/Volaný zobrazuje data profilování paměti .NET pro vybranou funkci a její nadřazené a podřízené funkce. Zobrazení Volající/Volaný obsahuje tři mřížky.

 **Aktuální funkce** je zobrazena ve střední mřížce a zobrazuje informace o profilování paměti o vybrané funkci. Hodnoty zahrnují všechny vzorkované volání funkce.

 **Funkce, které volaly aktuální funkci,** jsou zobrazeny v horní mřížce a zobrazují hodnotu vybrané (aktuální) funkce, která byla generována voláním z funkce volajícího (nadřazeného).

 **Funkce, které byly volány aktuální funkcí,** jsou zobrazeny v dolní mřížce a zobrazují data profilování paměti pro volané (podřízené) funkce vybrané funkce, když byla podřízená funkce volána aktuální funkcí.

 Poklepáním volajícího nebo volaný řádek funkce, aby tento řádek aktuální funkce.

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|
|**Název funkce**|Plně kvalifikovaný název funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Adresa funkce.|
|**Typ**|Kontext funkce:<br /><br /> **0** - aktuální funkce<br /><br /> **1** - funkce, která volá aktuální funkci<br /><br /> **2** - funkce, která je volána aktuální funkcí<br /><br /> Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|
|**Úroveň**|Hloubka funkce ve stromu volání. Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|
|**Inkluzivní přidělení**|- Pro aktuální funkce počet objektů, které byly přiděleny funkce v profilování spustit. Toto číslo zahrnuje objekty, které byly vytvořeny ve funkcích volaný.<br />- Pro volající funkce číslo včetně přidělení aktuální funkce, které byly generovány volání z této funkce.<br />- Pro volanou funkci počet objektů, které byly přiděleny instancemi této funkce, které byly volány aktuální funkcí. Číslo zahrnuje přidělení, které byly provedeny funkce, které byly volány volanou funkcí.|
|**Včetně přidělení %**|Procento všech objektů, které byly vytvořeny v profilování spustit, které byly včetně přidělení této funkce.|
|**Výhradní přidělení**|- Pro aktuální funkci počet objektů, které byly vytvořeny při spuštění funkce kódu těla funkce (to znamená, když byla funkce v horní části zásobníku volání). Číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány funkcí.<br />- Pro volající funkce číslo výhradní přidělení aktuální funkce, které byly generovány volání z této funkce.<br />- Pro volanou funkci počet objektů, které byly vytvořeny instancemi této funkce, které byly volány aktuální funkcí. Číslo nezahrnuje objekty, které byly vytvořeny funkcemi, které byly volány volanou funkcí.|
|**Výhradní přidělení %**|Procento všech objektů, které byly vytvořeny v profilování spustit, které byly včetně přidělení této funkce.|
|**Včetně bajtů**|- Pro aktuální funkce počet bajtů paměti, které byly přiděleny funkce v profilování spustit. Číslo zahrnuje paměť, která byla přidělena ve funkcích, které byly volány touto funkcí.<br />- Pro volající funkce, číslo včetně bajtů aktuální funkce, které byly generovány z volání volajícífunkce.<br />- Pro volanou funkci počet bajtů, které byly přiděleny instancemi této funkce, které byly generovány voláníz aktuální funkce. Číslo zahrnuje bajty, které byly přiděleny funkcemi, které byly volány volanou funkcí.|
|**Včetně bajtů %**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly včetně přidělení této funkce.|
|**Exkluzivní bajty**|- Pro aktuální funkce počet bajtů paměti, které byly přiděleny funkce v profilování spustit. Toto číslo nezahrnuje paměť, která byla přidělena funkcemi, které byly volány aktuální funkcí.<br />- Pro volající funkce, číslo výhradní bajty aktuální funkce, které byly generovány volání z volajícífunkce.<br />- Pro volanou funkci počet bajtů, které byly přiděleny instancemi funkce, které byly generovány voláním z aktuální funkce. Číslo nezahrnuje bajty, které byly přiděleny funkcemi, které byly volány volanou funkcí.|
|**Výhradní bajty %**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly výhradní přidělení této funkce.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení volajícího/volaných - data přístrojové paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Zobrazení volajícího/volaných - vzorkovací data](../profiling/caller-callee-view-sampling-data.md)
- [Zobrazení volajícího/volaných - data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)
