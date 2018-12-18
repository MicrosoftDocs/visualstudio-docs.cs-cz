---
title: Zobrazení stromu volání – Data kolizí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40e28eb246b2c4611a15dc4ce2cf6b1b02dd0100
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263178"
---
# <a name="call-tree-view---contention-data"></a>Zobrazení stromu volání – data kolizí
Zobrazení stromu volání zobrazuje cesty provádění funkce, které byly provázán v PROFILOVANÉHO aplikaci. Kořen stromu je vstupním bodem do součást nebo aplikace. Každý uzel funkce uvádí všechny funkce, které ji volat, počet pokusů, které funkce byl zablokován a množství času, který funkce byl zablokován, protože byla sporu pro prostředek s jinými vláken nebo procesy.  
  
 Hodnoty v zobrazení stromu volání jsou pro funkce instancí, které byly volá funkci nadřazené ve stromové struktuře volání. Procentní hodnoty se počítá srovnáním hodnota instance funkce celkový počet kolizí v profilaci spustit.  
  
## <a name="highlight-the-execution-hot-path"></a>Zvýraznit cestu aktivní provádění  
 Zobrazení stromu volání můžete rozbalit a zvýraznit cestu spouštění procesu nebo funkce, která vytvořila většina kolizí.  
  
-   Zobrazení Nejaktivnější cesty, klikněte pravým tlačítkem na proces nebo funkce a pak klikněte na tlačítko **rozbalte aktivní trase**.  
  
## <a name="set-the-call-tree-root-node"></a>Nastavit kořenový uzel stromu volání  
 Každý proces v profilaci spuštění se zobrazí jako kořenový uzel. Pokud chcete nastavit počáteční uzel volání stromové zobrazení, klikněte pravým tlačítkem na uzel, který chcete nastavit jako počáteční uzel a potom klikněte na **nastavit kořenové**.  
  
 Pokud nastavíte kořenového uzlu, můžete eliminovat všechny položky ze zobrazení s výjimkou podstrom uzlu, který jste vybrali. Pokud chcete resetovat kořenový uzel zpět do původního uzlu, klikněte pravým tlačítkem v zobrazení stromu volání a pak klikněte na tlačítko **resetovat kořenové**.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní blokované čas**|Čas, instance této funkce v této cestě provádění měla blokovat spouštění v profilaci spustit. Čas neobsahuje blokované čas podřízené funkcí, které byly volá funkci.|  
|**Výhradní blokované čas: %**|Procento všech blokovaných času v profilaci spustit, který byl výhradní blokované čas pro tuto funkci v této cestě provádění.|  
|**Výhradní kolizí**|Počet kolizí, k nimž došlo v instancích této funkce v této cestě provádění. Číslo nezahrnuje kolizí podřízené funkce volané funkce.|  
|**% Výhradní kolizí**|Procento všech kolizí v profilaci spuštění, které byly výhradní kolizí instancí této funkce, které byly volá funkci nadřazené ve stromové struktuře volání.|  
|**Adresa funkce**|Adresa funkce.|  
|**Název funkce**|Plně kvalifikovaný název funkce.|  
|**Blokované čas (včetně).**|Celkový čas, instance této funkce v této cestě provádění měla blokovat spouštění v profilaci spustit. Čas zahrnuje blokované době podřízené funkce volané funkce.|  
|**Včetně blokované čas: %**|Procento všech blokovaných času v profilaci spuštění, který byl včetně blokované čas pro instance této funkce v této cestě provádění.|  
|**Kolizí (včetně).**|Celkový počet kolizí zablokované instance této funkce v této cestě provádění. Počet zahrnuje kolizí podřízené funkcí volá funkci.|  
|**% Kolizí (včetně).**|Procento všech kolizí v profilaci spuštění, které byly včetně kolizí instance této funkce v této cestě provádění.|  
|**úroveň**|Úroveň funkce ve stromové struktuře volání. Pouze v sestavách VSReport příkazového řádku. Další informace najdete v tématu v [vsperfreport –](../profiling/vsperfreport.md).|  
|**Číslo řádku – funkce**|Číslo řádku spuštění této funkce ve zdrojovém souboru.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta modul, který obsahuje funkce.|  
|**ID procesu**|ID procesu (PID) z profilace spustit.|  
|**Název procesu**|Název procesu.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view.md)   
 [Zobrazení stromu volání – instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Volání stromové zobrazení – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)