---
title: 'CA1007: Použijte obecné typy, kde je to vhodné'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0d7783bea936b04fcb600563dadea6a65ac5ef5e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236524"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Použijte obecné typy, kde je to vhodné

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Externě viditelná metoda obsahuje referenční parametr typu <xref:System.Object?displayProperty=fullName>a sestavení obsahující cíle .NET Framework 2,0.

## <a name="rule-description"></a>Popis pravidla
Parametr reference je parametr, který je upraven pomocí `ref` klíčového slova (`ByRef` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Typ argumentu, který je zadán pro parametr odkazu, musí přesně odpovídat typu referenčního parametru. Chcete-li použít typ, který je odvozen z typu parametru reference, typ musí být nejprve převeden a přiřazen proměnné typu referenčního parametru. Použití obecné metody umožňuje všem typům, které podléhají omezením, předávat metodě bez předchozího přetypování typu na typ referenčního parametru.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, proveďte obecné metody a nahraďte <xref:System.Object> parametr pomocí parametru typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje rutinu swapu pro obecné účely, která je implementována jako neobecné a obecné metody. Všimněte si, jak efektivně jsou řetězce zahozeny pomocí obecné metody v porovnání s neobecnou metodou.

[!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
[!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA1005: Vyhnout se nadměrnému počtu parametrů u obecných typů](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Kolekce by měly implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002 Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006 Nevnořovat obecné typy v signaturách členů](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Použití instancí obecných obslužných rutin událostí](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Viz také:
[Obecné typy](/dotnet/csharp/programming-guide/generics/index)