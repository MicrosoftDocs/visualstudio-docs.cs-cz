---
title: Souhrnné zobrazení – data paměti .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61fe6d3982828d1e2a8ae4aeaba3d89b1b75f4f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193321"
---
# <a name="summary-view---net-memory-data"></a>Souhrnné zobrazení – data paměti .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V souhrnném zobrazení se zobrazí informace o funkcích a typech .NET, které přidělují nejvíc paměti, a typy, které byly vytvořeny ve většině případů při spuštění profilace. Další informace, včetně popisu odkazů na oznámení a seznamů sestav, najdete v tématu [souhrnné zobrazení](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Graf časové osy  
 Graf časové osy v zobrazení Souhrn ukazuje využití procesoru profilované aplikací v době, kdy k profilaci došlo. Graf časové osy můžete použít k filtrování zobrazení do vybraného časového rozsahu. Další informace najdete v tématu [Postup: filtrování zobrazení sestav na časové ose souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="functions-allocating-most-memory"></a>Funkce, které přiděluje většinu paměti  
 Zobrazuje seznam funkcí, které přidělily největší počet bajtů paměti při spuštění profilace.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Name**|Název funkce|  
|**Psaný**|Procento všech přidělených bajtů v běhu profilace, které byly přiděleny touto funkcí nebo podřízenou funkcí volanou touto funkcí.|  
  
## <a name="types-with-most-memory-allocated"></a>Typy s největším množstvím přidělené paměti  
 Zobrazí seznam typů, pro které byl při spuštění profilování přidělen největší počet bajtů paměti.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Name**|Název typu|  
|**Psaný**|Procento všech přidělených bajtů v běhu profilace, které byly přiděleny pro tento typ.|  
  
## <a name="types-with-most-instances"></a>Typy s největší instancí  
 Zobrazí seznam typů, které byly vytvořeny ve většině případů během spuštění profilace. hlíží  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Name**|Název typu|  
|**Instance**|Procentuální podíl celkového počtu objektů of.NET vytvořených při spuštění profilace, které byly instancemi tohoto typu.|  
  
## <a name="see-also"></a>Viz také  
 [Souhrnné zobrazení](../profiling/summary-view-sampling-data.md)   
 [Souhrnné zobrazení](../profiling/summary-view-instrumentation-data.md)
