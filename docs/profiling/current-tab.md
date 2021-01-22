---
title: Aktuální karta | Microsoft Docs
description: Vyberte aktuální kartu zobrazení vlákna, chcete-li zobrazit zásobník volání pro segment vlákna procesoru nebo blokující segment. K dispozici jsou také informace o segmentech rozhraní DirectX.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 65261d6304ead5ade7c28f40495fa68afb0c2171
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686211"
---
# <a name="current-tab"></a>Aktuální karta
Kliknutím na **aktuální** kartu zobrazíte zásobník volání (je-li k dispozici), který je nejblíže aktuálnímu bodu výběru na časové ose, pokud je vybrán segment vlákna procesoru.  V takovém případě je bod výběru reprezentován černou šipkou nebo blikajícím kurzorem nad časovou osou. Když je vybrán blokující segment, není blikající kurzor zobrazen, protože nebylo spuštěno. Segment je však stále zvýrazněn a zobrazí se zásobník volání.

 Na **aktuální** kartě se zobrazí také informace o segmentech aktivity rozhraní DirectX, značkách a vstupně-výstupních přístupech.  Pro segmenty aktivity rozhraní DirectX se zobrazí informace o způsobu zpracování paketů DMA pomocí hardwarové fronty.  V případě značek se zobrazí informace o popisu a typu značky.  Pro vstupně-výstupní přístup se zobrazí informace o souboru a počtu přečtených nebo zapsaných bajtů.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)