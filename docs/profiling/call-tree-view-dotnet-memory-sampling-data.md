---
title: Zobrazení stromu volání – vzorkování paměti .NET | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 76ea78f37cbc8c5e2b6df900aa0e3f320346300a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779763"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Zobrazení stromu volání – vzorkování paměti .NET
Zobrazení Strom volání zobrazuje cesty spuštění funkce, které byly provázány v profilované aplikaci. Kořen stromu je vstupní bod do aplikace nebo součásti. Každý uzel funkce obsahuje seznam všech funkcí, které volal, a data přidělení paměti .NET o těchto voláních funkcí.

 Hodnoty v zobrazení Strom volání jsou pro instance funkcí, které byly volány nadřazenou funkcí ve stromu volání. Procentuální hodnoty se vypočítají porovnáním hodnoty instance funkce s celkovým počtem nebo velikostí přidělení v systému profilování.

## <a name="highlight-the-execution-hot-path"></a>Zvýrazněte cestu spuštění hot
 Strom volání zobrazení můžete rozbalit a zvýraznit cestu spuštění procesu nebo funkce, která vytvořila největší nebo nejvíce objektů paměti. Chcete-li zobrazit nejaktivnější cestu, klepněte pravým tlačítkem myši na proces nebo funkci a potom klepněte na příkaz **Rozbalit aktivní cestu**.

## <a name="set-the-call-tree-root-node"></a>Nastavení kořenového uzlu kořenového stromu volání
 Každý proces v profilování spustit je zobrazen jako kořenový uzel. Chcete-li nastavit počáteční uzel zobrazení Strom volání na jiný uzel, klepněte pravým tlačítkem myši na uzel, který chcete nastavit jako počáteční uzel, a vyberte **nastavit kořenový adresář**.

 Když nastavíte kořenový uzel, odstraníte všechny ostatní položky ze zobrazení kromě podstromu vybraného uzlu. Kořenový uzel můžete obnovit zpět do uzlu, který jste prohlíželi; klepněte pravým tlačítkem myši v okně Zobrazení stromu volání a vyberte **příkaz Obnovit kořenový adresář**.

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
|**Úroveň**|Hloubka funkce ve stromu volání.|
|**Inkluzivní přidělení**|Počet objektů, které byly přiděleny instance této funkce, které byly volány nadřazenou funkcí ve stromu volání. Toto číslo zahrnuje přidělení, které byly provedeny podřízené funkce.|
|**Včetně přidělení %**|Procento všech objektů, které byly vytvořeny v profilování spustit, které byly včetně přidělení této funkce.|
|**Výhradní přidělení**|Počet objektů, které byly přiděleny instance této funkce, které byly volány nadřazenou funkcí ve stromu volání. Toto číslo nezahrnuje přidělení, které byly provedeny podřízené funkce.|
|**Výhradní přidělení %**|Procento všech objektů, které byly vytvořeny v profilování spustit, které byly výhradní přidělení instance funkce, které byly volány nadřazené funkce ve stromu volání.|
|**Včetně bajtů**|Počet bajtů v paměti, které byly přiděleny instance této funkce, které byly volány nadřazenou funkcí ve stromu volání. Toto číslo zahrnuje přidělení, které byly provedeny podřízené funkce.|
|**Včetně bajtů %**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly včetně přidělení této funkce.|
|**Exkluzivní bajty**|Počet bajtů v paměti, které byly přiděleny instance této funkce, které byly volány nadřazenou funkcí ve stromu volání. Toto číslo nezahrnuje přidělení, které byly provedeny podřízené funkce.|
|**Výhradní bajty %**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly výhradní přidělení této funkce.|

## <a name="see-also"></a>Viz také
- [Zobrazení stromu volání - instrumentace](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)
- [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)
