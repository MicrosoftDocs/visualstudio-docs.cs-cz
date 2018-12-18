---
title: Doba zpracování uživatelského rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad48cd912bfdc117496bc9f876a1a2174e76dc04
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477532"
---
# <a name="ui-processing-time"></a>Doba zpracování uživatelského rozhraní
Tyto segmenty v časové ose jsou přidruženy k blokování pokusů, které jsou klasifikovány jako zpracování uživatelského rozhraní. To znamená, že je čerpání zpráv systému Windows nebo provádění jiných uživatelské rozhraní (UI) pracovní vlákno. Během této doby je zablokovaný vlákna v rozhraní API, které je vizualizér souběžnosti počítání jako zpracování uživatelského rozhraní. Rozhraní API jako třeba `GetMessage()` a `MsgWaitForMultipleObjects()` do této skupiny patří.  
  
 Pokud se identifikuje žádné předdefinované blokování rozhraní API, zkontrolujte zásobníky volání a profilu, sestavy určit základní příčiny zpoždění.  
  
 Kategorie zpracování uživatelského rozhraní vám pomůže pochopit rychlost odezvy aplikací grafického uživatelského rozhraní a je žádoucí v aplikacích, které jsou závislé na odezvy uživatelského rozhraní. Například pokud vlákna uživatelského rozhraní v aplikaci, která patří dosahuje 100 % času při zpracování uživatelského rozhraní, je pravděpodobně nebude reagovat. Ale pokud vlákna uživatelského rozhraní tráví mnoho času v jiných kategoriích, vyhledejte základní příčiny a zvažte snížení kategorií bez uživatelského rozhraní v daném vláknu možnosti.  
  
## <a name="see-also"></a>Viz také:  
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)