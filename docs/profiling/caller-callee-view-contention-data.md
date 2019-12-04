---
title: Zobrazení Volající/Volaný – data kolizí | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779737"
---
# <a name="callercallee-view----contention-data"></a>Zobrazení Volající/Volaný – data kolizí
Zobrazení volající/volaný zobrazuje informace o sporu pro vybranou funkci a její nadřazené a podřízené funkce. Zobrazení volající/volaný obsahuje tři mřížky.

 **Aktuální funkce** se zobrazí v prostřední mřížce a zobrazí informace o sporu pro vybranou funkci. Mezi tyto hodnoty patří všechny blokující spory pro funkci.

 **Funkce, které se nazývají aktuální funkce** , se zobrazí v horní mřížce a zobrazují jednotlivé příspěvky volajícího (nadřazeného) funkce na hodnoty vybrané (aktuální) funkce.

 **Funkce, které byly volány aktuální funkcí** , jsou zobrazeny v dolní mřížce a zobrazují informace o sporu pro volané (podřízené) funkce vybrané funkce, pokud byla podřízená funkce volána aktuální funkcí.

|Sloupec|Popis|
|------------|-----------------|
|**Textový**|Kontext funkce:<br /><br /> -   **0** – aktuální funkce<br />-   **1** – funkce, která volá aktuální funkci<br />-   **2** – funkce, která je volána aktuální funkcí<br /><br /> Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|
|**Výhradní čas zablokování**|– Pro aktuální funkci bylo zablokováno spuštění kódu v těle funkce v době, kdy byla tato funkce zablokována. Čas zablokování ve funkcích volaných funkcí není zahrnutý.<br />– Pro funkci volajícího je část výhradního času zablokování aktuální funkce, ke které došlo, když tato funkce volala funkci Current.<br />– Pro funkci volaná byla tato funkce zablokovaná při provádění vlastního kódu, když byla tato funkce volána aktuální funkcí. Čas zablokování v podřízených funkcích volaných funkcí volaný není zahrnutý.|
|**% Výhradního času zablokování**|Procento veškerého času zablokování v běhu profilace, které bylo pro tuto funkci v tomto kontextu výhradní čas zablokování.|
|**Exkluzivní spory**|– Pro aktuální funkci počet, kolikrát byla tato funkce zablokována při provádění kódu v těle funkce. Spory, které nastaly ve funkcích, které byly volány funkcí, nejsou zahrnuty.<br />– Pro funkci volajícího se jedná o počet exkluzivních sporů aktuální funkce, k nimž došlo v případě, že tato funkce volala aktuální funkci.<br />– Pro funkci volaný počet, kolikrát byla tato funkce zablokována při provádění kódu v těle funkce, pokud byla tato funkce volána aktuální funkcí. Spory, které se vyskytly ve funkcích volaných funkcí volaný, nejsou zahrnuté.|
|**% Výhradních sporů**|Procento všech sporů v rámci profilace spuštění, které pro tuto funkci v tomto kontextu byly exkluzivním obsahem.|
|**Adresa funkce**|Adresa funkce nebo token.|
|**Název funkce**|Plně kvalifikovaný název funkce.|
|**Celková doba zablokování**|– Pro aktuální funkci se zablokovalo spuštění této funkce nebo jedné z funkcí, které byly volány touto funkcí. Je zahrnut čas zablokování ve funkcích, které byly volány aktuální funkcí.<br />– Pro funkci volání, část celkového času zablokování aktuální funkce, k níž došlo v případě, že tato funkce volala funkci Current.<br />– Pro funkci volaná bylo zablokováno spuštění této funkce nebo jedné z funkcí, které byly volány funkcí, pokud byla tato funkce volána aktuální funkcí. Je zahrnut čas zablokování ve funkcích, které byly volány funkcí volaný.|
|**% Celkového času zablokování**|Procento veškerého času zablokování v běhu profilace, které pro tuto funkci v tomto kontextu bylo zablokováno čas.|
|**Celkové spory**|– Pro aktuální funkci bylo zablokováno spuštění této funkce nebo jedné z funkcí, které byly volány funkcí. Jsou zahrnuty spory, které nastaly ve funkcích, které byly volány funkcí.<br />– Pro funkci volání, Počet zahrnutých sporů aktuální funkce, k nimž došlo v případě, že tato funkce volala aktuální funkci.<br />– Pro funkci volaný bylo zablokováno spuštění této funkce nebo jedné z funkcí, které byly volány funkcí, pokud byla tato funkce volána aktuální funkcí. Jsou zahrnuty spory, které nastaly ve funkcích volaných funkcí volaný.|
|**% Celkových sporů**|Procento všech sporů v rámci profilace spuštění, které pro tuto funkci v tomto kontextu byly exkluzivním obsahem.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu (PID) procesu, ve kterém došlo k sporům.|
|**Název procesu**|Název procesu.|
|**Název kořenové funkce**|Název aktuální funkce Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|

## <a name="see-also"></a>Viz také:
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení volající/volaný](../profiling/caller-callee-view.md)
- [Zobrazení Volající/Volaný – data vzorkování](../profiling/caller-callee-view-sampling-data.md)
- [Zobrazení Volající/Volaný – data instrumentace paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Zobrazení Volající/Volaný – data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Zobrazení Volající/Volaný – data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)
