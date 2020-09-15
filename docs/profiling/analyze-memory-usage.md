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
ms.openlocfilehash: f77fa9087673ff8e9a429caa27318a60f21d4a60
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075441"
---
# <a name="analyze-memory-usage"></a>Analýza využití paměti

Pokud chcete najít nevracení paměti a neefektivní využití paměti, můžete použít nástroje, jako je nástroj pro diagnostiku využití paměti integrovaného ladicího programu nebo nástroje v profileru výkonu, jako je nástroj pro přidělování objektů .NET a nástroj pro využití paměti po porážce.

Nástroj využití paměti umožňuje provést jeden nebo více *snímků* spravované a nativní haldy paměti. Můžete shromažďovat snímky aplikací .NET, ASP.NET, Native nebo smíšeného režimu (.NET a nativní). Nástroj **využití paměti** může běžet na otevřeném projektu sady Visual Studio, na nainstalované Microsoft Store aplikaci nebo připojeném ke spuštěné aplikaci nebo procesu. Nástroj **využití paměti** můžete spustit s laděním nebo bez něj. Další informace najdete v tématu [spuštění nástrojů pro profilaci pomocí ladicího programu nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md). V ladicím programu můžete zapnout nebo vypnout profilaci paměti a zobrazit rozpis využití paměti pro jednotlivé objekty. Můžete zobrazit výsledky využití paměti při pozastavení provádění, například na zarážce.

Nástroj pro **přidělování objektů .NET** vám pomůže identifikovat vzory přidělení a anomálie v kódu .NET. Tento nástroj se spouští jenom jako nástroj po porážce. Tento nástroj můžete spustit na místních nebo vzdálených počítačích.

Podrobné pokyny, které popisují použití nástrojů pro analýzu paměti, najdete v kurzu [Analýza využití paměti](../profiling/memory-usage.md) a [Nástroj pro přidělování objektů .NET](../profiling/dotnet-alloc-tool.md).

Nástroje pro profilaci bez ladicího programu můžete používat se systémem Windows 7 nebo novějším. Pro spuštění nástrojů pro profilaci pomocí ladicího programu (**diagnostické nástroje** okno) se vyžaduje systém Windows 8 nebo novější.

## <a name="blogs-and-videos"></a>Blogy a videa

[Analyzovat procesor a paměť během ladění](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: profilace paměti v Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Viz také

- [Analýza využití paměti bez ladicího programu](../profiling/memory-usage-without-debugging2.md)
- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
