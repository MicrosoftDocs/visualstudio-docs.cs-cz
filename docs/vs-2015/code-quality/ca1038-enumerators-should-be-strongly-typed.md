---
title: 'CA1038: enumerátory by měly být silného typu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e660b1af58dca8d0d69ce2844076382c4a5a1f12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548262"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Enumerátory by měly být silného typu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Veřejný nebo chráněný typ implementuje, <xref:System.Collections.IEnumerator?displayProperty=fullName> ale neposkytuje verzi silného typu <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> Vlastnosti. Typy, které jsou odvozeny z následujících typů, jsou vyloučeny z tohoto pravidla:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo vyžaduje <xref:System.Collections.IEnumerator> , aby implementace také poskytovaly verzi se silnými typy, aby uživatelé nemuseli <xref:System.Collections.IEnumerator.Current%2A> přetypování návratové hodnoty na silný typ při použití funkcí poskytovaných rozhraním. Toto pravidlo předpokládá, že typ, který implementuje, <xref:System.Collections.IEnumerator> obsahuje kolekci instancí typu, který je silnější než <xref:System.Object> .

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, implementujte vlastnost rozhraní explicitně (deklarujete jako `IEnumerator.Current` ). Přidejte veřejnou verzi se silným typem vlastnosti, deklarovaná jako `Current` a vraťte objekt silného typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění od tohoto pravidla při implementaci enumerátoru založeného na objektu pro použití s kolekcí založenou na objektech, jako je například binární strom. Typy, které rozšiřuje novou kolekci, budou definovat výčet silného typu a vystavit vlastnost silného typu.

## <a name="example"></a>Příklad
 Následující příklad ukazuje správný způsob, jak implementovat typ silného <xref:System.Collections.IEnumerator> typu.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1035: Implementace ICollection mají členy silného typu](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Seznamy jsou silného typu](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Viz také
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
