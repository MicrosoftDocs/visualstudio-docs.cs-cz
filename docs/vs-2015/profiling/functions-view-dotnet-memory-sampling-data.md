---
title: Zobrazení funkcí – data vzorkování paměti .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e77c6c2b3bf079e8aae88c9779c3b487ff97fe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141878"
---
# <a name="functions-view---net-memory-sampling-data"></a>Zobrazení funkcí – data vzorkování paměti .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení funkcí pro data profilování alokace paměti .NET, která byla shromážděna pomocí metody vzorkování, uvádí funkce, které přidělené paměti během profilace spouští a hlásí velikost a počet přidělení.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**ID procesu**|ID procesu (PID) pro spuštění profilace.|  
|**Název procesu**|Název procesu|  
|**Název modulu**|Název modulu, který obsahuje funkci.|  
|**Cesta k modulu**|Cesta modulu, který obsahuje funkci.|  
|**Zdrojový soubor**|Zdrojový soubor obsahující definici této funkce|  
|**Název funkce**|Plně kvalifikovaný název funkce.|  
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|  
|**Adresa funkce**|Adresa funkce|  
|**Celkové alokace**|Celkový počet objektů, které byly přiděleny touto funkcí a jejími podřízenými funkcemi.|  
|**% Celkových přidělení**|Procentuální podíl všech objektů, které byly přiděleny při spuštění profilace, včetně přidělení této funkce.|  
|**Exkluzivní přidělení**|Počet objektů, které byly vytvořeny v okamžiku, kdy byla funkce přímo spuštěna v horní části zásobníku volání. Toto číslo nezahrnuje objekty, které byly vytvořeny v podřízených funkcích.|  
|**% Exkluzivní alokace**|Procento všech objektů, které byly přiděleny při spuštění profilace, které byly exkluzivním přidělením této funkce.|  
|**Včetně bajtů**|Počet bajtů paměti, které byly přiděleny touto funkcí a jejími podřízenými funkcemi.|  
|**% Celkových bajtů**|Procento všech bajtů paměti, které byly přiděleny při spuštění profilace, včetně bajtů této funkce.|  
|**Exkluzivní počet bajtů**|Počet bajtů paměti, které byly přiděleny touto funkcí, ale nikoli jejími podřízenými funkcemi.|  
|**% Exkluzivních bajtů**|Procento všech bajtů paměti, které byly přiděleny při spuštění profilace, které byly výhradně bajty této funkce.|  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení funkcí – instrumentace](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Zobrazení funkcí](../profiling/functions-view-sampling-data.md)   
 [Zobrazení funkcí](../profiling/functions-view-instrumentation-data.md)
