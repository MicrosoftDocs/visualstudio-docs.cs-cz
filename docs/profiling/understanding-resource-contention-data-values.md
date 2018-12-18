---
title: Porozumění hodnotám dat kolizí prostředku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ffacfcd5eac9fd88cfd7bbaa2c7d2546836d87c6
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948554"
---
# <a name="understand-resource-contention-data-values"></a>Vysvětlení hodnotám dat kolizí prostředku

Profilace kolize prostředků shromažďuje podrobné informace v zásobníku volání pokaždé, když, že jsou konkurenční vlákna v aplikaci musí počkat na přístup ke sdíleným prostředkům.

Sestavy kolize prostředků zobrazují celkový počet kolizí a celkový čas, který byl vynaložen na čekání na prostředek pro moduly, funkce, řádky zdrojového kódu a instrukce, ve kterých došlo k čekání.

- Celkové hodnoty se zobrazí celkový počet sporů, které vynutit funkci čekat ve sporty prostředků a celková doba čekání funkce.  Spory, které byly způsobeny podřízené funkce, které byly volány funkce jsou součástí (včetně) hodnot.

- Výhradní hodnoty se zobrazí pouze počet sporů, který vynucené funkci čekat a, které byly způsobeny kódu v těle funkce. Tento počet sporů: způsobené podřízené funkce nejsou zahrnuty. Výhradní čas pro funkci také zahrnuje pouze dobu čekání, které byly způsobeny příkazy v těle funkce.

Zobrazení sestav kolize prostředků také zahrnovat grafech časové osy, které ukazují jednotlivých kolizní události v čase a zobrazit zásobníky volání, které vytvořeny určitá událost. Další informace naleznete v jednom z následujících témat:

- [Zobrazení podrobností o vláknu](../profiling/thread-details-view-contention-data.md)

- [Zobrazení podrobností o prostředku](../profiling/resource-details-view-contention-data.md)

Další informace o druhý režim profilace souběžnosti, naleznete v tématu [Vizualizátor souběžnosti](../profiling/concurrency-visualizer.md).