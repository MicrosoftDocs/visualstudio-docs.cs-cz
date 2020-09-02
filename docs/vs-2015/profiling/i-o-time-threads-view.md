---
title: Čas I/O (zobrazení vláken) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 86c14292edcf8f132a14b67e931c5121105a9dc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187448"
---
# <a name="io-time-threads-view"></a>Čas I/O (Zobrazení vláken)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tyto segmenty na časové ose jsou přidruženy k době blokování, které jsou zařazeny do kategorií v/v. To znamená, že vlákno čeká na dokončení vstupně-výstupních operací. Vlákno mohlo být zablokované v rozhraní API nebo jádro související s/O čeká na to, že Vizualizátor souběžnosti se počítá jako vstup a výstup. `CreateFile()` `ReadFile()` Do této skupiny patří rozhraní API, jako je, a `WSARecv()` .  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)
