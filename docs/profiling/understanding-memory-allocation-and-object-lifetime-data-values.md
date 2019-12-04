---
title: Vysvětlení přidělení paměti & hodnoty dat o životnosti objektů
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779997"
---
# <a name="understand-memory-allocation-and-object-lifetime-data-values"></a>Principy přidělování paměti a hodnot dat životnosti objektů

Metoda profilování *alokace paměti .net* [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroje pro profilaci shromažďuje informace o velikosti a počtu objektů, které byly vytvořeny v rámci přidělení nebo zničení v uvolňování paměti a další informace o *zásobníku volání* funkce při výskytu události. *Zásobník volání* je dynamická struktura, která ukládá informace o funkcích, které jsou spuštěny na procesoru.

Profiler paměti přerušuje procesor počítače při každém přidělení objektu .NET Framework v profilované aplikaci. Při shromažďování dat o době životnosti objektu přerušuje profiler procesor po každém uvolnění paměti rozhraní .NET Framework. Data jsou agregována pro každou profilovou funkci a pro každý typ objektu.

## <a name="allocation-data"></a>Alokační data

Při výskytu události. Memory se zvýší celkový počet a velikost objektů přidělených nebo zničených paměti.

Když dojde k události přidělení paměti, Profiler zvýší počty vzorků pro každou funkci v zásobníku volání. Když jsou data shromážděna, pouze jedna funkce v zásobníku volání aktuálně provádí kód v těle své funkce. Ostatní funkce v zásobníku jsou rodiče v hierarchii volání funkcí, které čekají na vrácení funkcí, které volají.

- V případě události alokace Profiler zvýší počet *exkluzivních* vzorků funkce, ve které aktuálně probíhá zpracování instrukcí. Vzhledem k tomu, že exkluzivní vzorek je také součástí celkových (*včetně*) vzorků funkce, je také zvýšen celkový počet vzorků aktuálně aktivní funkce.

- Profiler zvýší celkový počet vzorků všech ostatních funkcí v zásobníku volání.

## <a name="lifetime-data"></a>Data o životnosti

Systém uvolňování paměti .NET Framework spravuje přidělování a uvolňování paměti pro vaši aplikaci. Pro optimalizaci výkonu uvolňování paměti je spravovaná halda rozdělená na tři generace: 0, 1 a 2. Systém uvolňování paměti v době běhu ukládá nové objekty v generaci 0. Objekty, které zůstávají kolekce, jsou povýšeny a uloženy v generacích 1 a 2.

Uvolňování paměti uvolňuje paměť uvolněním celé generace objektů. Pro objekty, které vytvořil profilovaná aplikace, zobrazuje zobrazení životnost objektů počet a velikost objektů a generaci, když jsou uvolněny.
