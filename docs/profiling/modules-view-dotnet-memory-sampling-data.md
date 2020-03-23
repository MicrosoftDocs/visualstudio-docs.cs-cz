---
title: Zobrazení modulů – vzorkovací data paměti .NET | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 9d0d9b7ab681a266115673b48f2c2604c5ff869c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772724"
---
# <a name="modules-view---net-memory-sampling-data"></a>Zobrazení modulů – vzorkovací data paměti .NET
Zobrazení modulů dat přidělení paměti .NET, která jsou shromažďována pomocí metody vzorkování, seskupuje paměťová data moduly, které byly provedeny při spuštění profilování. Každý modul je kořenem hierarchického stromu. Funkce modulu jsou uvedeny pod uzlem modulu.

 Čísla řádků zdrojového souboru příkazů, které přidělují paměť, jsou uvedena pod uzlem funkce a adresy pokynů, které provádějí přidělení, jsou uvedeny pod uzlem řádku. Včetně a výhradní hodnoty jsou vždy stejné pro data linky a data instrukce.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název modulu, funkce, čísla řádku nebo adresy instrukce.|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Inkluzivní přidělení**|- Pro funkci celkový počet objektů, které byly vytvořeny funkce. Číslo zahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány touto funkcí.<br />- Pro modul počet objektů v profilování spustit, které byly přiděleny při alespoň jednu funkci z modulu byl spuštěn. Číslo zahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány funkce modulu.<br />- Pro řádek nebo instrukce, celkový počet objektů, které byly přiděleny řádek nebo instrukce.|
|**Včetně přidělení %**|Procento všech objektů, které byly přiděleny v profilování spustit, které byly včetně přidělení modulu, funkce, řádku nebo instrukce.|
|**Výhradní přidělení**|- Pro aktuální funkci počet objektů, které byly vytvořeny při spuštění funkce kódu těla funkce (to znamená, když byla funkce v horní části zásobníku volání). Číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány touto funkcí.<br />- Pro modul, součet výhradní přidělení funkcí v modulu.<br />- Pro řádek nebo instrukce, celkový počet objektů, které byly vytvořeny tímto řádku nebo instrukce.|
|**Výhradní přidělení %**|Procento všech objektů, které byly přiděleny v profilování spustit, které byly výhradní přidělení modulu, funkce, řádku nebo instrukce.|
|**Včetně bajtů**|- Pro funkci počet bajtů, které byly přiděleny funkce. Číslo zahrnuje bajty, které byly přiděleny ve funkcích, které byly volány touto funkcí.<br />- Pro modul počet bajtů, které byly přiděleny v profilování spustit, které byly přiděleny při alespoň jednu funkci z modulu byl spuštěn. Číslo zahrnuje objekty, které byly vytvořeny ve všech funkcích, které byly volány funkce modulu.<br />- Pro řádek nebo instrukce, celkový počet objektů, které byly vytvořeny řádek nebo instrukce.|
|**Včetně bajtů %**|Procento všech bajtů, které byly přiděleny v profilování spustit, které byly včetně bajtů modulu, funkce, řádku nebo instrukce.|
|**Exkluzivní bajty**|- Pro funkci celkový počet bajtů, které byly přiděleny funkce. Číslo nezahrnuje bajty, které byly přiděleny ve funkcích, které byly volány touto funkcí.<br />- Pro modul součet výhradních bajtů, které byly přiděleny funkcemi v modulu.<br />- Pro řádek nebo instrukce, celkový počet objektů, které byly přiděleny tento řádek nebo instrukce.|
|**Výhradní bajty %**|Procento všech bajtů, které byly přiděleny v profilování spustit, které byly výhradní bajty modulu, funkce, řádku nebo instrukce.|

## <a name="see-also"></a>Viz také
- [Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Pohled modulů - instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení modulů](../profiling/modules-view-sampling-data.md)
- [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)
