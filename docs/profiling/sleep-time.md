---
title: Čas přechodu do režimu spánku | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be2d566228367e2cdb07aecc2d73eaf82a6d961f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62980210"
---
# <a name="sleep-time"></a>Doba přechodu do režimu spánku
Tyto segmenty na časové ose jsou přidruženy k době blokování, který je zařazen do kategorie v režimu spánku. Kategorie spánku znamená, že vlákno má dobrovolně k dispozici svůj logický jádro a neprovádí žádnou práci. Během této doby bylo vlákno v rozhraní API zablokované, protože Vizualizér souběžnosti se počítá jako režim spánku. `Sleep()`Do této skupiny patří rozhraní API, například a `SwitchToThread()` .

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)