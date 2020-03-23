---
title: Principy datových hodnot konfliktů prostředků | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779984"
---
# <a name="understand-resource-contention-data-values"></a>Principy datových hodnot tvrzení o prostředcích

Profilování konfliktů prostředků shromažďuje podrobné informace zásobníku volání pokaždé, když konkurenční vlákna v aplikaci jsou nuceni čekat na přístup ke sdílenému prostředku.

Sestavy kolize prostředků zobrazují celkový počet kolizí a celkový čas, který byl vynaložen na čekání na prostředek pro moduly, funkce, řádky zdrojového kódu a instrukce, ve kterých došlo k čekání.

- Včetně hodnoty zobrazit celkový počet tvrzení, které vynucené funkce čekat podle tvrzení o prostředku a celkový čas, který funkce čekala.  Konflikty, které byly způsobeny podřízené funkce, které byly volány funkce jsou zahrnuty do včetně hodnoty.

- Výhradní hodnoty zobrazují pouze počet tvrzení, které vynutily čekání funkce a které byly způsobeny kódem v těle funkce. Konflikty způsobené podřízenými funkcemi nejsou zahrnuty. Výhradní čas pro funkci také zahrnuje pouze čekací doby, které byly způsobeny příkazy v těle funkce.

Zobrazení sestavy konfliktů zdrojů také obsahují grafy časové osy, které zobrazují jednotlivé konfliktní události v průběhu času a zobrazují zásobníky volání, které vytvořily konkrétní událost. Další informace naleznete v jednom z následujících témat:

- [Zobrazení podrobností vlákna](../profiling/thread-details-view-contention-data.md)

- [Zobrazení podrobností o zdroji](../profiling/resource-details-view-contention-data.md)

Další informace o druhém režimu profilování souběžnosti naleznete v tématu [Vizualizace souběžnosti](../profiling/concurrency-visualizer.md).
