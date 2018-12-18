---
title: 'CA1005: Vyhněte se nadbytečným parametrům na obecných typech'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e65427aecb2d4ecc135480d23834fdc07a413b05
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850123"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Vyhněte se nadbytečným parametrům na obecných typech

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Externě viditelný obecný typ má více než dva parametry typu.

## <a name="rule-description"></a>Popis pravidla
 Čím více parametrů typu obecný typ obsahuje, tím obtížnější je vědět a zapamatovat si, co každý z parametrů typu představuje. To je obvykle zřejmé s jedním parametrem typu, jako v `List<T>`a v některých případech se dvěma parametry typu, jako v `Dictionary<TKey, TValue>`. Pokud existuje více než dvěma parametry typu, je obtížné stane příliš velký pro většinu uživatelů (například `TooManyTypeParameters<T, K, V>` v jazyce C# nebo `TooManyTypeParameters(Of T, K, V)` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte návrhu a použít více než dvěma parametry typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění tohoto pravidla, pokud návrh naprosto vyžaduje více než dvěma parametry typu. Poskytuje obecné typy v syntaxi, která je snadno pochopitelný a snižuje čas, který je potřeba další informace a zvýší frekvence přijetí nové knihovny.

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