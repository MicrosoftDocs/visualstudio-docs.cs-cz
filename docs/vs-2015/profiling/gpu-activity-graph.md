---
title: Graf aktivity GPU | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ba74ac314710b1202f13373685ddbdda0df0f6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791121"
---
# <a name="gpu-activity-graph"></a>Graf aktivity GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Graf aktivity GPU ve vizualizátoru souběžnosti zobrazí danou úroveň aktivity DirectX v systému, jak se měří podle počtu DirectX moduly, které se používají v čase.  Grafu nezobrazí, které konkrétní moduly byly použity.  Modul se považuje za používán pokud zpracovává veškerou práci GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Barvy graf aktivity GPU  
 Zelená značí konzumace aktuální proces modulů rozhraní DirectX.  
  
 Světle šedá označuje využití strojů rozhraní DirectX s jinými procesy v systému. Ke snížení spotřeby modulů DirectX s jinými procesy, snižte počet dalších procesů spuštěných v systému.  
  
 Prázdné označuje dostupnosti nepoužité DirectX stroje v systému. Tyto moduly jsou k dispozici pro váš proces, pokud nemůžete najít další příležitosti k jejich zneužití. Některé moduly jde použít jenom pro určité druhy úloh.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení využití](../profiling/utilization-view.md)



