---
title: Aktivita GPU (jiné procesy) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a5b38423bd629dee0f518e0f62eedcf7c55c1db0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789834"
---
# <a name="gpu-activity-other-processes"></a>Aktivita GPU (jiné procesy)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Aktivita GPU (jiné procesy)** segmenty v zobrazení vlákna Vizualizátor souběžnosti představují časy, kdy GPU zpracovává požadavky jménem jiných procesů v systému. Tyto požadavky jsou odesílány GPU jako pakety paměti (DMA) přístup.  Délka segment, který představuje časový interval, zpracování paketu GPU.  
  
 Když vyberete tento druh segmentu, sestavy na **aktuální** karta zobrazuje informace o paketu, který byl zpracován.  Tyto informace zahrnují množství času, které paket čekání ve frontě hardwaru, který je spojen s modul rozhraní DirectX, proces, který odešle paket a čas, který je potřebný ke zpracování paketu.



