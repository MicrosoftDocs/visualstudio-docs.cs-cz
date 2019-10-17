---
title: 'CA1026: Neměly by být použity výchozí parametry'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bf388af2b39c9a10b58645f274a03739d60f23e
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449285"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Neměly by být použity výchozí parametry

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Kategorie|Microsoft. Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Externě viditelný typ obsahuje externě viditelnou metodu, která používá výchozí parametr.

## <a name="rule-description"></a>Popis pravidla
Metody používající výchozí parametry jsou povoleny v rámci specifikace CLS (Common Language Specification); specifikace CLS však umožňuje kompilátorům ignorovat hodnoty, které jsou přiřazeny těmto parametrům. Kód, který je napsán pro kompilátory, které ignorují výchozí hodnoty parametrů, musí explicitně zadat argumenty pro každý výchozí parametr. Chcete-li zachovat chování, které chcete v programovacích jazycích, metody, které používají výchozí parametry, by měly být nahrazeny přetíženími metod, které poskytují výchozí parametry.

Kompilátor C++ při přístupu ke spravovanému kódu ignoruje hodnoty výchozích parametrů pro spravované rozšíření. Kompilátor Visual Basic podporuje metody, které mají výchozí parametry, které používají klíčové slovo [Optional](/dotnet/visual-basic/language-reference/modifiers/optional) .

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, nahraďte metodu, která používá výchozí parametry, pomocí přetížení metod, které poskytují výchozí parametry.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje metodu, která používá výchozí parametry a přetížené metody, které poskytují ekvivalentní funkce.

[!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA1025: Nahraďte opakované argumenty polem parametrů](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Viz také:
[Jazyková nezávislost a jazykově nezávislé komponenty](/dotnet/standard/language-independence-and-language-independent-components)
