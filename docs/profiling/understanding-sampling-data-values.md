---
title: Porozumění hodnotám dat vzorkování | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6eb52273633e0b65aa4a7a7049198c49c20633d
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34476999"
---
# <a name="understand-sampling-data-values"></a>Pochopení hodnotám dat vzorkování

*Vzorkování* metoda Visual Studio Tools profilace profilace přerušují procesor počítače v nastavených intervalech a shromažďuje zásobníku volání funkce. A *zásobník volání* je dynamická struktura, která ukládá informace o funkcích, které jsou prováděny na procesor.

Analýza profileru určí, jestli je procesor provádění kódu v tento cílový proces. Pokud procesor není spuštěním kódu v procesu cíl, ukázce se zahodí.

Pokud procesor spouští cílový kód, profileru zvýší počet ukázka pro jednotlivé funkce v zásobníku volání. V době, vzorku jenom jednu funkci v zásobníku volání je aktuálně provádění kódu. Jiných funkcí v zásobníku jsou rodičů v hierarchii volání funkce, které čekají na jejich podřízené vrátit.

Pro událost vzorku, profileru zvýší *výhradní* počet funkce, která právě probíhá jeho pokyny vzorků. Protože výhradní ukázka je také součástí celkové (*včetně*) se taky zvýší ukázky funkce, včetně ukázkové počet aktuálně aktivních funkce.

 Profileru zvýší počet vzorků včetně všech funkcí v zásobníku volání.

## <a name="inclusive-samples"></a>Ukázky (včetně).

Celkový počet vzorků, které byly shromážděny během provádění funkce cíl.

To zahrnuje vzorků, které byly shromážděny během přímé provádění kódu funkce a ukázky, které byly shromážděny během provádění podřízené funkce, které se nazývají funkcí cíl.

## <a name="exclusive-samples"></a>Výhradní ukázky

Počet vzorků, které byly shromážděny během přímé provádění pokynů funkce cíl.

Výhradní ukázky nezahrnují vzorků, které byly shromážděny během provádění funkcí, které se nazývají funkcí cíl.

## <a name="inclusive-percent"></a>V procentech (včetně).

Procento celkového počtu v profilaci spustit včetně vzorků, které jsou včetně ukázky rozsahu funkce nebo data.

## <a name="exclusive-percent"></a>Výhradní procent

Procento celkového počtu v profilaci spustit výhradní vzorků, které jsou výhradní ukázky rozsahu funkce nebo data.

## <a name="see-also"></a>Viz také:

[Postupy: Výběr metod shromažďování](../profiling/how-to-choose-collection-methods.md)  
[Analýza dat nástrojů pro měření výkonu](../profiling/analyzing-performance-tools-data.md)