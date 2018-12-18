---
title: Zobrazení stromu volání – Data instrumentace paměti .NET | Dokumentace Microsoftu
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
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed87363751c18794d9cf4c00e156d75760e0bf8d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782502"
---
# <a name="call-tree-view---net-memory-instrumentation-data"></a>Zobrazení stromu volání – data instrumentace paměti .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení stromu volání .NET profilování data o přidělování paměti, která byla shromážděna pomocí metody instrumentace zobrazí cesty spuštění funkce, které byly Procházet v profilované aplikaci. Kořen stromu je vstupním bodem do aplikace nebo komponenty. Každý uzel funkce jsou uvedené všechny funkce, která je volána a paměti .NET a dat časování pro funkci.  
  
 Hodnoty v zobrazení stromu volání jsou pro instance funkce, které byly volány nadřazené funkce ve stromu volání. Procentní hodnoty se počítá srovnáním hodnota instance funkce celkového počtu nebo velikosti přidělení při spuštění profilace.  
  
## <a name="highlighting-the-execution-hot-path"></a>Zvýraznění provádění kritickou cestu  
 Zobrazení stromu volání můžete rozbalit a zvýrazňovat postupu provádění procesu nebo funkci, kterou vytvořili největší nebo většinu objektů v paměti. Zobrazit Nejaktivnější cestu, klikněte pravým tlačítkem myši na proces nebo funkci a klikněte na **rozbalit kritickou cestu**.  
  
## <a name="setting-the-call-tree-root-node"></a>Nastavení kořenový uzel stromu volání  
 Každý proces při spuštění profilování se zobrazí jako kořenový uzel. Počáteční uzel zobrazení stromu volání můžete nastavit tak, že pravým tlačítkem myši na uzel, který chcete nastavit jako počáteční uzel a pak vyberete **nastavit kořenový**.  
  
 Když nastavíte kořenový uzel, odstraníte všechny položky ze zobrazení s výjimkou podstrom vybraný uzel. Můžete resetovat kořenový uzel zpět do uzlu, který byl zobrazený; Klikněte pravým tlačítkem v okně zobrazení stromu volání a vyberte **resetování kořenového**.  
  
