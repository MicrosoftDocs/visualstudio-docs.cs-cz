---
title: Zobrazení volaný volající – data vzorkování paměti .NET | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74773306"
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Zobrazení Volající/Volaný – data vzorkování paměti .NET
Zobrazení volající/volaný zobrazuje data profilace paměti .NET pro vybranou funkci a její nadřazené a podřízené funkce. Zobrazení volající/volaný obsahuje tři mřížky.

 V prostřední mřížce se zobrazí **aktuální funkce** a zobrazí informace o profilaci paměti vybrané funkce. Hodnoty zahrnují všechna ukázková volání funkce.

 **Funkce, které se nazývají aktuální funkce** , se zobrazí v horní mřížce a zobrazuje množství hodnoty vybrané (aktuální) funkce, která byla vygenerována voláními z funkce volající (nadřazená).

 **Funkce, které byly volány aktuální funkcí** , se zobrazí v dolní mřížce a zobrazí data profilace paměti pro volané (podřízené) funkce vybrané funkce, pokud byla podřízená funkce volána aktuální funkcí.

 Dvojím kliknutím na řádek volajícího nebo volaného řádku můžete nastavit, aby byl řádek aktuální funkce.

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|
|**Název funkce**|Plně kvalifikovaný název funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Adresa funkce|
|**Textový**|Kontext funkce:<br /><br /> **0** – aktuální funkce<br /><br /> **1** – funkce, která volá aktuální funkci<br /><br /> **2** – funkce, která je volána aktuální funkcí<br /><br /> Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|
|**Obsah**|Hloubka funkce ve stromu volání. Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|
|**Celkové alokace**|– Pro aktuální funkci počet objektů, které byly přiděleny funkcí při spuštění profilace. Toto číslo zahrnuje objekty, které byly vytvořeny ve funkcích volaný.<br />– Pro funkci volajícího je počet celkových přidělení aktuální funkce, které byly vygenerovány voláními z této funkce.<br />– Pro funkci volaného je počet objektů, které byly přiděleny instancemi této funkce, které byly volány aktuální funkcí. Číslo zahrnuje přidělení, která byla vytvořena funkcemi, které byly volány funkcí volaný.|
|**% Celkových přidělení**|Procentuální podíl všech objektů, které byly vytvořeny v rámci profilace, které byly zahrnuty do přidělení této funkce.|
|**Exkluzivní přidělení**|– Pro aktuální funkci počet objektů, které byly vytvořeny v době, kdy funkce prováděla kód těla funkce (to znamená, když funkce byla v horní části zásobníku volání). Počet nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány funkcí.<br />– Pro funkci volajícího je číslo exkluzivní alokace aktuální funkce, která byla vygenerována voláním z této funkce.<br />– Pro funkci volaného je počet objektů, které byly vytvořeny instancemi této funkce, které byly volány aktuální funkcí. Počet nezahrnuje objekty, které byly vytvořeny funkcemi, které byly volány funkcí volaný.|
|**% Exkluzivní alokace**|Procentuální podíl všech objektů, které byly vytvořeny v rámci profilace, které byly zahrnuty do přidělení této funkce.|
|**Včetně bajtů**|– Pro aktuální funkci počet bajtů paměti, které byly přiděleny funkcí při spuštění profilace. Číslo zahrnuje paměť, která byla přidělena ve funkcích, které byly volány touto funkcí.<br />– Pro funkci volajícího je počet celkových bajtů aktuální funkce, které byly vygenerovány z volání funkcí volajícího.<br />– Pro funkci volaný počet bajtů, které byly přiděleny instancemi této funkce, které byly vygenerovány voláními z aktuální funkce. Číslo zahrnuje bajty, které byly přiděleny funkcemi, které byly volány funkcí volaný.|
|**% Celkových bajtů**|Procentuální podíl všech bajtů paměti, které byly přiděleny při spuštění profilace, včetně přidělení této funkce.|
|**Exkluzivní počet bajtů**|– Pro aktuální funkci počet bajtů paměti, které byly přiděleny funkcí při spuštění profilace. Toto číslo nezahrnuje paměť, která byla přidělena funkcemi, které byly volány aktuální funkcí.<br />– Pro funkci volajícího se jedná o počet exkluzivních bajtů aktuální funkce, které byly vygenerovány voláními z funkce Caller.<br />– Pro funkci volaný počet bajtů, které byly přiděleny instancemi funkce, které byly vygenerovány voláními z aktuální funkce. Počet nezahrnuje bajty, které byly přiděleny funkcemi, které byly volány funkcí volaný.|
|**% Exkluzivních bajtů**|Procento všech bajtů paměti, které byly přiděleny při spuštění profilace, které byly exkluzivním přidělením této funkce.|

## <a name="see-also"></a>Viz také:
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení Volající/Volaný – data instrumentace paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Zobrazení Volající/Volaný – data vzorkování](../profiling/caller-callee-view-sampling-data.md)
- [Zobrazení Volající/Volaný – data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)
