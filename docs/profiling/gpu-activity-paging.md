---
title: Aktivita GPU (stránkování) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bd28c7b41a01992ad52fa343b098b0a02460806
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969612"
---
# <a name="gpu-activity-paging"></a>Aktivita GPU (stránkování)
Segmenty **aktivity GPU (stránkování)** na kartě **vlákna** UDÁVAJÍ čas, kdy GPU zpracovával požadavky na stránkování.  Délka segmentu představuje dobu, po kterou GPU zpracovala stránkovací paket přímého přístupu do paměti (DMA). Obvykle jsou stránkovací pakety přidruženy k přenosu paměti mezi CPU a GPU.

 Když vyberete segment stránkování GPU, sestava na **aktuální** kartě zobrazuje informace o zpracovávaném paketu DMA. To zahrnuje dobu, kterou očekáváte v hardwarové frontě, která je přidružená k modulu DirectX, procesu, který odeslal paket DMA, a čas potřebný ke zpracování paketu.

## <a name="see-also"></a>Viz také
- [Zobrazení využití](../profiling/utilization-view.md)