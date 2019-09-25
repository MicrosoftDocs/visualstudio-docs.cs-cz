---
title: 'CA1038: Enumerátory by měly být silného typu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56c2281f76b9064427d1d651523b9cda441eb029
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236006"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Enumerátory by měly být silného typu

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Veřejný nebo chráněný typ implementuje <xref:System.Collections.IEnumerator?displayProperty=fullName> , ale neposkytuje verzi <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> silného typu vlastnosti. Typy, které jsou odvozeny z následujících typů, jsou vyloučeny z tohoto pravidla:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Popis pravidla
Toto pravidlo vyžaduje <xref:System.Collections.IEnumerator> , aby implementace také poskytovaly verzi <xref:System.Collections.IEnumerator.Current%2A> se silnými typy, aby uživatelé nemuseli přetypování návratové hodnoty na silný typ při použití funkcí poskytovaných rozhraním. Toto pravidlo předpokládá, že typ, který <xref:System.Collections.IEnumerator> implementuje, obsahuje kolekci instancí typu, který je silnější než. <xref:System.Object>

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, implementujte vlastnost rozhraní explicitně (deklarujete jako `IEnumerator.Current`). Přidejte veřejnou verzi se silným typem vlastnosti, deklarovaná jako `Current`a vraťte objekt silného typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačí upozornění od tohoto pravidla při implementaci enumerátoru založeného na objektu pro použití s kolekcí založenou na objektech, jako je například binární strom. Typy, které rozšiřuje novou kolekci, budou definovat výčet silného typu a vystavit vlastnost silného typu.

## <a name="example"></a>Příklad
Následující příklad ukazuje správný způsob, jak implementovat <xref:System.Collections.IEnumerator> typ silného typu.

[!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA1035: Implementace rozhraní ICollection mají členy silného typu](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1039: Seznamy jsou silného typu](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.IEnumerator?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>