## <a name="general"></a>Obecné  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Název funkce**|Název funkce.|  
|**Adresa funkce**|Adresa funkce.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Počet volání**|Celkový počet volání této funkce.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje funkci.|  
|**ID procesu**|ID procesu (PID) běhu profilování.|  
|**Název procesu**|Název, který je přiřazen k procesu.|  
|**Výhradní čas režie**|Časová náročnost této funkce, která způsobuje instrumentace. Režie byla odečtena od vylučuje všechny časy.|  
|**Celkový čas režie**|Časová náročnost této funkce a její podřízené funkce, jež je způsobena instrumentace. Test zatížení byla odečtena od fiskálního (včetně).|  
|**Typ**|Kontext funkce:<br /><br /> -   **0** -aktuální funkce<br />-   **1** – funkce, která volá aktuální funkci<br />-   **2** – funkce, která volá aktuální funkci<br /><br /> Pouze v [VSPerfReport](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
|**Název kořenové funkce**|Název aktuální funkce. Pouze v [VSPerfReport](../profiling/vsperfreport.md) příkazového řádku sestavy.|  
  
## <a name="net-memory-values"></a>Hodnoty paměti .NET  
 (Včetně) hodnot paměti .NET funkce označují číslo (přidělení) a velikost (bajty) objektů, které byly vytvořeny tak, že funkce a funkce, které byly volány funkce.  
  
 Výhradní paměti hodnoty označují, počtu a velikosti objektů, které byly vytvořeny pomocí kódu v těle funkce a ne pomocí funkcí, které byly volány funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celkově přidělení**|Počet objektů, které byly přiděleny instancí této funkce, které byly volány nadřazené funkce ve stromu volání. Toto číslo zahrnuje přidělení, které byly provedeny pomocí podřízených funkcí.|  
|**% Celkových přidělení**|Procento všech objektů, které byly vytvořeny v profilování, která se celkově přidělení instancí funkce, které byly volány nadřazené funkce ve stromu volání.|  
|**Výhradní přidělení**|Počet objektů, které byly přiděleny instancí této funkce, které byly volány nadřazené funkce ve stromu volání. Toto číslo nezahrnuje přidělení, které byly provedeny pomocí podřízených funkcí.|  
|**% Výhradních přidělení**|Procento všech objektů, které byly vytvořeny v profilování, které byly výhradních přidělení instancí funkce, které byly volány nadřazené funkce ve stromu volání.|  
  
## <a name="elapsed-inclusive-values"></a>Uplynulý včetně hodnoty  
 Uplynulý včetně hodnoty označuje datum a čas, který funkce byla v zásobníku volání. Čas obsahuje čas, který byl stráven ve funkcích, které volal funkci a ve volání do operačního systému, například vstupně výstupní operace a přepnutí kontextu.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý celkový čas**|Celkový uplynulý celkový čas všechna volání této funkce, když byla volána funkce nadřazené ve stromu volání.|  
|**% Uplynulého celkového času**|Procento celkového uplynulý celkový čas spuštění profilování, která se využilo na celkový uplynulý celkový čas této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Průměrný uplynulý celkový čas**|Průměr uplynulý celkový čas volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Maximální uplynulý celkový čas**|Maximální uplynulý celkový čas volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Minimální uplynulý celkový čas**|Minimální uplynulý celkový čas volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
  
## <a name="elapsed-exclusive-values"></a>Uplynulý výhradní hodnoty  
 Uplynulý výhradní hodnoty označuje datum a čas, který funkce byla spuštěna přímo v horní části zásobníku volání. Čas zahrnuje čas ve volání do operačního systému, například vstupně výstupní operace a přepnutí kontextu. Čas, ale nezahrnuje čas, který byl stráven ve funkcích, které byly volány funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Uplynulý výhradní čas**|Celkový uplynulý výhradní čas všechna volání této funkce, když byla volána funkce nadřazené ve stromu volání.|  
|**% Uplynulého výhradního času**|Procentuální podíl celkového počtu uplynulý výhradní čas spuštění profilování, která se využilo na celkový uplynulý výhradní čas této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Průměrný uplynulý výhradní čas**|Průměr uplynulý výhradní čas volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Maximální uplynulý výhradní čas**|Maximální uplynulý výhradní čas volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Minimální uplynulý výhradní čas**|Minimální uplynulý výhradní čas volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
  
## <a name="application-inclusive-values"></a>Aplikace (včetně) hodnot  
 Aplikace (včetně) hodnot označuje datum a čas, který funkce byla v zásobníku volání. Čas nezahrnuje čas, který byl stráven ve volání do operačního systému, například vstupně výstupní operace a přepnutí kontextu. Čas zahrnují čas, který byl stráven v podřízené funkce, které byly volány funkce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Celkový čas aplikace**|Celkový čas aplikace celkový počet všech volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**% Celkového času aplikace**|Procento celkového uplynulý celkový čas spuštění profilování, která se využilo na celkový čas celkový aplikace této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Průměrný celkový čas aplikace**|Celkový čas průměrná aplikace volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Maximální celkový čas aplikace**|Celkový čas aplikace maximální volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Minimální celkový čas aplikace**|Celkový čas aplikace minimální volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
  
## <a name="application-exclusive-values"></a>Výhradní hodnoty aplikace  
 Výhradní hodnoty, které aplikaci označuje čas, který byl vynaložen ve funkci, s výjimkou čas, který byl stráven v podřízené funkce, které byly volány funkce. Čas vylučuje volání do operačního systému, jako je například vstupně výstupní operace a přepnutí kontextu.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní čas aplikace**|Výhradní čas aplikace celkový počet všech volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**% Výhradního času aplikace**|Procentuální podíl celkového počtu uplynulý výhradní čas spuštění profilování, který byl vynaložen v výhradní čas aplikace celkový této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Průměrný výhradní čas aplikace**|Výhradní čas aplikace průměrné volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Maximální výhradní čas aplikace**|Výhradní čas aplikace maximální volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|  
|**Minimální výhradní čas aplikace**|Výhradní čas aplikace minimální volání této funkce, když se jmenovala nadřazené funkce ve stromu volání.|



