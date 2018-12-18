---
title: Volající - zobrazení volaný – vzorkování dat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b9b740689175f91f4bc69396121da0bed336532
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34548707"
---
# <a name="callercallee-view---sampling-data"></a>Zobrazení volající/volaný – vzorkování dat
Zobrazení volající/volaný zobrazí profilování informace o vybrané funkce a její nadřazené a podřízené funkce. Zobrazení volající/volaný obsahuje tři mřížky.  
  
 **Funkci Current** se zobrazí v prostředním mřížky a ukazuje profilace informace o vybrané funkce. Hodnoty zahrnují u všech vybraných volání funkce.  
  
 **Funkce, které volá funkci current** se zobrazí v horní mřížky, a zobrazuje jednotlivé příspěvky volajícího (nadřazené) funkce na hodnoty vybrané funkce (aktuální).  
  
 **Funkce, které byly volá funkci current** se zobrazí v mřížce dole ale zobrazí při volání funkce podřízené aktuální funkcí profilace informace pro funkce volaný (podřízená) vybrané funkce.  
  
> [!NOTE]
>  Funkce Rozšířené zabezpečení v systému Windows 8 a Windows Server 2012 vyžaduje významné změny ve způsobu, jakým Visual Studio profiler shromažďuje data na těchto platformách. Aplikace UWP také vyžadují nové techniky kolekce. V tématu [nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**ID procesu**|ID procesu (PID) z profilace spustit.|  
|**Název procesu**|Název procesu.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta modul, který obsahuje funkce.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název funkce**|Plně kvalifikovaný název funkce.|  
|**Číslo řádku – funkce**|Číslo řádku spuštění této funkce ve zdrojovém souboru.|  
|**Adresa funkce**|Adresa funkce.|  
|**Typ**|Kontext funkce:<br /><br /> -   **0** -aktuální funkce<br />-   **1** -funkci, která volá funkci current<br />-   **2** -funkci, která volá funkci current|  
|**Název kořenové – funkce**|Název aktuální funkce.|  
|**Ukázky (včetně).**|-Pro aktuální funkci Počet vzorků, které byly shromážděny, i když se provádí tuto funkci nebo jeden z jejích podřízených funkcí.<br />-Pro volající funkce, počet vzorků (včetně). aktuální funkce, které byly shromážděny při volání této funkce aktuální funkce.<br />-Pro funkci volaný, počet včetně ukázky této funkce, které byly shromážděny při funkci current volání této funkce.|  
|**% Ukázky (včetně).**|Procento všechny ukázky v profilaci spuštění, které byly včetně ukázky této funkce.|  
|**Výhradní ukázky**|-Pro funkci aktuální počet vzorků v profilaci spuštění, které byly shromážděny při tato funkce byla přímo provádění; To znamená, když tato funkce byla v horní části zásobníku volání. Ukázky, které byly shromážděny při podřízené funkce této funkce jsou prováděny nejsou v výhradní počty zahrnuty.<br />-Pro volající funkce počet výhradní vzorků aktuální funkce, které byly shromážděny při volání této funkce aktuální funkce.<br />-Pro funkci volaný, počet výhradní ukázky této funkce, které byly shromážděny při funkci current volání této funkce.|  
|**% Výhradní ukázky**|Procento všechny ukázky v profilaci spuštění, které byly výhradní ukázky této funkce.|  
  
## <a name="see-also"></a>Viz také:  
 [Zobrazení volající/volaný – data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Zobrazení volající/volaný – data instrumentace paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Zobrazení volající/volaný – data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)