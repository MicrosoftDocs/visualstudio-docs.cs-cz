---
title: Souhrnné zobrazení – data instrumentace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5dc0b4195d33a7bf72d17681b6d71e78f1bacfe5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157780"
---
# <a name="summary-view---instrumentation-data"></a>Souhrnné zobrazení – data instrumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V souhrnném zobrazení se zobrazí informace o nejdražších funkcích, které je náročné při spuštění profilace. Další informace, včetně popisu odkazů na oznámení a seznamů sestav, najdete v tématu [souhrnné zobrazení](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Graf časové osy  
 Graf časové osy v zobrazení Souhrn ukazuje využití procesoru profilované aplikací v době, kdy k profilaci došlo. Graf časové osy můžete použít k filtrování zobrazení do vybraného časového rozsahu. Další informace najdete v tématu [Postup: filtrování zobrazení sestav na časové ose souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Kritická cesta  
 **Cesta k Hotu** zobrazuje cestu spuštění, která spotřebuje nejvíce času. Kliknutím na funkci můžete zobrazit zobrazení podrobností funkce pro danou funkci. Chcete-li zobrazit další zobrazení pro tuto funkci, klikněte na ni pravým tlačítkem myši a potom klikněte na zobrazení v seznamu.  
  
 **Cesta Hot** obsahuje následující data pro každou funkci:  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Name**|Název funkce|  
|**% Uplynulého celkového času**|Procentuální podíl všech časů v datech profilace, které funkce strávila prováděním kódu v těle funkce a ve funkcích, které volal.|  
|**% Uplynulého výhradního času**|Procentuální podíl všech časů v datech profilace, které funkce strávila prováděním kódu v těle funkce. Čas strávený ve funkcích, které funkce volala, není zahrnutý.|  
  
## <a name="functions-with-most-individual-work"></a>Funkce s největší individuální prací  
 Seznam funkcí, které využily nejaktuálnější čas při provádění kódu v těle funkce a nikoli ve funkcích, které volal.  
  
 **Funkce s většinou individuální práce** obsahuje pro každou funkci následující data:  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Name**|Název funkce|  
|**% Výhradního času**|Procentuální podíl všech časů v datech profilace, které funkce strávila prováděním kódu v těle funkce. Čas strávený ve funkcích, které funkce volala, není zahrnutý.|  
  
## <a name="see-also"></a>Viz také  
 [Souhrnné zobrazení](../profiling/summary-view-sampling-data.md)   
 [Souhrnné zobrazení](../profiling/summary-view-dotnet-memory-data.md)
