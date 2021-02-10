---
title: Čas přerušení | Microsoft Docs
description: Přečtěte si o Premption čase a o tom, že tyto segmenty na časové ose jsou přidružené k době blokování, která je zařazená do kategorie jako předem ztracený.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8515043b228deb4fbcbf43c0e75b9826912f059
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957319"
---
# <a name="preemption-time"></a>Čas přerušení
Tyto segmenty na časové ose jsou přidruženy k době blokování, která je zařazena do kategorie jako předem ztracený. Tato kategorie předpokládá, že je vlákno přepnuto z jednoho z těchto důvodů:

- Plánovač ho nahradil pomocí vlákna s vyšší prioritou.

- Doba běhu vlákna vypršela a ostatní vlákna byly připraveny ke spuštění.

  Během této doby bylo vlákno zablokováno v důsledku čekání jádra, že Vizualizátor souběžnosti je počítán jako pre-ztracený. Ztracený segmenty začínají při vložení vlákna z logického jádra a ukončí, když vlákno pokračuje v provádění.

  Popisek pro předem přerušené segment zobrazuje název procesu nebo vlákna, které způsobilo předztracený. To však neznamená, že proces nebo podproces, které trvaly v průběhu období přerušení.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)