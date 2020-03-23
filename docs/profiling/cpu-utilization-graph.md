---
title: Graf využití procesoru | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e09526930bf98141ae4f9d4d204b20383763c208
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552873"
---
# <a name="cpu-utilization-graph"></a>Graf využití procesoru
Graf využití procesoru zobrazuje úroveň využití v aplikaci v průběhu času. Osa X představuje dobu trvání trasování a osa y představuje počet logických jader v systému. Graf nezobrazuje, které konkrétní jádro je v daném okamžiku aktivní. Například pokud jsou dvě jádra spuštěna s kapacitou 50 procent pro dané časové období, pak toto zobrazení ukazuje, že se využívá jedno logické jádro.

## <a name="cpu-utilization-graph-colors"></a>Barvy grafu využití procesoru

- Zelená označuje využití logických jader v systému aktuálním procesem.

- Světle šedá označuje využití logických jader jinými procesy v systému. Vysoké procento světle šedé v grafu procesoru znamená, že systém je silně načten jinými procesy a že váš proces je pravděpodobně předepisován. Chcete-li snížit spotřebu logických jader jinými procesy, snižte počet těchto procesů spuštěných v systému.

- Tmavě šedá označuje spotřebu logických jader systémovým procesem. Nelze přímo řídit, ale je užitečné vědět, kdy k němu dochází, protože to může ovlivnit dostupnost logických jader pro váš proces.

- Bílá označuje dostupnost nepoužívaných logických jader v systému. Tato jádra jsou k dispozici pro váš proces, pokud můžete najít více příležitostí pro paralelismus.

## <a name="see-also"></a>Viz také
- [Zobrazení využití](../profiling/utilization-view.md)
- [Průměrné využití procesoru](../profiling/average-cpu-utilization.md)