---
title: Čas správy paměti | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 442973edb18e75bafda8a9397eac799286c69dfa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62963778"
---
# <a name="memory-management-time"></a>Čas správy paměti
Tyto segmenty na časové ose jsou spojeny s blokování časy, které jsou rozděleny do kategorií jako správa paměti. Tento scénář znamená, že vlákno je blokován o událost, která je spojena s operací správy paměti, jako je například stránkování. Během této doby vlákno bylo zablokováno ve stavu rozhraní API nebo jádra, které vizualizátor souběžnosti počítá jako správu paměti. Patří mezi ně události, jako je například stránkování a přidělení paměti.

 Prozkoumejte přidružené zásobníky volání a sestavy profilů, abyste lépe porozuměli základním důvodům pro bloky, které jsou zařazeny do kategorií správa paměti.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)