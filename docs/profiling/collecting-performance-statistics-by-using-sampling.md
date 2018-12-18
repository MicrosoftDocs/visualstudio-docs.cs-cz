---
title: Shromažďování statistik výkonu pomocí vzorkování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a09253dbeff9adb2bed6ea21545675f343e15974
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836252"
---
# <a name="collect-performance-statistics-by-using-sampling"></a>Shromažďování statistik výkonu pomocí vzorkování

Ve výchozím nastavení Visual Studio nástroje pro profilaci sady metody vzorkování shromažďuje informace o profilování každých 10 000 000 cyklů procesoru (přibližně každých-setiny sekundy v počítači se 1 GHz). Metody vzorkování je užitečné pro vyhledání problémy s využitím procesoru a je navržený způsob spuštění většina vyšetřování výkonu.

> [!NOTE]
> Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Metoda vzorkování můžete zadat pomocí jedné z následujících postupů:

- Klikněte na první stránce průvodce Profilováním, **vzorkování procesoru (doporučeno)**.
- Na **prohlížeč výkonu** nástrojů v **metoda** klikněte na možnost **vzorkování**.
- Na **Obecné** stránky dialogovém okně Vlastnosti relace výkonu můžete kliknout na tlačítko **vzorkování**.

## <a name="common-tasks"></a>Běžné úlohy

Můžete zadat další možnosti v _relace výkonu_**stránky vlastností** dialogovému oknu relace výkonu. Chcete-li otevřít toto dialogové okno:

- V **prohlížeč výkonu**, klikněte pravým tlačítkem na název relace výkonu a potom klikněte na tlačítko **vlastnosti**.

  Úkoly v následující tabulce popisují možnosti, které můžete určit _relace výkonu_**stránky vlastností** dialogové okno při profilování pomocí metody vzorkování.

|Úloha|Související obsah|
|----------|---------------------|
|Na **Obecné** stránce, přidejte alokaci paměti .NET a shromažďování dat životnost a pojmenování detailů generovaného souboru dat profilování (.vsp).|- [Shromažďuje alokaci paměti .NET a Data o životním cyklu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Postupy: nastavení možností názvu datového souboru výkonu](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na **vzorkování** stránce, změna míry vzorkování, změní událost odběru vzorků z hodinových cyklů procesoru na jiný čítač výkonu procesoru nebo obě tyto hodnoty změnit...|- [Postupy: výběr událostí vzorkování](../profiling/how-to-choose-sampling-events.md)|
|Na **spuštění** stránky, zadejte aplikaci, aby začala a na začátek pořadí, pokud máte několik projektů .exe ve vašem kódu řešení.|- [Shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md)|
|Na **interakce vrstev** stránce, přidejte informace o volání ADO.NET na data shromažďovaná v theprofiling spustit.|- [Shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md)|
|Na **události Windows** stránky, zadejte jeden nebo více událostí trasování událostí pro Windows (ETW) pro shromažďování dat prostřednictvím data vzorkování.|- [Postupy: shromažďování trasování událostí pro Windows (ETW) dat.](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na **čítače Windows** stránky, zadejte jeden nebo více čítačů výkonu operačního systému pro přidání do profilových dat. jako značky.|- [Postupy: shromažďování dat čítačů Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na **Upřesnit** stránky, zadejte verzi modulu runtime rozhraní .NET Framework do profilu, pokud vaše aplikace moduly používat více verzí. Standardně je první verze načíst profilována.|- [Postupy: určení modulu Runtime rozhraní .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|