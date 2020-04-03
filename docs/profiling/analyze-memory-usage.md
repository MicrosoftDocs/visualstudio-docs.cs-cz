---
title: Analýza využití paměti
ms.custom: seodec18
ms.date: 03/30/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21522ba32990a850a388bfcf69ab239232a2c23d
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638415"
---
# <a name="analyze-memory-usage"></a>Analýza využití paměti

Chcete-li najít nevracení paměti a neefektivní využití paměti, můžete použít nástroje, jako je například ladicí program integrované využití paměti diagnostický nástroj nebo nástroje v profileru výkonu, jako je například nástroj pro alokaci objektů .NET a posmrtné využití paměti.

Nástroj využití paměti umožňuje pořizovat jeden nebo více *snímků* spravované a nativní paměti haldy. Můžete shromažďovat snímky aplikací .NET, ASP.NET, nativní nebo smíšený režim (.NET a nativní). Nástroj **Využití paměti** lze spustit v otevřeném projektu Sady Visual Studio, v nainstalované aplikaci Microsoft Store nebo připojenéke spuštěné aplikaci nebo procesu. Nástroj Využití **paměti** můžete spustit s laděním nebo bez něj. Další informace naleznete [v tématu Spuštění nástrojů profilování s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md). V ladicím programu můžete zapínat a vypínat profilování paměti a zobrazit rozdělení využití paměti na objekt. Výsledky využití paměti můžete zobrazit při pozastavení provádění, například v zarážky.

Nástroj **pro alokaci objektů .NET** pomáhá identifikovat vzory přidělení a anomálie v kódu .NET. Tento nástroj běží pouze jako post-mortem nástroj. Tento nástroj můžete spustit v místních nebo vzdálených počítačích.

Podrobné pokyny, které popisují použití nástrojů pro analýzu paměti, naleznete v tématu [Analýza využití paměti](../profiling/memory-usage.md) a nástroje pro [alokaci objektů .NET](../profiling/dotnet-alloc-tool.md).

Můžete použít profilování nástroje bez ladicího programu se systémem Windows 7 a novější. Windows 8 a novější je nutné spustit profilování nástroje s ladicím programem **(Diagnostické nástroje** okna).

## <a name="blogs-and-videos"></a>Blogy a videa

[Analýza procesoru a paměti při ladění](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: Profilování paměti ve Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
- [Analýza využití paměti bez ladicího programu](../profiling/memory-usage-without-debugging2.md)
