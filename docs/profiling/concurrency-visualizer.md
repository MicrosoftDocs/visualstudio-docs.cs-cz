---
title: Vizualizátor souběžnosti | Microsoft Docs
ms.date: 07/11/2017
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1e9109493ea78542afaedabbcce3841e3eac0e7
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128135"
---
# <a name="concurrency-visualizer"></a>Vizualizér souběžnosti

> [!NOTE]
> Vizualizátor souběžnosti je volitelným rozšířením sady Visual Studio. Stáhněte si nástroje Vizualizátor souběžnosti a kolekce Vizualizátor souběžnosti z následujících odkazů:
>
> - Stáhněte si rozšíření [Concurrency pro Vizualizér pro Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview) .
> - Stáhněte si rozšíření [Concurrency pro Vizualizér pro Visual Studio 2015](https://marketplace.visualstudio.com/items?itemName=Diagnostics.ConcurrencyVisualizerforVisualStudio2015) .
> - Stáhněte si [nástroje kolekce Vizualizátor souběžnosti pro Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=49103).
>
> [Nástroj příkazového řádku Vizualizátor souběžnosti (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) umožňuje shromažďovat trasování z příkazového řádku, které můžete zobrazit v Vizualizátor souběžnosti pro Visual Studio 2015. Nástroj lze použít na počítačích, ve kterých není nainstalována aplikace Visual Studio.

Pomocí Vizualizátor souběžnosti můžete zjistit, jak aplikace s více vlákny funguje. Zobrazení v Vizualizér souběžnosti poskytují grafická, tabulková a textová data, která zobrazují dočasné vztahy mezi vlákny v programu a systémem jako celek. Vizualizátor souběžnosti můžete použít k vyhledání problémových míst výkonu, nevytížení procesoru, kolize vláken, migrace vláken mezi jádry, zpoždění synchronizace, aktivity rozhraní DirectX, oblastí překrytých vstupně-výstupních operací a dalších informací. Zobrazení poskytují data, která lze použít propojením jejího grafického výstupu se zásobníky volání a zdrojového kódu.

> [!NOTE]
> Vizualizátor souběžnosti nepodporuje webové projekty.

Vizualizátor souběžnosti spoléhá na [trasování událostí pro funkce Windows](http://go.microsoft.com/fwlink/?LinkId=234579) .

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Zobrazení využití](../profiling/utilization-view.md)|Popisuje, jak zobrazit a analyzovat činnost systému napříč všemi procesory.|
|[Zobrazení vláken](../profiling/threads-view-parallel-performance.md)|Popisuje, jak analyzovat interakce mezi vlákny v programu.|
|[Zobrazení jader](../profiling/cores-view.md)|Popisuje, jak analyzovat migraci vláken napříč jádry.|
|[Obecné vzory pro vícevláknové aplikace s nevhodným chováním](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Popisuje několik běžných vzorů a ukazuje, jak se zobrazují ve Vizualizátor souběžnosti.|
|[Paralelní vývoj v blogu sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=235385)|Poskytuje tipy a osvědčené postupy pro Vizualizátor souběžnosti.|
|[Zobrazení sestav výkonu](../profiling/performance-report-views.md)|Poskytuje referenční informace o sestavách a zobrazeních sady Visual Studio Nástroje pro profilaci.|
|[SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)|Popisuje, jak instrumentovat zdrojový kód pro zobrazení dalších informací v Vizualizátor souběžnosti.|
|[Nástroj příkazového řádku Vizualizátor souběžnosti (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Popisuje, jak použít nástroj příkazového řádku Vizualizátor souběžnosti (CVCollectionCmd. exe) ke shromáždění a zpracování trasování na počítačích, které nemají aplikaci Visual Studio.|

## <a name="see-also"></a>Viz také:

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)
