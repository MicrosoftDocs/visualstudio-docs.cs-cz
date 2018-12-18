---
title: Čas přerušení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d0959f5e2725401424d0231ccd286b7835a7315
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894388"
---
# <a name="preemption-time"></a>Čas přerušení
Tyto segmenty na časové ose jsou přidruženy k blokování, který je zařazený do kategorie jako ztracený čas. Tato kategorie znamená, že je vlákno přepnutí z jednoho z těchto důvodů:  
  
- Plánovač se nahrazuje použití vyšší priorita vlákna.  
  
- Kvantové doby provádění vlákna vypršela platnost a byly jiná vlákna připravená ke spuštění.  
  
  Během této doby je blokovaná společností Důvod čekání jádra, která Vizualizátor souběžnosti se počítá jako ztracený vlákno. Ztracený segmenty spustit, když vlákno je vložena mimo logické jádro a ukončit, pokud bylo vlákno pokračuje v provádění.  
  
  Popis pro segment dojde ke zrušení zobrazí název procesu nebo vlákna, která způsobila ztracený. Nicméně to neznamená, že proces nebo vlákno, které převzal skutečně spustila v průběhu preempted období.  
  
## <a name="see-also"></a>Viz také:  
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)