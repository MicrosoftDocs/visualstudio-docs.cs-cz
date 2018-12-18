---
title: Doba spánku | Dokumentace Microsoftu
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
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f9b86ea0fa1b7880893e4d7300efbe51a029ce7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801794"
---
# <a name="sleep-time"></a>Doba spánku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tyto segmenty na časové ose jsou přidruženy k blokování čas, který je zařazený do kategorie jako přejít do režimu spánku. Kategorie z režimu spánku znamená, že vlákno dobrovolně udělil si jeho logické jádro a je to žádná práce. Během této doby je zablokovaný vlákno v rozhraní API, které Vizualizátor souběžnosti se počítá jako přejít do režimu spánku. Rozhraní API, jako `Sleep()` a `SwitchToThread()` spadají do této skupiny.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)



