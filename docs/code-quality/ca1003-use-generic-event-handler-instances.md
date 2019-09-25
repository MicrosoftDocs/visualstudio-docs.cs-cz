---
title: 'CA1003: Použijte instance obecných obslužných rutin události'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c654da177e4a9cf820887cf74977a4c3da5a57b6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236645"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Použijte instance obecných obslužných rutin události

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Typ obsahuje delegát, který vrací typ void a jehož signatura obsahuje dva parametry (první objekt a druhý typ, který lze přiřadit k EventArgs), a obsahující sestavení cílí na rozhraní .NET.

Ve výchozím nastavení toto pravidlo vyhledává pouze externě viditelné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Před rozhraním .NET, aby bylo možné předat vlastní informace obslužné rutině události, bylo nutné deklarovat nového delegáta, který zadal třídu odvozenou od <xref:System.EventArgs?displayProperty=fullName> třídy. V rozhraní .NET obecného <xref:System.EventHandler%601?displayProperty=fullName> delegáta umožňuje použití libovolné třídy odvozené z <xref:System.EventArgs> , která je použita společně s obslužnou rutinou události.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, odeberte delegáta a nahraďte jeho použití pomocí <xref:System.EventHandler%601?displayProperty=fullName> delegáta.

Pokud je delegát automaticky vygenerován kompilátorem Visual Basic, změňte syntaxi deklarace události pro použití <xref:System.EventHandler%601?displayProperty=fullName> delegáta.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (návrh). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje delegáta, který porušuje pravidlo. V příkladu Visual Basic komentáře popisují, jak upravit příklad pro splnění pravidla. C# Například následující příklad ukazuje upravený kód.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

Následující fragment kódu odebere deklaraci delegáta z předchozího příkladu, který splňuje pravidlo. Nahrazuje použití v `ClassThatRaisesEvent` metodách a `ClassThatHandlesEvent` pomocí <xref:System.EventHandler%601?displayProperty=fullName> delegáta.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Související pravidla

- [CA1005: Vyhnout se nadměrnému počtu parametrů u obecných typů](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: Kolekce by měly implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002 Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 Nevnořovat obecné typy v signaturách členů](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také:

- [Obecné typy](/dotnet/csharp/programming-guide/generics/index)