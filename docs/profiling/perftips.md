---
title: PerfTips | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93703bdd4bf2f0046176ceb1f6febd5564f61705
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "71128307"
---
# <a name="perftips"></a>Tipy pro výkon
Visual Studio ladicí program *PerfTips* a ladicí program integrované **diagnostické nástroje** vám pomohou sledovat a analyzovat výkon vaší aplikace při ladění.

 Přestože diagnostické nástroje integrované ladicím programem jsou skvělý způsob, jak se seznámit s problémy s výkonem při vývoji, ladicí program může mít významný dopad na výkon vaší aplikace. Chcete-li shromažďovat přesnější údaje o výkonu, zvažte použití nástrojů diagnostiky sady Visual Studio, které běží mimo ladicí program příliš jako další součást vyšetřování výkonu. Viz [Spuštění nástrojů profilování s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>Tipy pro výkon
 Když ladicí program zastaví provádění na zarážku nebo krokování operace, uplynulý čas mezi přestávkou a předchozí zarážka se zobrazí jako tip v okně editoru. Další informace naleznete [v tématu PerfTips: Performance Information at a tezi při ladění pomocí sady Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

 ![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Okno Nástroje diagnostiky
 Zarážky a přidružená časovací data jsou zaznamenány v okně **Diagnostické nástroje.**

 Následující obrázek znázorňuje okno **Diagnostické nástroje** v aktualizaci 1 sady Visual Studio 2015:

 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

- Časová **osa události přerušení** označují zarážky, které byly v relaci ladění zasaženy. Kliknutím na událost ji vyberte seznam podrobností **ladicího programu.**

- Graf **využití procesoru** zobrazuje změnu využití procesoru ve všech jádrech procesoru v relaci ladění.

- Seznam **Události** podokna podrobností **ladicího programu** obsahuje položky pro každou událost přerušení.

- Sloupec **Doba trvání** události přerušení zobrazuje uplynulý čas mezi událostí a předchozí zarážkou.

## <a name="turn-perftips-on-or-off"></a>Zapnutí nebo vypnutí perftips
 Povolení nebo zakázání perftips:

1. V nabídce **Ladění** zvolte **Možnosti**.

2. Při ladění zaškrtněte nebo zrušte **zaškrtnutí políčka Zobrazit uplynulý perftip**.

## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Zapnutí nebo vypnutí okna Diagnostické nástroje
 Povolení nebo zakázání okna Diagnostické nástroje:

1. V nabídce **Ladění** zvolte **Možnosti**.

2. Při ladění zaškrtněte nebo zrušte zaškrtnutí **políčka Povolit diagnostické nástroje**.

## <a name="see-also"></a>Viz také
- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
