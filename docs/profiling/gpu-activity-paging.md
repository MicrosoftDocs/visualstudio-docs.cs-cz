---
title: Aktivita GPU (stránkování) | Microsoft Docs
description: Zkontrolujte segmenty aktivity GPU (stránkování) na kartě vlákna v Vizualizér souběžnosti. Segmenty reprezentují čas, kdy procesor zpracovával požadavky na stránkování.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2bdf1fcffad90155baba8f92d11e31d1b316710b
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801183"
---
# <a name="gpu-activity-paging"></a>Aktivita GPU (stránkování)
Segmenty **aktivity GPU (stránkování)** na kartě **vlákna** UDÁVAJÍ čas, kdy GPU zpracovával požadavky na stránkování.  Délka segmentu představuje dobu, po kterou GPU zpracovala stránkovací paket přímého přístupu do paměti (DMA). Obvykle jsou stránkovací pakety přidruženy k přenosu paměti mezi CPU a GPU.

 Když vyberete segment stránkování GPU, sestava na **aktuální** kartě zobrazuje informace o zpracovávaném paketu DMA. To zahrnuje dobu, kterou očekáváte v hardwarové frontě, která je přidružená k modulu DirectX, procesu, který odeslal paket DMA, a čas potřebný ke zpracování paketu.

## <a name="see-also"></a>Viz také
- [Zobrazení využití](../profiling/utilization-view.md)