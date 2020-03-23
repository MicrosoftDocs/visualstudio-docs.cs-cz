---
title: Čas I-O (zobrazení vláken) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d7ba29383ddddc02160967a90b56046128d2f19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62995451"
---
# <a name="io-time-threads-view"></a>čas I/O (zobrazení vláken)
Tyto segmenty v časové ose jsou spojeny s blokování časy, které jsou rozděleny do kategorií jako vstupně-v./O. To znamená, že vlákno čeká na dokončení vstupně-va. Vlákno může být blokovánv rozhraní API nebo vstupně-o související jádro čekat, že souběžnost vizualizátor počítá jako V/O. api, jako `CreateFile()` `ReadFile()`je `WSARecv()` například , a spadají do této skupiny.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)