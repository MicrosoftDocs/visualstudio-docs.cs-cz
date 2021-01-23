---
title: Zobrazení modulů – data vzorkování paměti .NET | Microsoft Docs
description: Přečtěte si o zobrazeních dat o přidělování paměti .NET, která se shromažďují pomocí metody vzorkování.
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
ms.openlocfilehash: 7e05a3e1d915853689c436b192de9e266e86b13d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723293"
---
# <a name="modules-view---net-memory-sampling-data"></a>Zobrazení modulů – data vzorkování paměti .NET
Moduly zobrazení dat alokace paměti .NET shromažďovaných pomocí metody vzorkování seskupují data paměti moduly, které byly spuštěny při spuštění profilace. Každý modul je kořenovým adresářem hierarchického stromu. Funkce modulu jsou uvedeny pod uzlem modulu.

 Čísla řádků zdrojového souboru příkazů, které přidělují paměť, jsou uvedena pod uzlem funkce a adresy instrukcí, které jsou přiděleny, jsou uvedeny pod uzlem line. Zahrnuté a exkluzivní hodnoty jsou vždy stejné pro data řádků a instrukce.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název modulu, funkce, čísla řádku nebo adresy instrukcí.|
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta k modulu**|Cesta k modulu|
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Celkové alokace**|– Pro funkci celkový počet objektů, které byly vytvořeny funkcí. Číslo zahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány touto funkcí.<br />– Pro modul počet objektů v běhu profilace, které byly přiděleny, zatímco alespoň jedna funkce z modulu byla spuštěna. Toto číslo zahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány funkcemi modulu.<br />– Pro řádek nebo instrukci celkový počet objektů, které byly přiděleny řádkem nebo instrukcí.|
|**% Celkových přidělení**|Procentuální podíl všech objektů, které byly přiděleny při spuštění profilace, včetně přidělení modulu, funkce, řádku nebo instrukce.|
|**Exkluzivní přidělení**|– Pro aktuální funkci počet objektů, které byly vytvořeny v době, kdy funkce prováděla kód těla funkce (to znamená, když funkce byla v horní části zásobníku volání). Počet nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volány touto funkcí.<br />– Pro modul součet exkluzivního přidělení funkcí v modulu.<br />– Pro řádek nebo instrukci celkový počet objektů, které byly vytvořeny tímto řádkem nebo instrukcí.|
|**% Exkluzivní alokace**|Procento všech objektů, které byly přiděleny při spuštění profilace, které byly exkluzivním přidělením modulu, funkce, řádku nebo instrukce.|
|**Včetně bajtů**|– Pro funkci počet bajtů, které byly přiděleny funkcí. Číslo zahrnuje bajty, které byly přiděleny ve funkcích, které byly volány touto funkcí.<br />– Pro modul počet bajtů, které byly přiděleny v průběhu profilace, které byly přiděleny v době, kdy byla spuštěna alespoň jedna funkce z modulu. Toto číslo zahrnuje objekty, které byly vytvořeny ve všech funkcích, které byly volány funkcemi modulu.<br />– Pro řádek nebo instrukci celkový počet objektů, které byly vytvořeny pomocí řádku nebo instrukce.|
|**% Celkových bajtů**|Procento všech bajtů, které byly přiděleny při spuštění profilace, včetně bajtů modulu, funkce, řádku nebo instrukce.|
|**Exkluzivní počet bajtů**|– Pro funkci celkový počet bajtů, které byly přiděleny funkcí. Počet neobsahuje bajty, které byly přiděleny ve funkcích, které byly volány touto funkcí.<br />– Pro modul součet exkluzivních bajtů, které byly přiděleny funkcemi v modulu.<br />– Pro řádek nebo instrukci celkový počet objektů, které byly přiděleny tímto řádkem nebo instrukcí.|
|**% Exkluzivních bajtů**|Procento všech bajtů, které byly přiděleny při spuštění profilace, které byly výhradně bajty modulu, funkce, řádku nebo instrukce.|

## <a name="see-also"></a>Viz také
- [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)
- [Zobrazení modulů – instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení modulů](../profiling/modules-view-sampling-data.md)
- [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)
