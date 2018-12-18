---
title: Aktivita GPU (Tento proces) | Dokumentace Microsoftu
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
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1b0949a71dc4db1ee217d691d4aae7928faf301
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751409"
---
# <a name="gpu-activity-this-process"></a>Aktivita GPU (tento proces)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Aktivita GPU (Tento proces)** segmenty v zobrazení vláken ve vizualizátoru souběžnosti představují časy, kdy GPU zpracovává požadavky jménem aktuální proces. Tyto požadavky se odesílají do GPU jako pakety paměti (DMA) přístup. Délka segment, který představuje čas, GPU zpracování paketů DMA jménem aktuální proces.  
  
 Když vyberete na segment aktivity GPU, sestava **aktuální** karta zobrazuje informace o paketu DMA, který byl zpracován. Tyto informace zahrnují množství času, které paket čekání ve frontě hardwaru, který je spojen s modul rozhraní DirectX, proces, který odešle paket a čas, který je potřebný ke zpracování paketu. Procesu než aktuální proces může fyzicky odeslání paketů DMA do GPU. Vizualizátor souběžnosti lze rozpoznat, kdy se jiný proces odeslání práce GPU jménem aktuální proces.



