---
title: Porozumění hodnotám dat kolizí prostředků | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3f522d1854cae86d9dc6e757ef0c9a62f4511800
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74779984"
---
# <a name="understand-resource-contention-data-values"></a>Porozumění hodnotám dat kolizí prostředků

Profilace kolizí prostředků shromažďuje podrobné informace o zásobníku volání pokaždé, když jsou konkurenční vlákna v aplikaci vynuceně čekat na přístup ke sdílenému prostředku.

Sestavy kolize prostředků zobrazují celkový počet kolizí a celkový čas, který byl vynaložen na čekání na prostředek pro moduly, funkce, řádky zdrojového kódu a instrukce, ve kterých došlo k čekání.

- Hodnoty včetně hodnot zobrazují celkový počet sporů, které vynutily funkci pro čekání na spory prostředků a celkovou dobu, po kterou funkce čekala.  Spory, které byly způsobeny podřízenými funkcemi, které byly volány funkcí, jsou zahrnuty v hodnotách, které jsou k dispozici.

- Exkluzivní hodnoty zobrazují pouze počet sporů, které vynutily funkci čekání a které byly způsobeny kódem v těle funkce. Spory způsobené podřízenými funkcemi nejsou zahrnuty. Výhradní čas pro funkci obsahuje také pouze časy čekání, které byly způsobeny příkazy v těle funkce.

Zobrazení sestav kolizí prostředků zahrnuje také grafy časové osy, které v průběhu času znázorňují jednotlivé události kolizí a zobrazují zásobníky volání, které vytvořily konkrétní událost. Další informace naleznete v jednom z následujících témat:

- [Zobrazení podrobností o vláknu](../profiling/thread-details-view-contention-data.md)

- [Zobrazení podrobností o prostředku](../profiling/resource-details-view-contention-data.md)

Další informace o druhém režimu profilace souběžnosti najdete v tématu [Vizualizátor souběžnosti](../profiling/concurrency-visualizer.md).
