---
title: Doba synchronizace | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: ae73f7b9a9838a006dce47bf44b0ed46aa0b84fa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62965307"
---
# <a name="synchronization-time"></a>Čas synchronizace
Tyto segmenty v časové ose jsou spojeny s blokování časy, které jsou rozděleny do kategorií jako synchronizace. Pokud je vlákno při synchronizaci označeno jako blokované, je implikována jedna z těchto věcí:

- Spuštění podprocesu může mít za následek volání známé rozhraní API synchronizace vláken, jako `EnterCriticalSection()` jsou nebo `WaitForSingleObject()`.

- Algoritmus párování rozhraní API nemůže být zcela komplexní, a proto některá rozhraní API, která by mohla být mapována na jiné kategorie, se mohou také zobrazit jako synchronizace, protože rámec v zásobníku volání nakonec dosáhl základního jádra blokujícího primitiveho, který byl mapována na tuto kategorii.

  Chcete-li pochopit základní příčinu události blokování vlákna, pečlivě zkontrolujte blokování zásobníků volání a sestavy profilu.

## <a name="see-also"></a>Viz také
- [zobrazení vláken](../profiling/threads-view-parallel-performance.md)