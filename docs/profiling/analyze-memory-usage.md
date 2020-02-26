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
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578163"
---
# <a name="analyze-memory-usage"></a>Analýza využití paměti

Pokud chcete najít nevracení paměti a neefektivní využití paměti, můžete použít nástroje, jako je nástroj pro diagnostiku využití paměti integrovaného ladicího programu nebo nástroje v profileru výkonu, jako je nástroj pro přidělování objektů .NET a nástroj pro využití paměti po porážce. Nástroj využití paměti umožňuje provést jeden nebo více *snímků* spravované a nativní haldy paměti. Můžete shromažďovat snímky aplikací .NET, ASP.NET, nativní nebo smíšený režim (.NET a nativní). 

Nástroj **využití paměti** může běžet na otevřeném projektu sady Visual Studio, na nainstalované Microsoft Store aplikaci nebo připojeném ke spuštěné aplikaci nebo procesu. Nástroj můžete spustit na místních nebo vzdálených počítačích nebo na simulátoru nebo emulátoru. Další informace najdete v tématu [spuštění nástrojů pro profilaci pomocí ladicího programu nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Nástroj **využití paměti** můžete spustit s laděním nebo bez něj. V ladicím programu můžete zapnout nebo vypnout profilaci paměti a zobrazit rozpis využití paměti pro jednotlivé objekty. Můžete zobrazit výsledky využití paměti při pozastavení provádění, například na zarážce.

Nástroj pro **přidělování objektů .NET** se spouští jenom jako nástroj po porážce.

Podrobné pokyny, které popisují použití nástrojů pro analýzu paměti, najdete v kurzu [Analýza využití paměti](../profiling/memory-usage.md) a [Nástroj pro přidělování objektů .NET](../profiling/dotnet-alloc-tool.md).

Můžete použít profilovací nástroje bez ladicího programu s Windows 7 a novější. Pro spuštění nástrojů pro profilaci pomocí ladicího programu (**diagnostické nástroje** okno) se vyžaduje systém Windows 8 nebo novější.

## <a name="blogs-and-videos"></a>Blogy a videa

[Analyzovat procesor a paměť během ladění](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog C++ vizuálu: profilace paměti v jazyce C++ Visual 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První pohled na nástroje pro profilaci](../profiling/profiling-feature-tour.md)
- [Analýza využití paměti bez ladicího programu](../profiling/memory-usage-without-debugging2.md)
