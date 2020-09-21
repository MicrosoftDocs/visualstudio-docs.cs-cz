---
title: Shromažďovat data o době života & pro přidělení paměti .NET
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 1354fb95b543e73a67d19204871f3b79aec9ece9
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809424"
---
# <a name="collect-net-framework-memory-allocation-and-lifetime-data"></a>Shromažďovat data o přidělení a době životnosti .NET Framework paměti

Sada Visual Studio Nástroje pro profilaci podporuje shromažďování .NET Framework přidělování paměti a dat o životnosti objektů, což pomáhá detekovat problémy s výkonem související s pamětí ve vaší aplikaci.

- Data o přidělování paměti .NET zahrnují velikost a počet objektů .NET Framework paměti, které byly přiděleny.

- Data o životnosti objektu zahrnují velikost a počet objektů .NET Framework paměti, které byly získány v třech generacích uvolňování paměti.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Data můžete shromažďovat buď pomocí metody vzorkování, nebo profilace instrumentace.

- Když použijete metodu vzorkování, Profiler sleduje všechna přidělení paměti .NET a objekty, které jsou generovány procesem, který byl spuštěn nebo připojen ke službě.

- Když použijete metodu instrumentace, Profiler sleduje pouze přidělení paměti .NET a objekty, které jsou generovány instrumentované moduly.

> [!IMPORTANT]
> Při shromažďování dat paměti .NET (přidělení, životnosti objektů nebo obou) pomocí metody vzorkování se všechny události vzorkování zadané uživatelem ignorují a k shromažďování dat se použijí příslušné události přidělení paměti.

Pokud povolíte profilování přidělení paměti of.NET, povolíte také zobrazení přidělení. Pokud povolíte profilaci dat životnosti .NET, povolíte také zobrazení životnost objektů. Další informace naleznete v tématu zobrazení [přidělení](../profiling/dotnet-memory-allocations-view.md) a [zobrazení životnosti objektů](../profiling/object-lifetime-view.md).

Informace o tom, jak shromažďovat data paměti .NET pomocí Nástroje pro profilaci nástrojů příkazového řádku, najdete v tématu použití metod paměti .NET ke shromáždění dat o přidělení paměti a životnosti objektů v tématu [použití metod profilace z příkazového řádku](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).

## <a name="to-collect-net-memory-data"></a>Shromažďování dat paměti .NET

1. V **prohlížeč výkonu**klikněte pravým tlačítkem na relaci výkonu a pak klikněte na **vlastnosti**.

2. V dialogovém okně **stránky vlastností** *relace výkonu* klikněte na kartu **Obecné** a zaškrtněte políčko **shromáždit informace o přidělení objektů .NET** .

3. Chcete-li shromažďovat data o životnosti objektů .NET, zaškrtněte políčko **také shromažďovat informace o životnosti objektů .NET** .

## <a name="common-tasks"></a>Běžné úkoly

Další možnosti můžete zadat v dialogovém okně**stránky vlastností** _relace výkonu_v relaci výkonu. Chcete-li otevřít toto dialogové okno:

- V **prohlížeč výkonu**klikněte pravým tlačítkem myši na název relace výkonu a pak klikněte na **vlastnosti**.

Úlohy v následující tabulce popisují možnosti, které můžete zadat v dialogovém okně**stránky vlastností** _relace výkonu_při shromažďování dat paměti .NET.

|Úloha|Související obsah|
|----------|---------------------|
|Na stránce **Obecné** zadejte podrobnosti o pojmenování generovaného souboru dat profilování (. vsp).|- [Shromažďování dat o alokaci paměti a době života .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na stránce **spuštění** vyberte aplikaci, kterou chcete spustit, pokud máte více projektů. exe v rámci vašeho řešení kódu.|- [Shromáždit data interakce vrstev](../profiling/collecting-tier-interaction-data.md)|
|Na stránce **interakce vrstev** přidejte data volání ADO.NET do běhu profilace.|- [Shromáždit data interakce vrstev](../profiling/collecting-tier-interaction-data.md)|
|Na stránce **události systému Windows** zadejte jednu nebo více událostí trasování událostí pro Windows (ETW), které se mají shromažďovat s daty vzorkování.|- [Postupy: shromažďování dat trasování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na stránce **čítače systému Windows** zadejte jeden nebo více čítačů výkonu operačního systému, které mají být přidány do dat profilování jako značky.|- [Postupy: shromažďování dat čítače Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stránce **Upřesnit** určete verzi modulu runtime .NET Framework, který se má profilovat, pokud vaše aplikační moduly používají více verzí. Ve výchozím nastavení je první načtená verze profilovaná.|- [Postupy: určení modulu runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|

## <a name="instrumentation-tasks"></a>Úlohy instrumentace

Úlohy v následující tabulce jsou možnosti v dialogovém okně **stránky vlastností** , které jsou specifické pro profilaci s metodou instrumentace.

|Úloha|Související obsah|
|----------|---------------------|
|Na stránce **binární soubory** zadejte umístění pro instrumentované kopie modulů. Ve výchozím nastavení jsou původní binární soubory přesunuty do zálohovací složky.|- [Postupy: přemístění Instrumentních binárních souborů](../profiling/how-to-relocate-instrumented-binaries.md)|
|Na stránce **instrumentace** vylučte z profilace malé funkce, aby se snížila režie profilace, kód javascriptu v ASP.NET webové stránky a aby se příkazy spouštěly na příkazovém řádku před a po procesu instrumentace.|- [Postupy: vyloučení nebo zahrnutí krátkých funkcí z instrumentace](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />- [Postupy: profilování kódu JavaScriptu na webových stránkách](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />- [Postupy: určení příkazů před a po instrumentaci](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Na stránce **čítače CPU** zadejte jeden nebo více čítačů výkonu procesoru, které chcete přidat k datům profilace.|- [Postupy: shromažďování dat čítačů procesoru](../profiling/how-to-collect-cpu-counter-data.md)|
|Na stránce **Upřesnit** určete další požadované možnosti VSInstr.exe, například možnosti pro zahrnutí nebo vyloučení určitých funkcí. Další informace o možnostech VSInstr najdete v tématu [VSInstr](../profiling/vsinstr.md) .|- [Postupy: určení dalších možností instrumentace](../profiling/how-to-specify-additional-instrumentation-options.md)<br />- [Postupy: omezení instrumentace na konkrétní funkce](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|

## <a name="see-also"></a>Viz také

[Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md) 
 [Postupy: výběr metod shromažďování](../profiling/how-to-choose-collection-methods.md) 
 [Vlastnosti výkonnostní relace](../profiling/performance-session-properties.md)
