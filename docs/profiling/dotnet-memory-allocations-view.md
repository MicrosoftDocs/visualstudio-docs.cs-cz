---
title: Zobrazení alokace paměti .NET | Microsoft Docs
description: Seznamte se s zobrazením přidělení paměti .NET, které obsahuje typy, které byly vytvořeny během profilace spuštění.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.allocation
helpviewer_keywords:
- performance reports, allocation view
- Allocations view
- profiling tools, Allocation view
- profiling tools reports, Allocation view
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 47ab3cfd9ae57e48e7a5884729efce8413b543be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964794"
---
# <a name="net-memory-allocations-view"></a>Přidělení paměti .NET – zobrazení
Zobrazení přidělení zobrazuje seznam typů, které byly vytvořeny během profilace. Každý typ je kořenový uzel stromu volání, který zobrazuje cesty provádění funkce, jejichž výsledkem je přidělení typu.

 Data v řádku typu zobrazují celkový počet objektů typu, které byly vytvořeny během profilace, a celkový počet bajtů přidělených pro objekty daného typu. Zahrnuté a exkluzivní hodnoty pro typ jsou vždycky stejné.

- Hodnoty včetně jsou pro objekty vytvořené v instancích funkce a jejích podřízených funkcích, které byly volány nadřazenou funkcí ve stromu volání.

- Exkluzivní hodnoty jsou pro objekty, které byly vytvořeny přímo funkcí při volání nadřazené funkce. Objekty vytvořené v podřízených funkcích nejsou zahrnuty.

  Data pro funkci zobrazují počet vytvořených objektů a počet bajtů přidělených pro objekty nadřazeného typu.

## <a name="highlight-the-execution-hot-path"></a>Zvýraznit cestu k vykonání za běhu
 Můžete najít cestu spuštění stromu volání, která vytvořila většinu objektů nadřazeného typu.

- Chcete-li zobrazit nejvíce aktivních cest, klikněte pravým tlačítkem myši na typ nebo funkci a potom klikněte na **položku Rozbalit** kritickou cestu.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název přiděleného typu nebo funkce.|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu obsahujícího typ nebo funkci.|
|**Cesta k modulu**|Cesta modulu obsahujícího typ nebo funkci.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro typ nebo funkci.|
|**Číslo řádku funkce**|Číslo řádku začátku této definice typu nebo funkce ve zdrojovém souboru.|
|**Obsah**|Označuje, zda jsou data pro typ nebo funkci.|
|**Celkové alokace**|– Pro funkci celkový počet objektů nadřazeného typu, které byly vytvořeny funkcí. Toto číslo zahrnuje objekty vytvořené v podřízených funkcích.<br />– Pro typ je to celkový počet instancí tohoto typu, které byly vytvořeny.|
|**% Celkových přidělení**|– Pro funkci je procento všech objektů vytvořených v průběhu profilace, které byly součástí této funkce, včetně přidělení nadřazeného typu.<br />– Pro typ se jedná o procentuální podíl celkového počtu objektů, které byly vytvořeny v profilování, které byly instance daného typu.|
|**Exkluzivní přidělení**|– Pro funkci je počet objektů, které byly vytvořeny v době, kdy byla funkce přímo spuštěna v horní části zásobníku volání. Toto číslo nezahrnuje objekty vytvořené v podřízených funkcích.<br />– Pro typ je to celkový počet instancí tohoto typu, které byly vytvořeny.|
|**% Exkluzivní alokace**|– Pro funkci je procento všech objektů vytvořených v rámci profilace spuštěno jako exkluzivní přidělení nadřazeného typu pomocí funkce.<br />– Pro typ se jedná o procentuální podíl celkového počtu objektů, které byly vytvořeny v profilování, které byly instance daného typu.|
|**Včetně bajtů**|– Pro funkci počet bajtů paměti, které byly přiděleny funkcí pro objekty nadřazeného typu. Toto číslo zahrnuje paměť, která byla přidělena jeho podřízenými funkcemi.<br />– Pro typ je celkový počet bajtů, které byly přiděleny při spuštění profilování pro instance daného typu.|
|**% Celkových bajtů**|– Pro funkci je procento celé paměti přidělené při spuštění profilování, které je součástí této funkce, včetně přidělení nadřazeného typu.<br />– Pro typ je procento celé paměti přidělené při spuštění profilování, které bylo přiděleno pro instance daného typu.|
|**Exkluzivní počet bajtů**|– Pro funkci počet bajtů paměti, které byly přiděleny funkcí pro objekty nadřazeného typu. Toto číslo nezahrnuje paměť, která byla přidělena jeho podřízenými funkcemi.<br />– Pro typ je celkový počet bajtů, které byly přiděleny při spuštění profilování pro instance daného typu.|
|**% Exkluzivních bajtů**|– Pro funkci je procento celé paměti přidělené při spuštění profilování, které bylo funkcí exkluzivní pro přidělení nadřazeného typu.<br />– Pro typ je procento celé paměti přidělené při spuštění profilování, které bylo přiděleno pro instance daného typu.|
