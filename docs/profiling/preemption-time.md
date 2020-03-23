---
title: Preemption Time | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de7a02f7247e09876bc4598d44fc1c395161ebc2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62935890"
---
# <a name="preemption-time"></a>Doba prevence
Tyto segmenty v časové ose jsou spojeny s blokování čas, který je kategorizován jako pre-emption. Tato kategorie znamená, že vlákno je přepnutz z jednoho z těchto důvodů:

- Plánovač jej nahradil pomocí podprocesu s vyšší prioritou.

- Spuštění kvantové vlákno vypršela a další vlákna byla připravena k provedení.

  Během této doby vlákno bylo blokováno z důvodu čekání jádra, že vizualizér souběžnosti počítá jako pre-emption. Předemptionsegmenty spustit při vlákno je vytlačena z logickéjádro a končí, když toto vlákno pokračuje v provádění.

  Popispro předem vysunutý segment zobrazuje název procesu nebo vlákna, které předkupnímu procesu způsobily. To však neznamená, že proces nebo vlákno, které převzal ve skutečnosti běžel v průběhu období preempted.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)