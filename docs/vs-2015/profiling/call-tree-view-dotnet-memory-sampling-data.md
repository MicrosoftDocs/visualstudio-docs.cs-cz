---
title: Zobrazení stromu volání – Data vzorkování paměti .NET | Dokumentace Microsoftu
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
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6667d0e0ad76210434f40eaf89e4790430ffb0e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758612"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Zobrazení stromu volání – data vzorkování paměti .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení stromu volání zobrazí cesty spuštění funkce, které byly Procházet v profilované aplikaci. Kořen stromu je vstupním bodem do aplikace nebo komponenty. Každý uzel funkce jsou uvedené všechny funkce, které ji volaly a data o přidělování paměti .NET o volání těchto funkcí.  
  
 Hodnoty v zobrazení stromu volání jsou pro instance funkce, které byly volány nadřazené funkce ve stromu volání. Procentní hodnoty se počítá srovnáním hodnota instance funkce celkového počtu nebo velikosti přidělení při spuštění profilace.  
  
## <a name="highlighting-the-execution-hot-path"></a>Zvýraznění provádění kritickou cestu  
 Zobrazení stromu volání můžete rozbalit a zvýrazňovat postupu provádění procesu nebo funkci, kterou vytvořili největší nebo většinu objektů v paměti. Zobrazit Nejaktivnější cestu, klikněte pravým tlačítkem myši na proces nebo funkci a klikněte na **rozbalit kritickou cestu**.  
  
## <a name="setting-the-call-tree-root-node"></a>Nastavení kořenový uzel stromu volání  
 Každý proces při spuštění profilování se zobrazí jako kořenový uzel. Pokud chcete nastavit počáteční uzel zobrazení stromu volání na jiný uzel, klikněte pravým tlačítkem na uzel, který chcete nastavit jako počáteční uzel a vyberte **nastavit kořenový**.  
  
 Když nastavíte kořenový uzel, odstraníte všechny položky ze zobrazení s výjimkou podstrom vybraný uzel. Můžete resetovat kořenový uzel zpět do uzlu, který byl zobrazený; Klikněte pravým tlačítkem v okně zobrazení stromu volání a vyberte **resetování kořenového**.  
  
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
|**úroveň**|Hloubka funkce ve stromu volání.|  
|**Celkově přidělení**|Počet objektů, které byly přiděleny instancí této funkce, které byly volány nadřazené funkce ve stromu volání. Toto číslo zahrnuje přidělení, které byly provedeny pomocí podřízených funkcí.|  
|**% Celkových přidělení**|Procento všech objektů, které byly vytvořeny v profilování, která se celkově přidělení této funkce.|  
|**Výhradní přidělení**|Počet objektů, které byly přiděleny instancí této funkce, které byly volány nadřazené funkce ve stromu volání. Toto číslo nezahrnuje přidělení, které byly provedeny pomocí podřízených funkcí.|  
|**% Výhradních přidělení**|Procento všech objektů, které byly vytvořeny v profilování, které byly výhradních přidělení instancí funkce, které byly volány nadřazené funkce ve stromu volání.|  
|**Celkově bajtů**|Počet bajtů paměti, které byly přiděleny instancí této funkce, které byly volány nadřazené funkce ve stromu volání. Toto číslo zahrnuje přidělení, které byly provedeny pomocí podřízených funkcí.|  
|**% Celkových bajtů**|Procento bajtů paměti, které byly přiděleny v profilování, která se celkově přidělení této funkce.|  
|**Výhradní bajty**|Počet bajtů paměti, které byly přiděleny instancí této funkce, které byly volány nadřazené funkce ve stromu volání. Toto číslo nezahrnuje přidělení, které byly provedeny pomocí podřízených funkcí.|  
|**% Výhradních bajtů**|Procento všech počet bajtů paměti, které byly přiděleny v profilování, které byly výhradních přidělení této funkce.|  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení stromu volání – instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)



