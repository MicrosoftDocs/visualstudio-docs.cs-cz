---
title: Zobrazení stromu volání – data vzorkování | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 558cef408ceca48a55563ae31f2399da0e951b8e
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779750"
---
# <a name="call-tree-view---sampling-data"></a>Zobrazení stromu volání – vzorkování dat
Zobrazení stromu volání zobrazuje cesty provádění funkce, které byly provázány v profilované aplikaci.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Kořen stromu je vstupní bod do aplikace nebo komponenty. Každý uzel funkce obsahuje seznam všech funkcí, které zavolaly, a údaje o výkonu pro tato volání funkcí.

 Hodnoty ve stromovém zobrazení volání jsou pro instance funkcí, které byly volány nadřazenou funkcí ve stromu volání. Procentuální hodnoty se vypočtou porovnáním hodnoty instance funkce s celkovým počtem vzorků v běhu profilace.

## <a name="highlight-the-execution-hot-path"></a>Zvýraznit cestu k vykonání za běhu
 Zobrazení stromu volání může rozšiřovat a zvýrazňovat cestu spuštění procesu nebo funkce, která byla Navzorkovaná nejčastěji. Chcete-li zobrazit nejvíce aktivních cest, klikněte pravým tlačítkem myši na proces nebo funkci a potom klikněte na možnost Rozbalit kritickou **cestu**.

## <a name="set-the-call-tree-root-node"></a>Nastavit kořenový uzel stromu volání
 Každý proces v průběhu profilace se zobrazuje jako kořenový uzel. Chcete-li nastavit počáteční uzel zobrazení stromu volání, klikněte pravým tlačítkem myši na uzel, který chcete nastavit jako počáteční uzel, a vyberte **Nastavit kořen**.

 Když nastavíte kořenový uzel, eliminují se všechny ostatní záznamy z zobrazení kromě podstromu vybraného uzlu. Chcete-li obnovit kořenový uzel zpět na původní uzel, klikněte pravým tlačítkem myši v okně zobrazení stromu volání a vyberte **obnovit kořen**.

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|
|**Název funkce**|Plně kvalifikovaný název funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Adresa funkce|
|**Obsah**|Hloubka této funkce ve stromu volání. Pouze v sestavách příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) .|
|**Exkluzivní vzorky**|Počet vzorků, které byly shromážděny touto funkcí při volání nadřazené funkce ve stromu volání. Toto číslo neobsahuje vzorky, které byly shromážděny ve funkcích, které byly volány funkcí.|
|**% Exkluzivních vzorků**|Procento všech vzorků v běhu profilace, které byly exkluzivními vzorky této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|
|**Vzorky včetně**|Počet vzorků, které byly shromážděny touto funkcí při volání nadřazené funkce ve stromu volání. Toto číslo zahrnuje ukázky, které byly shromážděny ve funkcích, které byly volány funkcí.|
|**% Včetně vzorků**|Procentuální podíl všech vzorků v průběhu profilace, které byly včetně vzorků této funkce, pokud byla volána nadřazenou funkcí ve stromu volání.|

## <a name="see-also"></a>Viz také:
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení stromu volání – data vzorkování profileru](../profiling/call-Tree-view-sampling-data.md)
- [Zobrazení stromu volání – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Zobrazení stromu volání – instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)
