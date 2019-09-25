---
title: 'CA1002: Nezveřejňujte obecné seznamy'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0612886bf92a4ca6a30e5e15ae1c4a4950d9ddad
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236662"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Nezveřejňujte obecné seznamy

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Typ obsahuje externě viditelný člen, který je <xref:System.Collections.Generic.List%601?displayProperty=fullName> typu, <xref:System.Collections.Generic.List%601> vrátí typ, <xref:System.Collections.Generic.List%601> nebo jehož signatura obsahuje parametr.

## <a name="rule-description"></a>Popis pravidla

<xref:System.Collections.Generic.List%601?displayProperty=fullName>je obecná kolekce, která je navržena pro výkon a nikoli pro dědění. <xref:System.Collections.Generic.List%601>neobsahuje virtuální členy, které usnadňují změnu chování zděděné třídy. Následující obecné kolekce jsou navržené pro dědění a měly by být vystaveny <xref:System.Collections.Generic.List%601>namísto.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, změňte <xref:System.Collections.Generic.List%601?displayProperty=fullName> typ na jednu z obecných kolekcí, která je navržena pro dědění.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačí upozornění z tohoto pravidla, pokud sestavení, které vyvolává toto upozornění, není určeno jako opakovaně použitelná knihovna. Může být například bezpečné toto upozornění potlačit v aplikaci s vyladěným výkonem, kde výhoda výkonu byla získána z použití obecných seznamů.

## <a name="related-rules"></a>Související pravidla

[CA1005: Vyhnout se nadměrnému počtu parametrů u obecných typů](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Kolekce by měly implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1006 Nevnořovat obecné typy v signaturách členů](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Použití instancí obecných obslužných rutin událostí](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také:

[Obecné typy](/dotnet/csharp/programming-guide/generics/index)
