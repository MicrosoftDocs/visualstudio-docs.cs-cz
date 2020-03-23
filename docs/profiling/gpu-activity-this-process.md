---
title: Aktivita GPU (tento proces) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68e85fc44977a3d9756965de12e25d13d62dbb89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969535"
---
# <a name="gpu-activity-this-process"></a>Aktivita GPU (tento proces)
Segmenty **aktivity GPU (Tento proces)** v zobrazení vláken v vizualizéru souběžnosti představují časy, kdy GPU zpracovával požadavky jménem aktuálního procesu. Tyto požadavky jsou odesílány do GPU jako pakety přímého přístupu do paměti (DMA). Délka segmentu představuje čas, kdy GPU zpracovával paket DMA jménem aktuálního procesu.

 Když vyberete segment aktivity GPU, sestava na kartě **Aktuální** zobrazí informace o zpracovávaném paketu DMA. Tyto informace zahrnují dobu, po kterou paket čekal ve frontě hardwaru, která je přidružena k modulu DirectX, proces, který paket odeslal, a čas potřebný ke zpracování paketu. Jiný proces než aktuální proces mohl fyzicky odeslat paket DMA do grafického procesoru. Vizualizér souběžnosti můžete zjistit, kdy jiný proces odeslané práce gpu jménem aktuálního procesu.