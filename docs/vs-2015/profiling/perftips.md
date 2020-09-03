---
title: Tipy pro výkon | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa56b6731e359db486a111194a710069d41a2f1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295867"
---
# <a name="perftips"></a>Tipy pro výkon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladicí program sady Visual Studio *tipy pro výkon* a integrovaný ladicí program **diagnostické nástroje** vám pomůžou monitorovat a analyzovat výkon aplikace při ladění.  
  
 I když diagnostické nástroje integrované v ladicím programu představují skvělý způsob, jak se dozvědět o problémech s výkonem při vývoji, může mít ladicí program významný dopad na výkon vaší aplikace. Chcete-li shromažďovat přesnější data o výkonu, zvažte použití diagnostických nástrojů sady Visual Studio, které jsou spouštěny mimo ladicí program, a to jako další část šetření výkonu. Viz [spuštění nástrojů pro profilaci bez ladění](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01).  
  
## <a name="perftips"></a>Tipy pro výkon  
 Když ladicí program zastaví provádění na operaci zarážky nebo krokování, uplynulý čas mezi přerušením a předchozí zarážkou se zobrazí jako Tip v okně editoru. Další informace naleznete v tématu [tipy pro výkon: informace o výkonu při ladění v aplikaci Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).  
  
 ![PerfTip](../profiling/media/dbgdiag-perf-perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Okno diagnostické nástroje  
 Data zarážek a související časová data časování se zaznamenávají v okně Diagnostické nástroje  
  
 Následující obrázek znázorňuje okno Diagnostické nástroje v aplikaci Visual Studio 2015 Update 1:  
  
 ![DiagnosticTools&#45;-datum1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-v-datum1")  
  
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
