---
title: Zobrazení modulů – vzorkování dat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a885ca96ce58be7448f5b9b814457b38e08a1233
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742491"
---
# <a name="modules-view---sampling-data"></a>Zobrazení modulů – vzorkování dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení modulů vzorkování údaje o výkonu zobrazí data, která je seskupené podle modulů, které byly vzorkovány v dat profilování. Každý modul je kořen hierarchického stromu. Vzorky funkcí modulu jsou uvedeny pod uzlem modulu.  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Pokud funkce byla spuštěna při nebyly shromážděny vzorky (tj. funkce byla v horní části zásobníku volání aplikace), zdrojové řádky a instrukce adresy, které byly provádění jsou uvedeny pod uzlem funkce. Protože data se shromažďují pro zdrojový řádek nebo ukazatele na instrukci při řádku nebo instrukce provádí, zahrnuté a výhradní hodnoty jsou vždy stejné pro řádek dat a dat instrukce.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název modulu, funkce, číslo řádku nebo adresa ukazatele instrukce.|  
|**ID procesu**|ID procesu (PID) běhu profilování.|  
|**Název procesu**|Název procesu.|  
|**Název modulu**|Název modulu, který obsahuje ukazatel na funkci, řádek nebo instrukci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje ukazatel modulu, funkce, řádek nebo instrukci.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Celkových vzorků**|-Pro určitou funkci Počet vzorků, ve kterých tuto funkci nebo funkce, která volala se tato funkce byla spuštěna; To znamená, že počet volání zásobníku ukázky, které tuto funkci.<br />-Pro modul počet vzorků, ve které alespoň jednu funkci z modulu provádění.<br />-Pro řádek nebo instrukce, počet vzorků, ve kterém tento řádek nebo instrukce byla spuštěna.|  
|**% Celkových vzorků**|-Pro funkce nebo modulu procento všechny ukázky v profilování, které byly celkových vzorků této funkce nebo modulu.<br />-Pro řádek nebo instrukce procento všechny ukázky v Profilování spustit ve které tento řádek nebo instrukce byla spuštěna.|  
|**Výhradní vzorky**|-Pro určitou funkci Počet volání zásobníku ukázky, ve kterých byla tato funkce přímo provádění; To znamená, počet vzorků, ve kterých byla tato funkce v horní části zásobníku volání.<br />-Pro modul, součet výhradních vzorků funkce v modulu.<br />-Pro řádek nebo instrukce, počet vzorků, ve kterém tento řádek nebo instrukce byla spuštěna.|  
|**% Výhradních vzorků**|-Pro funkce nebo modulu procento všechny ukázky v profilování, které byly výhradních vzorků této funkce nebo modulu.<br />-Pro řádek nebo instrukce procento všechny ukázky v Profilování spustit ve které tento řádek nebo instrukce byla spuštěna.|  
  
## <a name="see-also"></a>Viz také  
 [Moduly zobrazení – vzorkování](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Zobrazení modulů – instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)



