---
title: 'CA1601: Nepoužívejte časovače, které zabraňují změně stavu napájení'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed9c0e2db15c3d707823105ba4e708be466a662e
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72439951"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Nepoužívejte časovače, které zabraňují změně stavu napájení

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Kategorie|Microsoft. mobility|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
V časovači je interval nastavený na více než jednu dobu za sekundu.

## <a name="rule-description"></a>Popis pravidla
Nedotazujte se častěji než jednou za sekundu nebo použijte časovače, ke kterým dochází častěji než jednou za sekundu. Vyšší frekvence periodické aktivity budou udržovat procesor zaneprázdněný a ovlivňovat časovače úspory energie nečinnosti, které vypnou zobrazení a pevné disky.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Nastavte intervaly časovače tak, aby se vyskytly méně než jeden čas za sekundu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Toto pravidlo by mělo být potlačeno pouze v případě, že je nutné vypálení časovače více než jednou za sekundu a požadavky na mobilitu lze bezpečně ignorovat.
