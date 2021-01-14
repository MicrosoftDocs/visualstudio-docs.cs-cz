---
title: Analýza využití paměti
description: Seznamte se s nástroji, které můžete použít k vyhledání nevrácené paměti a neefektivního využití paměti, nástrojů, jako je například nástroj využití paměti a nástroj pro přidělování objektů rozhraní .NET.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 675636b7abca10fb2f9f1898d753155235830f86
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205720"
---
# <a name="analyze-memory-usage"></a>Analýza využití paměti

Pokud chcete najít nevracení paměti a neefektivní využití paměti, můžete použít nástroje, jako je nástroj pro diagnostiku využití paměti integrovaného ladicího programu nebo nástroje v profileru výkonu, jako je nástroj pro přidělování objektů .NET a nástroj pro využití paměti po porážce.

Nástroj využití paměti umožňuje provést jeden nebo více *snímků* spravované a nativní haldy paměti. Můžete shromažďovat snímky aplikací .NET, ASP.NET, C++ nebo smíšeného režimu (.NET a nativní). Nástroj **využití paměti** může běžet na otevřeném projektu sady Visual Studio, na nainstalované Microsoft Store aplikaci nebo připojeném ke spuštěné aplikaci nebo procesu. Nástroj **využití paměti** můžete spustit s laděním nebo bez něj. Další informace najdete v tématu [spuštění nástrojů pro profilaci pomocí ladicího programu nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md). V ladicím programu můžete zapnout nebo vypnout profilaci paměti a zobrazit rozpis využití paměti pro jednotlivé objekty. Můžete zobrazit výsledky využití paměti při pozastavení provádění, například na zarážce.

Vývojáři rozhraní .NET mohou volit buď mezi nástrojem pro přidělování objektů rozhraní .NET nebo nástrojem [využití paměti](../profiling/memory-usage.md) .

- [Nástroj pro přidělování objektů .NET](../profiling/dotnet-alloc-tool.md) vám pomůže identifikovat vzory přidělení a anomálie v kódu .NET a pomáhá identifikovat běžné problémy s uvolňováním paměti. Tento nástroj se spouští jenom jako nástroj po porážce. Tento nástroj můžete spustit na místních nebo vzdálených počítačích.
- [Nástroj využití paměti](../profiling/memory-usage-without-debugging2.md) je užitečný při identifikaci nevracení paměti, které nejsou obvykle běžné v aplikacích .NET. Pokud potřebujete používat funkce ladicího programu při kontrole paměti, jako je například krokování prostřednictvím kódu, doporučuje se nástroj [pro integrované využití paměti ladicího programu](../profiling/memory-usage.md) .

Vývojáři C++ můžou použít nástroj pro využití paměti integrované ladicího programu nebo bez ladicího programu.

- [Analýza využití paměti pomocí ladicího programu](../profiling/memory-usage.md)
- [Analýza využití paměti bez ladicího programu](../profiling/memory-usage-without-debugging2.md)

Nástroje pro profilaci bez ladicího programu můžete používat se systémem Windows 7 nebo novějším. Pro spuštění nástrojů pro profilaci pomocí ladicího programu (**diagnostické nástroje** okno) se vyžaduje systém Windows 8 nebo novější.

## <a name="blogs-and-videos"></a>Blogy a videa

[Analyzovat procesor a paměť během ladění](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: profilace paměti v Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
