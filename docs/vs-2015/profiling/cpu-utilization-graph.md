---
title: Graf využití procesoru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8058995c8ae45c40f202aaa1e788891da3eb985d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180486"
---
# <a name="cpu-utilization-graph"></a>Graf využití procesoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Graf využití procesoru zobrazuje úroveň využití v aplikaci v průběhu času. Osa X představuje dobu trvání trasování a osa y představuje počet logických jader v systému. Graf nezobrazuje, které konkrétní jádro je v určitou dobu aktivní. Například pokud jsou dvě jádra spuštěny na úrovni 50% kapacity za dané časové období, pak toto zobrazení ukazuje, že je využíváno jedno logické jádro.  
  
## <a name="cpu-utilization-graph-colors"></a>Barvy grafu využití CPU  
  
- Zelená označuje využití logických jader v systému aktuálním procesem.  
  
- Světle šedá označuje využití logických jader jinými procesy v systému. Vysoké procento světle šedé v grafu CPU znamená, že systém je silně zavedený jinými procesy a že váš proces bude pravděpodobně předem přerušené. Chcete-li snížit spotřebu logických jader jinými procesy, snižte počet jejich spuštění v systému.  
  
- Tmavě šedá označuje spotřebu logických jader v rámci procesu systému. To není možné přímo ovládat, ale je užitečné znát, kdy se vyskytuje, protože může ovlivnit dostupnost logických jader pro váš proces.  
  
- Bílá označuje dostupnost nevyužitých logických jader v systému. Tyto jádra jsou k dispozici pro váš proces, pokud můžete najít více příležitostí pro paralelismus.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení využití](../profiling/utilization-view.md)   
 [Průměrné využití procesoru](../profiling/average-cpu-utilization.md)
