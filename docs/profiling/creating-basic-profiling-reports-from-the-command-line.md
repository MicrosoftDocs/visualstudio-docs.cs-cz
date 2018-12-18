---
title: Vytvoření sestavy z příkazového řádku profilaci Basic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6b076023f725ac037ae5863bc8955e6952285ac
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764904"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Vytváření základních sestav profilace z příkazového řádku
Tento článek popisuje základní vsperfreport – příkazy, které generování hodnot oddělených čárkami (. *CSV*) sestav z. *vsp* nebo. *vsps* profilace datový soubor. Popis všech možností sestav najdete v tématu [vsperfreport –](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Sestava příkazy  
 Použijte jednu z následujících příkazů pro vytvoření sestavy pro zadanou profilování datový soubor.  
  
 **Vsperfreport –** `VSPFile` **/Summary:All**  
 Generuje k dispozici pro všechny sestavy. *vsp* nebo. *vsps* souboru.  
  
 **Vsperfreport –** `VSPFile` **nebo souhrnných:**`ReportType`[,`ReportType`...]  
 Generuje typy zadané sestavy.  
  
 **Vsperfreport –** `VSPFile` **/CallTrace**  
 Generuje sestavu obsahující seznam každé události kolekce dat. Pouze instrumentace.  
  
## <a name="summary-report-type-parameters"></a>Souhrnná sestava parametry typu  
 Následující tabulka popisuje sestavy, které jsou generovány nástrojem možnost type zadané sestavy. Sloupce sestavy závisí na profilování metoda, která byla použita ke shromažďování dat.  
  
|Souhrn parametr|Popis sestavy|Odkaz na sestavy|  
|-----------------------|------------------------|----------------------|  
|**CallerCallee**|Představuje relace nadřazený podřízený mezi funkce.|-   [Vzorkování dat](../profiling/caller-callee-view-sampling-data.md)<br />-   [Data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Data instrumentace paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Data kolizí](../profiling/caller-callee-view-contention-data.md)|  
|**Funkce**|Seznamy profilace dat podle funkce.|-   [Vzorkování dat](../profiling/functions-view-sampling-data.md)<br />-   [Data instrumentace](../profiling/functions-view-instrumentation-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Data instrumentace paměti .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Data kolizí](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Představuje spuštění cesty a data profilování funkcí v profilaci spustit.|-   [Data instrumentace](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Vzorkování dat](../profiling/call-tree-view-sampling-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Data instrumentace paměti .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Data kolizí](../profiling/call-tree-view-contention-data.md)|  
|**Counter**|Seznamy profilace značky a hodnoty čítače výkonu systému Windows, které byly shromážděny během vytváření profilu spustit.|-   [Zobrazení značek](../profiling/marks-view.md)|  
|**IP**|Seznamy profilace dat podle instrukcí.|-   [Vzorkování dat](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Data kolizí](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Životnosti**|Uvádí dobu trvání přidělené objektů.|-   [Zobrazení doby života objektu](../profiling/object-lifetime-view.md)|  
|**řádek**|Seznamy profilace datový zdroj kódu řádku.|-   [Vzorkování dat](../profiling/lines-view-sampling-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Data kolizí](../profiling/lines-view-contention-data.md)|  
|**Záhlaví**|Profilace informaci hlavičky dat souboru.|Konkrétní do souboru.|  
|**Mark**|Profilace značky se shromažďují v profilaci spustit.|-   [Zobrazení značek](../profiling/marks-view.md)|  
|**Modul**|Seznamy profilace data pro moduly.|-   [Vzorkování dat](../profiling/modules-view-sampling-data.md)<br />-   [Data instrumentace](../profiling/modules-view-instrumentation-data.md)<br />-   [Data vzorkování paměti .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Data instrumentace paměti .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Data kolizí](../profiling/modules-view-contention-data.md)|  
|**Proces**|Seznamy profilace data pro procesy.|-   [Zobrazení procesů](../profiling/process-view.md)<br />-   [Data kolizí](../profiling/process-view-contention-data.md)|  
|**Přístup z více vláken**|Seznamy profilace data pro vlákna.|-   [Zobrazení procesů](../profiling/process-view.md)|  
|**Typ**|Zobrazí seznam dat podle typu profilaci přidělení.|-   [Přidělení – zobrazení](../profiling/dotnet-memory-allocations-view.md)|  
|**Kolizí**|Kolize prostředku –.|-   [Kolize prostředku –](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Zobrazí seznam pravidel problémy s výkonem.|-Obsahuje seznam CheckId, popis a umístění zdroje kódu pravidlo problému.|  
|**TRASOVÁNÍ UDÁLOSTÍ PRO WINDOWS**|Zobrazí události trasování událostí pro Windows (ETW) shromážděné v profilaci spustit.|-   [Sestavy trasování událostí pro Windows](../profiling/event-tracing-for-windows-etw-report.md)|