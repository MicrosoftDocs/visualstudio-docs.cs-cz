---
title: Shromažďování statistik výkonu pomocí vzorkování | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772875"
---
# <a name="collect-performance-statistics-by-using-sampling"></a>Shromažďování statistik výkonu pomocí vzorkování

Ve výchozím nastavení visual studio profilování nástroje vzorkování metoda shromažďuje informace o profilování každých 10 000 000 cyklů procesoru (přibližně každou setinu sekundy v počítači 1 GHz). Metoda vzorkování je užitečná pro zjištění problémů s využitím procesoru a je navrhovanou metodou pro spuštění většiny šetření výkonu.

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Metodu vzorkování můžete určit jedním z následujících postupů:

- Na první stránce Průvodce profilováním klepněte na **položku Vzorkování procesoru (doporučeno).**
- Na panelu nástrojů **Průzkumník výkonu** klikněte v seznamu **Metoda** na **položku Vzorkování**.
- Na stránce **Obecné** v dialogovém okně vlastností relace výkonu klepněte na **položku Vzorkování**.

## <a name="common-tasks"></a>Běžné úkoly

Další možnosti můžete zadat v dialogovém okně**Stránky vlastností relace** _výkonu_relace výkonu. Otevření tohoto dialogového okna:

- V **Průzkumníku výkonu**klepněte pravým tlačítkem myši na název relace výkonu a potom klepněte na příkaz **Vlastnosti**.

  Úkoly v následující tabulce popisují možnosti, které můžete zadat v dialogovém okně**Stránky vlastností relace** _výkonu_při profilování pomocí metody vzorkování.

|Úkol|Související obsah|
|----------|---------------------|
|Na stránce **Obecné** přidejte přidělení paměti .NET a shromažďování dat životnosti a zadejte podrobnosti pojmenování pro soubor generovaných profilování (.vsp).|- [Shromažďování dat přidělení paměti .NET a životnosti](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Postup: Nastavení možností názvu souboru dat výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na stránce **Vzorkování** změňte vzorkovací frekvenci, změňte událost vzorkování z cyklů hodin procesoru na jiný čítač výkonu procesoru nebo obojí..|- [Postup: Zvolte vzorkovací události](../profiling/how-to-choose-sampling-events.md)|
|Na stránce **Spuštění** zadejte aplikaci, která má být spuštěna, a počáteční pořadí, pokud máte v řešení kódu více projektů .exe.|- [Shromažďování dat interakce vrstvy](../profiling/collecting-tier-interaction-data.md)|
|Na stránce **Interakce s úrovní** přidejte ADO.NET informace o volání k datům shromážděným při spuštění profilování.|- [Shromažďování dat interakce vrstvy](../profiling/collecting-tier-interaction-data.md)|
|Na stránce **Události systému Windows** zadejte jednu nebo více událostí trasování událostí pro Windows (ETW), které se mají shromažďovat s vzorkovacími daty.|- [Postup: Shromažďování dat sledování událostí pro Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na stránce **Čítače systému Windows** zadejte jeden nebo více čítačů výkonu operačního systému, které chcete přidat k datům profilování jako značky.|- [Postup: Shromažďování dat čítačů systému Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stránce **Upřesnit** zadejte verzi modulu runtime rozhraní .NET Framework do profilu, pokud moduly aplikace používají více verzí. Ve výchozím nastavení je profilována první načtená verze.|- [Postup: Určení běhu rozhraní .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
