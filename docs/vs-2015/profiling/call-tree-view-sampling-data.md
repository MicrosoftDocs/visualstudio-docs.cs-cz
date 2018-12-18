---
title: Zobrazení stromu volání – Data vzorkování | Dokumentace Microsoftu
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
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc324b621bfc3e472d6eb86227a6081e3384d2af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798908"
---
# <a name="call-tree-view---sampling-data"></a>Zobrazení stromu volání – vzorkování dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení stromu volání zobrazí cesty spuštění funkce, které byly Procházet v profilované aplikaci.  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Kořen stromu je vstupním bodem do aplikace nebo komponenty. Každý uzel funkce obsahuje všechny funkce, které ji volaly a údaje o výkonu o volání těchto funkcí.  
  
 Hodnoty v zobrazení stromu volání jsou pro instance funkce, které byly volány nadřazené funkce ve stromu volání. Procentní hodnoty se počítá srovnáním hodnota instance funkce, která má celkový počet vzorků při spuštění profilování.  
  
## <a name="highlighting-the-execution-hot-path"></a>Zvýraznění provádění kritickou cestu  
 Zobrazení stromu volání můžete rozbalit a zvýraznit cestu spuštění procesu nebo funkce, která je Vzorkovaná nejčastěji. Zobrazení nejaktivnějších cesty, procesu nebo funkce klikněte pravým tlačítkem a pak klikněte na **rozbalit kritickou cestu**.  
  
## <a name="setting-the-call-tree-root-node"></a>Nastavení kořenový uzel stromu volání  
 Každý proces při spuštění profilování se zobrazí jako kořenový uzel. Pokud chcete nastavit počáteční uzel zobrazení stromu volání, klikněte pravým tlačítkem na uzel, který chcete nastavit jako počáteční uzel a vyberte **nastavit kořenový**.  
  
 Když nastavíte kořenový uzel, odstraníte všechny položky ze zobrazení s výjimkou podstrom vybraný uzel. Obnovit původní uzel kořenový uzel, klikněte pravým tlačítkem v okně zobrazení stromu volání a vyberte **resetování kořenového**.  
  
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
|**úroveň**|Hloubka tuto funkci ve stromu volání. Pouze v [VSPerfReport](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**Výhradní vzorky**|Počet vzorků, které byly shromážděny v této funkci, když se jmenovala nadřazené funkce ve stromu volání. Toto číslo nezahrnuje ukázky, které byly shromážděny v funkce, které byly volány funkce.|  
|**% Výhradních vzorků**|Procento všechny ukázky během spuštění profilování, které byly výhradních vzorků této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Celkových vzorků**|Počet vzorků, které byly shromážděny v této funkci, když se jmenovala nadřazené funkce ve stromu volání. Toto číslo zahrnuje ukázky, které byly shromážděny ve funkcích, které byly volány funkce.|  
|**% Celkových vzorků**|Procento všechny ukázky během spuštění profilování, které byly celkových vzorků této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení stromu volání – Data vzorkování Profiler](../profiling/call-tree-view-sampling-data.md)   
 [Zobrazení stromu volání – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Zobrazení stromu volání – instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)



