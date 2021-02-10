---
title: Zobrazení stromu volání | Microsoft Docs
description: Seznamte se se stromovým zobrazením volání, které zobrazuje cesty provádění funkce, které byly provázány v profilované aplikaci.
ms.custom: SEO-VS-2020
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3ee8f09c502f6125c6ce2e67e504a689c035ffd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957345"
---
# <a name="call-tree-view"></a>zobrazení stromu volání
Zobrazení stromu volání zobrazuje cesty provádění funkce, které byly provázány v profilované aplikaci. Kořen stromu je vstupní bod do aplikace nebo komponenty. Každý uzel funkce obsahuje seznam všech funkcí, které volaly, a údaje o výkonu těchto volání funkcí.

 Zobrazení stromu volání může také rozšiřovat a zvýrazňovat cestu spuštění funkce, která využila nejvíce času nebo byla Navzorkovaná častěji. Chcete-li zobrazit nejužitečnější cestu, klikněte na ni pravým tlačítkem myši a pak klikněte na Rozbalit kritickou **cestu**.

 Každý proces v průběhu profilace se zobrazuje jako kořenový uzel. Můžete nastavit počáteční uzel zobrazení stromu volání kliknutím pravým tlačítkem myši na uzel, který chcete nastavit jako počáteční uzel, a následným výběrem možnosti **Nastavit kořen**.

 Když nastavíte kořenový uzel, eliminují se všechny ostatní záznamy z zobrazení kromě podstromu vybraného uzlu. Kořenový uzel můžete obnovit zpátky na uzel, který jste si prohlíželi. V okně zobrazení stromu volání klikněte pravým tlačítkem myši a vyberte možnost **resetovat kořen**.

 Zobrazení stromu volání lze přizpůsobit přidáním nebo odebráním sloupců. Klikněte pravým tlačítkem myši na **záhlaví názvu sloupce** a pak vyberte **Přidat nebo odebrat sloupce**.

 Zobrazení stromu volání lze nakonfigurovat pro redukci hluku tím, že omezíte množství dat, která jsou zobrazena. Díky omezení šumu jsou problémy s výkonem výraznější v zobrazení. Pokud je snazší rozlišovat problémy s výkonem, je analýza jednodušší. Další informace najdete v tématu [Postupy: Konfigurace snížení šumu v zobrazeních sestav](../profiling/how-to-configure-noise-reduction-in-report-views.md).

> [!NOTE]
> Pokud je snížení šumu nakonfigurované tak, aby zobrazovalo upozornění, když je zapnuté, zobrazí se v sestavě informační panel.

 Další informace o definicích pro sloupce ve stromovém zobrazení volání naleznete v následujících tématech:

- [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)

- [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)

- [Zobrazení stromu volání – vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [Zobrazení stromu volání](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>Viz také
- [Zobrazení sestav výkonu](../profiling/performance-report-views.md)
- [Porozumění hodnotám dat instrumentace](../profiling/understanding-instrumentation-data-values.md)
- [Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)
