---
title: Zobrazení stromu volání – data konfliktů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e91e231f72b006d2020c8b4d5d96c7e24fa1dd9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779776"
---
# <a name="call-tree-view---contention-data"></a>Zobrazení stromu volání – data tvrzení
Zobrazení Strom volání zobrazuje cesty spuštění funkce, které byly provázány v profilované aplikaci. Kořen stromu je vstupní bod do aplikace nebo součásti. Každý uzel funkce uvádí všechny funkce, které volal, počet, kolikrát byla funkce blokována a množství času, který byla funkce blokována, protože bojovala o prostředek s jinými vlákny nebo procesy.

 Hodnoty v zobrazení Strom volání jsou pro instance funkcí, které byly volány nadřazenou funkcí ve stromu volání. Procentuální hodnoty jsou vypočteny porovnáním hodnoty instance funkce s celkovým počtem tvrzení v profilování spustit.

## <a name="highlight-the-execution-hot-path"></a>Zvýrazněte cestu spuštění hot
 Strom volání zobrazení můžete rozbalit a zvýraznit cestu spuštění procesu nebo funkce, která vytvořila nejvíce tvrzení.

- Chcete-li zobrazit nejaktivnější cestu, klepněte pravým tlačítkem myši na proces nebo funkci a potom klepněte na příkaz **Rozbalit aktivní cestu**.

## <a name="set-the-call-tree-root-node"></a>Nastavení kořenového uzlu kořenového stromu volání
 Každý proces v profilování spustit se zobrazí jako kořenový uzel. Chcete-li nastavit počáteční uzel zobrazení Strom volání, klepněte pravým tlačítkem myši na uzel, který chcete nastavit jako počáteční uzel, a potom klepněte na příkaz **Nastavit kořenový adresář**.

 Když nastavíte kořenový uzel, odstraníte všechny ostatní položky ze zobrazení s výjimkou podstromu vybraného uzlu. Chcete-li kořenový uzel obnovit zpět na původní uzel, klepněte pravým tlačítkem myši do zobrazení Strom volání a potom klepněte na příkaz **Obnovit kořenový adresář**.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní blokovaný čas**|Čas, který instance této funkce v této cestě spuštění byly blokovány provádění v profilování spustit. Čas nezahrnuje blokovaný čas podřízených funkcí, které byly volány funkcí.|
|**Výhradní blokovaný čas %**|Procento všech blokovaných čas v profilování spustit, který byl výhradní blokovaný čas pro tuto funkci v této cestě spuštění.|
|**Exkluzivní tvrzení**|Počet konfliktů, ke kterým došlo v instancích této funkce v této cestě spuštění. Číslo nezahrnuje konflikty podřízených funkcí volaných funkcí.|
|**Výhradní tvrzení %**|Procento všech tvrzení v profilování spustit, které byly výhradní tvrzení instance této funkce, které byly volány nadřazené funkce ve stromu volání.|
|**Adresa funkce**|Adresa funkce.|
|**Název funkce**|Plně kvalifikovaný název funkce.|
|**Včetně blokovaného času**|Celková doba, po kterou byly instance této funkce v této cestě spuštění blokovány v spuštění profilování. Čas zahrnuje blokovaný čas podřízených funkcí volaných funkcí.|
|**Včetně blokovaného času %**|Procento všech blokovaných čas v profilování spustit, který byl včetně blokovaný čas pro instance této funkce v této cestě spuštění.|
|**Inkluzivní tvrzení**|Celkový počet tvrzení, které blokovaly instance této funkce v této cestě spuštění. Číslo zahrnuje tvrzení podřízených funkcí volaných funkcí.|
|**Inkluzivní tvrzení %**|Procento všech tvrzení v profilování spustit, které byly včetně tvrzení instance této funkce v této cestě spuštění.|
|**Úroveň**|Úroveň funkce ve stromu volání. Pouze v sestavách příkazového řádku VSReport. Další informace naleznete v [vsperfreportu](../profiling/vsperfreport.md).|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení stromu volání](../profiling/call-tree-view.md)
- [Zobrazení stromu volání - instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení stromu volání – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)
- [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)
