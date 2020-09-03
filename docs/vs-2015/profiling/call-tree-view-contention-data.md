---
title: Zobrazení stromu volání – data kolizí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d12f1a2343018f05f0e741222b844c562b50f5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189368"
---
# <a name="call-tree-view---contention-data"></a>Zobrazení stromu volání – data kolizí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení stromu volání zobrazuje cesty provádění funkce, které byly provázány v profilované aplikaci. Kořen stromu je vstupní bod do aplikace nebo komponenty. Každý uzel funkce obsahuje seznam všech funkcí, které volá, počet zablokování funkce a dobu, po kterou byla funkce zablokovaná, protože se jednalo o prostředek s jinými vlákny nebo procesy.  
  
 Hodnoty ve stromovém zobrazení volání jsou pro instance funkcí, které byly volány nadřazenou funkcí ve stromu volání. Procentuální hodnoty se vypočtou porovnáním hodnoty instance funkce s celkovým počtem sporů při spuštění profilace.  
  
## <a name="highlighting-the-execution-hot-path"></a>Zvýrazňování kritické cesty spuštění  
 Zobrazení stromu volání může rozšiřovat a zvýrazňovat cestu spuštění procesu nebo funkce, která vytvořila většinu sporů.  
  
- Chcete-li zobrazit nejvíce aktivních cest, klikněte pravým tlačítkem myši na proces nebo funkci a potom klikněte na **položku Rozbalit**kritickou cestu.  
  
## <a name="setting-the-call-tree-root-node"></a>Nastavení kořenového uzlu stromu volání  
 Každý proces v průběhu profilace se zobrazuje jako kořenový uzel. Chcete-li nastavit počáteční uzel zobrazení stromu volání, klikněte pravým tlačítkem myši na uzel, který chcete nastavit jako spouštěcí uzel, a poté klikněte na možnost **Nastavit kořen**.  
  
 Když nastavíte kořenový uzel, eliminují se všechny ostatní položky ze zobrazení s výjimkou podstromu uzlu, který jste vybrali. Chcete-li obnovit kořenový uzel zpět na původní uzel, klikněte pravým tlačítkem myši v zobrazení stromu volání a potom klikněte na možnost **resetovat kořen**.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní čas zablokování**|Čas, kdy se instance této funkce v této cestě provádění zablokovaly při spuštění profilace. Čas nezahrnuje čas zablokování podřízených funkcí, které byly volány funkcí.|  
|**% Výhradního času zablokování**|Procento veškerého času zablokování v běhu profilace, které bylo exkluzivně zablokováno pro tuto funkci v této cestě spuštění.|  
|**Exkluzivní spory**|Počet sporů, ke kterým došlo v instancích této funkce v této cestě spuštění. Počet nezahrnuje spory podřízených funkcí volaných funkcí.|  
|**% Výhradních sporů**|Procentuální podíl všech sporů v rámci profilace, kterým byly exkluzivní spory instancí této funkce, které byly volány nadřazenou funkcí ve stromu volání.|  
|**Adresa funkce**|Adresa funkce|  
|**Název funkce**|Plně kvalifikovaný název funkce.|  
|**Celková doba zablokování**|Celková doba, kterou instance této funkce v této cestě spuštění zablokovaly spuštění při spuštění profilace. Čas zahrnuje čas zablokování podřízených funkcí volaných funkcí.|  
|**% Celkového času zablokování**|Procento veškerého času zablokování v běhu profilace, které bylo celková doba zablokování pro instance této funkce v této cestě spuštění.|  
|**Celkové spory**|Celkový počet sporů, které zablokovaly výskyt této funkce v této cestě spuštění. Toto číslo zahrnuje spory podřízených funkcí volaných funkcí.|  
|**% Celkových sporů**|Procento všech sporů v rámci profilace běhu, kterým byly zahrnuté spory instancí této funkce v této cestě spuštění.|  
|**Obsah**|Úroveň funkce ve stromu volání. Pouze v sestavách příkazového řádku VSReport. Další informace najdete v části v tématu [VSPerfReport](../profiling/vsperfreport.md).|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|  
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|  
|**Název procesu**|Název procesu|  
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view.md)   
 [Zobrazení stromu volání – instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení stromu volání – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)
