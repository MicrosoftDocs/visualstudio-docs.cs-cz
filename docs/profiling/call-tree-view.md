---
title: Zobrazení stromu volání | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b932d5f9e4a178c94f3e490c66cec64648ce4f6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773332"
---
# <a name="call-tree-view"></a>zobrazení stromu volání
Zobrazení Strom volání zobrazuje cesty spuštění funkce, které byly provázány v profilované aplikaci. Kořen stromu je vstupní bod do aplikace nebo součásti. Každý uzel funkce uvádí všechny funkce, které volal, a údaje o výkonu těchto volání funkcí.

 Strom volání zobrazení můžete také rozbalit a zvýraznit cestu spuštění funkce, která spotřebovává nejvíce času nebo byl vzorkován nejčastěji. Chcete-li zobrazit cestu nejdražší k výkonu, klepněte pravým tlačítkem myši na funkci a potom klepněte na příkaz **Rozbalit aktivní cestu**.

 Každý proces v profilování spustit je zobrazen jako kořenový uzel. Počáteční uzel zobrazení Strom volání můžete nastavit tak, že kliknete pravým tlačítkem myši na uzel, který chcete nastavit jako počáteční uzel, a pak vyberete **nastavit kořenový adresář**.

 Když nastavíte kořenový uzel, odstraníte všechny ostatní položky ze zobrazení kromě podstromu vybraného uzlu. Kořenový uzel můžete obnovit zpět na uzel, který jste si prohlíželi. V okně Strom volání klepněte pravým tlačítkem myši a vyberte **příkaz Obnovit kořenový adresář**.

 Zobrazení Strom volání lze přizpůsobit tak, aby bylo možné přidávat nebo odebírat sloupce. Klikněte pravým tlačítkem myši na **záhlaví názvu sloupce**a potom vyberte Přidat nebo **odebrat sloupce**.

 Strom volání zobrazení lze nakonfigurovat pro snížení šumu omezením množství dat, která je prezentována. Při použití snížení šumu jsou problémy s výkonem výraznější v zobrazení. Když jsou problémy s výkonem snadno rozlišitelné, analýza je jednodušší. Další informace naleznete v [tématu Postup: Konfigurace snížení šumu v zobrazeních sestavy](../profiling/how-to-configure-noise-reduction-in-report-views.md).

> [!NOTE]
> Pokud je redukce šumu nakonfigurována tak, aby se v sestavě zobrazovalo upozornění, zobrazí se informační panel.

 Další informace o definicích sloupců v zobrazení Strom volání naleznete v následujících tématech:

- [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)

- [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)

- [Zobrazení stromu volání – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [Zobrazení stromu volání](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>Viz také
- [Zobrazení sestavy výkonu](../profiling/performance-report-views.md)
- [Principy hodnot dat instrumentace](../profiling/understanding-instrumentation-data-values.md)
- [Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)
