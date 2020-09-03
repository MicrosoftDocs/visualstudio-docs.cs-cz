---
title: Zobrazení volající/volaný | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74779711"
---
# <a name="callercallee-view"></a>Volající/Volaný – zobrazení
Zobrazení volající/volaný zobrazí informace o profilování vybrané funkce a jejích nadřazených a podřízených funkcí. Zobrazení volající/volaný obsahuje tři mřížky:

 **Aktuální funkce** se zobrazí v prostřední mřížce a zobrazí informace o profilování pro vybranou funkci. Hodnoty zahrnují všechna volání funkce, která byla shromážděna při spuštění profilace.

 **Funkce, které se nazývají aktuální funkce** , se zobrazí v horní mřížce a zobrazuje počet hodnot vybrané (aktuální) funkce, která byla vygenerována voláními z funkce volající (nadřazená).

 **Funkce, které byly volány aktuální funkcí** , jsou zobrazeny v dolní mřížce a zobrazují informace o profilech pro volané (podřízené) funkce vybrané funkce, pokud byla podřízená funkce volána aktuální funkcí.

 Sloupce, které jsou k dispozici v zobrazení volající/volaný, závisí na metodě profilování (vzorkování nebo instrumentace), která byla použita ke shromažďování dat a zda byla data paměti .NET shromažďována při spuštění profilace.

 Můžete vybrat jinou funkci, která bude aktuální funkcí v prostřední části zobrazení sestavy, dvojím kliknutím na některou z funkcí, které jsou uvedeny v dalších dvou částech zobrazení. Zobrazení sestavy je aktualizováno automaticky, aby odráželo změny.

 Data můžete seřadit kliknutím na názvy sloupců. Další sloupce lze přidat do zobrazení volající/volaný. Další informace najdete v tématu [Postup: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md).

## <a name="see-also"></a>Viz také
- [Zobrazení Volající/Volaný – data vzorkování](../profiling/caller-callee-view-sampling-data.md)
- [Zobrazení Volající/Volaný – data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)
- [Zobrazení Volající/Volaný – data instrumentace paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Zobrazení Volající/Volaný – data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Zobrazení Volající/Volaný – data kolizí](../profiling/caller-callee-view-contention-data.md)
