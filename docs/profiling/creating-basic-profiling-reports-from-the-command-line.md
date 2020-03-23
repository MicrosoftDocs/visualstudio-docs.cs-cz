---
title: Vytváření sestav základního profilování z příkazového řádku | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777787"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Vytvoření základních sestav profilování z příkazového řádku
Tento článek popisuje základní příkazy VSPerfReport, které generují hodnotu oddělenou čárkou (.* csv*) zprávy z . *vsp* nebo . *vsps* profilování datového souboru. Popis všech možností sestavy naleznete [v tématu VSPerfReport](../profiling/vsperfreport.md).

## <a name="report-commands"></a>Příkazy sestavy
 K vytvoření sestavy pro zadaný datový soubor profilování použijte jeden z následujících příkazů.

 **VSPerfReport** `VSPFile` **/Summary:Všechny** generuje všechny sestavy, které jsou k dispozici pro rozhraní . *vsp* nebo . *vsps.*

 **VSPerfReport** `VSPFile` **/Shrnutí:**`ReportType``ReportType`[, ...] Generuje zadané typy sestav.

 **VSPerfReport** `VSPFile` **/CallTrace** Generuje sestavu, která obsahuje seznam jednotlivých událostí shromažďování dat. Pouze přístrojové vybavení.

## <a name="summary-report-type-parameters"></a>Parametry typu souhrnné sestavy
 Následující tabulka popisuje sestavy, které jsou generovány zadanou možností typu sestavy. Sloupce sestavy závisí na metodě profilování, která byla použita ke shromažďování dat.

|Souhrnný parametr|Popis sestavy|Odkaz na sestavu|
|-----------------------|------------------------|----------------------|
|**Volající hovor**|Představuje nadřazené a podřízené vztahy mezi funkcemi.|-   [Údaje o odběru vzorků](../profiling/caller-callee-view-sampling-data.md)<br />-   [Údaje o přístrojích](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Vzorkování paměti .NET data](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Data paměťových přístrojů .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Údaje o tvrzeních](../profiling/caller-callee-view-contention-data.md)|
|**Funkce**|Zobrazí seznam dat profilování podle funkce.|-   [Údaje o odběru vzorků](../profiling/functions-view-sampling-data.md)<br />-   [Údaje o přístrojích](../profiling/functions-view-instrumentation-data.md)<br />-   [Vzorkování paměti .NET data](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Data paměťových přístrojů .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Údaje o tvrzeních](../profiling/functions-view-contention-data.md)|
|**CallTree**|Představuje cesty spuštění a profilování data funkcí v profilování spustit.|-   [Údaje o přístrojích](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Údaje o odběru vzorků](../profiling/call-tree-view-sampling-data.md)<br />-   [Vzorkování paměti .NET data](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Data paměťových přístrojů .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Údaje o tvrzeních](../profiling/call-tree-view-contention-data.md)|
|**Čítač**|Seznam profilovacích značek a hodnot čítače výkonu systému Windows, které byly shromážděny během spuštění profilování.|-   [Zobrazení značek](../profiling/marks-view.md)|
|**Ip**|Zobrazí seznam dat profilování podle pokynů.|-   [Údaje o odběru vzorků](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Vzorkování paměti .NET data](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Údaje o tvrzeních](../profiling/instruction-pointers-ips-view-contention-data.md)|
|**Život**|Uvádí životnost přidělených objektů.|-   [Zobrazení životnosti objektu](../profiling/object-lifetime-view.md)|
|**Řádku**|Zobrazí seznam dat profilování podle řádku zdrojového kódu.|-   [Údaje o odběru vzorků](../profiling/lines-view-sampling-data.md)<br />-   [Vzorkování paměti .NET data](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Data tvrzení](../profiling/lines-view-contention-data.md)|
|**Záhlaví**|Profilování informací záhlaví datového souboru.|Specifické pro soubor.|
|**Označení**|Profilování značky shromážděné v profilování spustit.|-   [Zobrazení značek](../profiling/marks-view.md)|
|**Modul**|Zobrazí seznam dat profilování pro moduly.|-   [Údaje o odběru vzorků](../profiling/modules-view-sampling-data.md)<br />-   [Údaje o přístrojích](../profiling/modules-view-instrumentation-data.md)<br />-   [Vzorkování paměti .NET data](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Data paměťových přístrojů .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Údaje o tvrzeních](../profiling/modules-view-contention-data.md)|
|**Proces**|Uvádí data profilování pro procesy.|-   [Zobrazení procesu](../profiling/process-view.md)<br />-   [Údaje o tvrzeních](../profiling/process-view-contention-data.md)|
|**Vlákno**|Uvádí data profilování pro vlákna.|-   [Zobrazení procesu](../profiling/process-view.md)|
|**Typ**|Zobrazí seznam dat profilování přidělení podle typu.|-   [Zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md)|
|**Tvrzení**|Konflikty prostředků.|-   [Konflikty zdrojů](../profiling/resource-contentions-view-contention-data.md)|
|**Upozornění pravidel**|Uvádí problémy s pravidly výkonu.|- Zobrazí seznam checkid, popis a umístění zdrojového kódu problému pravidla.|
|**Trasování událostí pro Windows**|Zobrazí seznam událostí trasování událostí pro Windows (ETW) události shromážděné v profilování spustit.|-   [Sestava ETW](../profiling/event-tracing-for-windows-etw-report.md)|
