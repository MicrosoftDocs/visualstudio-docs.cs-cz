---
title: Zobrazení přidělení paměti .NET | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7a473a7c6758fe58c82f8894822d3a250165a43
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933674"
---
# <a name="net-memory-allocations-view"></a>Přidělení paměti .NET – zobrazení
Zobrazení přidělení jsou uvedeny typy, které byly vytvořeny během spuštění profilování. Každý typ je kořenový uzel stromu volání, která zobrazuje cesty spuštění funkce, z kterých vzniklo přidělení typu.  
  
 V typu řádku dat zobrazí celkový počet objektů typu, které byly vytvořeny během spuštění profilování a celkový počet bajtů přidělených pro objekty daného typu. Zahrnuté a výhradní hodnoty pro typ jsou vždy stejné.  
  
- Celkové hodnoty jsou pro objekty vytvořené v instancích funkci a její podřízené funkce, které byly volány nadřazené funkce ve stromu volání.  
  
- Výhradní hodnoty jsou pro objekty, které byly vytvořeny přímo pomocí funkce, když byly volány nadřazené funkce. Objekty vytvořené v podřízených funkce nejsou zahrnuty.  
  
  Data pro funkce zobrazuje počet objektů vytvořených a počet bajtů přidělených pro objekty tohoto nadřazeného typu.  
  
## <a name="highlight-the-execution-hot-path"></a>Zvýrazněte provádění kritickou cestu  
 Můžete najít cestu provádění volání stromu, který vytvořili většinu objektů z nadřazeného typu.  
  
-   Zobrazení Nejaktivnější cesty, klikněte pravým tlačítkem na typ nebo funkci a pak klikněte na **rozbalit kritickou cestu**.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název přiděleného typu nebo funkce.|  
|**ID procesu**|ID procesu (PID) běhu profilování.|  
|**Název procesu**|Název procesu.|  
|**Název modulu**|Název modulu, který obsahuje tento typ nebo funkce.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje tento typ nebo funkce.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro typ nebo funkce.|  
|**Číslo řádku funkce**|Číslo řádku začátku této definice typu nebo funkce ve zdrojovém souboru.|  
|**úroveň**|Označuje, zda data pro typ nebo funkce.|  
|**Celkově přidělení**|-Pro funkci, celkový počet objektů nadřazeného typu, které byly vytvořeny pomocí funkce. Toto číslo zahrnuje objekty vytvořené v podřízených funkce.<br />-Pro typ, celkový počet instancí tohoto typu, které byly vytvořeny.|  
|**% Celkových přidělení**|-Pro funkci, procento všechny objekty vytvořené během spuštění profilování, které byly celkových přidělení nadřazený typ funkce.<br />-Pro typ procento z celkového počtu objektů, které byly vytvořeny v profilování, která se instance daného typu.|  
|**Výhradní přidělení**|-Pro funkci, počet objektů, které se vytvořily při provádění funkce přímo v horní části zásobníku volání. Toto číslo nezahrnuje objekty vytvořené v podřízených funkce.<br />-Pro typ, celkový počet instancí tohoto typu, které byly vytvořeny.|  
|**% Výhradních přidělení**|-Pro funkci, procento všechny objekty vytvořené během spuštění profilování, které byly výhradních přidělení nadřazený typ funkce.<br />-Pro typ procento z celkového počtu objektů, které byly vytvořeny v profilování, která se instance daného typu.|  
|**Celkově bajtů**|-Pro funkci, počet bajtů paměti, které byly přiděleny pomocí funkce pro objekty tohoto nadřazeného typu. Toto číslo zahrnuje paměti, která byla přidělena pomocí její podřízené funkce.<br />-Pro typ, celkový počet bajtů, která byla přidělena v Profilování pro instance daného typu.|  
|**% Celkových bajtů**|-Pro určitou funkci procento všech paměti přidělené v profilování, která se celkově přidělení nadřazený typ funkce.<br />-Pro typ, procento všech paměti přidělené v profilování, která byla přidělena pro instance daného typu.|  
|**Výhradní bajty**|-Pro funkci, počet bajtů paměti, které byly přiděleny pomocí funkce pro objekty tohoto nadřazeného typu. Toto číslo nezahrnuje paměti, která byla přidělena pomocí její podřízené funkce.<br />-Pro typ celkový počet bajtů, které byly přiděleny v profilaci spouštět pro instance daného typu.|  
|**% Výhradních bajtů**|-Pro určitou funkci procento všech paměti přidělené v profilování, která byla výhradních přidělení nadřazený typ funkce.<br />-Pro typ, procento všech paměti přidělené v profilování, která byla přidělena pro instance daného typu.|