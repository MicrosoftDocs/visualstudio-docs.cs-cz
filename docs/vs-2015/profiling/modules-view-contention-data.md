---
title: Zobrazení modulů – Data kolizí | Dokumentace Microsoftu
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
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c98689007a9497a4186dc19086ec46588b0a842
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759399"
---
# <a name="modules-view---contention-data"></a>Zobrazení modulů – data kolizí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Moduly zobrazení dat kolizí zobrazí dat o souběžnosti seskupené podle modulů, které byly vzorkovány v dat profilování. Každý modul je kořen hierarchického stromu. Funkce modulu došlo k kolizní události jsou uvedeny pod uzlem modulu.  
  
 Pokud funkce byla spuštěna vlastní kód, kdy došlo k události kolize, tedy funkce byla v horní části zásobníku volání, zdrojové řádky a instrukce, adresy, které byly provádění jsou uvedeny v uzlu funkce. Protože data se shromažďují pro zdrojový řádek nebo ukazatele na instrukci při řádku nebo instrukce provádí, zahrnuté a výhradní hodnoty jsou vždy stejné pro řádek dat a dat instrukce.  
  
 Následující tabulka popisuje hodnot ve sloupcích v moduly zobrazení dat kolizí.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní čas zablokování**|-Pro funkci, čas, který tuto funkci bylo zablokováno provádění kódu v těle funkce. Čas zablokování ve funkcích, které byly volány funkce není součástí.<br />-Pro modul, součet výhradní čas zablokování funkce v modulu.<br />-Pro řádek nebo instrukce, čas, že tento řádek nebo instrukce bylo zablokováno provádění.|  
|**% Výhradního času zablokování**|-Pro funkce nebo modulu procento všech času zablokování při spuštění, který profilace byla výhradní čas zablokování této funkce nebo modulu.<br />-Pro řádek nebo instrukce, procento všech času blokování při spuštění profilování, ve kterém tento řádek nebo instrukce zablokoval spuštění.|  
|**Výhradní spory**|-Pro funkci, počet případů, kdy se tato funkce bylo zablokováno provádění kódu v těle funkce. Tento počet sporů: ve funkcích, které byly volány funkce nejsou zahrnuty.<br />-Pro modul, součet výhradních sporů funkce v modulu.<br />-Pro řádek nebo instrukce, počet, kolikrát, že se tento řádek nebo instrukce zablokoval spuštění.|  
|**% Výhradních sporů**|-Pro funkci nebo modul byly procento všech sporů při spuštění, který profilace výhradních sporů této funkce nebo modulu.<br />-Pro řádek nebo instrukce byly procento všech sporů při spuštění, který profilace sporů, zablokované tento řádek nebo instrukce spuštění.|  
|**Celkový čas zablokování**|-Pro funkci, čas, který tuto funkci nebo funkce, která byla volána pomocí této funkce bylo zablokováno provádění.<br />-Pro modul součet čas zablokování které alespoň jednu funkci z tohoto modulu byla v zásobníku.<br />-Pro řádek nebo instrukce, čas, že tento řádek nebo instrukce bylo zablokováno provádění.|  
|**% Celkového času zablokování**|-Pro funkce nebo modulu procento všech času zablokování při spuštění, který profilace byla celkový čas zablokování této funkce nebo modulu.<br />-Pro řádek nebo instrukce procento všech času zablokování v Profilování spustit ve které tento řádek nebo instrukce byla spuštěna.|  
|**Celkově sporů**|-Pro funkci, počet případů, kdy se tato funkce nebo funkce, která byla volána pomocí této funkce bylo zablokováno provádění.<br />-Pro modul počet sporů, ve které alespoň jednu funkci z tohoto modulu byla v zásobníku.<br />-Pro řádek nebo instrukce, počet, kolikrát, že se tento řádek nebo instrukce zablokoval spuštění.|  
|**% Celkových sporů**|-Pro funkci nebo modul byly procento všech sporů při spuštění, který profilace celkových sporů této funkce nebo modulu.<br />-Pro řádek nebo instrukce procento všech času zablokování v Profilování spustit ve které tento řádek nebo instrukce byla spuštěna.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Název modulu**|Název modulu, který obsahuje ukazatel na funkci, řádek nebo instrukci.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje ukazatel modulu, funkce, řádek nebo instrukci.|  
|**Jméno**|Název modulu nebo funkce.|  
|**ID procesu**|ID procesu (PID) běhu profilování.|  
|**Název procesu**|Název procesu.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení modulů](../profiling/modules-view.md)   
 [Zobrazení modulů – instrumentace](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Moduly zobrazení – vzorkování](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Zobrazení modulů](../profiling/modules-view-instrumentation-data.md)   
 [Zobrazení modulů](../profiling/modules-view-sampling-data.md)



