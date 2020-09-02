---
title: Doba zpracování uživatelského rozhraní | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 391b4582d03e32e738f0eade823326e72a662a43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "63004439"
---
# <a name="ui-processing-time"></a>Doba zpracování uživatelského rozhraní
Tyto segmenty na časové ose jsou přidruženy k době blokování, které jsou zařazeny do kategorie jako zpracování uživatelského rozhraní. To znamená, že vlákno provádí pumpu zpráv systému Windows nebo jiné fungování uživatelského rozhraní (UI). Během této doby bylo vlákno zablokováno v rozhraní API, které se v nástroji Vizualizátor souběžnosti počítá jako zpracování uživatelského rozhraní. `GetMessage()`Do této skupiny patří rozhraní API, například a `MsgWaitForMultipleObjects()` .

 Pokud není identifikované žádné předem definované blokující rozhraní API, zkontrolujte zásobníky volání a sestavy profilu a určete základní příčiny zpoždění.

 Kategorie zpracování uživatelského rozhraní vám pomůže pochopit rychlost odezvy aplikací GUI a je žádoucí v aplikacích, které závisí na rychlosti odezvy uživatelského rozhraní. Například pokud vlákno UI v aplikaci dosáhne 100% času při zpracování uživatelského rozhraní, je pravděpodobné, že bude reagovat. Nicméně pokud vlákno uživatelského rozhraní stráví značnou dobu v jiných kategoriích, hledejte hlavní příčiny a zvažte možnosti pro omezení kategorií bez uživatelského rozhraní v tomto vlákně.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)