---
title: Shromažďování statistik výkonu pomocí vzorkování | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cbe03f52b31664c59cb7e59d448db7c6b96b6487
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74772875"
---
# <a name="collect-performance-statistics-by-using-sampling"></a>Shromažďování statistik výkonu pomocí vzorkování

Ve výchozím nastavení služba Visual Studio Nástroje pro profilaci vzorkování shromažďuje informace profilování každých 10 000 000 cyklů procesoru (přibližně každé jedno setiny sekundy na počítači s 1 GHz). Metoda vzorkování je užitečná pro hledání problémů s využitím procesoru a je navrhovaná metoda pro spuštění většiny šetření výkonu.

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Metodu vzorkování můžete zadat pomocí jednoho z následujících postupů:

- Na první stránce průvodce profilování klikněte na **vzorkování procesoru (doporučeno)** .
- Na panelu nástrojů **prohlížeč výkonu** v seznamu **Metoda** klikněte na **vzorkování**.
- Na stránce **Obecné** v dialogovém okně Vlastnosti pro relaci výkonu klikněte na **vzorkování**.

## <a name="common-tasks"></a>Běžné úlohy

Další možnosti můžete zadat v dialogovém okně**stránky vlastností** _relace výkonu_v relaci výkonu. Chcete-li otevřít toto dialogové okno:

- V **prohlížeč výkonu**klikněte pravým tlačítkem myši na název relace výkonu a pak klikněte na **vlastnosti**.

  Úlohy v následující tabulce popisují možnosti, které můžete zadat v dialogovém okně**stránky vlastností** _relace výkonu_při profilování pomocí metody vzorkování.

|Úloha|Související obsah|
|----------|---------------------|
|Na stránce **Obecné** přidejte kolekci data alokace a životnosti paměti .NET a zadejte podrobnosti o pojmenování pro vygenerovaný soubor dat profilování (. vsp).|- [shromažďování dat o alokaci paměti a době života .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na stránce **vzorkování** změňte vzorkovací frekvenci, změňte událost vzorkování na časový cyklus procesoru na jiný čítač výkonu procesoru nebo změňte obě.|- [Postupy: výběr událostí vzorkování](../profiling/how-to-choose-sampling-events.md)|
|Na stránce **spuštění** zadejte aplikaci, kterou chcete spustit, a v případě, že máte více projektů. exe ve vašem řešení kódu.|- [shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md)|
|Na stránce **interakce vrstev** přidejte informace o volání ADO.NET do dat shromažďovaných v theprofiling běhu.|- [shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md)|
|Na stránce **události systému Windows** zadejte jednu nebo více událostí trasování událostí pro Windows (ETW), které se mají shromažďovat s daty vzorkování.|- [Postupy: shromáždění dat trasování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na stránce **čítače systému Windows** zadejte jeden nebo více čítačů výkonu operačního systému, které mají být přidány do dat profilování jako značky.|- [Postupy: shromažďování dat čítače Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stránce **Upřesnit** určete verzi modulu runtime .NET Framework, který se má profilovat, pokud vaše aplikační moduly používají více verzí. Ve výchozím nastavení je první načtená verze profilovaná.|- [Postupy: určení modulu Runtime .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
