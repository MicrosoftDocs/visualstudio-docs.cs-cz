---
title: Souhrnné zobrazení – Data paměti .NET | Dokumentace Microsoftu
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
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e0bfa7a6643aa27cba5e2b546ba9f2fc50fbd89
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816408"
---
# <a name="summary-view---net-memory-data"></a>Souhrnné zobrazení – Data paměti .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Souhrnné zobrazení zobrazuje informace o funkcích rozhraní .NET a typy, které nejvíce paměti přidělené a typy, které byly vytvořeny většinu doby v profilování. Další informace, včetně popisu odkazy oznámení a sestavy seznamy, naleznete v tématu [souhrnné zobrazení](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Časová osa grafu  
 Časová osa grafu v souhrnném zobrazení ukazuje využití procesoru (CPU) profilovaná aplikace v čase, které profilaci došlo k chybě. Časová osa grafu můžete použít k filtrování zobrazení tak, aby ve vybraném časovém rozsahu. Další informace najdete v tématu [postupy: filtrování zobrazení sestav ze časová osa souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="functions-allocating-most-memory"></a>Funkce přidělující nejvíce paměti  
 Seznam funkcí, které přiděleny nejvyšší počet bajtů paměti během spuštění profilování.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název funkce.|  
|**% Bajtů**|Procento všech přidělených bajtů při spuštění profilace, které byly přiděleny pomocí této funkce nebo podřízené funkce, která byla volaných touto funkcí.|  
  
## <a name="types-with-most-memory-allocated"></a>Typy s největším množstvím přidělené paměti  
 Obsahuje seznam typů, pro které byly přiděleny nejvyšší počet bajtů paměti při spuštění profilace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název typu.|  
|**% Bajtů**|Procento všech přidělených bajtů při spuštění profilace, které byly přiděleny u tohoto typu.|  
  
## <a name="types-with-most-instances"></a>Typy s největším množstvím instancí  
 Seznam typů, které byly vytvořeny nejvíce času během spuštění profilování. kdyby  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název typu.|  
|**% Instancí**|Procentuální podíl celkového počtu of.NET objektů, které byly vytvořeny v profilování, která byla instance tohoto typu.|  
  
## <a name="see-also"></a>Viz také  
 [Souhrnné zobrazení](../profiling/summary-view-sampling-data.md)   
 [Souhrnné zobrazení](../profiling/summary-view-instrumentation-data.md)



