---
title: 'CA1004: Obecné metody by měly poskytnout parametr typu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f4c5f9c001505a76f19f2d675d552124c611f3d5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236630"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: Obecné metody by měly poskytnout parametr typu

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Signatura parametru externě viditelné obecné metody neobsahuje typy, které odpovídají všem parametrům typu metody.

## <a name="rule-description"></a>Popis pravidla
Argument typu obecné metody je z argumentu typu předávaného metodě odvozen namísto explicitního určení argumentu typu. Má-li být odvozování povoleno, musí předpis parametrů obecné metody zahrnovat parametr stejného typu jako parametr typu metody. V tomto případě nemusí být argument typu zadán. Použijete-li odvození pro všechny parametry typu, syntaxe pro volání generických a neobecných metod instance je shodná. To zjednodušuje použitelnost obecných metod.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, změňte návrh tak, aby signatura parametru obsahovala stejný typ pro každý parametr typu metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo. Poskytování generických v syntaxi, která je snadno srozumitelná a používá, zkracuje dobu potřebnou k tomu, abyste se seznámili a zvyšovali rychlost přijímání nových knihoven.

## <a name="example"></a>Příklad
Následující příklad ukazuje syntaxi pro volání dvou obecných metod. Argument typu pro `InferredTypeArgument` je odvozený a argument typu pro `NotInferredTypeArgument` musí být explicitně zadaný.

[!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
[!code-csharp[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA1005: Vyhnout se nadměrnému počtu parametrů u obecných typů](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Kolekce by měly implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002 Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006 Nevnořovat obecné typy v signaturách členů](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1003: Použití instancí obecných obslužných rutin událostí](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také:
[Obecné typy](/dotnet/csharp/programming-guide/generics/index)