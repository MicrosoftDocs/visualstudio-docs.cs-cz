---
title: 'CA1035: Implementace ICollection mají členy silného typu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bcf5218f41a11d50b6cc3f36767190cce5deab1b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545525"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Implementace ICollection mají členy silného typu

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ implementuje <xref:System.Collections.ICollection?displayProperty=fullName> ale neposkytuje metodu silného typu pro <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. Verzi silného typu <xref:System.Collections.ICollection.CopyTo%2A> musí přijmout dva parametry a nemůže mít <xref:System.Array?displayProperty=fullName> nebo pole <xref:System.Object?displayProperty=fullName> jako svůj první parametr.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo vyžaduje <xref:System.Collections.ICollection> implementace důrazně poskytovaly členy typu tak, aby uživatelé nebudou muset přetypovávat argumenty na <xref:System.Object> zadejte při využívání funkčnosti poskytované rozhraní. Toto pravidlo předpokládá, že tento typ, který implementuje <xref:System.Collections.ICollection> nemá chci spravovat kolekci instancí typu silnějšího než <xref:System.Object>.

 <xref:System.Collections.ICollection> implementuje <xref:System.Collections.IEnumerable?displayProperty=fullName> rozhraní. Pokud objekty v kolekci rozšíření <xref:System.ValueType?displayProperty=fullName>, je nutné zadat silného typu člena, který <xref:System.Collections.IEnumerable.GetEnumerator%2A> aby se zabránilo snížení výkonu, jež je způsobena zabalení. To není potřeba když jsou objekty kolekce typu odkazu.

 K implementaci verzi silného typu člena rozhraní implementovat členy rozhraní explicitně pomocí názvů ve formě `InterfaceName.InterfaceMemberName`, jako například <xref:System.Collections.ICollection.CopyTo%2A>. Členy explicitní rozhraní datové typy, které jsou deklarovány pomocí rozhraní. Implementovat členy silného typu pomocí názvu členu rozhraní <xref:System.Collections.ICollection.CopyTo%2A>. Deklarace členy se silnými typy jako veřejnou a deklarovat parametry a návratové hodnoty bude silného typu, který spravuje kolekci. Silné typy nahradit slabší typy, jako <xref:System.Object> a <xref:System.Array> , které jsou deklarovány pomocí rozhraní.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, implementovat člena rozhraní explicitně (deklarujte ho jako <xref:System.Collections.ICollection.CopyTo%2A>). Přidejte veřejnou silného typu člen deklarovaný jako `CopyTo`, a jeho trvat pole jako svůj první parametr silného typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění tohoto pravidla, pokud se rozhodnete implementovat nové založenou na objektech kolekce, jako je například binární strom, kde určit typy, které rozšiřují nová kolekce silného typu. Tyto typy by měly splňovat toto pravidlo a vystavit členy se silnými typy.

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