---
title: 'CA1049: Typy, které vlastní nativní prostředky, by měly být uvolnitelné'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: ef7b72eade7ea8e4486d5c317c06026bb4d0b95f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235733"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typy, které vlastní nativní prostředky, by měly být uvolnitelné

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Typ odkazuje na <xref:System.IntPtr?displayProperty=fullName> pole <xref:System.UIntPtr?displayProperty=fullName> , pole nebo <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> pole, ale neimplementuje <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo předpokládá, <xref:System.IntPtr>že <xref:System.UIntPtr>, a <xref:System.Runtime.InteropServices.HandleRef> pole ukládají ukazatele do nespravovaných prostředků. Typy, které přidělují nespravované <xref:System.IDisposable> prostředky, by měly implementovat, aby volajícím uvolnili tyto prostředky na vyžádání a zkrátili životnost objektů, které uchovávají prostředky.

Doporučený návrhový vzor pro vyčištění nespravovaných prostředků je poskytnout implicitní a explicitní způsob, jak uvolnit tyto prostředky pomocí <xref:System.Object.Finalize%2A?displayProperty=fullName> metody <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> a metody, v uvedeném pořadí. Systém uvolňování paměti volá <xref:System.Object.Finalize%2A> metodu objektu v neurčitém čase po zjištění, že je objekt již dostupný. Po <xref:System.Object.Finalize%2A> volání je vyžadován další uvolňování paměti pro uvolnění objektu. <xref:System.IDisposable.Dispose%2A> Metoda umožňuje volajícímu explicitně uvolnit prostředky na vyžádání, a to dříve, než budou prostředky uvolněny, pokud zbývá do uvolňování paměti. Po vyčištění nespravovaných prostředků <xref:System.IDisposable.Dispose%2A> by měla <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> zavolat metodu, aby systém uvolňování paměti věděl, že <xref:System.Object.Finalize%2A> již není nutné volat, což eliminuje nutnost dalšího uvolňování paměti a zkrátí doba života objektu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, implementujte <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Pokud typ neodkazuje na nespravovaný prostředek, je bezpečné potlačit upozornění od tohoto pravidla. V opačném případě potlačí upozornění z tohoto pravidla, protože selhání <xref:System.IDisposable> implementace může způsobit nedostupnost nespravovaných prostředků nebo nepoužívané.

## <a name="example"></a>Příklad
Následující příklad ukazuje typ, který implementuje <xref:System.IDisposable> k vyčištění nespravovaného prostředku.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA2115: Vyvolejte GC. Udržení naživu při použití nativních prostředků](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Vyvolejte GC. SuppressFinalize správně](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA2216: Typy na jedno použití by měly deklarovat finalizační metodu](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA1001: Typy, které vlastní pole na jedno použití, by měly být jednorázové.](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Viz také:

- [Vymazání nespravovaných prostředků](/dotnet/standard/garbage-collection/unmanaged)
- [Vzor pro metodu Dispose](/dotnet/standard/design-guidelines/dispose-pattern)