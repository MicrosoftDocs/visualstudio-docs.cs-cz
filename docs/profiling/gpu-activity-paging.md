---
title: Aktivita GPU (stránkování) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969612"
---
# <a name="gpu-activity-paging"></a>Aktivita GPU (stránkování)
Segmenty **aktivity GPU (Stránkování)** na kartě **Vlákna** představují časy, kdy GPU zpracovával požadavky na stránkování.  Délka segmentu představuje dobu, po kterou GPU zpracovával stránkovací paket přímého přístupu do paměti (DMA). Pagingové pakety jsou obvykle přidruženy k přenosu paměti mezi procesorem a grafickým procesorem.

 Když vyberete segment stránkování GPU, sestava na kartě **Aktuální** zobrazí informace o zpracovávaném paketu DMA. To zahrnuje dobu, po kterou čekal ve frontě hardwaru, který je přidružen k modulu DirectX, proces, který odeslal paket DMA, a čas potřebný ke zpracování paketu.

## <a name="see-also"></a>Viz také
- [Zobrazení využití](../profiling/utilization-view.md)