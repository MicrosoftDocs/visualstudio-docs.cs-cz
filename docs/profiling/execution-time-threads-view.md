---
title: Doba spuštění (zobrazení vláken) | Microsoft Docs
description: Zkontrolujte dobu spuštění v zobrazení vláken Vizualizátor souběžnosti. Čas spuštění je reprezentován segmenty, které ukazují, kdy vlákno aktivně pracuje na logickém jádru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5c62c57e3037b38c2729917d2b882550b9c2d126
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861605"
---
# <a name="execution-time-threads-view"></a>Doba spuštění (zobrazení vláken)
Tyto segmenty v časové ose zobrazení vlákna reprezentují dobu provádění, když vlákno aktivně pracuje na logickém jádru v systému.

 Změny stavu vlákna se zjišťují prostřednictvím událostí přepínače kontextu jádra. Trasování událostí pro Windows (ETW) zachycuje ukázkové zásobníky každých milisekund. Ve velmi krátkém zeleném segmentu je možné, že není provedena žádná ukázka. Proto některé z krátkých segmentů spuštění nesmějí zobrazovat žádný zásobník volání.

 Když kliknete na segment spuštění, Vizualizér souběžnosti zobrazí vzorový zásobník, který je nejblíže umístění tohoto kliknutí. Umístění tohoto ukázkového zásobníku se zobrazuje černou šipkou nebo blikajícím kurzorem nad časovou osou a ukázka zásobníku se zobrazí na **aktuální** kartě.

 Chcete-li zobrazit tradiční profil vzorkování pro všechny segmenty spuštění v aktuálním zobrazení, klikněte na možnost **spuštění** v profilu viditelné časové osy.

## <a name="see-also"></a>Viz také
- [Sestava profilu spuštění](../profiling/execution-profile-report.md)
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)