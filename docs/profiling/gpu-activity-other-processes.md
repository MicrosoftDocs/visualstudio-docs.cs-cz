---
title: Aktivita GPU (jiné procesy) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969499"
---
# <a name="gpu-activity-other-processes"></a>Aktivita GPU (jiné procesy)
Segment **aktivity GPU (jiné procesy)** v zobrazení vláken Vizualizátor souběžnosti představuje čas, kdy GPU zpracovával požadavky jménem jiných procesů v systému. Tyto požadavky odesílají GPU jako pakety přímého přístupu do paměti (DMA).  Délka segmentu představuje dobu, po kterou byl paket zpracován grafickým procesorem.

 Když vyberete tento druh segmentu, sestava na **aktuální** kartě zobrazuje informace o zpracovávaném paketu.  Tyto informace zahrnují dobu, po kterou paket čekal ve frontě hardwaru přidružené k modulu DirectX, procesu, který paket odeslal, a čas potřebný ke zpracování paketu.