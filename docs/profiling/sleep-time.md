---
title: Čas přechodu do režimu spánku | Microsoft Docs
description: Přečtěte si, že kategorie v režimu spánku znamená, že vlákno má dobrovolně k dispozici svůj logický jádro a neprovádí žádnou práci.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a433d11c2684a4a39660759f33d49bd719c2b2ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960166"
---
# <a name="sleep-time"></a>Doba přechodu do režimu spánku
Tyto segmenty na časové ose jsou přidruženy k době blokování, který je zařazen do kategorie v režimu spánku. Kategorie spánku znamená, že vlákno má dobrovolně k dispozici svůj logický jádro a neprovádí žádnou práci. Během této doby bylo vlákno v rozhraní API zablokované, protože Vizualizér souběžnosti se počítá jako režim spánku. `Sleep()`Do této skupiny patří rozhraní API, například a `SwitchToThread()` .

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)