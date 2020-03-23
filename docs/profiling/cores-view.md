---
title: Zobrazení jader | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b26b913a42a563e0226ff2697b947684dfec53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62553055"
---
# <a name="cores-view"></a>Zobrazení jader
**Zobrazení jader** ukazuje, jak bylo namapováno spuštění vlákna na jádra logického procesoru (zvolte **Analyzovat** > **vizualizaci souběžnosti** a spusťte vizualizér souběžnosti). Pokud píšete serverové aplikace, toto zobrazení vám může pomoci optimalizovat výkon mezipaměti pomocí spřažení vláken nebo správy fondu vláken. Může také pomoci prozkoumat případy, kdy použití spřažení vláken mohlo zhoršit problém migrace mezi jádry. Zobrazení jader má dvě části, graf a legendu.

 Graf zobrazuje logická jádra na ose y a čas na ose x. Každé vlákno v grafu má jedinečnou barvu, takže můžete sledovat jeho pohyb mezi jádry v průběhu času. Vlákna v tomto grafu můžete filtrovat tak, že je vyberete v oblasti legendy.

 Oblast legendy má položku pro každou barvu v grafu. Každá položka zobrazuje barvu a název vlákna, počet přepnutí kontextu mezi jádry, celkový počet přepnutí kontextu a procento přepnutí kontextu, které protínají jádra. Legenda je seřazena podle počtu přepínačů kontextu mezi jádry v sestupném pořadí. Obsahuje pouze vlákna, která byla spuštěna během zobrazeného časového rozsahu.  Seznam se aktualizuje, pokud přiblížíte nebo posunete.

## <a name="see-also"></a>Viz také
- [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)
- [Zobrazení využití](../profiling/utilization-view.md)
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)