---
title: Volající – zobrazení volaný – vzorkování dat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e46befbdd8f727485884197a3cfb284fa5a8cf6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796958"
---
# <a name="caller--callee-view---sampling-data"></a>Volající / volaný zobrazení – vzorkování dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení volající/volaný zobrazí profilování informace pro vybrané funkce a jeho funkce pro nadřazené a podřízené. Zobrazení volající/volaný obsahuje tři mřížky.  
  
 **Aktuální funkce** se zobrazí v mřížce střední který ukazuje profilování informace pro vybrané funkce. Hodnoty zahrnují všechny vzorky volání funkce.  
  
 **Funkce, které volaly aktuální funkcí** se zobrazí v hlavní mřížky a funkce na hodnoty vybrané – funkce (aktuální) ukazuje jednotlivé příspěvky volající (nadřazené).  
  
 **Funkce, které byly volány aktuální funkcí** se zobrazí v mřížce dolů který ukazuje profilace informace pro volaných (podřízený) funkce vybrané funkce, pokud podřízený funkce byla volána aktuální funkce.  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**ID procesu**|ID procesu (PID) běhu profilování.|  
|**Název procesu**|Název procesu.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje funkci.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název funkce**|Plně kvalifikovaný název funkce.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Adresa funkce**|Adresa funkce.|  
|**Typ**|Kontext funkce:<br /><br /> -   **0** -aktuální funkce<br />-   **1** – funkce, která volá aktuální funkci<br />-   **2** – funkce, která volá aktuální funkci|  
|**Název kořenové funkce**|Název aktuální funkce.|  
|**Celkových vzorků**|-Pro aktuální funkci Počet vzorků, které byly shromážděny, i když tato funkce nebo jeden z jeho podřízených funkce byla spuštěna.<br />-Pro volající funkci, počet celkových vzorků aktuální funkce, které byly shromážděny při volání této funkce aktuální funkce.<br />-Pro volaných funkce Počet celkových vzorků této funkce, které byly shromážděny při volání této funkce aktuální funkce.|  
|**% Celkových vzorků**|Procento všechny ukázky v profilování, které byly celkových vzorků této funkce.|  
|**Výhradní vzorky**|-Pro aktuální funkci Počet vzorků v profilování, které byly shromážděny když tato funkce byla spuštěna přímo; To znamená, když tato funkce byla v horní části zásobníku volání. Ukázky, které jsou shromažďovány, když spouštíte podřízené funkce této funkce nejsou v exkluzivitou zahrnuty.<br />-Pro volající funkci, počet výhradních vzorků aktuální funkce, které byly shromážděny při volání této funkce aktuální funkce.<br />-Pro volaných funkce počet výhradních vzorků této funkce, které byly shromážděny při volání této funkce aktuální funkce.|  
|**% Výhradních vzorků**|Procento všechny ukázky v profilování, které byly výhradních vzorků této funkce.|  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení volající/volaný – Data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Zobrazení volající/volaný – Data instrumentace paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Zobrazení volající/volaný – Data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)



