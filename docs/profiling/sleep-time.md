---
title: Doba spánku | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62980210"
---
# <a name="sleep-time"></a>Doba spánku
Tyto segmenty v časové ose jsou spojeny s blokování čas, který je kategorizován jako režim spánku. Kategorie spánku znamená, že vlákno se dobrovolně vzdalo svého logického jádra a nedělá žádnou práci. Během této doby vlákno bylo zablokováno v rozhraní API, které concurrency Visualizer počítá jako sleep. API, jako `Sleep()` `SwitchToThread()` je například a spadají do této skupiny.

## <a name="see-also"></a>Viz také
- [zobrazení vláken](../profiling/threads-view-parallel-performance.md)