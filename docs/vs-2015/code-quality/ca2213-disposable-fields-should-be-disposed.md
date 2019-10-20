---
title: 'CA2213: pole na jedno použití by mělo být uvolněno | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8ebeae3e5e367bb2c1a09bc1cb38dcc80d2c3826
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662899"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Uvolnitelné pole by mělo být uvolněno
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Typ, který implementuje <xref:System.IDisposable?displayProperty=fullName>, deklaruje pole typů, která také implementují <xref:System.IDisposable>. Metoda <xref:System.IDisposable.Dispose%2A> pole není volána metodou <xref:System.IDisposable.Dispose%2A> deklarující typu.

## <a name="rule-description"></a>Popis pravidla
 Typ zodpovídá za likvidaci všech spravovaných prostředků; To je provedeno implementací <xref:System.IDisposable>. Toto pravidlo zkontroluje, zda `T` typ, který deklaruje pole `F`, které je instancí typu `FT`. Pro každé pole `F` se pravidlo pokusí vyhledat volání `FT.Dispose`. Pravidlo vyhledá metody volané `T.Dispose` a jednu nižší úroveň (metody volané metodami, které volá `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zavolejte <xref:System.IDisposable.Dispose%2A> pro pole, která jsou implementována <xref:System.IDisposable> Pokud zodpovídáte za přidělování a uvolňování nespravovaných prostředků držených polem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění od tohoto pravidla, pokud nezodpovídáte za uvolnění prostředku uloženého v poli nebo pokud volání <xref:System.IDisposable.Dispose%2A> dochází na hlubší úrovni volání než kontroly pravidla.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ `TypeA`, který implementuje <xref:System.IDisposable> (`FT` v předchozí diskuzi).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ `TypeB`, který porušuje toto pravidlo deklarováním pole `aFieldOfADisposableType` (`F` v předchozí diskusi) jako typ na jedno (`TypeA`) a nevolá <xref:System.IDisposable.Dispose%2A> v poli. `TypeB` odpovídá `T` v předchozí diskuzi.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Viz také
 [vzor Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb) <xref:System.IDisposable?displayProperty=fullName>
