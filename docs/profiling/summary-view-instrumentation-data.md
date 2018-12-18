---
title: Souhrnné zobrazení – Data instrumentace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 606ba5ebe7c485adb33fbcfa6884ad5e625d821e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675966"
---
# <a name="summary-view---instrumentation-data"></a>Souhrnné zobrazení – data instrumentace
Souhrnné zobrazení zobrazuje informace o výkonu – nejdražší funkce v profilování. Další informace, včetně popisu odkazy oznámení a sestavy seznamy, naleznete v tématu [zobrazení se souhrnnými](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Časová osa grafu  
 Časová osa grafu v souhrnném zobrazení ukazuje využití procesoru (CPU) profilovaná aplikace v čase, které profilaci došlo k chybě. Časová osa grafu můžete použít k filtrování zobrazení tak, aby ve vybraném časovém rozsahu. Další informace najdete v tématu [postupy: filtrování zobrazení sestav ze časová osa souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Kritická cesta  
 **Kritickou cestu** cesta spuštění, které nejvíce času. Můžete kliknout na funkci, kterou chcete zobrazit podrobnosti o funkci pro funkci. Další zobrazení, pro funkce, klikněte pravým tlačítkem na funkci a potom klikněte na zobrazit ze seznamu.  
  
 **Kritickou cestu** zahrnuje následující data pro každou funkci:  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název funkce.|  
|**% Uplynulého celkového času**|Procento celou dobu profilování dat, které funkce strávený prováděním kódu v těle jeho funkce a funkce, které ji volaly.|  
|**% Uplynulého výhradního času**|Procento všech času v profilaci dat, který funkce stráví prováděním kódu v těle jeho funkce. Času stráveného ve funkcích, které volá se, funkce není součástí.|  
  
## <a name="functions-with-most-individual-work"></a>Funkce s většinou jednotlivé práce  
 Seznam funkcí, které spotřebovávají nejvíce času prováděním kódu v těle funkce a ne v funkce, které ji volaly.  
  
 **Funkce s nejvíce individuální práce** zahrnuje následující data pro každou funkci:  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název funkce.|  
|**% Výhradního času**|Procento všech času v profilaci dat, který funkce stráví prováděním kódu v těle jeho funkce. Času stráveného ve funkcích, které volá se, funkce není součástí.|  
  
## <a name="see-also"></a>Viz také:  
 [Souhrnné zobrazení – vzorkování dat](../profiling/summary-view-sampling-data.md)   
 [Souhrnné zobrazení – data paměti .NET](../profiling/summary-view-dotnet-memory-data.md)