---
title: Aktivita GPU (stránkování) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b8b682c47844a9bc88afdce4a532b1188746a85
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238030"
---
# <a name="gpu-activity-paging"></a>Aktivita GPU (stránkování)
**Aktivita GPU (stránkování)** segmentuje na **vláken** kartě představují dobu, kdy GPU zpracovává požadavky stránkování.  Délka segment představuje doba, aby byl na grafický procesor s zpracování paket stránkování paměti přímý přístup (DMA). Obvykle jsou přidruženy k přenosu paměti mezi procesoru a GPU stránkování paketů.  
  
 Když vyberete segment stránkování GPU sestavy na **aktuální** karta zobrazuje informace o DMA paketu, který byl zpracován. To zahrnuje množství času, který ho čekali ve frontě hardwaru, který je spojen s modul DirectX, proces, který odeslal paket DMA a čas, které je nutné zpracovat paketu.  
  
## <a name="see-also"></a>Viz také:  
 [Zobrazení využití](../profiling/utilization-view.md)