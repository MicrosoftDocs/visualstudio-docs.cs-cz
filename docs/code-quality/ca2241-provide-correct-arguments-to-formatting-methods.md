---
title: 'CA2241: Zadejte správné argumenty pro metody formátování'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 10a4cdaa1e2de768cadc569424a490aa4adb7135
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253216"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Zadejte správné argumenty pro metody formátování

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Řetězcový argument předaný metodě <xref:System.Console.WriteLine%2A>jako, <xref:System.Console.Write%2A>nebo <xref:System.String.Format%2A?displayProperty=fullName> neobsahuje položku formátu, která odpovídá jednotlivým argumentům objektu, nebo naopak. `format`

## <a name="rule-description"></a>Popis pravidla
Argumenty metody jako <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>a <xref:System.String.Format%2A> se skládají z formátovacího řetězce následovaného několika <xref:System.Object?displayProperty=fullName> instancemi. Formátovací řetězec se skládá z položek textu a vloženého formátu ve formuláři, {index [, Alignment] [: formatString]}. ' index ' je celé číslo založené na nule, které určuje, které objekty mají být naformátované. Pokud objekt nemá odpovídající index ve formátovacím řetězci, objekt se ignoruje. Pokud objekt určený pomocí ' index ' neexistuje, <xref:System.FormatException?displayProperty=fullName> je vyvolána v době běhu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, zadejte položku formátu pro každý argument objektu a zadejte argument objektu pro každou položku formátu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje dvě porušení pravidla.

[!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
[!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]