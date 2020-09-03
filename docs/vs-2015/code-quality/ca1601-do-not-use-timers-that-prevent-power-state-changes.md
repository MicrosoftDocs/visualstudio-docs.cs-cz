---
title: 'CA1601: Nepoužívejte časovače, které zabraňují změnám stavu napájení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7928b2fff8c12ca3f0cc3c58bee31fe5809517e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545636"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Nepoužívejte časovače, které zabraňují změně stavu napájení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Kategorie|Microsoft. mobility|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 V časovači je interval nastavený na více než jednu dobu za sekundu.

## <a name="rule-description"></a>Popis pravidla
 Nedotazujte se častěji než jednou za sekundu nebo použijte časovače, ke kterým dochází častěji než jednou za sekundu. Vyšší frekvence periodické aktivity budou udržovat procesor zaneprázdněný a ovlivňovat časovače úspory energie nečinnosti, které vypnou zobrazení a pevné disky.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Nastavte intervaly časovače tak, aby se vyskytly méně než jeden čas za sekundu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Toto pravidlo by mělo být potlačeno pouze v případě, že je nutné vypálení časovače více než jednou za sekundu a požadavky na mobilitu lze bezpečně ignorovat.
