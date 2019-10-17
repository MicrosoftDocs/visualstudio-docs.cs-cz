---
title: 'CA1006: Nevnořujte obecné typy v signaturách členu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8e69a32e7215e9609d1e1cb2c23572997b11a7fc
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446901"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: Nevnořujte obecné typy v signaturách členu

|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Kategorie|Microsoft. Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Externě viditelný člen má signaturu, která obsahuje vnořený argument typu.

## <a name="rule-description"></a>Popis pravidla
Vnořený typ argumentu je typ argumentu, který je také obecným typem. Chce-li uživatel zavolat člen, jehož předpis obsahuje vnořený argument typu, musí nejprve vytvořit instanci jednoho obecného typu a předat tento typ konstruktoru druhého obecného typu. Potřebná procedura a syntaxe je složitá a je vhodné se jí vyhnout.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, změňte návrh pro odebrání vnořeného argumentu typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo. Poskytování generických v syntaxi, která je snadno srozumitelná a používá, zkracuje dobu potřebnou k tomu, abyste se seznámili a zvyšovali rychlost přijímání nových knihoven.

## <a name="example"></a>Příklad
Následující příklad ukazuje metodu, která je v rozporu s pravidlem a syntaxí, která je požadována pro volání porušené metody.

[!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
[!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA1005: Vyhněte se nadbytečným parametrům na obecných typech](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Kolekce musí implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Použijte instance obecných obslužných rutin události](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také:
[Obecné typy](/dotnet/csharp/programming-guide/generics/index)
