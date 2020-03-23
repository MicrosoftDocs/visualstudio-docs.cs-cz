---
title: Volající - Zobrazení volaných - vzorkovací data | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 008aa6bd9402cde760ffc61a613aba778c8ec96f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773267"
---
# <a name="callercallee-view---sampling-data"></a>Zobrazení volajícího/volaných - vzorkovací data
Zobrazení Volající/Volaný zobrazuje informace o profilování pro vybranou funkci a její nadřazené a podřízené funkce. Zobrazení Volající/Volaný obsahuje tři mřížky.

 **Aktuální funkce** je zobrazena ve střední mřížce a zobrazuje informace o profilování pro vybranou funkci. Hodnoty zahrnují všechny vzorkované volání funkce.

 **Funkce, které volaly aktuální funkci,** jsou zobrazeny v horní mřížce a zobrazují jednotlivé příspěvky volající (nadřazené) funkce k hodnotám vybrané (aktuální) funkce.

 **Funkce, které byly volány aktuální funkcí,** jsou zobrazeny v dolní mřížce a zobrazují informace o profilování volaných (podřízených) funkcí vybrané funkce, když byla podřízená funkce volána aktuální funkcí.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

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
|**Typ**|Kontext funkce:<br /><br /> -   **0** - aktuální funkce<br />-   **1** - funkce, která volá aktuální funkci<br />-   **2** - funkce, která je volána aktuální funkcí|
|**Název kořenové funkce**|Název aktuální funkce.|
|**Včetně vzorků**|- Pro aktuální funkci byl spuštěn počet vzorků, které byly odebrány, i když tato funkce nebo jedna z jejích podřízených funkcí byla spuštěna.<br />- Pro volající funkce, počet včetně vzorky aktuální funkce, které byly shromážděny při volání této funkce aktuální funkce.<br />- Pro volanou funkci počet včetně vzorků této funkce, které byly shromážděny při volání aktuální funkce této funkce.|
|**Včetně vzorků %**|Procento všech vzorků v profilování spustit, které byly včetně vzorky této funkce.|
|**Exkluzivní ukázky**|- Pro aktuální funkci počet vzorků v profilování spustit, které byly shromážděny, když tato funkce byla přímo spuštěna; to znamená, když tato funkce byla v horní části zásobníku volání. Ukázky, které jsou shromažďovány při provádění podřízených funkcí této funkce nejsou započítány do výhradnípočty.<br />- Pro volající funkce, počet výhradní vzorky aktuální funkce, které byly shromážděny při volání této funkce aktuální funkce.<br />- Pro volanou funkci počet výhradních vzorků této funkce, které byly shromážděny při volání aktuální funkce této funkce.|
|**Exkluzivní vzorky %**|Procento všech vzorků v profilování spustit, které byly výhradní ukázky této funkce.|

## <a name="see-also"></a>Viz také
- [Zobrazení volajícího/volaných – vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Zobrazení volajícího/volaných - data přístrojové paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Zobrazení volajícího/volaných - data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)
