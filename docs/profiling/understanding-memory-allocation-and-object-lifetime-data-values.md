---
title: Porozumět alokaci paměti & hodnotám dat životnosti objektu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6eec0c4bc5fc27e07bc04a8445ca14ce538ac376
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779997"
---
# <a name="understand-memory-allocation-and-object-lifetime-data-values"></a>Porozumět hodnotám dat přidělení paměti a životnosti objektu

Metoda profilování přidělení paměti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] *.NET* profilování profilování nástroje shromažďuje informace o velikosti a počtu objektů, které byly vytvořeny v přidělení nebo zničeny v uvolňování paměti a další informace o *zásobníku volání* funkce, když došlo k události. *Zásobník volání* je dynamická struktura, která ukládá informace o funkcích, které jsou spuštěny na procesoru.

Profiler paměti přeruší procesor počítače při každém přidělení objektu rozhraní .NET Framework v profilované aplikaci. Při shromažďování dat o době životnosti objektu přerušuje profiler procesor po každém uvolnění paměti rozhraní .NET Framework. Data jsou agregována pro každou profilovanou funkci a pro každý typ objektu.

## <a name="allocation-data"></a>Údaje o přidělení

Dojde-li k události .memory, celkový počet a velikost přidělené nebo zničené objekty paměti jsou přírůstky.

Dojde-li k události přidělení .memory, profiler zintáží vzorek počítá pro každou funkci v zásobníku volání. Při shromažďování dat pouze jedna funkce v zásobníku volání aktuálně provádí kód v jeho těle funkce. Ostatní funkce v zásobníku jsou rodiče v hierarchii volání funkcí, které čekají na funkce, které volal vrátit.

- Pro událost přidělení profiler zvětšuje *počet výhradní* ukázkový počet funkce, která je aktuálně provádění jeho pokyny. Vzhledem k tomu, že výhradní vzorek je také součástí celkového *(včetně)* vzorků funkce, inkluzívý počet vzorků aktuálně aktivní funkce se také zvětší.

- Profiler zintáží včetně počet vzorků všech ostatních funkcí v zásobníku volání.

## <a name="lifetime-data"></a>Data životnosti

Systém uvolňování paměti rozhraní .NET Framework spravuje přidělení a uvolnění paměti pro vaši aplikaci. Chcete-li optimalizovat výkon systému uvolňování paměti, je spravovaná halda rozdělena do tří generací: 0, 1 a 2. Uvolňování paměti za běhu ukládá nové objekty v generaci 0. Objekty, které přežijí kolekce jsou povýšen a uloženy v generacích 1 a 2.

Systém uvolňování paměti uvolňuje paměť zrušením přidělení celé generace objektů. U objektů, které profilovaná aplikace vytvořila, zobrazí zobrazení Životnost objektu počet a velikost objektů a generování při jejich rekultivaci.
