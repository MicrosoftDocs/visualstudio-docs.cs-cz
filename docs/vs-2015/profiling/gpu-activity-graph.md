---
title: Graf aktivity GPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4546c3be480349f3e2cb36f483fa8711bc2ac49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434212"
---
# <a name="gpu-activity-graph"></a>Graf aktivity GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Graf aktivity GPU v Vizualizér souběžnosti zobrazuje úroveň aktivity rozhraní DirectX v systému podle počtu používaných modulů rozhraní DirectX v čase.  Graf nezobrazuje, které konkrétní stroje byly použity.  Modul se považuje za používaný, pokud zpracovává veškerou práci GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Barvy grafu aktivity GPU  
 Zelená označuje, že se v rámci aktuálního procesu spotřebují moduly DirectX.  
  
 Světlá šedá znamená, že se v systému využije modul DirectX pro jiné procesy. Chcete-li snížit spotřebu rozhraní DirectX pomocí jiných procesů, snižte počet dalších procesů spuštěných v systému.  
  
 Bílá označuje dostupnost nepoužívaných modulů DirectX v systému. Tyto moduly jsou k dispozici pro váš proces, pokud můžete najít více příležitostí k jejich zneužití. Některé moduly lze použít pouze pro konkrétní druhy úkolů.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení využití](../profiling/utilization-view.md)
