---
title: Graf aktivity GPU | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5734b9eb1b4307f7c32dcb8a170f7c6c571f46ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969563"
---
# <a name="gpu-activity-graph"></a>Graf aktivity GPU
Graf aktivity GPU v vizualizéru souběžnosti zobrazuje úroveň aktivity DirectX v systému měřenou počtem motorů DirectX, které se v průběhu času používají.  Graf neukazuje, které konkrétní motory byly použity.  Motor se považuje za používán, pokud zpracovává jakékoli gpu práce.

## <a name="gpu-activity-graph-colors"></a>Barvy grafu aktivity GPU
 Zelená barva označuje spotřebu motorů DirectX aktuálním procesem.

 Světle šedá označuje spotřebu modulů DirectX u jiných procesů v systému. Chcete-li snížit spotřebu motorů DirectX jinými procesy, snižte počet dalších procesů spuštěných v systému.

 Bílá označuje dostupnost nepoužívaných motorů DirectX v systému. Tyto motory jsou k dispozici pro váš proces, pokud můžete najít více příležitostí k jejich využití. Některé motory lze použít pouze pro určité druhy úkolů.

## <a name="see-also"></a>Viz také
- [Zobrazení využití](../profiling/utilization-view.md)