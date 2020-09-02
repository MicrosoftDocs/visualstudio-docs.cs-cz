---
title: Graf využití procesoru | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62552873"
---
# <a name="cpu-utilization-graph"></a>Graf využití procesoru
Graf využití procesoru zobrazuje úroveň využití v aplikaci v průběhu času. Osa X představuje dobu trvání trasování a osa y představuje počet logických jader v systému. Graf nezobrazuje, které konkrétní jádro je v určitou dobu aktivní. Například pokud jsou dvě jádra spuštěny na úrovni 50% kapacity za dané časové období, pak toto zobrazení ukazuje, že je využíváno jedno logické jádro.

## <a name="cpu-utilization-graph-colors"></a>Barvy grafu využití CPU

- Zelená označuje využití logických jader v systému aktuálním procesem.

- Světle šedá označuje využití logických jader jinými procesy v systému. Vysoké procento světle šedé v grafu CPU znamená, že systém je silně zavedený jinými procesy a že váš proces bude pravděpodobně předem přerušené. Chcete-li snížit spotřebu logických jader jinými procesy, snižte počet jejich spuštění v systému.

- Tmavě šedá označuje spotřebu logických jader v rámci procesu systému. To není možné přímo ovládat, ale je užitečné znát, kdy se vyskytuje, protože může ovlivnit dostupnost logických jader pro váš proces.

- Bílá označuje dostupnost nevyužitých logických jader v systému. Tyto jádra jsou k dispozici pro váš proces, pokud můžete najít více příležitostí pro paralelismus.

## <a name="see-also"></a>Viz také
- [Zobrazení využití](../profiling/utilization-view.md)
- [Průměrné využití procesoru](../profiling/average-cpu-utilization.md)