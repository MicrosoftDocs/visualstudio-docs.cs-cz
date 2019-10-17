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
ms.openlocfilehash: 86dab876992227107beaa843412809a609ff1e4d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446903"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: Obecné metody by měly poskytnout parametr typu

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|Kategorie|Microsoft. Design|
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
Následující příklad ukazuje syntaxi pro volání dvou obecných metod. Argument typu pro `InferredTypeArgument` je odvozen a argument typu `NotInferredTypeArgument` musí být explicitně zadán.

[!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
[!code-csharp[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA1005: Vyhněte se nadbytečným parametrům na obecných typech](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Kolekce musí implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Nevnořujte obecné typy v signaturách členu](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1003: Použijte instance obecných obslužných rutin události](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také:
[Obecné typy](/dotnet/csharp/programming-guide/generics/index)
