---
title: Analýza využití paměti
description: Seznamte se s nástroji, které můžete použít k vyhledání nevrácené paměti a neefektivnímu využití paměti, o nástrojích, jako je využití paměti a nástroj pro přidělování objektů .NET.
ms.custom: SEO-VS-2020
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a6af0cd98e69a3c43ba70f5609567243e6285201
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387967"
---
# <a name="analyze-memory-usage"></a>Analýza využití paměti

K vyhledání nevrácené paměti a neefektivnímu využití paměti můžete použít nástroje, jako je například diagnostický nástroj využití paměti integrovaný do ladicího programu nebo nástroje v nástroji Profiler výkonu, jako je například nástroj pro přidělování objektů .NET a nástroj pro postnámální využití paměti.

Nástroj Využití paměti umožňuje pořovat jeden nebo *více* snímků haldy spravované a nativní paměti. Můžete shromažďovat snímky aplikací .NET, ASP.NET, C++ nebo aplikací ve smíšeném režimu (.NET a nativní). Nástroj **Využití paměti** lze spustit v otevřeném Visual Studio, v nainstalované aplikaci Microsoft Store nebo připojené ke spuštěné aplikaci nebo procesu. Nástroj Využití paměti můžete spustit **s** laděním nebo bez něj. Další informace najdete v tématu [Spuštění nástrojů pro profilaci s ladicím programem nebo bez něj.](../profiling/running-profiling-tools-with-or-without-the-debugger.md) V ladicím programu můžete profilaci paměti zapnout a vypnout a zobrazit rozpis využití paměti pro každý objekt. Při pozastavení provádění můžete zobrazit výsledky využití paměti, například na zarážce.

Vývojáři .NET si mohou vybrat mezi nástrojem pro přidělování objektů .NET nebo [nástrojem využití](../profiling/memory-usage.md) paměti.

- Nástroj [pro přidělování objektů .NET](../profiling/dotnet-alloc-tool.md) pomáhá identifikovat vzory přidělování a anomálie v kódu .NET a pomáhá identifikovat běžné problémy s uvolňováním paměti. Tento nástroj běží pouze jako postnámední nástroj. Tento nástroj můžete spustit na místních nebo vzdálených počítačích.
- Nástroj [Využití paměti je](../profiling/memory-usage-without-debugging2.md) užitečný při identifikaci nevrácené paměti, které nejsou v aplikacích .NET obvykle běžné. Pokud při kontrole paměti potřebujete použít funkce ladicího programu, [](../profiling/memory-usage.md) například krokování kódu, doporučuje se nástroj využití paměti integrovaný do ladicího programu.

Vývojáři jazyka C++ mohou použít buď nástroj využití paměti integrovaný do ladicího programu, nebo bez ladicího programu.

- [Analýza využití paměti pomocí ladicího programu](../profiling/memory-usage.md)
- [Analýza využití paměti bez ladicího programu](../profiling/memory-usage-without-debugging2.md)

Nástroje pro profilaci můžete používat bez ladicího programu se systémem Windows 7 a novějším. Windows 8 a novější se vyžaduje ke spuštění nástrojů pro profilaci pomocí ladicího programu (**Diagnostické nástroje** okno).

## <a name="blogs-and-videos"></a>Blogy a videa

[Analýza procesoru a paměti během ladění](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: Profilace paměti v Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
