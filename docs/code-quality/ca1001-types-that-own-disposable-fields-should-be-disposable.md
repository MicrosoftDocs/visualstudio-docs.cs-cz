---
title: 'CA1001: Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3bda8fc80992a2246c30e28582eb93b4624ab81c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236682"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategorie|Microsoft.Design|
|Zásadní změna|Bez přerušení – Pokud typ není viditelný vně sestavení.<br /><br /> Přerušení – Pokud je typ viditelný mimo sestavení.|

## <a name="cause"></a>příčina
Třída deklaruje a implementuje pole instance, které je <xref:System.IDisposable?displayProperty=fullName> typu a třída neimplementuje. <xref:System.IDisposable>

## <a name="rule-description"></a>Popis pravidla
Třída implementuje <xref:System.IDisposable> rozhraní pro uvolnění nespravovaných prostředků, které vlastní. Pole instance, které je <xref:System.IDisposable> typu, označuje, že pole vlastní nespravovaný prostředek. Třída, která deklaruje <xref:System.IDisposable> pole nepřímo vlastní nespravovaný prostředek a měla by <xref:System.IDisposable> implementovat rozhraní. Pokud třída přímo nevlastní žádné nespravované prostředky, neměli byste implementovat finalizační metodu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, implementujte <xref:System.IDisposable> a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> z metody zavolejte <xref:System.IDisposable.Dispose%2A> metodu pole.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje třídu, která porušuje pravidlo a třídu, která splňuje pravidlo implementací <xref:System.IDisposable>. Třída neimplementuje finalizační metodu, protože třída přímo nevlastní žádné nespravované prostředky.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA2213: Pole na jedno použití by mělo být uvolněno](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

[CA2216: Typy na jedno použití by měly deklarovat finalizační metodu](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA2215: Metody Dispose by měly volat uvolnění základní třídy.](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

[CA1049: Typy, které vlastní nativní prostředky by měly být na jedno použití](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)