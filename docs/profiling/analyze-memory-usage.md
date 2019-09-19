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
ms.openlocfilehash: 124b792e134b31a5964c8f202c7870a58bc0878b
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128241"
---
# <a name="analyze-memory-usage"></a>Analýza využití paměti
Použijte integrovaný ladicí program **využití paměti** diagnostický nástroj k vyhledání nevrácené paměti a využití paměti neefektivní. Umožňuje nástroj využití paměti, můžete provést jeden nebo více *snímky* spravovaný a nativní paměti haldy. Můžete shromažďovat snímky aplikací .NET, ASP.NET, nativní nebo smíšený režim (.NET a nativní).

- Jeden snímek pochopit jeho relativní dopad typů objektů na využití paměti a vyhledání kódu vaší aplikace, která používá paměť neefektivně, můžete analyzovat.

- Můžete také porovnat (rozdíl) dvěma snímky vyhledejte oblasti v kódu aplikace, které způsobují využití paměti časem zvětšuje.

Podrobné pokyny najdete v tématu [analýza využití paměti](../profiling/memory-usage.md) kurzu.  V současné době k měření využití paměti pro aplikace .NET Core, musíte použít nástroj s připojeným ladícím nástrojem. Pro další spravované a nativní aplikace, můžete pomocí nástroje s nebo bez ladicí program připojený.

Můžete použít profilovací nástroje bez ladicího programu s Windows 7 a novější. Windows 8 a novější se vyžaduje pro spuštění nástrojů pro profilaci s ladicím programem (**diagnostické nástroje** okno).

## <a name="blogs-and-videos"></a>Blogy a videa

[Analýza využití procesoru a paměti během ladění](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog C++ vizuálu: Profilace paměti v jazyce C++ Visual 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Viz také:

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)