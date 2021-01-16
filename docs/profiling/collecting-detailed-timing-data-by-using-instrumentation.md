---
title: Shromažďování podrobných dat časování pomocí instrumentace
description: Použijte metodu instrumentace Nástroje pro profilaci pro podrobné informace o časování oddílu kódu a pochopení dopadu vstupně-výstupních operací.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 17c569a9f5a50b769af0881d47fe810afe18058e
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533846"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Shromažďování podrobných dat časování pomocí instrumentace
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Metoda instrumentace nástroje pro profilaci vloží kód profilace do kopie modulu. Kód zaznamenává každé zadání, ukončení a volání funkce v modulu během běhu profilace. Metoda instrumentace je užitečná pro shromažďování podrobných informací o časování oddílu kódu a pro porozumění dopadu vstupních a výstupních operací na výkon aplikace.

 Metodu instrumentace můžete určit pomocí jednoho z následujících postupů:

- Na první stránce průvodce profilace vyberte **instrumentace**.

- Na panelu nástrojů **prohlížeč výkonu** v seznamu **Metoda** klikněte na **instrumentace**.

- Na stránce **Obecné** v dialogovém okně Vlastnosti pro relaci výkonu vyberte **instrumentace**.

## <a name="common-tasks"></a>Běžné úkoly
 Další možnosti můžete zadat v dialogovém okně **stránky vlastností** _relace výkonu_ v relaci výkonu. Chcete-li otevřít toto dialogové okno:

- V **prohlížeč výkonu** klikněte pravým tlačítkem myši na název relace výkonu a pak klikněte na **vlastnosti**.

  Úlohy v následující tabulce popisují možnosti, které můžete zadat v dialogovém okně **stránky vlastností** _relace výkonu_ při profilaci pomocí metody instrumentace.

|Úkol|Související obsah|
|----------|---------------------|
|Na stránce **Obecné** přidejte data o přidělování paměti .NET a životnosti a zadejte podrobnosti o pojmenování generovaného souboru dat profilování (. vsp).|-   [Shromažďování dat o alokaci paměti a době života .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
|Pokud máte v řešení více projektů. exe, na **spouštěcí** stránce. Zadejte aplikaci, kterou chcete spustit, a jejich počáteční pořadí.|-   [Postupy: Určení binárního souboru ke spuštění](../profiling/how-to-specify-the-binary-to-start.md)|
|Na stránce **binární soubory** zadejte umístění pro instrumentované kopie modulů. Ve výchozím nastavení jsou původní binární soubory přesunuty do zálohovací složky.|-   [Postupy: přemístění instrumentních binárních souborů](../profiling/how-to-relocate-instrumented-binaries.md)|
|Na stránce **interakce vrstev** přidejte data volání ADO.NET do běhu profilace.|-   [Shromáždit data interakce vrstev](../profiling/collecting-tier-interaction-data.md)|
|Na stránce **instrumentace** vylučte z profilace malé funkce, aby se snížila režie profilace, kód javascriptu v ASP.NET webové stránky a aby se příkazy spouštěly na příkazovém řádku před a po procesu instrumentace.|-   [Postupy: vyloučení nebo zahrnutí krátkých funkcí z instrumentace](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Postupy: profilování kódu JavaScriptu na webových stránkách](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Postupy: určení příkazů před a po instrumentaci](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Na stránce **čítače CPU** zadejte jeden nebo více čítačů výkonu procesoru, které chcete přidat k datům profilace.|-   [Postupy: shromažďování dat čítačů procesoru](../profiling/how-to-collect-cpu-counter-data.md)|
|Na stránce **události systému Windows** vyberte jednu nebo více událostí trasování událostí pro Windows (ETW), které se mají shromažďovat s daty vzorkování.|-   [Postupy: shromažďování dat trasování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na stránce **čítače systému Windows** zadejte jeden nebo více čítačů výkonu operačního systému, které mají být přidány do dat profilování jako značky.|-   [Postupy: shromažďování dat čítače Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stránce **Upřesnit** určete další možnosti, které chcete předat programu VSInstr instrumentace, například možnosti pro zahrnutí nebo vyloučení určitých funkcí.|-   [Postupy: určení dalších možností instrumentace](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Postupy: omezení instrumentace na konkrétní funkce](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
