---
title: 'CA1005: Vyhněte se nadbytečným parametrům na obecných typech'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77f913a2dc31ee77445ee90b417f1a7d1cf23b8d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449356"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Vyhněte se nadbytečným parametrům na obecných typech

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Kategorie|Microsoft. Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Externě viditelný obecný typ má více než dva parametry typu.

## <a name="rule-description"></a>Popis pravidla
Čím více parametrů typu obecný typ obsahuje, tím obtížnější je vědět a zapamatovat si, co každý z parametrů typu představuje. Je obvykle zřejmé s jedním parametrem typu, jako v `List<T>` a v některých případech se dvěma parametry typu, jako v `Dictionary<TKey, TValue>`. Pokud existuje více než dva parametry typu, je problém pro většinu uživatelů příliš velký (například `TooManyTypeParameters<T, K, V>` v C# nebo `TooManyTypeParameters(Of T, K, V)` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, změňte návrh tak, aby nepoužíval více než dva parametry typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačí upozornění z tohoto pravidla, pokud návrh naprosto nepožaduje více než dva parametry typu. Poskytování generických v syntaxi, která je snadno srozumitelná a používá, zkracuje dobu potřebnou k tomu, abyste se seznámili a zvyšovali rychlost přijímání nových knihoven.

## <a name="related-rules"></a>Související pravidla
[CA1010: Kolekce musí implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Nevnořujte obecné typy v signaturách členu](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Použijte instance obecných obslužných rutin události](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také:
[Obecné typy](/dotnet/csharp/programming-guide/generics/index)
