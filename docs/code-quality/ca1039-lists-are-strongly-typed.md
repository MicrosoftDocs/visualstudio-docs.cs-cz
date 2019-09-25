---
title: 'CA1039: Seznamy jsou silného typu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcc399457f4dde1c65836d9c9498c782ba92ecc2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235991"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Seznamy jsou silného typu

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Veřejný nebo chráněný typ implementuje <xref:System.Collections.IList?displayProperty=fullName> , ale neposkytuje metodu silného typu pro jednu nebo více z následujících možností:

- IList. Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo vyžaduje <xref:System.Collections.IList> implementace, aby poskytovaly členy se silnými typy, aby uživatelé nemuseli přetypování <xref:System.Object?displayProperty=fullName> argumentů na typ při použití funkcí poskytovaných rozhraním. <xref:System.Collections.IList> Rozhraní je implementováno kolekcemi objektů, které jsou k dispozici pomocí indexu. Toto pravidlo předpokládá, že typ, který <xref:System.Collections.IList> implementuje, spravuje kolekci instancí typu, který je silnější než. <xref:System.Object>

<xref:System.Collections.IList>implementuje rozhraní <xref:System.Collections.IEnumerable?displayProperty=fullName>a. <xref:System.Collections.ICollection?displayProperty=fullName> Pokud implementujete <xref:System.Collections.IList>, musíte poskytnout požadované členy silného typu pro <xref:System.Collections.ICollection>. Pokud se objekty v kolekci rozšiřují <xref:System.ValueType?displayProperty=fullName>, je nutné poskytnout člen silného typu pro <xref:System.Collections.IEnumerable.GetEnumerator%2A> , aby se zabránilo poklesu výkonu, který je způsoben zabalením. to není vyžadováno, pokud jsou objekty kolekce typu odkaz.

Aby bylo toto pravidlo vyhověno, implementujte členy rozhraní explicitně pomocí názvů ve tvaru InterfaceName. InterfaceMemberName, například <xref:System.Collections.IList.Add%2A>. Explicitní členové rozhraní používají datové typy, které jsou deklarovány rozhraním. Implementujte členy silného typu pomocí názvu člena rozhraní, například `Add`. Deklarovat členy silného typu jako veřejné a deklarovat parametry a návratové hodnoty, aby byly silného typu, který je spravován kolekcí. Silné typy nahrazují slabší typy <xref:System.Object> jako a <xref:System.Array> , které jsou deklarovány rozhraním.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, explicitně implementujte <xref:System.Collections.IList> členy a poskytněte alternativy silného typu pro členy, kteří byli uvedeni dříve. Pro kód, který správně implementuje <xref:System.Collections.IList> rozhraní a poskytuje požadované členy silného typu, si přečtěte následující příklad.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačí upozornění od tohoto pravidla při implementaci nové kolekce založené na objektech, jako je například propojený seznam, kde typy, které rozšiřuje novou kolekci, určují silný typ. Tyto typy by měly dodržovat toto pravidlo a zveřejnit členy silného typu.

## <a name="example"></a>Příklad
V následujícím příkladu typ `YourType` rozšiřuje <xref:System.Collections.CollectionBase?displayProperty=fullName>, stejně jako všechny kolekce silného typu. <xref:System.Collections.CollectionBase>poskytuje explicitní implementaci <xref:System.Collections.IList> rozhraní za vás. Proto je nutné zadat pouze členy silného typu pro <xref:System.Collections.IList> a. <xref:System.Collections.ICollection>

[!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA1035: Implementace rozhraní ICollection mají členy silného typu](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1038: Enumerátory by měly být silného typu](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.IList?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>