---
title: Prázdný segment časové osy | Microsoft Docs
description: V Vizualizátor souběžnosti sady Visual Studio je třeba pochopit důvody, proč může být sekce časové osy prázdná (má bílé pozadí) pro druh kanálu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a4a3265c3b31653d94a686fa8fda12f7699596e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955265"
---
# <a name="empty-timeline-segment"></a>Prázdný segment časové osy
V Vizualizátor souběžnosti je důvodem, že část časové osy je prázdná (má bílé pozadí), závisí na typu kanálu.

- V případě kanálu vlákna procesoru to znamená, že vlákno v této části časové osy neexistovalo. Pokud vás zajímá vlákno, můžete najít jeho vykonáváný oddíl pomocí ovládacího prvku zvětšení nebo posouvání vodorovně.

- U vstupně-výstupních kanálů to znamená, že v daném časovém okamžiku nedošlo k žádnému přístupu k disku jménem cílového procesu.

- Pro kanál DirectX to znamená, že v rámci této části časové osy nebyla žádná práce GPU provedena jménem cílového procesu.

- U kanálu značek to znamená, že nebyly vygenerovány žádné značky.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)
- [Ovládací prvek Lupa (zobrazení vláken)](../profiling/zoom-control-threads-view.md)