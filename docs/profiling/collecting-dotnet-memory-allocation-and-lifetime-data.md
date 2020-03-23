---
title: Shromažďování dat o přidělení paměti .NET a životnosti | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 6a8c5d431b7be54c4c5bc1a1c37619deb67de751
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779581"
---
# <a name="collect-net-memory-allocation-and-lifetime-data"></a>Shromažďování dat o alokaci paměti a době platnosti objektů .NET

Nástroje profilování sady Visual Studio podporují kolekci dat o přidělení paměti .NET a životnosti objektu, což vám pomůže zjistit problémy s výkonem související s pamětí ve vaší aplikaci.

- Data o přidělení paměti .NET zahrnují velikost a počet paměťových objektů rozhraní .NET Framework, které byly přiděleny.

- Data životnosti objektu zahrnuje velikost a počet objektů paměti rozhraní .NET Framework, které byly uvolněny ve třech generacích uvolňování paměti.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Data můžete shromažďovat pomocí vzorkování nebo metody profilování instrumentace.

- Při použití metody vzorkování profiler sleduje všechna přidělení paměti .NET a objekty, které jsou generovány procesem, který byl spuštěn nebo připojen k.

- Při použití metody instrumentace profiler sleduje pouze ty přidělení paměti .NET a objekty, které jsou generovány instrumentované moduly.

> [!IMPORTANT]
> Při shromažďování dat paměti .NET (přidělení, životnost objektu nebo obojí) pomocí metody vzorkování jsou ignorovány všechny uživatelem zadané vzorkovací události a příslušné události přidělení paměti se používají ke shromažďování dat.

Pokud povolíte profilování of.NET přidělení paměti, povolíte také zobrazení přidělení. Pokud povolíte profilování dat životnosti rozhraní .NET, povolíte také zobrazení životnosti objektů. Další informace naleznete v [tématu Zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md) a [Zobrazení pocelou dobu životnosti objektu](../profiling/object-lifetime-view.md).

Informace o shromažďování dat paměti rozhraní .NET pomocí nástrojů příkazového řádku Nástroje profilování naleznete v tématu Použití metod paměti .NET ke shromažďování přidělení paměti a dat životnosti objektu v [části Použití metod profilování z příkazového řádku](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).

## <a name="to-collect-net-memory-data"></a>Shromažďování dat paměti .NET

1. V **Průzkumníku výkonu**klepněte pravým tlačítkem myši na relaci výkonu a potom klepněte na příkaz **Vlastnosti**.

2. V dialogovém okně **Stránky vlastností relace** *výkonu* klepněte na kartu **Obecné** a zaškrtněte políčko Shromáždit informace o **přidělení objektu .NET.**

3. Chcete-li shromažďovat data životnosti objektu .NET, zaškrtněte políčko **Také shromažďovat informace o životnosti objektu .NET.**

## <a name="common-tasks"></a>Běžné úkoly

Další možnosti můžete zadat v dialogovém okně**Stránky vlastností relace** _výkonu_relace výkonu. Otevření tohoto dialogového okna:

- V **Průzkumníku výkonu**klepněte pravým tlačítkem myši na název relace výkonu a potom klepněte na příkaz **Vlastnosti**.

Úkoly v následující tabulce popisují možnosti, které můžete zadat v dialogovém okně**Stránky vlastností** _relace výkonu_při shromažďování dat paměti .NET.

|Úkol|Související obsah|
|----------|---------------------|
|Na stránce **Obecné** zadejte podrobnosti pojmenování pro soubor generateovaných profilování (.vsp).|- [Shromažďování dat přidělení paměti .NET a životnosti](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Postup: Nastavení možností názvu souboru dat o výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na stránce **Spuštění** zvolte aplikaci, která se má spustit, pokud máte v řešení kódu více projektů .exe.|- [Shromažďování dat interakce vrstvy](../profiling/collecting-tier-interaction-data.md)|
|Na stránce **Interakce s vrstvou** přidejte ADO.NET data volání do spuštění profilování.|- [Shromažďování dat interakce vrstvy](../profiling/collecting-tier-interaction-data.md)|
|Na stránce **Události systému Windows** zadejte jednu nebo více událostí trasování událostí pro Windows (ETW), které se mají shromažďovat s vzorkovacími daty.|- [Postup: Shromažďování dat sledování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na stránce **Čítače systému Windows** zadejte jeden nebo více čítačů výkonu operačního systému, které chcete přidat k datům profilování jako značky.|- [Postup: Shromažďování dat čítačů systému Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stránce **Upřesnit** zadejte verzi modulu runtime rozhraní .NET Framework do profilu, pokud moduly aplikace používají více verzí. Ve výchozím nastavení je profilována první načtená verze.|- [Postup: Určení runtime rozhraní .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|

## <a name="instrumentation-tasks"></a>Instrumentační úkoly

Úkoly v následující tabulce jsou možnosti v dialogovém **okně Stránky vlastností,** které jsou specifické pro profilování s metodou instrumentace.

|Úkol|Související obsah|
|----------|---------------------|
|Na stránce **Binární soubory** zadejte umístění instrumentovaných kopií modulů. Ve výchozím nastavení jsou původní binární soubory přesunuty do záložní složky.|- [Postup: Přemístění instrumentovaných binárních souborů](../profiling/how-to-relocate-instrumented-binaries.md)|
|Na stránce **Instrumentace** vylučte malé funkce z profilování, abyste snížili režii profilování, profilujte kód Jazyka JavaScript na ASP.NET webových stránkách a zadejte příkazy, které mají být spuštěny na příkazovém řádku před a po procesu instrumentace.|- [Postup: Vyloučení nebo zahrnutí krátkých funkcí z instrumentace](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />- [Postup: Profil javascriptového kódu na webových stránkách](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />- [Postup: Určení příkazů před a po přístrojové desce](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Na stránce **Čítače procesoru** zadejte jeden nebo více čítačů výkonu procesoru, které chcete přidat k datům profilování.|- [Postup: Shromažďování dat čítače procesoru](../profiling/how-to-collect-cpu-counter-data.md)|
|Na stránce **Upřesnit** zadejte všechny další požadované možnosti vsouborných rámci VSInstr.exe, například možnosti zahrnutí nebo vyloučení určitých funkcí. Další informace o možnostech VSInstr naleznete v tématu [VSInstr](../profiling/vsinstr.md)|- [Postup: Zadání dalších možností instrumentace](../profiling/how-to-specify-additional-instrumentation-options.md)<br />- [Postup: Omezení instrumentace na konkrétní funkce](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|

## <a name="see-also"></a>Viz také

[Konfigurace relací](../profiling/configuring-performance-sessions.md)
výkonu[Postup: Volba metod](../profiling/how-to-choose-collection-methods.md)
kolekce[Vlastnosti relace výkonu](../profiling/performance-session-properties.md)
