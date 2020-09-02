---
title: Čas I/O (zobrazení vláken) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62995451"
---
# <a name="io-time-threads-view"></a>čas I/O (zobrazení vláken)
Tyto segmenty na časové ose jsou přidruženy k době blokování, které jsou zařazeny do kategorií v/v. To znamená, že vlákno čeká na dokončení vstupně-výstupních operací. Vlákno mohlo být zablokované v rozhraní API nebo jádro související s/O čeká na to, že Vizualizátor souběžnosti se počítá jako vstup a výstup. `CreateFile()` `ReadFile()` Do této skupiny patří rozhraní API, jako je, a `WSARecv()` .

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)