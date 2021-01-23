---
title: Čas synchronizace | Microsoft Docs
description: Přečtěte si, jak jsou segmenty na časové ose přidružené k době blokování, které jsou zařazeny do kategorií jako synchronizace.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0e8c2243d01a5801b6846445995bbdfdcff78c9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719822"
---
# <a name="synchronization-time"></a>Čas synchronizace
Tyto segmenty na časové ose jsou přidruženy k době blokování, které jsou zařazeny do kategorií jako synchronizace. Pokud je vlákno označeno jako blokované při synchronizaci, předpokládá se jedna z těchto věcí:

- Výsledkem provedení vlákna může být volání známého rozhraní API synchronizace vláken, například `EnterCriticalSection()` nebo `WaitForSingleObject()` .

- Algoritmus odpovídající rozhraní API se nedá úplně komplexní, takže některá rozhraní API, která se dají namapovat na jiné kategorie, se můžou zobrazit jako synchronizace, protože rámec v zásobníku volání nakonec dosáhl základní třídy blokujícího jádra, která se namapovala na tuto kategorii.

  Pro pochopení základní příčiny události blokující vlákno pečlivě prověřte blokující zásobníky volání a sestavy profilů.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)