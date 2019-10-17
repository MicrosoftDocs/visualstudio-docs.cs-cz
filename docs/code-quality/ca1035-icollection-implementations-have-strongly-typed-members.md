---
title: 'CA1035: Implementace ICollection mají členy silného typu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0eb96957048a91685049349bf0c796c4eebab196
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446667"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Implementace ICollection mají členy silného typu

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategorie|Microsoft. Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Veřejný nebo chráněný typ implementuje <xref:System.Collections.ICollection?displayProperty=fullName>, ale neposkytuje metodu silného typu pro <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. Verze <xref:System.Collections.ICollection.CopyTo%2A> silného typu musí přijmout dva parametry a nemůže mít <xref:System.Array?displayProperty=fullName> nebo pole <xref:System.Object?displayProperty=fullName> jako svůj první parametr.

## <a name="rule-description"></a>Popis pravidla
Toto pravidlo vyžaduje implementace <xref:System.Collections.ICollection> pro poskytování členů se silnými typy, aby uživatelé nemuseli přetypování argumentů na typ <xref:System.Object> při použití funkcí poskytovaných rozhraním. Toto pravidlo předpokládá, že typ, který implementuje <xref:System.Collections.ICollection>, tak bude spravovat kolekci instancí typu, který je silnější než <xref:System.Object>.

 <xref:System.Collections.ICollection> implementuje rozhraní <xref:System.Collections.IEnumerable?displayProperty=fullName>. Pokud objekty v kolekci rozšiřují <xref:System.ValueType?displayProperty=fullName>, je nutné zadat člena silného typu pro <xref:System.Collections.IEnumerable.GetEnumerator%2A>, aby se zabránilo poklesu výkonu, který je způsoben zabalením. To není vyžadováno, pokud jsou objekty kolekce typu odkaz.

Chcete-li implementovat verzi silného typu člena rozhraní, implementujte členy rozhraní explicitně pomocí názvů ve formě `InterfaceName.InterfaceMemberName`, jako je například <xref:System.Collections.ICollection.CopyTo%2A>. Explicitní členové rozhraní používají datové typy, které jsou deklarovány rozhraním. Implementujte členy silného typu pomocí názvu člena rozhraní, například <xref:System.Collections.ICollection.CopyTo%2A>. Deklarovat členy silného typu jako veřejné a deklarovat parametry a návratové hodnoty, aby byly silného typu, který je spravován kolekcí. Silné typy nahrazují slabší typy, jako <xref:System.Object> a <xref:System.Array>, které jsou deklarovány rozhraním.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, implementujte člen rozhraní explicitně (deklarujte ho jako <xref:System.Collections.ICollection.CopyTo%2A>). Přidejte veřejný člen se silnými typy deklarovaný jako `CopyTo` a pokaždé, když se jako první parametr převezme pole silného typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačí upozornění z tohoto pravidla, Pokud implementujete novou kolekci založenou na objektech, jako je například binární strom, kde typy, které rozšiřuje novou kolekci, určují silný typ. Tyto typy by měly dodržovat toto pravidlo a zveřejnit členy silného typu.

## <a name="example"></a>Příklad
Následující příklad ukazuje správný způsob implementace <xref:System.Collections.ICollection>.

[!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA1038: Enumerátory by měly být silného typu](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

[CA1039: Seznamy jsou silného typu](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
