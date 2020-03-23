---
title: Doba spuštění (zobrazení vláken) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac0cf2a60fd194176b7cd9091f4e7dc7a758006f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969911"
---
# <a name="execution-time-threads-view"></a>Doba spuštění (zobrazení vláken)
Tyto segmenty v časové ose zobrazení vláken představují čas spuštění, kdy vlákno aktivně pracuje na logickém jádru v systému.

 Změny stavu vlákna jsou zjištěny prostřednictvím událostí přepnutí kontextu jádra. Trasování událostí pro Windows (ETW) zachycuje ukázkové zásobníky každou milisekundu. Ve velmi krátkém zeleném segmentu je možné, že se neodebere žádný vzorek. Proto některé segmenty krátké spuštění může zobrazit žádné zásobníku volání.

 Po klepnutí na segment spuštění, Vizualizér souběžnosti zobrazí ukázkový zásobník nejblíže k umístění kliknutí. Umístění tohoto ukázkového zásobníku je zobrazeno černou šipkou nebo stříškou nad časovou osou a ukázkový zásobník se zobrazí na kartě **Aktuální.**

 Chcete-li zobrazit tradiční profil vzorkování pro všechny segmenty spuštění v aktuálním zobrazení, klikněte na **tlačítko Spuštění** v profilu viditelné časové osy.

## <a name="see-also"></a>Viz také
- [Sestava profilu spuštění](../profiling/execution-profile-report.md)
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)