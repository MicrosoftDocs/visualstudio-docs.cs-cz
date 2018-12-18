---
title: 'CA1039: Seznamy jsou silného typu. | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 681c1ada7600743c0a548f8a774dada6863f7d0d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853412"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Seznamy jsou silného typu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ implementuje <xref:System.Collections.IList?displayProperty=fullName> ale neposkytuje metodu silného typu pro jeden nebo více z následujících akcí:

-   IList.Item

-   IList.Add

-   IList.Contains

-   IList.IndexOf

-   IList.Insert

-   IList.Remove

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo vyžaduje <xref:System.Collections.IList> implementace důrazně poskytovaly členy typu tak, aby uživatelé nebudou muset přetypovávat argumenty na <xref:System.Object?displayProperty=fullName> zadejte při využívání funkčnosti poskytované rozhraní. <xref:System.Collections.IList> Rozhraní je implementováno kolekce objektů, které lze využívat pomocí indexu. Toto pravidlo předpokládá, že tento typ, který implementuje <xref:System.Collections.IList> to spravovat kolekci instancí typu silnějšího než <xref:System.Object>.

 <xref:System.Collections.IList> implementuje <xref:System.Collections.ICollection?displayProperty=fullName> a <xref:System.Collections.IEnumerable?displayProperty=fullName> rozhraní. Pokud se rozhodnete implementovat <xref:System.Collections.IList>, je nutné zadat požadované členy silného typu pro <xref:System.Collections.ICollection>. Pokud objekty v kolekci rozšíření <xref:System.ValueType?displayProperty=fullName>, je nutné zadat silného typu člena, který <xref:System.Collections.IEnumerable.GetEnumerator%2A> aby se zabránilo snížení výkonu, který je způsobeno tím, zabalení, tento krok není povinný když jsou objekty kolekce typu odkazu.

 Pro dosažení souladu s tímto pravidlem, implementovat členy rozhraní explicitně pomocí názvů v podobě InterfaceName.InterfaceMemberName, jako například <xref:System.Collections.IList.Add%2A>. Členy explicitní rozhraní datové typy, které jsou deklarovány pomocí rozhraní. Implementovat členy silného typu pomocí názvu členu rozhraní `Add`. Deklarace členy se silnými typy jako veřejnou a deklarovat parametry a návratové hodnoty bude silného typu, který spravuje kolekci. Silné typy nahradit slabší typy, jako <xref:System.Object> a <xref:System.Array> , které jsou deklarovány pomocí rozhraní.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, explicitně implementovat <xref:System.Collections.IList> členy a nabízí alternativu silného typu pro členy, které jste si poznamenali dříve. Pro kód, který implementuje správně <xref:System.Collections.IList> rozhraní a poskytuje požadované členy se silnými typy, viz následující příklad.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění tohoto pravidla, Pokud implementujete nové založenou na objektech kolekce, jako je například propojený seznam, kde určit typy, které rozšiřují nová kolekce silného typu. Tyto typy by měly splňovat toto pravidlo a vystavit členy se silnými typy.

## <a name="example"></a>Příklad
 V následujícím příkladu typ `YourType` rozšiřuje <xref:System.Collections.CollectionBase?displayProperty=fullName>, jako by všechny kolekce silného typu. Všimněte si, že <xref:System.Collections.CollectionBase> poskytuje explicitní implementaci <xref:System.Collections.IList> rozhraní za vás. Proto musíte zadat jenom členy se silnými typy pro <xref:System.Collections.IList> a <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1035: Implementace ICollection mají členy silného typu](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Enumerátory by měly být silného typu](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Viz také
 <xref:System.Collections.CollectionBase?displayProperty=fullName><xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>



