---
title: Zobrazení Volající/Volaný – data vzorkování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2f20f67f2f86c94f83362af1df416b387884c13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64830986"
---
# <a name="caller--callee-view---sampling-data"></a>Zobrazení Volající/Volaný – data vzorkování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení volající/volaný zobrazí informace o profilování vybrané funkce a jejích nadřazených a podřízených funkcí. Zobrazení volající/volaný obsahuje tři mřížky.  
  
 **Aktuální funkce** se zobrazí v prostřední mřížce a zobrazí informace o profilování pro vybranou funkci. Hodnoty zahrnují všechna ukázková volání funkce.  
  
 **Funkce, které se nazývají aktuální funkce** , se zobrazí v horní mřížce a zobrazují jednotlivé příspěvky volajícího (nadřazeného) funkce na hodnoty vybrané (aktuální) funkce.  
  
 **Funkce, které byly volány aktuální funkcí** , jsou zobrazeny v dolní mřížce a zobrazují informace o profilech pro volané (podřízené) funkce vybrané funkce, pokud byla podřízená funkce volána aktuální funkcí.  
  
> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro Windows Store vyžadují také nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|  
|**Název procesu**|Název procesu|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|  
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|  
|**Název funkce**|Plně kvalifikovaný název funkce.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Adresa funkce**|Adresa funkce|  
|**Typ**|Kontext funkce:<br /><br /> -   **0** – aktuální funkce<br />-   **1** – funkce, která volá aktuální funkci<br />-   **2** – funkce, která je volána aktuální funkcí|  
|**Název kořenové funkce**|Název aktuální funkce|  
|**Vzorky včetně**|– Pro aktuální funkci byl zjištěn počet vzorků, které byly shromážděny i v případě, že byla spuštěna tato funkce nebo jedna z jejích podřízených funkcí.<br />– Pro funkci volání, Počet zahrnutých vzorků aktuální funkce, které byly shromážděny v případě, že tato funkce se nazývá aktuální funkce.<br />– Pro funkci volaný se jedná o počet zahrnutých vzorků této funkce, které byly shromážděny, když je tato funkce volána aktuální funkce.|  
|**% Včetně vzorků**|Procentuální podíl všech vzorků v průběhu profilace, které byly zahrnuté do vzorků této funkce.|  
|**Exkluzivní vzorky**|– Pro aktuální funkci počet vzorků v běhu profilace, které byly shromážděny při přímém spuštění této funkce; To znamená, že pokud tato funkce byla v horní části zásobníku volání. Vzorky shromážděné při provádění podřízených funkcí této funkce se nepočítají ve výhradních počtech.<br />– Pro funkci volajícího se jedná o počet exkluzivních vzorků aktuální funkce, které byly shromážděny, když tato funkce volá aktuální funkci.<br />– Pro funkci volaného se jedná o počet exkluzivních vzorků této funkce, které byly shromážděny, když je tato funkce volána aktuální funkce.|  
|**% Exkluzivních vzorků**|Procentuální podíl všech vzorků v rámci profilace spuštění, které byly exkluzivními ukázkami této funkce.|  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení Volající/Volaný – data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Zobrazení Volající/Volaný – data instrumentace paměti NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Zobrazení Volající/Volaný – data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)
