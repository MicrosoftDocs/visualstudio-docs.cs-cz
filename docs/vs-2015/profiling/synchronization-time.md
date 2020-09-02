---
title: Čas synchronizace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 218f333f97e8252993f87893238a0f51f964d6c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151389"
---
# <a name="synchronization-time"></a>Čas synchronizace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tyto segmenty na časové ose jsou přidruženy k době blokování, které jsou zařazeny do kategorií jako synchronizace. Pokud je vlákno označeno jako blokované při synchronizaci, předpokládá se jedna z těchto věcí:  
  
- Výsledkem provedení vlákna může být volání známého rozhraní API synchronizace vláken, například `EnterCriticalSection()` nebo `WaitForSingleObject()` .  
  
- Algoritmus odpovídající rozhraní API se nedá úplně komplexní, takže některá rozhraní API, která se dají namapovat na jiné kategorie, se můžou zobrazit jako synchronizace, protože rámec v zásobníku volání nakonec dosáhl základní třídy blokujícího jádra, která se namapovala na tuto kategorii.  
  
  Pro pochopení základní příčiny události blokující vlákno pečlivě prověřte blokující zásobníky volání a sestavy profilů.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)
