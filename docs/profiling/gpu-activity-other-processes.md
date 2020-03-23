---
title: Aktivita GPU (jiné procesy) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a502590c20fce1455d9259ae681178d9cd48e33
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969499"
---
# <a name="gpu-activity-other-processes"></a>Aktivita GPU (jiné procesy)
Segmenty **aktivity GPU (ostatní procesy)** v zobrazení vláken vizualizéru souběžnosti představují časy, kdy GPU zpracovával požadavky jménem jiných procesů v systému. Tyto požadavky jsou odesílány GPU jako pakety přímého přístupu do paměti (DMA).  Délka segmentu představuje dobu, po kterou byl paket zpracován grafickým procesorem.

 Když vyberete tento druh segmentu, sestava na kartě **Aktuální** zobrazí informace o zpracovávaném paketu.  Informace zahrnují dobu, po kterou paket čekal ve frontě hardwaru, která je přidružena k modulu DirectX, proces, který paket odeslal, a čas potřebný ke zpracování paketu.