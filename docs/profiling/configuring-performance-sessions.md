---
title: Konfigurace relací výkonu | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 1bdf1c372ffcb3ad3a0ebf102827565853947e2b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777865"
---
# <a name="configure-performance-sessions"></a>Konfigurace výkonnostních relací
Pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástrojů pro profilování můžete shromažďovat širokou škálu dat o výkonu pro velký počet typů aplikací. Tato část ukazuje, jak používat Průvodce výkonem a vlastnosti relace výkonu a cílový binární konfigurace nástroje profilování shromažďovat data, která vás zajímá. Profilování Nástroje konfigurace vlastnosti lze také určit, kolik dat je shromažďována v profilování spustit. Další informace naleznete v [tématu Řízení shromažďování dat](../profiling/controlling-data-collection.md).

> [!NOTE]
> V mnoha případech je použití výchozích vlastností Průvodce výkonem efektivním způsobem shromažďování dat profilování. Další informace naleznete v [tématu Průvodce začátečníky k profilování výkonu](../profiling/beginners-guide-to-performance-profiling.md) a [začínáme](../profiling/getting-started-with-performance-tools.md).

## <a name="common-tasks"></a>Běžné úkoly

| Úkol | Související obsah |
| - | - |
| **Nastavte základní možnosti profilování:** Měli byste [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] nakonfigurovat použití serveru symbolů společnosti Microsoft. Tím zajistíte, že budete mít přístup k symbolům, jako jsou názvy funkcí a parametrů, pro aktuální verzi systému Windows a dalších aplikací společnosti Microsoft. Před zahájením relace profilování můžete také určit další obecné možnosti, například systémová oprávnění k nástrojům profilování a názvy datových souborů profilování. | -   [Postup: Odkaz na informace o symbolech systému Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Postup: Serializace informací o symbolech](../profiling/how-to-serialize-symbol-information.md)<br />-   [Postup: Nastavení aktuální relace](../profiling/how-to-set-the-current-session.md)<br />-   [Postup: Nastavení oprávnění](../profiling/how-to-set-permissions.md)<br />-   [Postup: Nastavení možností názvu souboru dat o výkonu](../profiling/how-to-set-performance-data-file-name-options.md) |
| **Zadejte data, která chcete shromažďovat:** Postupy, které slouží ke konfiguraci relace profilování závisí na typu cílové aplikace, kterou chcete profilovat, a typu dat o výkonu, které chcete shromažďovat. | -   [Postup: Zvolte metody kolekce](../profiling/how-to-choose-collection-methods.md)<br />-   [Shromážděte statistiky výkonu pomocí vzorkování](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Shromažďování dat přidělení paměti .NET a životnosti](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Shromažďování podrobných časovacích dat pomocí instrumentace](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Postup: Profil javascriptového kódu na webových stránkách](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Shromažďování dat souběžnosti vláken a procesů](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Shromažďování dalších údajů o výkonu](../profiling/collecting-additional-performance-data.md) |
| **Nastavte upřesňující možnosti konfigurace:** Při profilování aplikací rozhraní .NET Framework, které načítají více verzí běžného jazyka run-time (CLR), můžete určit, kterou verzi profilujete. Pokud máte v relaci výkonu více souborů EXE, můžete nastavit pořadí zahájení binárních souborů. | -   [Postup: Určení runtime rozhraní .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Postup: Zadejte binární soubor, který má být zahájen](../profiling/how-to-specify-the-binary-to-start.md) |

## <a name="related-sections"></a>Související oddíly
- [Řízení shromažďování dat](../profiling/controlling-data-collection.md)

## <a name="see-also"></a>Viz také
- [Prohlížeč výkonu](../profiling/performance-explorer.md)
