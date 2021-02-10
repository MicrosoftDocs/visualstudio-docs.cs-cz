---
title: Graf využití procesoru | Microsoft Docs
description: Přečtěte si o grafu využití procesoru, který zobrazuje úroveň využití v aplikaci v průběhu času. Využití se zobrazuje jako počet používaných logických jader.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5ec57ac6601557bf644c818822fea70a296fd0c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956006"
---
# <a name="cpu-utilization-graph"></a>Graf využití procesoru
Graf využití procesoru zobrazuje úroveň využití v aplikaci v průběhu času. Osa X představuje dobu trvání trasování a osa y představuje počet logických jader v systému. Graf nezobrazuje, které konkrétní jádro je v určitou dobu aktivní. Například pokud jsou dvě jádra spuštěny na úrovni 50% kapacity za dané časové období, pak toto zobrazení ukazuje, že je využíváno jedno logické jádro.

## <a name="cpu-utilization-graph-colors"></a>Barvy grafu využití CPU

- Zelená označuje využití logických jader v systému aktuálním procesem.

- Světle šedá označuje využití logických jader jinými procesy v systému. Vysoké procento světle šedé v grafu CPU znamená, že systém je silně načítán jinými procesy a že je možné, že je váš proces přerušený. Chcete-li snížit spotřebu logických jader jinými procesy, snižte počet jejich spuštění v systému.

- Tmavě šedá označuje spotřebu logických jader v rámci procesu systému. To není možné přímo ovládat, ale je užitečné znát, kdy se vyskytuje, protože může ovlivnit dostupnost logických jader pro váš proces.

- Bílá označuje dostupnost nevyužitých logických jader v systému. Tyto jádra jsou k dispozici pro váš proces, pokud můžete najít více příležitostí pro paralelismus.

## <a name="see-also"></a>Viz také
- [Zobrazení využití](../profiling/utilization-view.md)
- [Průměrné využití procesoru](../profiling/average-cpu-utilization.md)