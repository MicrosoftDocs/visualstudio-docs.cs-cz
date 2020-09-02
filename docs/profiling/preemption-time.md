---
title: Čas přerušení | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62935890"
---
# <a name="preemption-time"></a>Čas přerušení
Tyto segmenty na časové ose jsou přidruženy k době blokování, která je zařazena do kategorie jako předem ztracený. Tato kategorie předpokládá, že je vlákno přepnuto z jednoho z těchto důvodů:

- Plánovač ho nahradil pomocí vlákna s vyšší prioritou.

- Doba běhu vlákna vypršela a ostatní vlákna byly připraveny ke spuštění.

  Během této doby bylo vlákno zablokováno v důsledku čekání jádra, že Vizualizátor souběžnosti je počítán jako pre-ztracený. Ztracený segmenty začínají při vložení vlákna z logického jádra a ukončí, když vlákno pokračuje v provádění.

  Popisek pro předem přerušené segment zobrazuje název procesu nebo vlákna, které způsobilo předztracený. To však neznamená, že proces nebo podproces, které trvaly v průběhu období přerušení.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)