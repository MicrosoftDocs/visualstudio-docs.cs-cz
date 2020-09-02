---
title: Zobrazení stromu volání – data vzorkování paměti .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ed0d8a2ccf8e33b493ddcb71f9ce3a794a06862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150747"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Zobrazení stromu volání – data vzorkování paměti .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení stromu volání zobrazuje cesty provádění funkce, které byly provázány v profilované aplikaci. Kořen stromu je vstupní bod do aplikace nebo komponenty. Každý uzel funkce obsahuje seznam všech funkcí, které jsou volány, a data o přidělování paměti .NET týkající se těchto volání funkce.  
  
 Hodnoty ve stromovém zobrazení volání jsou pro instance funkcí, které byly volány nadřazenou funkcí ve stromu volání. Procentuální hodnoty se vypočtou porovnáním hodnoty instance funkce s celkovým počtem nebo velikostí přidělení při spuštění profilace.  
  
## <a name="highlighting-the-execution-hot-path"></a>Zvýrazňování kritické cesty spuštění  
 Zobrazení stromu volání může rozšiřovat a zvýrazňovat cestu spuštění procesu nebo funkce, která vytvořila největší nebo nejvíc objektů paměti. Chcete-li zobrazit nejvíce aktivních cest, klikněte pravým tlačítkem myši na proces nebo funkci a potom klikněte na **položku Rozbalit**kritickou cestu.  
  
## <a name="setting-the-call-tree-root-node"></a>Nastavení kořenového uzlu stromu volání  
 Každý proces v průběhu profilace se zobrazuje jako kořenový uzel. Chcete-li nastavit počáteční uzel zobrazení stromu volání na jiný uzel, klikněte pravým tlačítkem myši na uzel, který chcete nastavit jako počáteční uzel, a vyberte **Nastavit kořen**.  
  
 Když nastavíte kořenový uzel, eliminují se všechny ostatní záznamy z zobrazení kromě podstromu vybraného uzlu. Kořenový uzel můžete obnovit zpátky na uzel, který jste si prohlíželi. v okně zobrazení stromu volání klikněte pravým tlačítkem myši a vyberte **obnovit kořen**.  
  
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
|**Obsah**|Hloubka funkce ve stromu volání.|  
|**Celkové alokace**|Počet objektů, které byly přiděleny instancemi této funkce, které byly volány nadřazenou funkcí ve stromu volání. Toto číslo zahrnuje přidělení, která byla provedena pomocí podřízených funkcí.|  
|**% Celkových přidělení**|Procentuální podíl všech objektů, které byly vytvořeny v rámci profilace, které byly zahrnuty do přidělení této funkce.|  
|**Exkluzivní přidělení**|Počet objektů, které byly přiděleny instancemi této funkce, které byly volány nadřazenou funkcí ve stromu volání. Toto číslo nezahrnuje přidělení, která byla provedena v podřízených funkcích.|  
|**% Exkluzivní alokace**|Procentuální podíl všech objektů, které byly vytvořeny v rámci profilace, které byly exkluzivním přidělením instancí funkcí, které byly volány nadřazenou funkcí ve stromu volání.|  
|**Včetně bajtů**|Počet bajtů v paměti, které byly přiděleny instancemi této funkce, které byly volány nadřazenou funkcí ve stromu volání. Toto číslo zahrnuje přidělení, která byla provedena pomocí podřízených funkcí.|  
|**% Celkových bajtů**|Procentuální podíl všech bajtů paměti, které byly přiděleny při spuštění profilace, včetně přidělení této funkce.|  
|**Exkluzivní počet bajtů**|Počet bajtů v paměti, které byly přiděleny instancemi této funkce, které byly volány nadřazenou funkcí ve stromu volání. Toto číslo nezahrnuje přidělení, která byla provedena v podřízených funkcích.|  
|**% Exkluzivních bajtů**|Procento všech bajtů paměti, které byly přiděleny při spuštění profilace, které byly exkluzivním přidělením této funkce.|  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení stromu volání – instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)
