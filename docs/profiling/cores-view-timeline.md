---
title: Časová osa zobrazení jader | Microsoft Docs
description: 'Seznamte se se základy časové osy: jak určit, ve kterém vlákně je jádro v jakémkoli okamžiku, a jak se přiblížit nebo oddálit.'
custom.ms: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.timeline.threads
helpviewer_keywords:
- Concurrency Visualizer, Cores View Timeline
ms.assetid: 10f0c666-ac2f-4ac5-9fb5-a88f660ab840
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: de09394bfc071cbe3dd1fedad52d1e5a511b62c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882892"
---
# <a name="cores-view-timeline"></a>Časová osa zobrazení jader
Každý řádek časové osy představuje jádro logického procesoru v profilované soustavě. U každého řádku zobrazuje vodorovná osa, které vlákno bylo spuštěno v logickém jádru v daném časovém okamžiku. Najeďte myší na barvu zájmu na časové ose, abyste vrátili popis, který identifikuje vlákno. Pro usnadnění identifikace vlákna, legenda v dolní části okna ukazuje, co každá barva představuje. Přiblížení a oddálení pomocí nástroje Lupa můžete kliknutím a přetažením nebo stisknutím klávesy CTRL a přesunutím kolečka myši. Konzistence lupy se udržuje při přepínání mezi zobrazením jader a zobrazením vláken.

## <a name="see-also"></a>Viz také
- [Zobrazení jader](../profiling/cores-view.md)
- [Ovládací prvek Lupa (zobrazení vláken)](../profiling/zoom-control-threads-view.md)