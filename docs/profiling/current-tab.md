---
title: Aktuální karta | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f48ba44d41286f1cf5eda6ececb68d21d39abd14
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552785"
---
# <a name="current-tab"></a>Aktuální karta
Kliknutím na kartu **Aktuální** uvidíte zásobník volání (pokud je k dispozici), který je nejblíže aktuálnímu bodu výběru na časové ose, pokud je vybrán segment vlákna procesoru.  V tomto případě je bod výběru reprezentován černou šipkou nebo stříškou nad časovou osou. Pokud je vybrán blokující segment, stříška se nezobrazí, protože nedošlo k žádnému spuštění. Segment je však stále zvýrazněn a zobrazí se zásobník volání.

 Karta **Aktuální** také zobrazuje informace o segmentech aktivity DirectX, značkách a vstupně-va.  U segmentů aktivity rozhraní DirectX se zobrazí informace o způsobu zpracování paketů DMA hardwarovou frontou.  U značek se zobrazí informace o popisu a typu značky.  Pro vstupně-out přístup jsou zobrazeny informace o souboru a počet přečtených nebo zapsaných bajtů.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)