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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e66e62c2f7d78003581b12121844090c9754c2cc
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720056"
---
# <a name="sleep-time"></a>Doba přechodu do režimu spánku
Tyto segmenty na časové ose jsou přidruženy k době blokování, který je zařazen do kategorie v režimu spánku. Kategorie spánku znamená, že vlákno má dobrovolně k dispozici svůj logický jádro a neprovádí žádnou práci. Během této doby bylo vlákno v rozhraní API zablokované, protože Vizualizér souběžnosti se počítá jako režim spánku. `Sleep()`Do této skupiny patří rozhraní API, například a `SwitchToThread()` .

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)