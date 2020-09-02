---
title: Čas přechodu do režimu spánku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8a79bbca9f6275f115105cc2ba6b001ac0ca7d44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198379"
---
# <a name="sleep-time"></a>Doba spánku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tyto segmenty na časové ose jsou přidruženy k době blokování, který je zařazen do kategorie v režimu spánku. Kategorie spánku znamená, že vlákno má dobrovolně k dispozici svůj logický jádro a neprovádí žádnou práci. Během této doby bylo vlákno v rozhraní API zablokované, protože Vizualizér souběžnosti se počítá jako režim spánku. `Sleep()`Do této skupiny patří rozhraní API, například a `SwitchToThread()` .  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)
