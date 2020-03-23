---
title: Vizualizér souběžnosti | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: d3b4e151db08ad5490ed6238223d553f9e76aa0f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77192400"
---
# <a name="concurrency-visualizer"></a>Vizualizér souběžnosti

> [!NOTE]
> Vizualizér souběžnosti je volitelné rozšíření sady Visual Studio. Stáhněte si vizualizér souběžnosti a nástroje kolekce vizualizérů souběžnosti z následujících odkazů:
>
> - Stáhněte si rozšíření [Vizualizátor souběžnosti pro Visual Studio 2019.](https://marketplace.visualstudio.com/items?itemName=Diagnostics.DiagnosticsConcurrencyVisualizer2019#overview)
> - Stáhněte si rozšíření [Vizualizátor souběžnosti pro Visual Studio 2017.](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview)
> - Stáhněte si rozšíření [Vizualizátor souběžnosti pro Visual Studio 2015.](https://marketplace.visualstudio.com/items?itemName=Diagnostics.ConcurrencyVisualizerforVisualStudio2015)
> - Stáhněte si [nástroje kolekce vizuálů souběžnosti pro Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103).
>
> [Nástroj vizualizéru příkazového řádku souběžnosti (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) umožňuje shromažďovat trasování z příkazového řádku, které můžete zobrazit v vizualizéru souběžnosti pro Visual Studio 2015. Nástroj lze použít v počítačích, ve kterých není nainstalována sada Visual Studio.

Můžete použít Vizualizér souběžnosti, abyste viděli, jak si vaše aplikace s více vlákny provádí. Zobrazení v akcepční vizualizér poskytují grafická, tabulková a textová data, která zobrazuje časové vztahy mezi vlákny v programu a systémem jako celkem. Vizualizátor souběžnosti můžete použít k vyhledání kritických bodů výkonu, nedostatečnévyužití procesoru, konflikty vláken, migrace mezijádrových vláken, zpoždění synchronizace, aktivita Rozhraní DirectX, oblasti překrývajících se vstupně-neodchytů a další informace. Zobrazení poskytují data, která můžete jednat propojením jeho grafický výstup volání zásobníky a zdrojový kód.

> [!NOTE]
> Vizualizér souběžnosti nepodporuje webové projekty.

Vizualizér souběžnosti závisí na [funkci trasování událostí pro systém Windows.](/windows/win32/etw/event-tracing-portal)

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Zobrazení využití](../profiling/utilization-view.md)|Popisuje, jak zobrazit a analyzovat činnost systému ve všech procesorech.|
|[Zobrazení vláken](../profiling/threads-view-parallel-performance.md)|Popisuje, jak analyzovat interakce mezi vlákny v programu.|
|[Zobrazení jader](../profiling/cores-view.md)|Popisuje, jak analyzovat migraci vláken mezi jádry.|
|[Obecné vzory pro vícevláknové aplikace s nevhodným chováním](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Popisuje několik běžných vzorů a ukazuje, jak se zobrazí v vizualizéru souběžnosti.|
|[Paralelní vývoj v blogu Visual Studia](https://blogs.msdn.microsoft.com/visualizeparallel/)|Poskytuje tipy a osvědčené postupy pro vizualizér souběžnosti.|
|[Zobrazení sestav výkonu](../profiling/performance-report-views.md)|Obsahuje referenční informace pro sestavy a zobrazení nástrojů profilování sady Visual Studio.|
|[SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)|Popisuje, jak instrumentovat zdrojový kód pro zobrazení dalších informací v vizualizéru souběžnosti.|
|[Nástroj příkazového řádku vizualizéru souběžnosti (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Popisuje, jak použít nástroj příkazového řádku souběžnosti Visualizer (CVCollectionCmd.exe) ke shromažďování a zpracování trasování v počítačích, které nemají Visual Studio.|

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
