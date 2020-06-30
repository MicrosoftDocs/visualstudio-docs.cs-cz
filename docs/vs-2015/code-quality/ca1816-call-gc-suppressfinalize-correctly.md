---
title: 'CA1816: volání GC. SuppressFinalize správně | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 532478a8d6ed6b88347d196b4a74b6f19a38ef85
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546767"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Volejte správně GC.SuppressFinalize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategorie|Microsoft. Využití|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina

- Metoda, která je implementací, <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> nevolá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

- Metoda, která není implementací <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> volání <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

- Metoda volá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> a projde něco jiného než this (já v Visual Basic).

## <a name="rule-description"></a>Popis pravidla
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>Metoda umožňuje uživatelům uvolnit prostředky kdykoli předtím, než se objekt stane dostupným pro uvolnění paměti. Pokud <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> je metoda volána, uvolní prostředky objektu. To způsobuje nutnost finalizace. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>by mělo zavolat, <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> aby systém uvolňování paměti nevolal finalizační metodu objektu.

 Chcete-li zabránit odvozeným typům pomocí finalizační metody pro opětovné nasazení [System. IDisposable] (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) a pro jeho volání by se měly stále volat nezapečetěné typy bez finalizační metody <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla:

 Pokud je metoda implementací <xref:System.IDisposable.Dispose%2A> , přidejte volání do <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 Pokud metoda není implementací <xref:System.IDisposable.Dispose%2A> , buď odeberte volání <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> nebo ho přesuňte do <xref:System.IDisposable.Dispose%2A> implementace typu.

 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>Chcete-li to předat, změňte všechna volání na. (já v Visual Basic).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud záměrně používáte <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> k řízení životnosti jiných objektů, potlačí upozornění od tohoto pravidla. Potlačit upozornění z tohoto pravidla, pokud implementace <xref:System.IDisposable.Dispose%2A> nevolá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> . V takovém případě neúspěšné potlačení efektivity snižuje výkon a neposkytuje žádné výhody.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která nesprávně volá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která správně volá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2215: Metody Dispose by měly volat uvolnění základní třídy](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Viz také
 [Vzor pro metodu Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
