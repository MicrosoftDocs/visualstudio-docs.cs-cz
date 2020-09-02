---
title: Aktivita GPU (jiné procesy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a3b0e97d82d67916aa71f932038930dba48c17e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434134"
---
# <a name="gpu-activity-other-processes"></a>Aktivita GPU (jiné procesy)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Segment **aktivity GPU (jiné procesy)** v zobrazení vláken Vizualizátor souběžnosti představuje čas, kdy GPU zpracovával požadavky jménem jiných procesů v systému. Tyto požadavky odesílají GPU jako pakety přímého přístupu do paměti (DMA).  Délka segmentu představuje dobu, po kterou byl paket zpracován grafickým procesorem.  
  
 Když vyberete tento druh segmentu, sestava na **aktuální** kartě zobrazuje informace o zpracovávaném paketu.  Tyto informace zahrnují dobu, po kterou paket čekal ve frontě hardwaru přidružené k modulu DirectX, procesu, který paket odeslal, a čas potřebný ke zpracování paketu.
