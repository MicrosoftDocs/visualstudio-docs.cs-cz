---
title: Souhrnné zobrazení – zobrazení kolize prostředků | Dokumentace Microsoftu
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
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45052997e9dd8332518ce5fb7804963f88e97959
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791849"
---
# <a name="summary-view---resource-contention-view"></a>Souhrnné zobrazení – zobrazení kolize prostředků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Souhrnné zobrazení zobrazuje informace o událostech ve vaší aplikaci, ve kterém byl pozastaven vlákna nebo procesu při čekání na přístup k prostředku.  
  
 Další informace, včetně popisu odkazy oznámení a sestavy seznamy, naleznete v tématu [souhrnné zobrazení](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Časová osa grafu  
 Časová osa grafu v souhrnném zobrazení zobrazuje počet kolizní události profilované aplikace v čase, které profilaci došlo k chybě. Časová osa grafu můžete použít k filtrování zobrazení tak, aby ve vybraném časovém rozsahu. Další informace najdete v tématu [postupy: filtrování zobrazení sestav ze časová osa souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="most-contended-resources"></a>Nejspornější prostředky  
 **Většinu prostředků ve sporných** seznam prostředků v aplikaci, která způsobila nejvíce kolizní události. Můžete kliknout na název prostředku k zobrazení sporů. Zobrazení kolizí poskytuje podrobné časová osa sporů prostředků vláknem.  
  
 **Většinu prostředků ve sporných** zahrnuje následující data pro jednotlivé prostředky.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Jméno**|Název prostředku.|  
|**% Sporů**|Procento všech kolizní události v profilaci dat, které byly sporů za tento prostředek.|  
  
## <a name="most-contended-thread"></a>Většina Nejspornější vlákna  
 **Většina ve sporných vláken** vypíše vlákna, v aplikaci, která měla největší počet kolizní události. Můžete kliknout na název vlákna k zobrazení sporů, která poskytuje podrobné časová osa sporů prostředků tím, že vlákno.  
  
 **Většina ve sporných vláken** zahrnuje následující údaje pro každé vlákno.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**ID**|Identifikátor vlákna.|  
|**Jméno**|Název procesu, který vlastní vlákno.|  
|**% Sporů**|Procento všech kolizní události v profilaci dat, které byly sporů za tento prostředek.|



