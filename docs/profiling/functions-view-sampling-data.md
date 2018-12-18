---
title: Zobrazení funkcí – vzorkování dat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9084aad27d14825f4b3d0a648f0880d4db329c78
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237491"
---
# <a name="functions-view---sampling-data"></a>Zobrazení funkcí – data vzorkování
Zobrazení sestavy funkce pro metody vzorkování profil obsahuje seznam funkcí, které byly vzorkovat při vytváření profilu spustit.  
  
> [!NOTE]
>  Funkce Rozšířené zabezpečení v systému Windows 8 a Windows Server 2012 vyžaduje významné změny ve způsobu, jakým Visual Studio profiler shromažďuje data na těchto platformách. Aplikace UWP také vyžadují nové techniky kolekce. V tématu [nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**ID procesu**|ID procesu (PID) z profilace spustit.|  
|**Název procesu**|Název procesu.|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta modulu**|Cesta modul, který obsahuje funkce.|  
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici pro tuto funkci.|  
|**Název funkce**|Plně kvalifikovaný název funkce.|  
|**Číslo řádku – funkce**|Číslo řádku spuštění této funkce ve zdrojovém souboru.|  
|**Adresa funkce**|Adresa funkce.|  
|**Ukázky (včetně).**|Celkový počet vzorků, které byly shromážděny při provádění této funkce; To znamená, počet vzorků, které byly shromážděny při tato funkce v zásobníku volání. Obsahuje počet vzorků, které byly shromážděny při byly provádění funkcí, které byly volat pomocí této funkce.|  
|**% Ukázky (včetně).**|Procento všechny ukázky v profilaci spuštění, které byly včetně ukázky této funkce.|  
|**Výhradní ukázky**|Celkový počet vzorků, které byly shromážděny při provádění kódu v těle této funkce; To znamená, když tato funkce byla v horní části zásobníku volání. Ukázky, které byly shromážděny v funkce, které byly volat pomocí této funkce nejsou zahrnuty.|  
|**% Výhradní ukázky**|Procento všechny ukázky v profilaci spuštění, které byly výhradní ukázky této funkce.|  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md)   
 [Zobrazení funkcí – instrumentace](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení funkcí – vzorkování](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Zobrazení funkcí](../profiling/functions-view-instrumentation-data.md)