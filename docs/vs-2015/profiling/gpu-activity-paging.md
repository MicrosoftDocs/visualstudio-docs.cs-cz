---
title: Aktivita GPU (stránkování) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5979ccf8cafedb849b7ae9f7af6b0b35096e624f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434160"
---
# <a name="gpu-activity-paging"></a>Aktivita GPU (stránkování)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Segmenty **aktivity GPU (stránkování)** na kartě vlákna udávají čas, kdy GPU zpracovával požadavky na stránkování.  Délka segmentu představuje dobu, po kterou GPU zpracovala stránkovací paket přímého přístupu do paměti (DMA). Obvykle jsou stránkovací pakety přidruženy k přenosu paměti mezi CPU a GPU.  
  
 Když vyberete segment stránkování GPU, sestava na **aktuální** kartě zobrazuje informace o zpracovávaném paketu DMA. To zahrnuje dobu, kterou očekáváte v hardwarové frontě, která je přidružená k modulu DirectX, procesu, který odeslal paket DMA, a čas potřebný ke zpracování paketu.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení využití](../profiling/utilization-view.md)
