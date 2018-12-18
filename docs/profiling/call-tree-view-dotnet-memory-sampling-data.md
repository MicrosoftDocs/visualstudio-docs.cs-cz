---
title: Zobrazení stromu volání – Data vzorkování paměti .NET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c3c7c70057380289272e86cf7187680746dafdd2
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2018
ms.locfileid: "34336042"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Zobrazení stromu volání – data vzorkování paměti .NET
Zobrazení stromu volání zobrazuje cesty provádění funkce, které byly provázán v PROFILOVANÉHO aplikaci. Kořen stromu je vstupním bodem do součást nebo aplikace. Každý uzel funkce jsou uvedeny všechny funkce, které ji volat a data přidělení paměti .NET o těchto volání funkcí.  
  
 Hodnoty v zobrazení stromu volání jsou pro funkce instancí, které byly volá funkci nadřazené ve stromové struktuře volání. Procentní hodnoty se počítá srovnáním hodnotu instance funkce pro celkový počet nebo velikost přidělení v profilaci spustit.  
  
## <a name="highlight-the-execution-hot-path"></a>Zvýraznit cestu aktivní provádění  
 Zobrazení stromu volání můžete rozbalit a zvýraznit cestu spouštění procesu nebo funkce, která vytvořila na největší nebo většinu objektů paměti. Zobrazení Nejaktivnější cesty, klikněte pravým tlačítkem na proces nebo funkce a pak klikněte na tlačítko **rozbalte aktivní trase**.  
  
## <a name="set-the-call-tree-root-node"></a>Nastavit kořenový uzel stromu volání  
 Každý proces v profilaci spuštění se zobrazí jako kořenový uzel. Pokud chcete nastavit počáteční uzel zobrazení stromu volání na jiný uzel, klikněte pravým tlačítkem na uzel, který chcete nastavit jako počáteční uzel a vyberte **nastavit kořenové**.  
  
 Pokud nastavíte kořenového uzlu, můžete eliminovat všechny položky ze zobrazení s výjimkou podstrom vybraného uzlu. Můžete resetovat kořenový uzel zpět do uzlu, který se zobrazil; v okně zobrazení stromu volání klikněte pravým tlačítkem a vyberte **resetovat kořenové**.  
  
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
|**úroveň**|Hloubka funkce ve stromové struktuře volání.|  
|**Přidělení (včetně).**|Počet objektů, které byly přiděleny instancí této funkce, které byly volá funkci nadřazené ve stromové struktuře volání. Tato hodnota zahrnuje přidělení, které byly provedeny podle podřízené funkce.|  
|**% Přidělení (včetně).**|Procento všech objektů, které byly vytvořeny v profilaci spuštění, které byly včetně přidělení této funkce.|  
|**Výhradní přidělení**|Počet objektů, které byly přiděleny instancí této funkce, které byly volá funkci nadřazené ve stromové struktuře volání. Toto číslo nezahrnuje přidělení, které byly provedeny podle podřízené funkce.|  
|**Výhradní přidělení %**|Procento všech objektů, které byly vytvořeny v profilaci spuštění, které byly výhradní přidělení instancí funkce, které byly volá funkci nadřazené ve stromové struktuře volání.|  
|**Bajtů (včetně).**|Počet bajtů v paměti, které byly přiděleny instancí této funkce, které byly volá funkci nadřazené ve stromové struktuře volání. Tato hodnota zahrnuje přidělení, které byly provedeny podle podřízené funkce.|  
|**% Bajtů (včetně).**|Procento všech bajtů paměti, které byly přiděleny v profilaci spuštění, které byly včetně přidělení této funkce.|  
|**Výhradní bajtů**|Počet bajtů v paměti, které byly přiděleny instancí této funkce, které byly volá funkci nadřazené ve stromové struktuře volání. Toto číslo nezahrnuje přidělení, které byly provedeny podle podřízené funkce.|  
|**% Výhradní bajtů**|Procento všech bajtů paměti, které byly přiděleny v profilaci spuštění, které byly výhradní přidělení této funkce.|  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení stromu volání – instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)