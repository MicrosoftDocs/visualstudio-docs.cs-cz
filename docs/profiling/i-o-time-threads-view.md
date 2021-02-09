---
title: Čas I/O (zobrazení vláken) | Microsoft Docs
description: Přečtěte si, jak jsou segmenty v/v času přidruženy k době blokování, které jsou zařazeny do kategorií v/v, což znamená, že vlákno čeká na dokončení vstupně-výstupních operací.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e147d97616f846339dc12e3941f6944f277d8318
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906864"
---
# <a name="io-time-threads-view"></a>čas I/O (zobrazení vláken)
Tyto segmenty na časové ose jsou přidruženy k době blokování, které jsou zařazeny do kategorií v/v. To znamená, že vlákno čeká na dokončení vstupně-výstupních operací. Vlákno mohlo být zablokované v rozhraní API nebo jádro související s/O čeká na to, že Vizualizátor souběžnosti se počítá jako vstup a výstup. `CreateFile()` `ReadFile()` Do této skupiny patří rozhraní API, jako je, a `WSARecv()` .

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)