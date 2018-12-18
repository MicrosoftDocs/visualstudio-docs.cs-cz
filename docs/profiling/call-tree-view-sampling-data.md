---
title: Zobrazení stromu volání – Data vzorkování | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 90035daf13008122e7d529408a6de0389b311628
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262366"
---
# <a name="call-tree-view---sampling-data"></a>Zobrazení stromu volání – data vzorkování
Zobrazení stromu volání zobrazuje cesty provádění funkce, které byly provázán v PROFILOVANÉHO aplikaci.  
  
> [!NOTE]
>  Funkce Rozšířené zabezpečení v systému Windows 8 a Windows Server 2012 vyžaduje významné změny ve způsobu, jakým Visual Studio profiler shromažďuje data na těchto platformách. Aplikace UWP také vyžadují nové techniky kolekce. V tématu [nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Kořen stromu je vstupním bodem do součást nebo aplikace. Každý uzel funkce uvádí všechny funkce, které ji volat a údaje o výkonu o těchto volání funkcí.  
  
 Hodnoty v zobrazení stromu volání jsou pro funkce instancí, které byly volá funkci nadřazené ve stromové struktuře volání. Procentní hodnoty se počítá srovnáním hodnota instance funkce celkového počtu vzorků v profilaci spustit.  
  
## <a name="highlight-the-execution-hot-path"></a>Zvýraznit cestu aktivní provádění  
 Zobrazení stromu volání můžete rozbalit a zvýraznit cestu spouštění procesu nebo funkce, která byla vzorkovat nejčastěji. Zobrazení Nejaktivnější cesty, klikněte pravým tlačítkem na proces nebo funkce a potom klikněte na **rozbalte aktivní trase**.  
  
## <a name="set-the-call-tree-root-node"></a>Nastavit kořenový uzel stromu volání  
 Každý proces v profilaci spuštění se zobrazí jako kořenový uzel. Pokud chcete nastavit počáteční uzel volání stromové zobrazení, klikněte pravým tlačítkem na uzel, který chcete nastavit jako počáteční uzel a vyberte **nastavit kořenové**.  
  
 Pokud nastavíte kořenového uzlu, můžete eliminovat všechny položky ze zobrazení s výjimkou podstrom vybraného uzlu. Chcete-li obnovit na původní uzel na kořenový uzel, klikněte pravým tlačítkem myši v okně zobrazení stromu volání a vyberte **resetovat kořenové**.  
  
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
|**úroveň**|Hloubka této funkce ve stromové struktuře volání. Pouze v [vsperfreport –](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**Výhradní ukázky**|Počet vzorků, které byly shromážděny v této funkci, pokud byla volána funkce nadřazené ve stromové struktuře volání. Toto číslo nezahrnuje vzorků, které byly shromážděny v funkce, které byly volá funkci.|  
|**% Výhradní ukázky**|Procento všechny vzorky v profilaci spuštění, které byly výhradní ukázky této funkce, pokud byla volána funkce nadřazené ve stromové struktuře volání.|  
|**Ukázky (včetně).**|Počet vzorků, které byly shromážděny v této funkci, pokud byla volána funkce nadřazené ve stromové struktuře volání. Toto číslo zahrnuje vzorků, které byly shromážděny v funkce, které byly volá funkci.|  
|**% Ukázky (včetně).**|Procento všechny vzorky v profilaci spuštění, které byly včetně ukázky této funkce, pokud byla volána funkce nadřazené ve stromové struktuře volání.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení stromu volání – data vzorkování profileru](../profiling/call-Tree-view-sampling-data.md)   
 [Volání stromové zobrazení – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Zobrazení stromu volání – instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)