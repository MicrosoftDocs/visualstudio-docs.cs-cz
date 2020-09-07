---
title: Upozornění udržovatelnosti
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb985a6482b76b79604ce58f85e7f8cf3e83e97c
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509897"
---
# <a name="maintainability-warnings"></a>Upozornění udržovatelnosti

Upozornění udržovatelnosti podporují údržbu knihovny a aplikace.

## <a name="in-this-section"></a>V této části

| Pravidlo | Popis |
|-----------|-----------------------------------|
| [CA1501: Vyhněte se nadměrné dědičnosti](../code-quality/ca1501.md) | Typ je více než čtyři úrovně hluboko v hierarchii dědičnosti. Hluboce vnořené hierarchie typů může být obtížné sledovat, pochopit a udržovat. |
| [CA1502: Vyhněte se nadměrné složitosti](../code-quality/ca1502.md) | Toto pravidlo měří počet lineárně nezávislých cest skrze metodu, což je určeno počtem a složitostí podmínkových větví. |
| [CA1505: Vyhněte se neudržovatelnému kódu](../code-quality/ca1505.md) | Typ nebo metoda má nízkou hodnotu indexu udržovatelnosti. Nízký index udržovatelnosti označuje, že typ nebo metodu je pravděpodobně obtížné udržovat a je vhodné ji znovu navrhnout. |
| [CA1506: Vyhněte se nadměrnému párování tříd](../code-quality/ca1506.md) | Toto pravidlo měří párování tříd podle počtu jedinečných odkazů na typ, které typ nebo metoda obsahuje. |
| [CA1507: Místo řetězce použijte výraz nameof.](../code-quality/ca1507.md) | Řetězcový literál se používá jako argument, ve kterém `nameof` by se mohl použít výraz. |
| [CA1508: Vyhněte se mrtvému podmíněnému kódu](../code-quality/ca1508.md) | Metoda má podmíněný kód, který se vždy vyhodnocuje `true` za `false` běhu nebo za běhu. To vede k nedoručenému kódu ve `false` větvi podmínky. |
| [CA1509: Neplatná položka v souboru konfigurace metrik kódu](../code-quality/ca1509.md) | Pravidla metrik kódu, například [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) a [CA1506](ca1506.md), dodaly konfigurační soubor s názvem `CodeMetricsConfig.txt` , který má neplatnou položku. |

## <a name="see-also"></a>Viz také

- [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/code-metrics-values.md)
