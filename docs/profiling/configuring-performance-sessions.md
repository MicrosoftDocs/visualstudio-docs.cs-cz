---
title: Konfigurace relací výkonu | Microsoft Docs
description: Naučte se, jak nakonfigurovat Nástroje pro profilaci sady Visual Studio tak, aby shromáždila požadovaná data výkonu. Tento článek obsahuje seznam běžných úloh a obsahuje odkazy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 52e2575e034dbabe5e380857edd95e4bc46f56d2
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721005"
---
# <a name="configure-performance-sessions"></a>Konfigurace výkonnostních relací
Pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci můžete shromažďovat širokou škálu údajů o výkonu pro velký počet typů aplikací. V této části se dozvíte, jak pomocí Průvodce výkonem a vlastností relace výkonu a cílového binárního souboru nakonfigurovat Nástroje pro profilaci pro shromažďování dat, která vás zajímají. Vlastnosti konfigurace Nástroje pro profilaci lze také použít k řízení množství dat, která jsou shromažďována při spuštění profilace. Další informace najdete v tématu [řízení sběru dat](../profiling/controlling-data-collection.md).

> [!NOTE]
> V mnoha případech je používání výchozích vlastností Průvodce výkonem účinným způsobem shromažďování dat profilace. Další informace najdete v tématu [Příručka pro začátečníky k profilaci výkonu](../profiling/beginners-guide-to-performance-profiling.md) a [Začínáme](../profiling/getting-started-with-performance-tools.md).

## <a name="common-tasks"></a>Běžné úkoly

| Úkol | Související obsah |
| - | - |
| **Nastavte základní možnosti profilace:** Měli byste nakonfigurovat [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , aby používaly Microsoft symbol server. Tím zajistíte, že budete mít přístup k symbolům, jako jsou funkce a názvy parametrů, pro aktuální verzi Windows a další aplikace Microsoftu. Můžete také zadat další obecné možnosti před spuštěním relace profilování, například oprávnění systému pro nástroje pro profilaci a názvy datových souborů profilování. | -   [Postupy: odkazování na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Postupy: serializace informací o symbolu](../profiling/how-to-serialize-symbol-information.md)<br />-   [Postupy: nastavení aktuální relace](../profiling/how-to-set-the-current-session.md)<br />-   [Postupy: nastavení oprávnění](../profiling/how-to-set-permissions.md)<br />-   [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md) |
| **Zadejte data, která chcete shromažďovat:** Postupy, které slouží ke konfiguraci relace profilování, závisí na typu cílové aplikace, kterou chcete profilovat, a na typu údajů o výkonu, které chcete shromáždit. | -   [Postupy: výběr metod shromažďování](../profiling/how-to-choose-collection-methods.md)<br />-   [Shromažďování statistik výkonu pomocí vzorkování](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Shromažďování dat o alokaci paměti a době života .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Postupy: profilování kódu JavaScriptu na webových stránkách](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Shromažďování dat o souběžnosti vláken a procesů](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Shromažďování dalších dat o výkonu](../profiling/collecting-additional-performance-data.md) |
| **Nastavit upřesňující možnosti konfigurace:** Při profilování .NET Framework aplikací, které načítají více verzí modulu CLR (Common Language Runtime), můžete určit, která verze se má profilovat. Pokud máte více souborů. exe v relaci výkonu, můžete nastavit pořadí spouštění binárních souborů. | -   [Postupy: určení modulu runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Postupy: Určení binárního souboru ke spuštění](../profiling/how-to-specify-the-binary-to-start.md) |

## <a name="related-sections"></a>Související oddíly
- [Řízení shromažďování dat](../profiling/controlling-data-collection.md)

## <a name="see-also"></a>Viz také
- [Prohlížeč výkonu](../profiling/performance-explorer.md)
