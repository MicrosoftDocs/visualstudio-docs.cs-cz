---
title: Doba zpracování uživatelského rozhraní | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bbed9d8c4725b6bd497377d4a9dee22f2f8573d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145488"
---
# <a name="ui-processing-time"></a>Doba zpracování uživatelského rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tyto segmenty na časové ose jsou přidruženy k době blokování, které jsou zařazeny do kategorie jako zpracování uživatelského rozhraní. To znamená, že vlákno provádí pumpu zpráv systému Windows nebo jiné fungování uživatelského rozhraní (UI). Během této doby bylo vlákno zablokováno v rozhraní API, které se v nástroji Vizualizátor souběžnosti počítá jako zpracování uživatelského rozhraní. `GetMessage()`Do této skupiny patří rozhraní API, například a `MsgWaitForMultipleObjects()` .  
  
 Pokud není identifikované žádné předem definované blokující rozhraní API, zkontrolujte zásobníky volání a sestavy profilu a určete základní příčiny zpoždění.  
  
 Kategorie zpracování uživatelského rozhraní je důležitá pro porozumění rychlosti používání aplikací GUI a je žádoucí v aplikacích, které závisí na rychlosti odezvy uživatelského rozhraní. Například pokud vlákno uživatelského rozhraní v aplikaci dosáhne 100% času při zpracování uživatelského rozhraní, je pravděpodobné, že bude velmi reagovat. Nicméně pokud vlákno uživatelského rozhraní stráví značnou dobu v jiných kategoriích, hledejte hlavní příčiny a zvažte možnosti pro omezení kategorií bez uživatelského rozhraní v tomto vlákně.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)
