---
title: Zobrazení stromu volání – Data kolizí | Dokumentace Microsoftu
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
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 003e25121b3761a6e9440dcd4f0885975e0d98c1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816452"
---
# <a name="call-tree-view---contention-data"></a>Zobrazení stromu volání – data kolizí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení stromu volání zobrazí cesty spuštění funkce, které byly Procházet v profilované aplikaci. Kořen stromu je vstupním bodem do aplikace nebo komponenty. Každý uzel funkce jsou uvedené všechny funkce, které ji volaly, počet pokusů, které funkce se zablokovala a množství času, které funkce byl zablokován, protože byl sporům o prostředek s jiných vláknech či procesy.  
  
 Hodnoty v zobrazení stromu volání jsou pro instance funkce, které byly volány nadřazené funkce ve stromu volání. Procentní hodnoty se počítá srovnáním hodnota instance funkce celkový počet sporů během spuštění profilování.  
  
## <a name="highlighting-the-execution-hot-path"></a>Zvýraznění provádění kritickou cestu  
 Zobrazení stromu volání můžete rozbalit a zvýrazňovat postupu provádění procesu nebo funkci, kterou vytvořili většina sporů.  
  
-   Zobrazit Nejaktivnější cestu, klikněte pravým tlačítkem myši na proces nebo funkci a klikněte na **rozbalit kritickou cestu**.  
  
## <a name="setting-the-call-tree-root-node"></a>Nastavení kořenový uzel stromu volání  
 Každý proces při spuštění profilování se zobrazí jako kořenový uzel. Pokud chcete nastavit počáteční uzel zobrazení stromu volání, klikněte pravým tlačítkem na uzel, který chcete nastavit jako počáteční uzel a potom klikněte na tlačítko **nastavit kořenový**.  
  
 Když nastavíte kořenový uzel, odstraníte všechny položky ze zobrazení s výjimkou podstrom uzel, který jste vybrali. Obnovit původní uzel kořenový uzel, klikněte pravým tlačítkem v zobrazení stromu volání a pak klikněte na **resetování kořenového**.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní čas zablokování**|Čas, který se zablokoval instance této funkce v této cestě provádění spuštění při spuštění profilace. Čas nezahrnuje čas zablokování podřízené funkcí, které byly volány funkce.|  
|**% Výhradního času zablokování**|Procento všech času zablokování spuštění profilování, která byla pro tuto funkci v této cestě provádění výhradní čas zablokování.|  
|**Výhradní spory**|Počet sporů, ke kterým došlo v instancích této funkce v této cestě spuštění. Číslo nezahrnuje spory podřízené funkce volané funkce.|  
|**% Výhradních sporů**|Procento sporů během spuštění profilování, které byly výhradních sporů instancí této funkce, které byly volány nadřazené funkce ve stromu volání.|  
|**Adresa funkce**|Adresa funkce.|  
|**Název funkce**|Plně kvalifikovaný název funkce.|  
|**Celkový čas zablokování**|Celkový čas, který se zablokoval instance této funkce v této cestě provádění spuštění při spuštění profilace. Čas obsahuje čas zablokování podřízené funkcí volaných funkcí.|  
|**% Celkového času zablokování**|Procento všech času zablokování při spuštění, který profilace byla celkový čas zablokování pro instance této funkce v této cestě spuštění.|  
|**Celkově sporů**|Celkový počet sporů, zablokované instance této funkce v této cestě spuštění. Číslo obsahuje tento počet sporů: podřízené funkcí volaných funkcí.|  
|**% Celkových sporů**|Procento všech sporů při spuštění, který profilace se celkově sporů instancí této funkce v této cestě spuštění.|  
|**úroveň**|Úroveň funkce ve stromu volání. Pouze v sestavách VSReport příkazového řádku. Další informace najdete v tématu v [VSPerfReport](../profiling/vsperfreport.md).|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje funkci.|  
|**ID procesu**|ID procesu (PID) běhu profilování.|  
|**Název procesu**|Název procesu.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view.md)   
 [Zobrazení stromu volání – instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení stromu volání – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)



