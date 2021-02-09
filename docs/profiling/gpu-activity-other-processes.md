---
title: Aktivita GPU (jiné procesy) | Microsoft Docs
description: Přečtěte si o segmentech aktivity GPU (jiné procesy) v zobrazení vláken Vizualizátor souběžnosti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e57d40910dfdff9b2eb1d5a9db76bac6ec8657d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907257"
---
# <a name="gpu-activity-other-processes"></a>Aktivita GPU (jiné procesy)
Segment **aktivity GPU (jiné procesy)** v zobrazení vláken Vizualizátor souběžnosti představuje čas, kdy GPU zpracovával požadavky jménem jiných procesů v systému. Tyto požadavky odesílají GPU jako pakety přímého přístupu do paměti (DMA).  Délka segmentu představuje dobu, po kterou byl paket zpracován grafickým procesorem.

 Když vyberete tento druh segmentu, sestava na **aktuální** kartě zobrazuje informace o zpracovávaném paketu.  Tyto informace zahrnují dobu, po kterou paket čekal ve frontě hardwaru přidružené k modulu DirectX, procesu, který paket odeslal, a čas potřebný ke zpracování paketu.