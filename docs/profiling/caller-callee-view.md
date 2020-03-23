---
title: Zobrazení volajícího a volaní | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bab816a0b71adef190a7d919b5ada7138a6a0e7c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779711"
---
# <a name="callercallee-view"></a>Volající/Volaný – zobrazení
Zobrazení Volající/Volaný zobrazuje informace o profilování pro vybranou funkci a její nadřazené a podřízené funkce. Zobrazení Volající/Volaný obsahuje tři mřížky:

 **Aktuální funkce** je zobrazena ve střední mřížce a zobrazuje informace o profilování pro vybranou funkci. Hodnoty zahrnují všechna volání funkce, které byly shromážděny v profilování spustit.

 **Funkce, které volaly aktuální funkci,** jsou zobrazeny v horní mřížce a zobrazují počet hodnot vybrané (aktuální) funkce, které byly generovány voláním z funkce volajícího (nadřazeného).

 **Funkce, které byly volány aktuální funkcí,** jsou zobrazeny v dolní mřížce a zobrazují informace o profilování volaných (podřízených) funkcí vybrané funkce, když byla podřízená funkce volána aktuální funkcí.

 Sloupce, které jsou k dispozici v zobrazení Volající/Volaný závisí na metodě profilování (vzorkování nebo instrumentace), která byla použita ke shromažďování dat, a na tom, zda byla při spuštění profilování shromážděna data paměti .NET.

 Můžete vybrat jinou funkci, která má být aktuální funkce ve střední části zobrazení sestavy poklepáním na některou z funkcí, které jsou uvedeny v dalších dvou částech zobrazení. Zobrazení Sestavy se aktualizuje automaticky tak, aby odráželo změny.

 Data můžete seřadit kliknutím na názvy sloupců. Další sloupce lze přidat do zobrazení Volající/Volaný. Další informace naleznete v [tématu Postup: Přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md).

## <a name="see-also"></a>Viz také
- [Zobrazení volajícího/volaných - vzorkovací data](../profiling/caller-callee-view-sampling-data.md)
- [Zobrazení volajícího/volaných - data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)
- [Zobrazení volajícího/volaných - data přístrojové paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Zobrazení volajícího/volaných – vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Zobrazení volajícího/volaných - data tvrzení](../profiling/caller-callee-view-contention-data.md)
