---
title: Zobrazení přidělení paměti .NET | Dokumenty společnosti Microsoft
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ce16f65947fd69b5a54e564ba6bec061bc68e328
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777374"
---
# <a name="net-memory-allocations-view"></a>Přidělení paměti .NET – zobrazení
Zobrazení Přidělení uvádí typy, které byly vytvořeny během spuštění profilování. Každý typ je kořenový uzel stromu volání, který zobrazuje cesty spuštění funkce, které vedly k přidělení typu.

 Data v řádku typu zobrazuje celkový počet objektů typu, které byly vytvořeny v profilování spustit a celkový počet bajtů přidělených pro objekty tohoto typu. Včetně a výhradní hodnoty pro typ jsou vždy stejné.

- Včetně hodnoty jsou pro objekty vytvořené v instancích funkce a její podřízené funkce, které byly volány nadřazenou funkcí ve stromu volání.

- Výhradní hodnoty jsou pro objekty, které byly vytvořeny přímo funkcí, když byly volány nadřazenou funkcí. Objekty vytvořené v podřízených funkcích nejsou zahrnuty.

  Data pro funkci zobrazuje počet vytvořených objektů a počet bajtů přidělených pro objekty nadřazeného typu.

## <a name="highlight-the-execution-hot-path"></a>Zvýrazněte cestu spuštění hot
 Můžete najít cestu spuštění stromu volání, který vytvořil nejvíce objektů nadřazeného typu.

- Chcete-li zobrazit nejaktivnější cestu, klepněte pravým tlačítkem myši na typ nebo funkci a potom klepněte na příkaz **Rozbalit aktivní cestu**.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název přiděleného typu nebo funkce.|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje typ nebo funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje typ nebo funkci.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici typu nebo funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této definice typu nebo funkce ve zdrojovém souboru.|
|**Úroveň**|Označuje, zda jsou data pro typ nebo funkci.|
|**Inkluzivní přidělení**|- Pro funkci celkový počet objektů nadřazeného typu, které byly vytvořeny funkcí. Toto číslo zahrnuje objekty vytvořené v podřízených funkcích.<br />- Pro typ, celkový počet instancí tohoto typu, které byly vytvořeny.|
|**Včetně přidělení %**|- Pro funkci procento všech objektů vytvořených v profilování spustit, které byly včetně přidělení nadřazeného typu funkce.<br />- Pro typ procento z celkového počtu objektů, které byly vytvořeny v profilování spustit, které byly instance typu.|
|**Výhradní přidělení**|- Pro funkci počet objektů, které byly vytvořeny při spuštění funkce přímo v horní části zásobníku volání. Toto číslo nezahrnuje objekty vytvořené v podřízených funkcích.<br />- Pro typ, celkový počet instancí tohoto typu, které byly vytvořeny.|
|**Výhradní přidělení %**|- Pro funkci procento všech objektů vytvořených v profilování spustit, které byly výhradní přidělení nadřazeného typu funkce.<br />- Pro typ procento z celkového počtu objektů, které byly vytvořeny v profilování spustit, které byly instance typu.|
|**Včetně bajtů**|- Pro funkci počet bajtů paměti, které byly přiděleny funkce pro objekty nadřazeného typu. Toto číslo zahrnuje paměť, která byla přidělena jeho podřízené funkce.<br />- Pro typ celkový počet bajtů, které byly přiděleny v profilování spustit pro instance typu.|
|**Včetně bajtů %**|- Pro funkci procento všech paměti přidělené v profilování spustit, který byl včetně přidělení nadřazeného typu funkce.<br />- Pro typ procento všech paměti přidělené v profilování spustit, který byl přidělen pro instance typu.|
|**Exkluzivní bajty**|- Pro funkci počet bajtů paměti, které byly přiděleny funkce pro objekty nadřazeného typu. Toto číslo nezahrnuje paměť, která byla přidělena jeho podřízené funkce.<br />- Pro typ celkový počet bajtů, které byly přiděleny v profilování spustit pro instance typu.|
|**Výhradní bajty %**|- Pro funkci procento všech paměti přidělené v profilování spustit, který byl výhradní přidělení nadřazeného typu funkce.<br />- Pro typ procento všech paměti přidělené v profilování spustit, který byl přidělen pro instance typu.|
