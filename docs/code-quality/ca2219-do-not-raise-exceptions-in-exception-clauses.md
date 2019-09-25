---
title: 'CA2219: Nevyvolávejte výjimky v klauzulích výjimky'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c06f8693034b9943de8072f110f4661b87098a5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231154"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Nevyvolávejte výjimky v klauzulích výjimky

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nerozdělování, přerušení|

## <a name="cause"></a>příčina
Výjimka je vyvolána z `finally`klauzule, Filter nebo Fault.

## <a name="rule-description"></a>Popis pravidla
Je-li v klauzuli Exception vyvolána výjimka, významně se tím zvyšuje obtížnost ladění.

Pokud je výjimka vyvolána v `finally` klauzuli nebo chyby, nová výjimka skryje aktivní výjimku, pokud je k dispozici. Tím je původní chybě obtížné detekovat a ladit.

Pokud je v klauzuli filtru vyvolána výjimka, modul runtime tuto výjimku tiše zachytí a způsobí, že se filtr vyhodnotí jako NEPRAVDA. Neexistuje žádný způsob, jak určit rozdíl mezi filtrem vyhodnoceným na hodnotu false a vyvoláním výjimky z filtru. Díky tomu je obtížné detekovat a ladit chyby v logice filtru.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit toto porušení tohoto pravidla, Nevolejte explicitně výjimku z `finally`klauzule, Filter nebo Fault.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačit upozornění pro toto pravidlo. Neexistují žádné scénáře, za kterých výjimka vyvolaná v klauzuli Exception poskytuje výhodu pro provádění kódu.

## <a name="related-rules"></a>Související pravidla
[CA1065: Nevyvolávání výjimek v neočekávaných umístěních](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Viz také:
[Upozornění ohledně návrhu](../code-quality/design-warnings.md)