---
title: 'CA2241: Poskytněte správné argumenty pro metody formátování | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 112065b2a8b9a88241ce62dda7b32a2f2c22fc75
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672018"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Poskytněte správné argumenty metodě formátování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Argument řetězce `format` předaný metodě jako <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> nebo <xref:System.String.Format%2A?displayProperty=fullName> neobsahuje položku formátu, která odpovídá každému argumentu objektu, nebo naopak.

## <a name="rule-description"></a>Popis pravidla
 Argumenty metody jako <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> a <xref:System.String.Format%2A> se skládají z formátovacího řetězce následovaného několika instancemi <xref:System.Object?displayProperty=fullName>. Formátovací řetězec se skládá z položek textu a vloženého formátu ve formuláři, {index [, Alignment] [: formatString]}. ' index ' je celé číslo založené na nule, které určuje, které objekty mají být naformátované. Pokud objekt nemá odpovídající index ve formátovacím řetězci, objekt se ignoruje. Pokud objekt určený parametrem index neexistuje, <xref:System.FormatException?displayProperty=fullName> je vyvolána za běhu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zadejte položku formátu pro každý argument objektu a zadejte argument objektu pro každou položku formátu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dvě porušení pravidla.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
