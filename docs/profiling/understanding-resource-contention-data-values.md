---
title: Porozumění hodnotám dat kolizí prostředků | Microsoft Docs
description: Přečtěte si, jak profilace kolizí prostředků shromažďuje podrobné informace o tom, že konkurenční vlákna v aplikaci jsou nucená čekat na přístup ke sdílenému prostředku.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5e050879fc9a1bd74f95ae5d24a92dc7a59a73c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886064"
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
