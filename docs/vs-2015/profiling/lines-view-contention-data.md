---
title: Zobrazení řádků – Data kolizí | Dokumentace Microsoftu
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
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d85173dcf2ab5632fdb18233f9f27f329ddd3769
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773194"
---
# <a name="lines-view---contention-data"></a>Zobrazení řádků – data kolizí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení řádků dat kolizí obsahuje údaje o výkonu pro příkazy, které se spouští při ukázky byly shromážděny během spuštění profilování. Ve zdrojovém souboru příkaz se týkají více než jeden řádek ve zdrojovém souboru a jeden řádek může obsahovat více než jeden výraz.  
  
 Příkaz je identifikován následující data:  
  
- Zdrojový soubor, který obsahuje Function – příkaz  
  
- Funkce, která obsahuje příkaz.  
  
- Zdrojový řádek, ve kterém se spustí příkaz.  
  
- Znak ve zdrojovém řádku, ve kterém se spustí příkaz.  
  
- Řádku zdroje, u které končí příkaz.  
  
- Znak ve zdrojovém řádku, kdy příkaz skončí.  
  
  Sloupec název řádek obsahuje seřaditelné zřetězení těchto dat identifikátor.  
  
  Následující tabulka popisuje sloupce řádky zobrazit sestavu.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Výhradní čas zablokování**|Množství času, během které byl tento příkaz blokovat spouštění kódu v příkazu z důvodu kolize události. Čas zablokování ve funkcích, které volá příkaz není součástí.|  
|**% Výhradního času zablokování**|Procento času zablokování všech proces, který byl výhradní čas zablokování příkazu.|  
|**Výhradní spory**|Počet případů, kdy se tento příkaz bylo zablokováno spouštění kódu v příkazu z důvodu kolize události. Kolizní události ve funkcích, které volá příkaz nejsou zahrnuty.|  
|**% Výhradních sporů**|Procento kolizní události v procesu, které byly výhradních sporů tohoto prohlášení.|  
|**Adresa funkce**|Adresa funkce, která obsahuje tento příkaz.|  
|**Název funkce**|Plně kvalifikovaný název funkce, která obsahuje tento příkaz.|  
|**Celkový čas zablokování**|Čas zablokování v této smlouvě a funkce se volá v příkazu.|  
|**% Celkového času zablokování**|Procento času zablokování všech proces, který byl celkový čas zablokování příkazu.|  
|**Celkově sporů**|Počet pokusů, že tento příkaz a funkce, které byly volány v příkazu se zablokoval spuštění.|  
|**% Celkových sporů**|Procento kolizní události v procesu, které byly celkových sporů tohoto prohlášení.|  
|**Název čáry**|Profiler generovaný identifikátor řádku. Identifikátor se používá následující syntaxe:`SourceFile`**; [** `LineNumberStart` **,**`CharacterStart`**] ->; [**`LineNumberEnd`**,**`CharacterEnd`**]**|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Název modulu**|Název modulu, který obsahuje příkaz.|  
|**Cesta modulu**|Cesta k napadenému modulu, který obsahuje příkaz.|  
|**ID procesu**|ID procesu (PID) PROFILOVANÉHO procesu.|  
|**Název procesu**|Název procesu.|  
|**Počáteční znak zdrojového kódu**|Odsazení počátečního znaku ve zdrojovém souboru řádku, na který tento příkaz spustí.|  
|**Koncový znak zdrojového kódu**|Odsazení počátečního znaku ve zdrojovém souboru řádku, u které končí tento příkaz.|  
|**Zdrojový soubor**|Název zdrojového souboru, který obsahuje příkaz funkce.|  
|**Začátek řádku zdroje**|Číslo řádku ve zdrojovém souboru, ve kterém se spustí příkaz.|  
|**Konec řádku zdroje**|Číslo řádku ve zdrojovém souboru, u které končí příkaz.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení řádků](../profiling/lines-view.md)   
 [Zobrazení řádků – vzorkování](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Zobrazení řádků](../profiling/lines-view-sampling-data.md)



