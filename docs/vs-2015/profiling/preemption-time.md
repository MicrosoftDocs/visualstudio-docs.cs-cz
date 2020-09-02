---
title: Čas přerušení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fd209f65464126650106eb4509cd3de39ad8c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198068"
---
# <a name="preemption-time"></a>Čas přerušení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tyto segmenty na časové ose jsou přidruženy k době blokování, která je zařazena do kategorie přerušení. Tato kategorie předpokládá, že je vlákno přepnuto z jednoho z těchto důvodů:  
  
- Plánovač ho nahradil pomocí vlákna s vyšší prioritou.  
  
- Doba běhu vlákna vypršela a ostatní vlákna byly připraveny ke spuštění.  
  
  Během této doby bylo vlákno zablokované v důsledku čekání jádra, že Vizualizátor souběžnosti se počítá jako přerušení. Segmenty přerušení jsou spouštěny, když je vlákno vloženo z logického jádra a končí, když vlákno pokračuje v provádění.  
  
  Popis pro zrušený segment zobrazuje název procesu nebo vlákna, které způsobily přerušení. To však neznamená, že proces nebo podproces, které trvaly v průběhu období přerušení.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)
