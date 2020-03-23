---
title: Volající - Zobrazení volaných - Údaje o sporu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 083386a808f7b91a18b3ea685ae657118c723978
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779737"
---
# <a name="callercallee-view----contention-data"></a>Zobrazení volajícího/volaných - data tvrzení
Zobrazení Volající/Volaný zobrazuje informace o konfliktu pro vybranou funkci a její nadřazené a podřízené funkce. Zobrazení Volající/Volaný obsahuje tři mřížky.

 **Aktuální funkce** je zobrazena ve střední mřížce a zobrazuje informace o kolizi pro vybranou funkci. Hodnoty zahrnují všechny blokování tvrzení pro funkci.

 **Funkce, které volaly aktuální funkci,** jsou zobrazeny v horní mřížce a zobrazují jednotlivé příspěvky volající (nadřazené) funkce k hodnotám vybrané (aktuální) funkce.

 **Funkce, které byly volány aktuální funkcí,** jsou zobrazeny v dolní mřížce a zobrazují informace o konfliktech pro volané (podřízené) funkce vybrané funkce, když byla podřízená funkce volána aktuální funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Typ**|Kontext funkce:<br /><br /> -   **0** - aktuální funkce<br />-   **1** - funkce, která volá aktuální funkci<br />-   **2** - funkce, která je volána aktuální funkcí<br /><br /> Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|
|**Exkluzivní blokovaný čas**|- Pro aktuální funkci čas, kdy tato funkce byla zablokována z provádění kódu v těle funkce. Blokovaný čas ve funkcích volaných funkcí není zahrnut.<br />- Pro volající funkce část výhradní blokovaný čas aktuální funkce, ke kterým došlo, když tato funkce voláaktuální funkce.<br />- Pro volanou funkci čas, kdy byla tato funkce zablokována v provádění vlastního kódu, když byla tato funkce volána aktuální funkcí. Blokovaný čas v podřízených funkcích volaných není zahrnut.|
|**Výhradní blokovaný čas %**|Procento všech blokovaných čas v profilování spustit, který byl výhradní blokovaný čas pro tuto funkci v tomto kontextu.|
|**Exkluzivní tvrzení**|- Pro aktuální funkci, kolikrát tato funkce byla zablokována z provádění kódu v těle funkce. Konflikty, ke kterým došlo ve funkcích, které byly volány funkcí, nejsou zahrnuty.<br />- Pro volající funkce, počet výhradní tvrzení aktuální funkce, ke kterým došlo, když tato funkce voláaktuální funkce.<br />- Pro volanou funkci, kolikrát byla tato funkce zablokována v provádění kódu v těle funkce, když byla tato funkce volána aktuální funkcí. Konflikty, ke kterým došlo ve funkcích volané funkce nejsou zahrnuty.|
|**Výhradní tvrzení %**|Procento všech tvrzení v profilování spustit, které byly výhradní tvrzení pro tuto funkci v tomto kontextu.|
|**Adresa funkce**|Adresa funkce nebo token.|
|**Název funkce**|Plně kvalifikovaný název funkce.|
|**Včetně blokovaného času**|- Pro aktuální funkci byl zablokován čas, kdy tato funkce nebo jedna z funkcí, které byly volány touto funkcí, byla zablokována. Blokovaný čas ve funkcích, které byly volány aktuální funkcí, je zahrnut.<br />- Pro volající funkce, část včetně blokované čas aktuální funkce, ke kterým došlo, když tato funkce voláaktuální funkce.<br />- Pro volanou funkci byl čas, kdy tato funkce nebo jedna z funkcí, která byla volána funkcí, zablokován při volání této funkce aktuální funkcí. Blokovaný čas ve funkcích, které byly volány volanou funkcí, je součástí balení.|
|**Včetně blokovaného času %**|Procento všech blokovaných čas v profilování spustit, který byl včetně blokovaný čas pro tuto funkci v tomto kontextu.|
|**Inkluzivní tvrzení**|- Pro aktuální funkci, kolikrát tato funkce nebo jedna z funkcí, které byly volány funkce byla zablokována z provádění. Konflikty, ke kterým došlo ve funkcích, které byly volány funkcí, jsou zahrnuty.<br />- Pro volající funkce, počet včetně tvrzení aktuální funkce, ke kterým došlo, když tato funkce voláaktuální funkce.<br />- Pro volanou funkci, kolikrát tato funkce nebo jedna z funkcí, které byly volány funkcí, byly zablokovány při volání této funkce aktuální funkcí. Konflikty, ke kterým došlo ve funkcích volané funkce jsou zahrnuty.|
|**Inkluzivní tvrzení %**|Procento všech tvrzení v profilování spustit, které byly výhradní tvrzení pro tuto funkci v tomto kontextu.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu , ve kterém došlo k tvrzení.|
|**Název procesu**|Název procesu|
|**Název kořenové funkce**|Název aktuální funkce. Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení Volající/Volaný](../profiling/caller-callee-view.md)
- [Zobrazení volajícího/volaných - vzorkovací data](../profiling/caller-callee-view-sampling-data.md)
- [Zobrazení volajícího/volaných - data přístrojové paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Zobrazení volajícího/volaných – vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Zobrazení volajícího/volaných - data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)
