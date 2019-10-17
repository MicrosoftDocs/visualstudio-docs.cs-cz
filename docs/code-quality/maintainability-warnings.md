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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79e9e24e7769cf4c632faab7795fe2f67844fe7d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445679"
---
# <a name="maintainability-warnings"></a>Upozornění udržovatelnosti

Upozornění udržovatelnosti podporují údržbu knihovny a aplikace.

## <a name="in-this-section"></a>V tomto oddílu

| Pravidlo | Popis |
|-----------|-----------------------------------|
| [CA1500: Názvy proměnných by neměly odpovídat názvům polí](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | Metoda instance deklaruje parametr nebo místní proměnnou, jejíž název odpovídá poli instance deklarovaného typu, který vede k chybám. |
| [CA1501: Vyhněte se nadměrné dědičnosti](../code-quality/ca1501-avoid-excessive-inheritance.md) | Typ je více než čtyři úrovně hluboko v hierarchii dědičnosti. Hluboce vnořené hierarchie typů může být obtížné sledovat, pochopit a udržovat. |
| [CA1502: Vyhněte se nadměrné složitosti](../code-quality/ca1502-avoid-excessive-complexity.md) | Toto pravidlo měří počet lineárně nezávislých cest skrze metodu, což je určeno počtem a složitostí podmínkových větví. |
| [CA1504: Revize zavádějících názvů polí](../code-quality/ca1504-review-misleading-field-names.md) | Název pole instance začíná řetězcem "s_", nebo název statického pole (Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) začíná řetězcem "m_". |
| [CA1505: Vyhněte se neudržovatelnému kódu](../code-quality/ca1505-avoid-unmaintainable-code.md) | Typ nebo metoda má nízkou hodnotu indexu udržovatelnosti. Nízký index udržovatelnosti označuje, že typ nebo metodu je pravděpodobně obtížné udržovat a je vhodné ji znovu navrhnout. |
| [CA1506: Vyhněte se nadměrnému párování tříd](../code-quality/ca1506-avoid-excessive-class-coupling.md) | Toto pravidlo měří párování tříd podle počtu jedinečných odkazů na typ, které typ nebo metoda obsahuje. |
| [CA1507: místo řetězce použijte nameof.](../code-quality/ca1507.md) | Řetězcový literál se používá jako argument, ve kterém by se mohl použít výraz `nameof`. |

## <a name="see-also"></a>Viz také:

- [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/code-metrics-values.md)
