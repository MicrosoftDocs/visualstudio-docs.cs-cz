---
title: Zobrazení modulů – data kolizí | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74780010"
---
# <a name="modules-view---contention-data"></a>Zobrazení modulů – data kolizí
Zobrazení modulů dat o kolizí zobrazuje data souběžnosti seskupená podle modulů, které byly v datech profilování vzorků. Každý modul je kořenovým adresářem hierarchického stromu. Funkce modulu, ve kterém došlo k událostem sporů, jsou uvedeny pod uzlem modulu.

 Pokud funkce prováděla vlastní kód při výskytu události kolizí, to znamená, že funkce byla v horní části zásobníku volání, zdrojové řádky a adresy instrukcí, které byly spuštěny, jsou uvedeny pod uzlem funkce. Vzhledem k tomu, že data jsou shromažďována pro zdrojový řádek nebo ukazatel instrukcí při provádění řádku nebo instrukce, jsou všechny a exkluzivní hodnoty vždy stejné pro data řádku i pro data instrukcí.

 V následující tabulce jsou popsány hodnoty sloupců v zobrazení modulů dat o kolizí.

|Sloupec|Popis|
|------------|-----------------|
|**Výhradní čas zablokování**|– Pro funkci, čas, kdy byla tato funkce zablokována při provádění kódu v těle funkce. Čas zablokování ve funkcích, které byly volány funkcí, není zahrnutý.<br />– Pro modul součet exkluzivního času zablokování funkcí v modulu.<br />– Pro řádek nebo instrukci je čas, kdy byl tento řádek nebo instrukce zablokován, spuštěn.|
|**% Výhradního času zablokování**|– Pro funkci nebo modul je procento veškerého času zablokování při spuštění profilování, které bylo výhradním časem zablokování této funkce nebo modulu.<br />– Pro řádek nebo instrukci je procento všech blokovaných časů v profilaci běhu, ve kterém se tento řádek nebo instrukce zablokovaly při provádění.|
|**Exkluzivní spory**|– Pro funkci, kolikrát byla tato funkce zablokována při provádění kódu v těle funkce. Spory ve funkcích, které byly volány funkcí, nejsou zahrnuty.<br />– Pro modul součet exkluzivních sporů funkcí v modulu.<br />– Pro řádek nebo instrukci, kolikrát se zablokovalo spuštění tohoto řádku nebo instrukce.|
|**% Výhradních sporů**|– Pro funkci nebo modul je procento všech sporů v rámci profilace spuštěných s výhradními spory této funkce nebo modulu.<br />– Pro řádek nebo instrukci procentuální podíl všech sporů v rámci profilace, které byly kolizí, které zablokovaly spuštění tohoto řádku nebo instrukce.|
|**Celková doba zablokování**|– Pro funkci bylo zablokováno spuštění této funkce nebo funkce, která byla volána touto funkcí.<br />– Pro modul se součet času zablokování, ve kterém je minimálně jedna funkce z tohoto modulu v zásobníku.<br />– Pro řádek nebo instrukci je čas, kdy byl tento řádek nebo instrukce zablokován, spuštěn.|
|**% Celkového času zablokování**|– Pro funkci nebo modul je procento veškerého času zablokování v běhu profilace, které se zablokovalo v čase této funkce nebo modulu.<br />– Pro řádek nebo instrukci je procento všech blokovaných časů v profilaci spuštěných, ve kterém se tento řádek nebo instrukce spouští.|
|**Celkové spory**|– Pro funkci je zablokováno spuštění této funkce nebo funkce, která byla volána touto funkcí.<br />– Pro modul je počet sporů, ve kterých byla alespoň jedna funkce z tohoto modulu v zásobníku.<br />– Pro řádek nebo instrukci, kolikrát se zablokovalo spuštění tohoto řádku nebo instrukce.|
|**% Celkových sporů**|– Pro funkci nebo modul je procento všech sporů v rámci profilace, kterým byly zahrnuté spory této funkce nebo modulu.<br />– Pro řádek nebo instrukci je procento všech blokovaných časů v profilaci spuštěných, ve kterém se tento řádek nebo instrukce spouští.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Název modulu**|Název modulu, který obsahuje funkci, řádek nebo ukazatel na instrukci.|
|**Cesta k modulu**|Cesta modulu obsahujícího ukazatel modulu, funkce, řádku nebo instrukce.|
|**Name**|Název modulu nebo funkce.|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|

## <a name="see-also"></a>Viz také
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení modulů](../profiling/modules-view.md)
- [Zobrazení modulů – instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení modulů – vzorkování](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)
- [Zobrazení modulů](../profiling/modules-view-sampling-data.md)
