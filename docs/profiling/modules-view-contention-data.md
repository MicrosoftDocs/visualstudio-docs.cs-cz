---
title: Zobrazení modulů – data konfliktů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2de844867e9c0a8d95abdaa13f860a6487254bfe
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780010"
---
# <a name="modules-view---contention-data"></a>Zobrazení modulů - data tvrzení
Zobrazení modulů dat kolizí zobrazuje data souběžnosti seskupená podle modulů, které byly vzorkovány v datech profilování. Každý modul je kořenem hierarchického stromu. Funkce modulu, ve kterém došlo k konfliktní události jsou uvedeny v uzlu modulu.

 Pokud funkce prováděla svůj vlastní kód, když došlo k události konfliktu, to znamená, že funkce byla v horní části zásobníku volání, zdrojové řádky a instrukční adresy, které byly spuštěny, jsou uvedeny pod uzlem funkce. Vzhledem k tomu, že data jsou shromažďována pro zdrojový řádek nebo ukazatel instrukce při provádění řádku nebo instrukce, včetně a výhradní hodnoty jsou vždy stejné pro data řádku a data instrukce.

 Následující tabulka popisuje hodnoty sloupců v zobrazení modulů dat kolizí.

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní blokovaný čas**|- Pro funkci čas, kdy tato funkce byla zablokována z provádění kódu v těle funkce. Blokovaný čas ve funkcích, které byly volány funkcí, není zahrnut.<br />- Pro modul, součet výhradního zablokovaného času funkcí v modulu.<br />- Pro řádek nebo instrukce, čas, který tento řádek nebo instrukce byla zablokována z provádění.|
|**Výhradní blokovaný čas %**|- Pro funkci nebo modul, procento všech blokovaných času v profilování spustit, který byl výhradní blokovaný čas této funkce nebo modulu.<br />- Pro řádek nebo instrukce procento všech blokovaných čas v profilování spustit, ve kterém tento řádek nebo instrukce byla zablokována provádění.|
|**Exkluzivní tvrzení**|- Pro funkci, kolikrát tato funkce byla zablokována z provádění kódu v těle funkce. Konflikty ve funkcích, které byly volány funkcí, nejsou zahrnuty.<br />- Pro modul, součet výhradních tvrzení funkcí v modulu.<br />- Pro řádek nebo instrukce, kolikrát tento řádek nebo instrukce byla zablokována z provádění.|
|**Výhradní tvrzení %**|- Pro funkci nebo modul, procento všech tvrzení v profilování spustit, které byly výhradní tvrzení této funkce nebo modulu.<br />- Pro řádek nebo instrukce procento všech tvrzení v profilování spustit, které byly tvrzení, která zablokovala tento řádek nebo instrukce z provádění.|
|**Včetně blokovaného času**|- Pro funkci čas, který tato funkce nebo funkce, která byla volána touto funkcí byla zablokována provádění.<br />- Pro modul, součet blokovaného času, ve kterém alespoň jedna funkce z tohoto modulu byl na zásobníku.<br />- Pro řádek nebo instrukce, čas, který tento řádek nebo instrukce byla zablokována z provádění.|
|**Včetně blokovaného času %**|- Pro funkci nebo modul, procento všech blokovaných času v profilování spustit, který byl včetně blokovaný čas této funkce nebo modulu.<br />- Pro řádek nebo instrukce procento všech blokovaných čas v profilování spustit, ve kterém byl tento řádek nebo instrukce provádění.|
|**Inkluzivní tvrzení**|- Pro funkci, kolikrát tato funkce nebo funkce, která byla volána touto funkcí byla zablokována provádění.<br />- Pro modul počet tvrzení, ve kterém alespoň jedna funkce z tohoto modulu byl na zásobníku.<br />- Pro řádek nebo instrukce, kolikrát tento řádek nebo instrukce byla zablokována z provádění.|
|**Inkluzivní tvrzení %**|- Pro funkci nebo modul, procento všech tvrzení v profilování spustit, které byly včetně tvrzení této funkce nebo modulu.<br />- Pro řádek nebo instrukce procento všech blokovaných čas v profilování spustit, ve kterém byl tento řádek nebo instrukce provádění.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje ukazatel funkce, řádku nebo instrukce.|
|**Cesta modulu**|Cesta modulu, který obsahuje modul, funkce, řádek nebo ukazatel instrukce.|
|**Název**|Název modulu nebo funkce.|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení modulů](../profiling/modules-view.md)
- [Pohled modulů - instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení modulů - odběr vzorků](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)
- [Zobrazení modulů](../profiling/modules-view-sampling-data.md)
