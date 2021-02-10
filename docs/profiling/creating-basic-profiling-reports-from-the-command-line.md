---
title: Profilace z příkazového řádku – vytvoření základních sestav
description: Seznamte se s CallTrace a možnostmi pro VSPerfReport.exe, které vytváří sestavy. CSV (oddělené čárkami-hodnota) z datového souboru profilace. vsp nebo. vsps.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4d5e263d68ff2fbfbd963e9e3ee3833bd266aaba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955993"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Vytvoření základních sestav profilace z příkazového řádku
Tento článek popisuje základní příkazy VSPerfReport, které generují čárkami oddělené hodnoty (.*CSV*) sestavy z. *VSP* nebo. soubor dat profilování *vsps* . Popis všech možností sestavy naleznete v tématu [VSPerfReport](../profiling/vsperfreport.md).

## <a name="report-commands"></a>Příkazy sestavy
 Pomocí jednoho z následujících příkazů vytvořte sestavu pro zadaný soubor dat profilování.

 **VSPerfReport** `VSPFile` **/Summary: vše** Generuje všechny sestavy, které jsou k dispozici pro. *VSP* nebo. soubor *vsps*

 **VSPerfReport** `VSPFile` **/Summary:** `ReportType` [,`ReportType`...] Vygeneruje zadané typy sestav.

 **VSPerfReport** `VSPFile` **/CallTrace** Vygeneruje sestavu se seznamem každé události shromažďování dat. Jenom instrumentace.

## <a name="summary-report-type-parameters"></a>Parametry typu souhrnné sestavy
 Následující tabulka popisuje sestavy, které jsou generovány zadanou možností typu sestavy. Sloupce sestavy závisí na metodě profilování, která byla použita ke shromažďování dat.

|Parametr Summary|Popis sestavy|Odkaz na sestavu|
|-----------------------|------------------------|----------------------|
|**CallerCallee**|Představuje vztahy nadřazenosti a podřízenosti mezi funkcemi.|-   [Vzorkování dat](../profiling/caller-callee-view-sampling-data.md)<br />-   [Data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Data instrumentace paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Data sporu](../profiling/caller-callee-view-contention-data.md)|
|**Funkce**|Vypíše data profilování podle funkcí.|-   [Vzorkování dat](../profiling/functions-view-sampling-data.md)<br />-   [Data instrumentace](../profiling/functions-view-instrumentation-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Data instrumentace paměti .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Data sporu](../profiling/functions-view-contention-data.md)|
|**Stromu volání**|Představuje cesty provádění a data profilace funkcí při spuštění profilace.|-   [Data instrumentace](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Vzorkování dat](../profiling/call-tree-view-sampling-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Data instrumentace paměti .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Data sporu](../profiling/call-tree-view-contention-data.md)|
|**Čítač**|Zobrazí seznam značek profilace a hodnot čítače výkonu systému Windows, které byly shromážděny při spuštění profilace.|-   [Zobrazení značek](../profiling/marks-view.md)|
|**IP**|Zobrazuje data profilování podle instrukcí.|-   [Vzorkování dat](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Data sporu](../profiling/instruction-pointers-ips-view-contention-data.md)|
|**Záchranný**|Vypíše dobu života přidělených objektů.|-   [Zobrazení doby života objektu](../profiling/object-lifetime-view.md)|
|**Čára**|Vypíše data profilování podle řádku zdrojového kódu.|-   [Vzorkování dat](../profiling/lines-view-sampling-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Data sporu](../profiling/lines-view-contention-data.md)|
|**Hlavička**|Informace hlavičky souboru dat profilování.|Specifické pro soubor.|
|**Označení**|Značky profilace shromážděné při spuštění profilace.|-   [Zobrazení značek](../profiling/marks-view.md)|
|**Modul**|Vypisuje data profilování pro moduly.|-   [Vzorkování dat](../profiling/modules-view-sampling-data.md)<br />-   [Data instrumentace](../profiling/modules-view-instrumentation-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Data instrumentace paměti .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Data sporu](../profiling/modules-view-contention-data.md)|
|**Proces**|Vypisuje data profilování pro procesy.|-   [Zobrazení procesu](../profiling/process-view.md)<br />-   [Data sporu](../profiling/process-view-contention-data.md)|
|**Doporučujeme**|Vypisuje data profilování pro vlákna.|-   [Zobrazení procesu](../profiling/process-view.md)|
|**Typ**|Vypíše data profilování přidělení podle typu.|-   [Zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md)|
|**Kolize**|Spory prostředků.|-   [Spory prostředků](../profiling/resource-contentions-view-contention-data.md)|
|**RuleWarnings**|Vypisuje problémy s pravidly o výkonu.|– Vypíše CheckId, popis a umístění zdrojového kódu problému pravidla.|
|**Trasování událostí pro Windows**|Vypíše události trasování událostí pro Windows (ETW) shromážděné při spuštění profilace.|-   [Sestava ETW](../profiling/event-tracing-for-windows-etw-report.md)|
