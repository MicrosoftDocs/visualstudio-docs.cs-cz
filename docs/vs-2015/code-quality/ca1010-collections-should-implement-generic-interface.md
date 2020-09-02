---
title: 'CA1010: kolekce by měly implementovat obecné rozhraní | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b141d755c717ad6650d2a49c98c2b26547066b7a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545519"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Kolekce musí implementovat obecné rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Externě viditelný typ implementuje <xref:System.Collections.IEnumerable?displayProperty=fullName> rozhraní, ale neimplementuje <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> rozhraní a obsahuje cíle sestavení [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] . Toto pravidlo ignoruje typy, které implementují <xref:System.Collections.IDictionary?displayProperty=fullName> .

## <a name="rule-description"></a>Popis pravidla
 Použitelnost kolekce lze rozšířit implementací jednoho z rozhraní obecné kolekce. Potom lze kolekci použít k naplnění typů obecných kolekcí, jako jsou následující:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, implementujte jedno z následujících rozhraní Obecné kolekce:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění od tohoto pravidla; kolekce však bude mít více omezeného použití.

## <a name="example-violation"></a>Příklad porušení

### <a name="description"></a>Popis
 Následující příklad ukazuje třídu (typ odkazu), která je odvozena od neobecné `CollectionBase` třídy, která toto pravidlo porušuje.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>Komentáře
 Chcete-li opravit porušení tohoto porušení, měli byste buď implementovat Obecná rozhraní, nebo změnit základní třídu na typ, který již implementuje obecná i neobecná rozhraní, jako je například `Collection<T>` Třída.

## <a name="fix-by-base-class-change"></a>Opravit se změnou základní třídy

### <a name="description"></a>Popis
 Následující příklad opravuje porušení změnou základní třídy kolekce z neobecné `CollectionBase` třídy na obecnou `Collection<T>` ( `Collection(Of T)` v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) třídu.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>Komentáře
 Změna základní třídy již vydané třídy je považována za zásadní změnu u stávajících příjemců.

## <a name="fix-by-interface-implementation"></a>Oprava podle implementace rozhraní

### <a name="description"></a>Popis
 Následující příklad opravuje porušení implementací těchto obecných rozhraní: `IEnumerable<T>` , `ICollection<T>` , a `IList<T>` (, a `IEnumerable(Of T)` `ICollection(Of T)` `IList(Of T)` v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1005: Vyhněte se nadbytečným parametrům u obecných typů](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nevnořujte obecné typy do signatur členu](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Použijte instance obecných obslužných rutin události](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také
 [Obecné typy](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
