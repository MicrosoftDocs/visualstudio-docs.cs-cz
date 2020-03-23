---
title: 'Postup: Zvolte metody sběru | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3c633e12b2e0bf157ffd94ef06a5898fdc3ec830
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776342"
---
# <a name="how-to-choose-collection-methods"></a>Postup: Zvolte metody kolekce

Nástroje profilování visual studio podporují tři metody shromažďování dat o výkonu: vzorkování, instrumentace a souběžnost. Vzorkování nebo instrumentace můžete také použít ke shromažďování dat o přidělení paměti .NET a životnosti.

Můžete použít metodu relace výkonu **k** určení nejvhodnější metody kolekce pro vaši aplikaci. Metodu kolekce můžete nastavit z Průvodce výkonem, Průzkumníka výkonu nebo ze stránek vlastností relace výkonu. Pokud používáte nástroje příkazového řádku, další informace naleznete [v tématu Profilování z příkazového řádku.](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="performance-wizard"></a>Průvodce výkonu

### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Výběr metody kolekce pomocí Průvodce výkonem

- Na první stránce průvodce vyberte jednu z následujících možností:

| Možnost | Popis |
|----------------------------| - |
| **Vzorkování procesoru** | Shromažďuje statistiky aplikací, které jsou užitečné pro počáteční analýzu a pro analýzu problémů s využitím procesoru. |
| **Instrumentation** | Shromažďuje podrobná časovací data, která jsou užitečná pro cílenou analýzu a pro analýzu problémů s výkonem vstupu a výstupu. |
| **Přidělení paměti .NET** | Shromažďuje data přidělení paměti rozhraní .NET Framework pomocí metody profilování vzorkování. |
| **Souběžnost** | Shromažďuje číselná data o konfliktech prostředků. |

## <a name="performance-explorer"></a>Prohlížeč výkonu

### <a name="to-select-a-collection-method-using-performance-explorer"></a>Výběr metody kolekce pomocí Průzkumníka výkonu

1. Na panelu nástrojů **Průzkumník výkonu** klikněte na šipku vedle rozevíracího seznamu **Metoda.**

2. Klikněte na metodu kolekce, kterou dáváte přednost.

## <a name="performance-session-property-pages"></a>Stránky vlastností relace výkonu

### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Výběr metody vzorkování nebo instrumentace pomocí vlastností relace výkonu

1. V **Průzkumníku výkonu**vyberte relaci výkonu.

     Název souboru relace výkonu má . *prodloužení psess.*

2. Klepněte pravým tlačítkem myši na relaci výkonu a potom klepněte na příkaz **Vlastnosti**.

3. Na **stránkách vlastností**klepněte na **tlačítko Obecné**.

4. Klikněte na metodu kolekce, kterou dáváte přednost.

    - Informace o dalších možnostech, které jsou k dispozici při shromažďování dat vzorkování, naleznete [v tématu Shromažďování statistik výkonu pomocí vzorkování](../profiling/collecting-performance-statistics-by-using-sampling.md)

    - Informace o dalších možnostech, které jsou k dispozici při shromažďování dat vzorkování, naleznete [v tématu Shromažďování podrobných časovacích dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).

### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Výběr kolekce dat paměti .NET pomocí vlastností relace výkonu

1. V **Průzkumníku výkonu**vyberte relaci výkonu.

     Název souboru relace výkonu má příponu Psess.

2. Klepněte pravým tlačítkem myši na relaci výkonu a potom klepněte na příkaz **Vlastnosti**.

3. Na **stránkách vlastností**klepněte na **tlačítko Obecné**.

4. Klepněte na **položku Vzorkování** nebo **Instrumentace**.

5. Chcete-li shromáždit velikost a počet přidělení objektů rozhraní .NET Framework, klepněte na tlačítko Shromáždit informace o přidělení objektu rozhraní **.NET.**

6. (Nepovinné) Klepněte na **tlačítko Také shromažďovat informace o životnosti objektu .NET** ke shromažďování dat o generacích uvolňování paměti, ve kterých byla uvolněna paměť objektu.

     Informace o dalších možnostech, které jsou k dispozici při shromažďování dat paměti .NET, naleznete v [tématu Shromažďování přidělení paměti .NET a dat životnosti](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).

### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Výběr shromažďování dat souběžnosti pomocí vlastností relace výkonu

1. V **Průzkumníku výkonu**klepněte pravým tlačítkem myši na relaci výkonu a potom klepněte na příkaz **Vlastnosti**.

2. Na **stránkách vlastností**klepněte na **tlačítko Obecné**.

3. Klepněte na **položku Souběžnost**.

## <a name="see-also"></a>Viz také

[Konfigurace relací](../profiling/configuring-performance-sessions.md)
výkonu[Principy vlastností](../profiling/understanding-sampling-data-values.md)
dat vzorkování[výkonu](../profiling/performance-session-properties.md)
