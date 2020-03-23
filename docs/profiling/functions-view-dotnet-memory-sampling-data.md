---
title: Zobrazení funkcí – vzorkovací data paměti .NET | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: cce13da0c2dfee61d70da8bc288d1f0ff4690deb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780036"
---
# <a name="functions-view---net-memory-sampling-data"></a>Zobrazení funkcí – vzorkovací data paměti .NET
Zobrazení Funkce profilování profilování paměti .NET, která byla shromážděna pomocí metody vzorkování, uvádí funkce, které přidělily paměť během spuštění profilování, a hlásí velikost a počet přidělení.

|Sloupec|Popis|
|------------|-----------------|
|**ID procesu**|ID procesu (PID) profilování spustit.|
|**Název procesu**|Název procesu|
|**Název modulu**|Název modulu, který obsahuje funkci.|
|**Cesta modulu**|Cesta modulu, který obsahuje funkci.|
|**Zdrojový soubor**|Zdrojový soubor, který obsahuje definici této funkce.|
|**Název funkce**|Plně kvalifikovaný název funkce.|
|**Číslo řádku funkce**|Číslo řádku začátku této funkce ve zdrojovém souboru.|
|**Adresa funkce**|Adresa funkce.|
|**Inkluzivní přidělení**|Celkový počet objektů, které byly přiděleny v této funkci a její podřízené funkce.|
|**Včetně přidělení %**|Procento všech objektů, které byly přiděleny v profilování spustit, které byly včetně přidělení této funkce.|
|**Výhradní přidělení**|Počet objektů, které byly vytvořeny při spuštění funkce přímo v horní části zásobníku volání. Toto číslo nezahrnuje objekty, které byly vytvořeny v podřízených funkcích.|
|**Výhradní přidělení %**|Procento všech objektů, které byly přiděleny v profilování spustit, které byly výhradní přidělení této funkce.|
|**Včetně bajtů**|Počet bajtů paměti, které byly přiděleny touto funkcí a její podřízené funkce.|
|**Včetně bajtů %**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly včetně bajtů této funkce.|
|**Exkluzivní bajty**|Počet bajtů paměti, které byly přiděleny touto funkcí, ale ne její podřízené funkce.|
|**Výhradní bajty %**|Procento všech bajtů paměti, které byly přiděleny v profilování spustit, které byly výhradní bajty této funkce.|

## <a name="see-also"></a>Viz také
- [Zobrazení funkcí - instrumentace](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Zobrazení funkcí](../profiling/functions-view-sampling-data.md)
- [Zobrazení funkcí](../profiling/functions-view-instrumentation-data.md)
