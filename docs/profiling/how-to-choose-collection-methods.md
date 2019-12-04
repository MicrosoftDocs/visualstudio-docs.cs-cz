---
title: 'Postupy: výběr metod shromažďování | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74776342"
---
# <a name="how-to-choose-collection-methods"></a>Postupy: výběr metod shromažďování

Visual Studio Nástroje pro profilaci podporuje tři metody shromažďování údajů o výkonu: vzorkování, instrumentace a souběžnost. K shromažďování dat o přidělování a životnosti paměti .NET můžete použít také metodu vzorkování nebo instrumentace.

Vlastnost **Metoda** relace výkonu můžete použít k určení nejvhodnější metody shromažďování pro vaši aplikaci. Můžete nastavit metodu shromažďování z Průvodce výkonem, Prohlížeč výkonu nebo na stránkách vlastností relace výkonu. Pokud používáte nástroje příkazového řádku, přečtěte si další informace v tématu [profilace z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md) .

## <a name="performance-wizard"></a>Průvodce výkonu

### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Výběr metody kolekce pomocí Průvodce výkonem

- Na první stránce průvodce vyberte jednu z následujících možností:

| Možnost | Popis |
|----------------------------| - |
| **Vzorkování procesoru** | Shromažďuje statistiky aplikací, které jsou užitečné při počáteční analýze a při analýze problémů s využitím procesoru. |
| **Instrumentace** | Shromažďuje detailní časová data, která jsou užitečná pro cílené analýzy a pro analýzu problémů s výkonem vstupu a výstupu. |
| **Alokace paměti .NET** | Shromažďuje .NET Framework data o přidělování paměti pomocí metody profilace vzorkování. |
| **Souběžnost** | Shromažďuje data o obsahu kolizí číselných prostředků. |

## <a name="performance-explorer"></a>Prohlížeč výkonu

### <a name="to-select-a-collection-method-using-performance-explorer"></a>Výběr metody kolekce pomocí Prohlížeč výkonu

1. Na panelu nástrojů **prohlížeč výkonu** klikněte na šipku vedle rozevíracího seznamu **Metoda** .

2. Klikněte na metodu shromažďování, kterou dáváte přednost.

## <a name="performance-session-property-pages"></a>Stránky vlastností výkonnostní relace

### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Výběr metody vzorkování nebo instrumentace pomocí vlastností výkonnostní relace

1. V **prohlížeč výkonu**vyberte relaci výkonu.

     Název souboru výkonnostní relace má. rozšíření *psess* .

2. Klikněte pravým tlačítkem na výkonnostní relaci a pak klikněte na **vlastnosti**.

3. Na **stránkách vlastností**klikněte na **Obecné**.

4. Klikněte na metodu shromažďování, kterou dáváte přednost.

    - Informace o dalších možnostech, které jsou k dispozici při shromažďování dat vzorkování, najdete v tématu [shromažďování statistik výkonu pomocí vzorkování](../profiling/collecting-performance-statistics-by-using-sampling.md) .

    - Informace o dalších možnostech, které jsou k dispozici při shromažďování dat vzorkování, najdete v tématu [shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).

### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Výběr shromažďování dat paměti .NET pomocí vlastností výkonnostní relace

1. V **prohlížeč výkonu**vyberte relaci výkonu.

     Název souboru relace výkonu má příponu. psess.

2. Klikněte pravým tlačítkem na výkonnostní relaci a pak klikněte na **vlastnosti**.

3. Na **stránkách vlastností**klikněte na **Obecné**.

4. Klikněte na **vzorkování** nebo **instrumentace**.

5. Kliknutím na **shromáždit informace o přidělení objektů .NET Shromážděte informace** o velikosti a počtu přidělení .NET Framework objektů.

6. Volitelné Klikněte **také na shromažďovat informace o životnosti objektů .NET** , abyste mohli shromažďovat data o generacích uvolňování paměti, ve kterých byla paměť objektu uvolněna.

     Informace o dalších možnostech, které jsou k dispozici při shromažďování dat o paměti .NET, najdete v tématu [shromažďování dat o přidělení paměti .NET a době života](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).

### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Výběr shromažďování dat souběžnosti pomocí vlastností výkonnostní relace

1. V **prohlížeč výkonu**klikněte pravým tlačítkem na relaci výkonu a pak klikněte na **vlastnosti**.

2. Na **stránkách vlastností**klikněte na **Obecné**.

3. Klikněte na **souběžnost**.

## <a name="see-also"></a>Viz také:

[Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)
[porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)
[vlastností výkonnostní relace](../profiling/performance-session-properties.md)
