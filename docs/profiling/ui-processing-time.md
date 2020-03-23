---
title: Doba zpracování uj | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 391b4582d03e32e738f0eade823326e72a662a43
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "63004439"
---
# <a name="ui-processing-time"></a>Doba zpracování ui
Tyto segmenty v časové ose jsou spojeny s blokování časy, které jsou rozděleny do kategorií jako zpracování ui. To znamená, že vlákno je čerpání zpráv systému Windows nebo provádění jiných uživatelských rozhraní (UI) práce. Během této doby vlákno bylo zablokováno v rozhraní API, které concurrency Visualizer počítá jako zpracování uživatelského rozhraní. API, jako `GetMessage()` `MsgWaitForMultipleObjects()` je například a spadají do této skupiny.

 Pokud není identifikováno žádné předdefinované blokovací rozhraní API, zkontrolujte zásobníky volání a sestavy profilů k určení základních příčin zpoždění.

 Kategorie Zpracování uživatelského rozhraní vám pomůže pochopit odezvu aplikací grafického uživatelského rozhraní a je žádoucí v aplikacích, které závisí na odezvě uživatelského rozhraní. Například pokud vlákno uživatelského rozhraní v aplikaci dosáhne 100 % času ve zpracování uživatelského rozhraní, je pravděpodobně responzivní. Pokud však vlákno uživatelského rozhraní stráví značnou dobu v jiných kategoriích, vyhledejte hlavní příčiny a zvažte možnosti pro snížení kategorií mimo uživatelské rozhraní v tomto vlákně.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)