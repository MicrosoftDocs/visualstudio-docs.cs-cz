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
ms.openlocfilehash: acc86c278faa877897d294e72632762eff834a76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668388"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Volejte správně GC.SuppressFinalize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategorie|Microsoft. Použití|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina

- Metoda, která je implementací <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, nevolá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Metoda, která není implementací <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> volá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

- Metoda volá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> a předá něco jiného než to (já v Visual Basic).

## <a name="rule-description"></a>Popis pravidla
 Metoda <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> umožňuje uživatelům uvolnit prostředky kdykoli předtím, než se objekt stane dostupným pro uvolňování paměti. Pokud je volána metoda <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, uvolní prostředky objektu. To způsobuje nutnost finalizace. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> by měl volat <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>, aby systém uvolňování paměti nevolal finalizační metodu objektu.

 Chcete-li zabránit odvozeným typům pomocí finalizační metody pro opětovné nasazení [System. IDisposable] (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) a pro jeho volání by měly být nezapečetěné typy bez finalizační metody nadále volány <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla:

 Pokud je metodou implementace <xref:System.IDisposable.Dispose%2A>, přidejte volání <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 Pokud metoda není implementací <xref:System.IDisposable.Dispose%2A>, buď odeberte volání pro <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> nebo ho přesuňte do implementace <xref:System.IDisposable.Dispose%2A> typu.

 Pokud to chcete předat, změňte všechna volání na <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> (já v Visual Basic).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud záměrně používáte <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> k řízení životnosti jiných objektů, potlačí upozornění od tohoto pravidla. Potlačit upozornění z tohoto pravidla, pokud implementace <xref:System.IDisposable.Dispose%2A> nevolá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. V takovém případě neúspěšné potlačení efektivity snižuje výkon a neposkytuje žádné výhody.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která nesprávně volá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která správně volá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2215: Metody Dispose by měly volat uvolnění třídy Base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Viz také
 [Vzor pro metodu Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
