---
title: Vytváření základních sestav profilace z příkazového řádku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f13921dea810ab2185e626cc2889f339d9d174f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537179"
---
# <a name="creating-basic-profiling-reports-from-the-command-line"></a>Vytváření základních sestav profilace z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje základní příkazy VSPerfReport, které generují sestavy hodnot oddělených čárkami (. csv) z datového souboru profilace. vsp nebo. vsps. Popis všech možností sestavy naleznete v tématu [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Příkazy sestavy  
 Pomocí jednoho z následujících příkazů vytvořte sestavu pro zadaný soubor dat profilování.  
  
 **VSPerfReport** `VSPFile` **/Summary: vše**  
 Generuje všechny sestavy, které jsou k dispozici pro soubor. vsp nebo. vsps.  
  
 **VSPerfReport** `VSPFile` **/Summary:** `ReportType` [,`ReportType`...]  
 Vygeneruje zadané typy sestav.  
  
 **VSPerfReport** `VSPFile` **/CallTrace**  
 Vygeneruje sestavu se seznamem každé události shromažďování dat. Jenom instrumentace.  
  
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
|**Řádek**|Vypíše data profilování podle řádku zdrojového kódu.|-   [Vzorkování dat](../profiling/lines-view-sampling-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Data sporu](../profiling/lines-view-contention-data.md)|  
|**Hlaviček**|Informace hlavičky souboru dat profilování.|Specifické pro soubor.|  
|**Označení**|Značky profilace shromážděné při spuštění profilace.|-   [Zobrazení značek](../profiling/marks-view.md)|  
|**Modul**|Vypisuje data profilování pro moduly.|-   [Vzorkování dat](../profiling/modules-view-sampling-data.md)<br />-   [Data instrumentace](../profiling/modules-view-instrumentation-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Data instrumentace paměti .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Data sporu](../profiling/modules-view-contention-data.md)|  
|**Proces**|Vypisuje data profilování pro procesy.|-   [Zobrazení procesu](../profiling/process-view.md)<br />-   [Data sporu](../profiling/process-view-contention-data.md)|  
|**Doporučujeme**|Vypisuje data profilování pro vlákna.|-   [Zobrazení procesu](../profiling/process-view.md)|  
|**Typ**|Vypíše data profilování přidělení podle typu.|-   [Zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md)|  
|**Kolize**|Spory prostředků.|-   [Spory prostředků](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Vypisuje problémy s pravidly o výkonu.|– Vypíše CheckId, popis a umístění zdrojového kódu problému pravidla.|  
|**Trasování událostí pro Windows**|Vypíše události trasování událostí pro Windows (ETW) shromážděné při spuštění profilace.|-   [Sestava ETW](../profiling/event-tracing-for-windows-etw-report.md)|
