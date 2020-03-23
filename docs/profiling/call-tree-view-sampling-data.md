---
title: Zobrazení stromu volání – vzorkovací data | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779750"
---
# <a name="call-tree-view---sampling-data"></a>Zobrazení stromu volání – vzorkovací data
Zobrazení Strom volání zobrazuje cesty spuštění funkce, které byly provázány v profilované aplikaci.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Kořen stromu je vstupní bod do aplikace nebo součásti. Každý uzel funkce uvádí všechny funkce, které volal a údaje o výkonu těchto volání funkce.

 Hodnoty v zobrazení Strom volání jsou pro instance funkcí, které byly volány nadřazenou funkcí ve stromu volání. Procentuální hodnoty jsou vypočteny porovnáním hodnoty instance funkce s celkovým počtem vzorků v profilování.

## <a name="highlight-the-execution-hot-path"></a>Zvýrazněte cestu spuštění hot
 Strom volání zobrazení můžete rozbalit a zvýraznit cestu spuštění procesu nebo funkce, která byla vzorkována nejčastěji. Chcete-li zobrazit nejaktivnější cestu, klepněte pravým tlačítkem myši na proces nebo funkci a potom klepněte na příkaz **Rozbalit aktivní cestu**.

## <a name="set-the-call-tree-root-node"></a>Nastavení kořenového uzlu kořenového stromu volání
 Každý proces v profilování spustit je zobrazen jako kořenový uzel. Chcete-li nastavit počáteční uzel zobrazení Strom volání, klepněte pravým tlačítkem myši na uzel, který chcete nastavit jako počáteční uzel, a vyberte **nastavit kořenový adresář**.

 Když nastavíte kořenový uzel, odstraníte všechny ostatní položky ze zobrazení kromě podstromu vybraného uzlu. Chcete-li kořenový uzel obnovit zpět na původní uzel, klepněte pravým tlačítkem myši v okně Zobrazení stromu volání a vyberte **příkaz Obnovit kořenový adresář**.

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|
|**Název funkce**|Plně kvalifikovaný název funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Adresa funkce.|
|**Úroveň**|Hloubka této funkce ve stromu volání. Pouze v sestavách příkazového řádku [VSPerfReport.](../profiling/vsperfreport.md)|
|**Exkluzivní ukázky**|Počet vzorků, které byly shromážděny v této funkci, když byla volána nadřazenou funkcí ve stromu volání. Toto číslo nezahrnuje vzorky, které byly shromážděny ve funkcích, které byly volány funkcí.|
|**Exkluzivní vzorky %**|Procento všech vzorků v profilování spustit, které byly výhradní ukázky této funkce, když byla volána nadřazenou funkcí ve stromu volání.|
|**Včetně vzorků**|Počet vzorků, které byly shromážděny v této funkci, když byla volána nadřazenou funkcí ve stromu volání. Toto číslo zahrnuje vzorky, které byly shromážděny ve funkcích, které byly volány funkcí.|
|**Včetně vzorků %**|Procento všech vzorků v profilování spustit, které byly včetně vzorky této funkce, když byla volána nadřazenou funkcí ve stromu volání.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení stromu volání – vzorkovací data profileru](../profiling/call-Tree-view-sampling-data.md)
- [Zobrazení stromu volání – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Zobrazení stromu volání - instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)
