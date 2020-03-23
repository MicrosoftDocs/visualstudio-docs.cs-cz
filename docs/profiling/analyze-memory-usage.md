---
title: Analýza využití paměti
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ddb082bf2451759be239d5c16404e82bcd84733
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77578163"
---
# <a name="analyze-memory-usage"></a>Analýza využití paměti

chcete-li najít nevracení paměti a neefektivní využití paměti, můžete použít nástroje, jako je například ladicí program integrované využití paměti diagnostický nástroj nebo nástroje v profileru výkonu, jako je například nástroj pro alokaci objektů .NET a posmrtné využití paměti. Nástroj využití paměti umožňuje pořizovat jeden nebo více *snímků* spravované a nativní paměti haldy. Můžete shromažďovat snímky aplikací .NET, ASP.NET, nativní nebo smíšený režim (.NET a nativní). 

Nástroj **Využití paměti** lze spustit v otevřeném projektu Sady Visual Studio, v nainstalované aplikaci Microsoft Store nebo připojenéke spuštěné aplikaci nebo procesu. Nástroj můžete spustit na místních nebo vzdálených počítačích nebo na simulátoru nebo emulátoru. Další informace naleznete [v tématu Spuštění nástrojů profilování s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Nástroj Využití **paměti** můžete spustit s laděním nebo bez něj. V ladicím programu můžete zapínat a vypínat profilování paměti a zobrazit rozdělení využití paměti na objekt. Výsledky využití paměti můžete zobrazit při pozastavení provádění, například v zarážky.

Nástroj **pro alokaci objektů .NET** je spuštěn pouze jako nástroj po smrti.

Podrobné pokyny, které popisují použití nástrojů pro analýzu paměti, naleznete v tématu [Analýza využití paměti](../profiling/memory-usage.md) a nástroje pro [alokaci objektů .NET](../profiling/dotnet-alloc-tool.md).

Můžete použít profilování nástroje bez ladicího programu se systémem Windows 7 a novější. Windows 8 a novější je nutné spustit profilování nástroje s ladicím programem **(Diagnostické nástroje** okna).

## <a name="blogs-and-videos"></a>Blogy a videa

[Analýza procesoru a paměti při ladění](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: Profilování paměti ve Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
- [Analýza využití paměti bez ladicího programu](../profiling/memory-usage-without-debugging2.md)
