---
title: Zobrazení jader | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62553055"
---
# <a name="cores-view"></a>Zobrazení jader
V **zobrazení jádra** se dozvíte, jak bylo spuštění vlákna namapováno na jádra logického procesoru (zvolením možnosti **analyzovat**  >  **Vizualizátor souběžnosti** spustíte Vizualizér souběžnosti). Pokud píšete serverové aplikace, toto zobrazení vám může pomoci optimalizovat výkon mezipaměti pomocí spřažení vlákna nebo správy fondu vláken. Může vám taky posuzovat případy, kdy použití spřažení vlákna mohlo zhoršit problémy s migrací mezi jádry. Zobrazení jádra má dvě části, graf a legendu.

 Graf znázorňuje logické jádra na ose y a čas na ose x. Každé vlákno v grafu má jedinečnou barvu, abyste mohli sledovat jeho pohyb napříč jádry v průběhu času. Vlákna v tomto grafu můžete filtrovat tak, že je vyberete v oblasti legenda.

 Oblast legendy obsahuje záznam pro každou barvu v grafu. Každá položka zobrazuje barvu a název vlákna, počet přepínačů kontextu mezi jádry, celkový počet přepínačů kontextu a procento přepínačů kontextu, které kříží jádro. Legenda je seřazena podle počtu přepínačů kontextu křížového jádra v klesajícím pořadí. Obsahuje pouze vlákna, která byla provedena během zobrazeného časového rozsahu.  Seznam se aktualizuje, když přiblížíte nebo posunete.

## <a name="see-also"></a>Viz také
- [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)
- [Zobrazení využití](../profiling/utilization-view.md)
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)