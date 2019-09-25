---
title: 'CA1816: Volejte správně GC.SuppressFinalize'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3fdd20df37586e50b5236872f1d84de48d08c87a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233530"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Volejte správně GC.SuppressFinalize

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategorie|Microsoft. Použití|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Porušení tohoto pravidla mohou způsobovat tyto příčiny:

- Metoda, která je implementací <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> a nevolá. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

- Metoda, která není implementací <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> a volání. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

- Metoda, která volá <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> a projde něco jiného než [This (C#)](/dotnet/csharp/language-reference/keywords/this) nebo [mne (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Popis pravidla

<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> Metoda umožňuje uživatelům uvolnit prostředky kdykoli předtím, než se objekt stane dostupným pro uvolnění paměti. Pokud je <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metoda volána, uvolní prostředky objektu. To způsobuje nutnost finalizace. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>by mělo <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> zavolat, aby systém uvolňování paměti nevolal finalizační metodu objektu.

Chcete-li zabránit odvozeným typům pomocí finalizační metody, <xref:System.IDisposable> aby bylo možné je znovu implementovat a volat, nezapečetěné typy bez finalizační <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>metody by měly pořád volat.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla:

- Pokud je metoda implementací <xref:System.IDisposable.Dispose%2A>, přidejte volání do. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

- Pokud metoda není implementací <xref:System.IDisposable.Dispose%2A>, buď odeberte <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> volání nebo <xref:System.IDisposable.Dispose%2A> ho přesuňte do implementace typu.

- Změňte všechna volání <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> na k předání [tohoto (C#)](/dotnet/csharp/language-reference/keywords/this) nebo [mne (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pokud záměrně nepoužíváte <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> k řízení životnosti jiných objektů, potlačí upozornění od tohoto pravidla. Potlačí upozornění z tohoto pravidla, pokud implementace <xref:System.IDisposable.Dispose%2A> nevolá. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> V takovém případě neúspěšné potlačení efektivity snižuje výkon a neposkytuje žádné výhody.

## <a name="example-that-violates-ca1816"></a>Příklad, který porušuje CA1816

Tento kód ukazuje metodu, která volá <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>, ale neprojde [tuto (C#)](/dotnet/csharp/language-reference/keywords/this) nebo [mne (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). V důsledku toho tento kód porušuje pravidla CA1816.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Příklad, který splňuje CA1816

Tento příklad ukazuje metodu, která správně volá <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> předáním [This (C#)](/dotnet/csharp/language-reference/keywords/this) nebo [mě (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Související pravidla

- [CA2215: Metody Dispose by měly volat uvolnění základní třídy.](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: Typy na jedno použití by měly deklarovat finalizační metodu](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Viz také:

- [Vzor Dispose](/dotnet/standard/design-guidelines/dispose-pattern)