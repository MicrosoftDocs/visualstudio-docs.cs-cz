---
title: 'CA1000: Nedeklarujte statické členy v obecných typech'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4cc33c51af7d596fb9c784b76f8cc2f255ddf5a5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236717"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: Nedeklarujte statické členy v obecných typech

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Obecný typ obsahuje `static` člen (`Shared` v Visual Basic).

Ve výchozím nastavení toto pravidlo vyhledává pouze externě viditelné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Při volání `static` členu obecného typu musí být pro tento typ zadán argument typu. Je-li zavolán obecný člen instance, který nepodporuje odvozování, musí být pro tento člen zadán argument typu. Syntaxe pro určení argumentu typu v těchto dvou případech je odlišná a snadno zaměňována, protože následující volání ukazují:

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

Obecně platí, že obě předchozí deklarace by se měly vyhnout, aby se při volání člena nemusel zadat argument typu. Výsledkem je syntaxe pro volání členů v obecných typech, které se neliší od syntaxe pro neobecné typy. Další informace najdete v tématu [CA1004: Obecné metody by měly poskytnout parametr](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)typu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, odeberte statického člena nebo ho změňte na člen instance.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo. Poskytování generických v syntaxi, která je snadno srozumitelná a používá, zkracuje dobu potřebnou k tomu, abyste se seznámili a zvyšovali rychlost přijímání nových knihoven.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1000.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (návrh). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Související pravidla

- [CA1005: Vyhnout se nadměrnému počtu parametrů u obecných typů](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: Kolekce by měly implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1002 Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 Nevnořovat obecné typy v signaturách členů](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Použití instancí obecných obslužných rutin událostí](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také:

- [Obecné typy](/dotnet/csharp/programming-guide/generics/index)