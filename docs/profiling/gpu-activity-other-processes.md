---
title: Aktivita GPU (jiné procesy) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 586aeb9b2b6d674c14106a911872c967c272f3e6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/19/2018
ms.locfileid: "31573073"
---
# <a name="gpu-activity-other-processes"></a>Aktivita GPU (jiné procesy)
**Aktivita GPU (jiné procesy)** segmentů v zobrazení vláken vizualizér souběžnosti představují dobu, kdy GPU zpracovává požadavky jménem jiné procesy v systému. Tyto požadavky jsou odesílány GPU v paměti přímý přístup (DMA) paketů.  Délka segment představuje dobu trvání čas, který byl zpracován paketu GPU.  
  
 Když vyberete tento druh segmentu, sestavy na **aktuální** karta zobrazuje informace o paketu, který byl zpracován.  Informace zahrnují množství času, který paketu čekali ve frontě hardwaru, který je spojen s modul DirectX, proces, který odeslal paketu a čas, které je nutné zpracovat paketu.