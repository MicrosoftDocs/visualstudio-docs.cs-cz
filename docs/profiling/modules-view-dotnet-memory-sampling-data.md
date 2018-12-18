---
title: Zobrazení modulů – Data vzorkování paměti .NET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c5cbae58aeaa1164aab6c254f62e0959da02d31c
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257670"
---
# <a name="modules-view---net-memory-sampling-data"></a>Zobrazení modulů – data vzorkování paměti .NET
Zobrazení modulů dat přidělení paměti .NET, které jsou shromažďovány prostřednictvím metody vzorkování seskupení dat paměti moduly, které byly provedeny v profilaci spustit. Každý modul je kořenem hierarchickou stromovou strukturu. Funkce modulu jsou uvedené pod tímto uzlem modulu.  
  
 Čísla řádků zdrojového souboru příkazů, které přidělit paměť jsou uvedené pod tímto uzlem funkce a pokyny, které provádějí přidělení adresy jsou uvedené pod tímto uzlem řádku. (Včetně) a výhradní hodnoty je vždy stejný pro řádek data a instrukce data.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název modulu, funkce, číslo řádku nebo adresa instrukce.|  
|**ID procesu**|ID procesu (PID) z profilace spustit.|  
|**Název procesu**|Název procesu.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta k modulu.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Číslo řádku – funkce**|Číslo řádku spuštění této funkce ve zdrojovém souboru.|  
|**Přidělení (včetně).**|-Pro funkce, celkový počet objektů, které byly vytvořené pomocí funkce. Počet zahrnuje objekty, které byly vytvořeny ve funkcích, které byly volat pomocí této funkce.<br />-Pro modul se provádí počet objektů v profilaci spustit, které byly přiděleny při alespoň jednu funkci z modulu. Počet zahrnuje objekty, které byly vytvořeny ve funkcích, které byly volá funkce modulu.<br />-Pro řádek nebo instrukce, celkový počet objektů, které byly přiděleny na řádek nebo instrukcí.|  
|**% Přidělení (včetně).**|Procento všech objektů, které byly přiděleny v profilaci spuštění, které byly včetně přidělení modulu, funkce, čáry nebo instrukcí.|  
|**Výhradní přidělení**|-Pro funkci aktuální počet objektů, které byly vytvořeny při funkce provádění kódu tělo funkce (to znamená, když funkce se v horní části zásobníku volání). Číslo nezahrnuje objekty, které byly vytvořeny ve funkcích, které byly volat pomocí této funkce.<br />-Pro modul, součet výhradní přidělení funkcí v modulu.<br />-Pro řádek nebo instrukce, celkový počet objektů, které pocházejí z tohoto řádku nebo instrukcí.|  
|**Výhradní přidělení %**|Procento všech objektů, které byly přiděleny v profilaci spuštění, které byly výhradní přidělení modulu, funkce, čáry nebo instrukcí.|  
|**Bajtů (včetně).**|-Pro funkce, počet bajtů, které byly přiděleny funkcí. Počet bajtů, které byly přiděleny zahrnuje ve funkcích, které byly volat pomocí této funkce.<br />-Pro modul se provádí počet bajtů, které byly přiděleny v profilaci spustit, které byly přiděleny při alespoň jednu funkci z modulu. Počet zahrnuje objekty, které byly vytvořeny všechny funkce, které byly volá funkce modulu.<br />-Pro řádek nebo instrukce, celkový počet objektů, které byly vytvořeny řádku nebo instrukcí.|  
|**% Bajtů (včetně).**|Procento všech bajtů, které byly přiděleny v profilaci spuštění, které byly včetně bajtů modulu, funkce, čáry nebo instrukcí.|  
|**Výhradní bajtů**|-Pro funkce, celkový počet bajtů, které byly přiděleny funkcí. Číslo nezahrnuje bajtů, které byly přiděleny ve funkcích, které byly volat pomocí této funkce.<br />-Pro modul, součet výhradní bajtů, které byly přiděleny pomocí funkce v modulu.<br />-Pro řádek nebo instrukce, celkový počet objektů, které byly přiděleny touto řádku nebo instrukcí.|  
|**% Výhradní bajtů**|Procento všech bajtů, které byly přiděleny v profilaci spuštění, které byly výhradní bajtů modulu, funkce, čáry nebo instrukcí.|  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení modulů – instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení modulů](../profiling/modules-view-sampling-data.md)   
 [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)