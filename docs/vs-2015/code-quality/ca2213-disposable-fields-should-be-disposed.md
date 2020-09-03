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
ms.openlocfilehash: 887600bad0c3d05ff78050aa4449cf49dc882027
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534573"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Uvolnitelná pole by měla být uvolněna
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Typ, který implementuje <xref:System.IDisposable?displayProperty=fullName> deklaraci polí typů, které také implementují <xref:System.IDisposable> . <xref:System.IDisposable.Dispose%2A>Metoda pole není volána metodou deklarovaného <xref:System.IDisposable.Dispose%2A> typu.

## <a name="rule-description"></a>Popis pravidla
 Typ zodpovídá za likvidaci všech spravovaných prostředků; To je provedeno implementací <xref:System.IDisposable> . Toto pravidlo zkontroluje, zda typ jednorázového `T` objektu deklaruje pole `F` , které je instancí typu na jedno použití `FT` . Pro každé pole `F` se pravidlo pokusí vyhledat volání `FT.Dispose` . Pravidlo vyhledá metody volané `T.Dispose` a jednu nižší úroveň (metody volané metodami, které volá `FT.Dispose` ).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zavolejte <xref:System.IDisposable.Dispose%2A> na pole, která jsou typu implementovaná, <xref:System.IDisposable> Pokud zodpovídáte za přidělování a uvolňování nespravovaných prostředků držených polem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění od tohoto pravidla, pokud nezodpovídáte za uvolnění prostředku, který je držen polem, nebo pokud volání <xref:System.IDisposable.Dispose%2A> proběhne na hlubší úrovni volání než kontroly pravidla.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ `TypeA` , který implementuje <xref:System.IDisposable> ( `FT` v předchozí diskuzi).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ `TypeB` , který toto pravidlo porušuje deklarováním pole `aFieldOfADisposableType` ( `F` v předchozí diskusi) jako typu na jedno použití ( `TypeA` ) a nevoláním <xref:System.IDisposable.Dispose%2A> pole. `TypeB` odpovídá `T` v předchozí diskusi.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.IDisposable?displayProperty=fullName>[Vzor Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
