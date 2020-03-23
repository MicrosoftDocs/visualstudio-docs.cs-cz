---
title: Prázdný segment časové osy | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a96cdc7ae4edc7ea7193d5b95dfc73fa1747c1fb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970106"
---
# <a name="empty-timeline-segment"></a>Prázdný segment časové osy
Ve vizualizéru souběžnosti důvod, proč část časové osy je prázdný (má bílé pozadí) závisí na druhu kanálu.

- Pro kanál vlákna procesoru to znamená, že vlákno během této části časové osy neexistovalo. Pokud máte zájem o vlákno, můžete najít jeho prováděcí oddíl pomocí ovládacího prvku lupy nebo posouváním vodorovně.

- Pro vstupně-v., znamená to, že žádný přístup k disku došlo jménem cílového procesu v tomto okamžiku.

- Pro kanál DirectX to znamená, že během této části časové osy nebyla provedena žádná práce gpu jménem cílového procesu.

- Pro kanál značky to znamená, že nebyly generovány žádné značky.

## <a name="see-also"></a>Viz také
- [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)
- [Ovládání lupy (zobrazení vláken)](../profiling/zoom-control-threads-view.md)