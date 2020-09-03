---
title: Zobrazení funkcí – data kolizí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1aaab824f40c0cd6ba0a240a6f3035d7ebcccd00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141892"
---
# <a name="functions-view---contention-data"></a>Zobrazení funkcí – data kolizí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení sestav s daty o kolize zobrazuje funkce v průběhu profilace, které byly během spuštění profilace zablokované.  
  
 V následující tabulce jsou vysvětleny hodnoty, které se zobrazí v zobrazení Functions souboru dat profilování, který byl shromážděn pomocí metody souběžnosti.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní čas zablokování**|Množství času, během kterého byla tato funkce zablokována při provádění kódu v těle funkce. Čas zablokování ve funkcích, které byly volány funkcí, není zahrnutý.|  
|**% Výhradního času zablokování**|Procento veškerého času zablokování v běhu profilace, které bylo výhradním časem zablokování této funkce.|  
|**Exkluzivní spory**|Počet, kolikrát byla tato funkce zablokována při provádění kódu v těle funkce. Spory ve funkcích, které byly volány funkcí, nejsou zahrnuty.|  
|**% Výhradních sporů**|Procento všech sporů v rámci profilace spuštění bylo exkluzivní pro spory této funkce.|  
|**Adresa funkce**|Adresa funkce|  
|**Název funkce**|Plně kvalifikovaný název funkce.|  
|**Celková doba zablokování**|Čas, kdy byla tato funkce nebo funkce, která byla volána touto funkcí, se zablokovala při provádění.|  
|**% Celkového času zablokování**|Procentuální hodnota veškerého času zablokování v běhu profilace, která byla včetně času zablokování této funkce nebo modulu.|  
|**Celkové spory**|Počet, kolikrát byla tato funkce nebo funkce, která byla volána touto funkcí, zablokovány pro spuštění.|  
|**% Celkových sporů**|Procentuální podíl všech sporů v rámci profilace, kterým byly zahrnuté spory této funkce nebo modulu.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|  
|**ID procesu**|ID procesu (PID) procesu, ve kterém byla funkce prováděna.|  
|**Název procesu**|Název procesu|  
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení funkcí](../profiling/functions-view.md)   
 [Zobrazení funkcí – instrumentace](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení funkcí – vzorkování](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Zobrazení funkcí](../profiling/functions-view-instrumentation-data.md)   
 [Zobrazení funkcí](../profiling/functions-view-sampling-data.md)
