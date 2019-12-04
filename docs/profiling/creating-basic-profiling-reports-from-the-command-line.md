---
title: Vytváření základních sestav profilace z příkazového řádku | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cd9748d88a9398792274c386a42bdaa3ce48ba70
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777787"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Vytvoření základních sestav profilace z příkazového řádku
Tento článek popisuje základní příkazy VSPerfReport, které generují čárkami oddělené hodnoty (. *CSV*) sestavy z. *VSP* nebo. soubor dat profilování *vsps* . Popis všech možností sestavy naleznete v tématu [VSPerfReport](../profiling/vsperfreport.md).

## <a name="report-commands"></a>Příkazy sestavy
 Pomocí jednoho z následujících příkazů vytvořte sestavu pro zadaný soubor dat profilování.

 **VSPerfReport** `VSPFile` **/summary: vše** vygeneruje všechny sestavy, které jsou k dispozici pro. *VSP* nebo. soubor *vsps*

 **VSPerfReport** `VSPFile` **/summary:** `ReportType`[,`ReportType`...] Vygeneruje zadané typy sestav.

 **VSPerfReport** `VSPFile` **/CallTrace** generuje sestavu se seznamem každé události shromažďování dat. Jenom instrumentace.

## <a name="summary-report-type-parameters"></a>Parametry typu souhrnné sestavy
 Následující tabulka popisuje sestavy, které jsou generovány zadanou možností typu sestavy. Sloupce sestavy závisí na metodě profilování, která byla použita ke shromažďování dat.

|Parametr Summary|Popis sestavy|Odkaz na sestavu|
|-----------------------|------------------------|----------------------|
|**CallerCallee**|Představuje vztahy nadřazenosti a podřízenosti mezi funkcemi.|-   [data vzorkování](../profiling/caller-callee-view-sampling-data.md)<br />-   [dat instrumentace](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />[data instrumentace paměti -   .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [data](../profiling/caller-callee-view-contention-data.md) kolizí|
|**Slouží**|Vypíše data profilování podle funkcí.|-   [data vzorkování](../profiling/functions-view-sampling-data.md)<br />-   [dat instrumentace](../profiling/functions-view-instrumentation-data.md)<br />-   [data vzorkování paměti .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />[data instrumentace paměti -   .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [data](../profiling/functions-view-contention-data.md) kolizí|
|**Stromu volání**|Představuje cesty provádění a data profilace funkcí při spuštění profilace.|-   [dat instrumentace](../profiling/call-tree-view-instrumentation-data.md)<br />-   [data vzorkování](../profiling/call-tree-view-sampling-data.md)<br />-   [data vzorkování paměti .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />[data instrumentace paměti -   .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [data](../profiling/call-tree-view-contention-data.md) kolizí|
|**Counter**|Zobrazí seznam značek profilace a hodnot čítače výkonu systému Windows, které byly shromážděny při spuštění profilace.|[zobrazení značek](../profiling/marks-view.md) -   |
|**IP**|Zobrazuje data profilování podle instrukcí.|-   [data vzorkování](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [data vzorkování paměti .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [data](../profiling/instruction-pointers-ips-view-contention-data.md) kolizí|
|**Záchranný**|Vypíše dobu života přidělených objektů.|[zobrazení doby života -   objektů](../profiling/object-lifetime-view.md)|
|**Link**|Vypíše data profilování podle řádku zdrojového kódu.|-   [data vzorkování](../profiling/lines-view-sampling-data.md)<br />-   [data vzorkování paměti .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [data](../profiling/lines-view-contention-data.md) kolizí|
|**Hlaviček**|Informace hlavičky souboru dat profilování.|Specifické pro soubor.|
|**Mark**|Značky profilace shromážděné při spuštění profilace.|[zobrazení značek](../profiling/marks-view.md) -   |
|**Modul**|Vypisuje data profilování pro moduly.|-   [data vzorkování](../profiling/modules-view-sampling-data.md)<br />-   [dat instrumentace](../profiling/modules-view-instrumentation-data.md)<br />-   [data vzorkování paměti .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />[data instrumentace paměti -   .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [data](../profiling/modules-view-contention-data.md) kolizí|
|**Přihlášení**|Vypisuje data profilování pro procesy.|[zobrazení procesu](../profiling/process-view.md) -   <br />-   [data](../profiling/process-view-contention-data.md) kolizí|
|**Doporučujeme**|Vypisuje data profilování pro vlákna.|[zobrazení procesu](../profiling/process-view.md) -   |
|**Textový**|Vypíše data profilování přidělení podle typu.|[zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md) -   |
|**Kolize**|Spory prostředků.|-   [sporů prostředků](../profiling/resource-contentions-view-contention-data.md)|
|**RuleWarnings**|Vypisuje problémy s pravidly o výkonu.|– Vypíše CheckId, popis a umístění zdrojového kódu problému pravidla.|
|**FUNKCE**|Vypíše události trasování událostí pro Windows (ETW) shromážděné při spuštění profilace.|-   [Sestava trasování událostí pro Windows](../profiling/event-tracing-for-windows-etw-report.md)|
