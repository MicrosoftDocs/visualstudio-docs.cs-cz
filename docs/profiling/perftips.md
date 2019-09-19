---
title: Tipy pro výkon | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93703bdd4bf2f0046176ceb1f6febd5564f61705
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128307"
---
# <a name="perftips"></a>Tipy pro výkon
Ladicí program sady Visual Studio *tipy pro výkon* a integrovaný ladicí program **diagnostické nástroje** vám pomůžou monitorovat a analyzovat výkon aplikace při ladění.

 I když diagnostické nástroje integrované v ladicím programu představují skvělý způsob, jak se dozvědět o problémech s výkonem při vývoji, může mít ladicí program významný dopad na výkon vaší aplikace. Chcete-li shromažďovat přesnější data o výkonu, zvažte použití diagnostických nástrojů sady Visual Studio, které jsou spouštěny mimo ladicí program, a to jako další část šetření výkonu. Zobrazit [spustit s nebo bez ladicího programu nástroje pro profilaci](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>Tipy pro výkon
 Když ladicí program zastaví provádění na operaci zarážky nebo krokování, uplynulý čas mezi přerušením a předchozí zarážkou se zobrazí jako Tip v okně editoru. Další informace najdete v tématu [tipy pro výkon: Informace o výkonu na první pohled při ladění v aplikaci Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

 ![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Okno diagnostické nástroje
 Zarážky a související časová data se zaznamenávají v okně **diagnostické nástroje** .

 Následující obrázek znázorňuje okno **diagnostické nástroje** v aplikaci Visual Studio 2015 Update 1:

 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

- Časová osa **událostí přerušení** označuje zarážky, které byly dosaženy v relaci ladění. Kliknutím na událost můžete vybrat seznam podrobností **ladicího programu** .

- Graf **využití procesoru** zobrazuje změnu v využití CPU napříč všemi jádry procesoru v relaci ladění.

- Seznam **událostí** v podokně podrobností **ladicího programu** obsahuje položky pro každou událost přerušení.

- Sloupec **Trvání** události break zobrazuje uplynulý čas mezi událostí a předchozí zarážkou.

## <a name="turn-perftips-on-or-off"></a>Zapnout nebo vypnout tipy pro výkon
 Povolení nebo zakázání tipy pro výkon:

1. V nabídce **ladění** vyberte **možnost možnosti**.

2. Zaškrtnutí nebo zrušení zaškrtnutí **Zobrazit uplynulý PerfTip při ladění**.

## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Zapnout nebo vypnout okno Diagnostické nástroje
 Chcete-li povolit nebo zakázat okno Diagnostické nástroje:

1. V nabídce **ladění** vyberte **možnost možnosti**.

2. Zaškrtněte nebo zrušte zaškrtnutí políčka **Povolit diagnostické nástroje při ladění**.

## <a name="see-also"></a>Viz také:
- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)
