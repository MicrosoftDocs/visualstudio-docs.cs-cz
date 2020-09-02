---
title: Aktivita GPU (Tento proces) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969535"
---
# <a name="gpu-activity-this-process"></a>Aktivita GPU (tento proces)
Segmenty **aktivity GPU (Tento proces)** v zobrazení vlákna ve Vizualizér souběžnosti reprezentují čas, kdy procesor zpracovával požadavky jménem aktuálního procesu. Tyto požadavky jsou odesílány do GPU jako paketů přímého přístupu do paměti (DMA). Délka segmentu představuje čas, po který procesor GPU zpracovává paket DMA jménem aktuálního procesu.

 Když vyberete segment aktivity GPU, sestava na **aktuální** kartě zobrazuje informace o zpracovávaném paketu DMA. Tyto informace zahrnují dobu, po kterou paket čekal ve frontě hardwaru přidružené k modulu DirectX, procesu, který paket odeslal, a čas potřebný ke zpracování paketu. Jiný proces než aktuální proces mohl fyzicky odeslat paket DMA do GPU. Vizualizátor souběžnosti může zjistit, kdy jiný proces odeslal svou práci na GPU jménem aktuálního procesu.