---
title: Shromažďování podrobných časových dat pomocí instrumentace | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: bfd22edc9bd672a8d82c94a705b523ce7d836169
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779620"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Shromažďování podrobných dat časování pomocí instrumentace
Metoda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instrumentace profilovacích nástrojů vloží profilovací kód do kopie modulu. Kód zaznamenává každou položku, ukončení a volání funkce funkcí v modulu během profilování spustit. Metoda instrumentace je užitečná pro shromažďování podrobných informací o časování o části kódu a pro pochopení dopadu vstupních a výstupních operací na výkon aplikace.

 Metodu instrumentace můžete určit pomocí jednoho z následujících postupů:

- Na první stránce Průvodce profilováním vyberte **instrumentace**.

- Na panelu nástrojů **Průzkumník výkonu** klepněte v seznamu **Metoda** na **položku Instrumentace**.

- Na stránce **Obecné** v dialogovém okně vlastností relace výkonu vyberte **instrumentace**.

## <a name="common-tasks"></a>Běžné úkoly
 Další možnosti můžete zadat v dialogovém okně**Stránky vlastností relace** _výkonu_relace výkonu. Otevření tohoto dialogového okna:

- V **Průzkumníku výkonu**klepněte pravým tlačítkem myši na název relace výkonu a potom klepněte na příkaz **Vlastnosti**.

  Úkoly v následující tabulce popisují možnosti, které můžete zadat v dialogovém okně**Stránky vlastností** _relace výkonu_při profilování pomocí metody instrumentace.

|Úkol|Související obsah|
|----------|---------------------|
|Na stránce **Obecné** přidejte přidělení paměti .NET a data životnosti a zadejte podrobnosti pojmenování pro soubor generateovaných profilování (.vsp).|-   [Shromažďování dat přidělení paměti .NET a životnosti](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Postup: Nastavení možností názvu souboru dat o výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na stránce **Spuštění,** pokud máte více projektů .exe ve vašem solution.specify aplikace spustit a jejich počáteční pořadí.|-   [Postup: Zadejte binární soubor, který má být zahájen](../profiling/how-to-specify-the-binary-to-start.md)|
|Na stránce **Binární soubory** zadejte umístění instrumentovaných kopií modulů. Ve výchozím nastavení jsou původní binární soubory přesunuty do záložní složky.|-   [Postup: Přemístění instrumentovaných binárních souborů](../profiling/how-to-relocate-instrumented-binaries.md)|
|Na stránce **Interakce s vrstvou** přidejte ADO.NET data volání do spuštění profilování.|-   [Shromažďování dat interakce vrstvy](../profiling/collecting-tier-interaction-data.md)|
|Na stránce **Instrumentace** vylučte malé funkce z profilování, abyste snížili režii profilování, profilujte kód Jazyka JavaScript na ASP.NET webových stránkách a zadejte příkazy, které mají být spuštěny na příkazovém řádku před a po procesu instrumentace.|-   [Postup: Vyloučení nebo zahrnutí krátkých funkcí z instrumentace](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Postup: Profil javascriptového kódu na webových stránkách](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Postup: Určení příkazů před a po přístroji](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Na stránce **Čítače procesoru** zadejte jeden nebo více čítačů výkonu procesoru, které chcete přidat k datům profilování.|-   [Jak: shromažďovat data čítače procesoru](../profiling/how-to-collect-cpu-counter-data.md)|
|Na stránce **Události systému Windows** vyberte jednu nebo více událostí trasování událostí pro Windows (ETW), které chcete shromažďovat s vzorkovacími daty.|-   [Postup: Shromažďování trasování událostí pro windows (ETW) data](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na stránce **Čítače systému Windows** zadejte jeden nebo více čítačů výkonu operačního systému, které chcete přidat k datům profilování jako značky.|-   [Postup: Shromažďování dat čítačů systému Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stránce **Upřesnit** zadejte všechny další možnosti, které chcete předat programu instrumentace VSInstr, například možnosti zahrnutí nebo vyloučení určitých funkcí.|-   [Postup: Zadání dalších možností instrumentace](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Postup: Omezení instrumentace na konkrétní funkce](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
