---
title: Doba zpracování uživatelského rozhraní | Microsoft Docs
description: Přečtěte si, že segmenty na časové ose jsou přidruženy k době blokování, které jsou zařazeny do kategorií jako zpracování uživatelského rozhraní.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 809af327fc2bb608647a76575736bd0e2b00c5b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922037"
---
# <a name="ui-processing-time"></a>Doba zpracování uživatelského rozhraní
Tyto segmenty na časové ose jsou přidruženy k době blokování, které jsou zařazeny do kategorie jako zpracování uživatelského rozhraní. To znamená, že vlákno provádí pumpu zpráv systému Windows nebo jiné fungování uživatelského rozhraní (UI). Během této doby bylo vlákno zablokováno v rozhraní API, které se v nástroji Vizualizátor souběžnosti počítá jako zpracování uživatelského rozhraní. `GetMessage()`Do této skupiny patří rozhraní API, například a `MsgWaitForMultipleObjects()` .

 Pokud není identifikované žádné předem definované blokující rozhraní API, zkontrolujte zásobníky volání a sestavy profilu a určete základní příčiny zpoždění.

 Kategorie zpracování uživatelského rozhraní vám pomůže pochopit rychlost odezvy aplikací GUI a je žádoucí v aplikacích, které závisí na rychlosti odezvy uživatelského rozhraní. Například pokud vlákno UI v aplikaci dosáhne 100% času při zpracování uživatelského rozhraní, je pravděpodobné, že bude reagovat. Nicméně pokud vlákno uživatelského rozhraní stráví značnou dobu v jiných kategoriích, hledejte hlavní příčiny a zvažte možnosti pro omezení kategorií bez uživatelského rozhraní v tomto vlákně.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)