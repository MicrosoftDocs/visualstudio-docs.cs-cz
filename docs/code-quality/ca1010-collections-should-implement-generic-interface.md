---
title: 'CA1010: Kolekce musí implementovat obecné rozhraní'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5264292e6dc1e8cf86a64d41dc15154d836a8444
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915279"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Kolekce musí implementovat obecné rozhraní

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Externě viditelný typ implementuje <xref:System.Collections.IEnumerable?displayProperty=fullName> rozhraní, ale neimplementuje <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> rozhraní a obsahující cíle sestavení [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]. Toto pravidlo ignoruje typy, které implementují <xref:System.Collections.IDictionary?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 Použitelnost kolekce lze rozšířit implementací jednoho z rozhraní obecné kolekce. Potom kolekci lze použít k zaplnění typů obecných kolekcí, jako je následující:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, implementujte jednu z následujících rozhraní obecné kolekce:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla; kolekci však mají omezenější použití.

## <a name="example-violation"></a>Příklad porušení

### <a name="description"></a>Popis
 Následující příklad ukazuje třídu (odkaz), která je odvozena z neobecné `CollectionBase` třídu, která poruší toto pravidlo.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

### <a name="comments"></a>Komentáře
 Chcete-li opravit porušení toto porušení, by měla buď implementovat obecné rozhraní nebo změňte základní třídy na typ, který již implementuje oba obecných a neobecných rozhraní, jako například `Collection<T>` třídy.

## <a name="fix-by-base-class-change"></a>Opravit změnou základní třídy

### <a name="description"></a>Popis
 V následujícím příkladu řeší porušení změnou základní třídy kolekce z neobecné `CollectionBase` třídy obecného `Collection<T>` (`Collection(Of T)` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) třídy.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

### <a name="comments"></a>Komentáře
 Změna základní třídy již vydané třídy se považuje za rozbíjející změny stávajícím příjemcům.

## <a name="fix-by-interface-implementation"></a>Vyřešit tím, že implementace rozhraní

### <a name="description"></a>Popis
 V následujícím příkladu řeší porušení implementací těmito obecnými rozhraními: `IEnumerable<T>`, `ICollection<T>`, a `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, a `IList(Of T)` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Související pravidla
 [CA1005: Vyhněte se nadbytečným parametrům na obecných typech](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nevnořujte obecné typy v signaturách členu](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Použijte instance obecných obslužných rutin události](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také:
 [Obecné typy](/dotnet/csharp/programming-guide/generics/index)