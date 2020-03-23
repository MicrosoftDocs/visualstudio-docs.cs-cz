---
title: Principy hodnot vzorkovacích dat | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 289f92deaceca32a44249ed77c17187743a34fa4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778047"
---
# <a name="understand-sampling-data-values"></a>Principy hodnot vzorkovacích dat

Metoda *profilování vzorkování* nástrojů profilování sady Visual Studio přerušuje procesor počítače v nastavených intervalech a shromažďuje zásobník volání funkce. *Zásobník volání* je dynamická struktura, která ukládá informace o funkcích, které jsou spuštěny na procesoru.

Analýza profileru určuje, zda procesor provádí kód v cílovém procesu. Pokud procesor neprovádí kód v cílovém procesu, ukázka je zahozena.

Pokud procesor provádí cílový kód, profiler inkumuje počty vzorků pro každou funkci v zásobníku volání. V době, kdy je odebrána ukázka, pouze jedna funkce v zásobníku volání je aktuálně provádění kódu. Ostatní funkce v zásobníku jsou rodiče v hierarchii volání funkce, které čekají na jejich děti vrátit.

Pro ukázkovou událost profiler zvětšuje *počet výhradní* ukázkový počet funkce, která je aktuálně provádění jeho pokyny. Vzhledem k tomu, že výhradní vzorek je také součástí celkového *(včetně)* vzorků funkce, inkluzívý počet vzorků aktuálně aktivní funkce se také zvětší.

 Profiler zintáží včetně počet vzorků všech ostatních funkcí v zásobníku volání.

## <a name="inclusive-samples"></a>Včetně vzorků

Celkový počet vzorků, které jsou shromážděny během provádění cílové funkce.

To zahrnuje vzorky, které jsou shromažďovány během přímého provádění kódu funkce a vzorky, které jsou shromažďovány během provádění podřízených funkcí, které jsou volány cílovou funkcí.

## <a name="exclusive-samples"></a>Exkluzivní vzorky

Počet vzorků, které jsou shromážděny během přímého provádění pokynů cílové funkce.

Výhradní vzorky nezahrnují vzorky, které jsou shromažďovány během provádění funkcí, které jsou volány cílovou funkcí.

## <a name="inclusive-percent"></a>Včetně procenta

Procento z celkového počtu včetně vzorků v profilování spustit, které jsou včetně vzorky funkce nebo oblasti dat.

## <a name="exclusive-percent"></a>Výhradní procento

Procento z celkového počtu výhradní vzorky v profilování spustit, které jsou výhradní vzorky funkce nebo oblasti dat.

## <a name="see-also"></a>Viz také

[Postup: Volba metod](../profiling/how-to-choose-collection-methods.md)
kolekce[Analýza dat nástrojů výkonu](../profiling/analyzing-performance-tools-data.md)
