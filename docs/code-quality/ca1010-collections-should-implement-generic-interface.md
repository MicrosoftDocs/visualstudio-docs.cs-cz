---
title: 'CA1010: Kolekce musí implementovat obecné rozhraní'
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 066b9d013847f5362ee0dd712002cf8578fb57a6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236444"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Kolekce musí implementovat obecné rozhraní

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Typ implementuje <xref:System.Collections.IEnumerable?displayProperty=fullName> rozhraní, ale <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> neimplementuje rozhraní a nadřazené sestavení cílí na rozhraní .NET. Toto pravidlo ignoruje typy, <xref:System.Collections.IDictionary?displayProperty=fullName>které implementují.

Ve výchozím nastavení toto pravidlo vyhledává pouze externě viditelné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Použitelnost kolekce lze rozšířit implementací jednoho z rozhraní obecné kolekce. Potom lze kolekci použít k naplnění typů obecných kolekcí, jako jsou následující:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, implementujte jedno z následujících rozhraní Obecné kolekce:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Je bezpečné potlačit upozornění od tohoto pravidla; použití kolekce bude ale omezenější.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (návrh). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Příklad porušení

Následující příklad ukazuje třídu (typ odkazu), která je odvozena od neobecné `CollectionBase` třídy, která toto pravidlo porušuje.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Chcete-li opravit porušení tohoto pravidla, proveďte jednu z následujících akcí:

- Implementujte Obecná rozhraní.
- Změňte základní třídu na typ, který již implementuje obecná i neobecná rozhraní, jako je `Collection<T>` například třída.

## <a name="fix-by-base-class-change"></a>Opravit se změnou základní třídy

Následující příklad opravuje porušení změnou základní třídy kolekce z neobecné `CollectionBase` třídy na obecnou `Collection<T>` třídu (`Collection(Of T)` v Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

Změna základní třídy již vydané třídy je považována za zásadní změnu u stávajících příjemců.

## <a name="fix-by-interface-implementation"></a>Oprava podle implementace rozhraní

Následující příklad opravuje porušení implementací těchto obecných rozhraní `IEnumerable<T>`:, `ICollection<T>`, `IList(Of T)` a `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`a v Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Související pravidla

- [CA1005: Vyhnout se nadměrnému počtu parametrů u obecných typů](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002 Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 Nevnořovat obecné typy v signaturách členů](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Použití instancí obecných obslužných rutin událostí](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také:

- [Obecné typy](/dotnet/csharp/programming-guide/generics/index)