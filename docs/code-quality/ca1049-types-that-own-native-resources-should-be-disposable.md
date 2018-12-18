---
title: 'CA1049: Typy, které vlastní nativní prostředky by měly být uvolnitelné'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: f9a2eeb032951df86d38075220c14fe98488edef
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551988"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typy, které vlastní nativní prostředky by měly být uvolnitelné

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina

Odkazuje na typ <xref:System.IntPtr?displayProperty=fullName> pole, <xref:System.UIntPtr?displayProperty=fullName> pole, nebo <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> pole, ale neimplementuje <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo předpokládá, že <xref:System.IntPtr>, <xref:System.UIntPtr>, a <xref:System.Runtime.InteropServices.HandleRef> ukládání pole ukazatelů na nespravované prostředky. Typy, které přidělují nespravované prostředky by měly implementovat <xref:System.IDisposable> umožníte volajícím uvolnit tyto prostředky na požádání a zkrátit životní cyklus objektů, které obsahují prostředky.

Doporučený návrhový vzor pro vyčištění nespravovaných prostředků je poskytnout implicitní a explicitní znamená, že k uvolnění těchto prostředků s použitím <xref:System.Object.Finalize%2A?displayProperty=fullName> metoda a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metoda, v uvedeném pořadí. Uvolňování paměti zavolá <xref:System.Object.Finalize%2A> metodu objektu v době, po objektu je určena být již nebude dostupná. Po <xref:System.Object.Finalize%2A> je volána, zobrazí se další uvolňování paměti se vyžaduje k uvolnění objektu. <xref:System.IDisposable.Dispose%2A> Metoda umožňuje volajícímu explicitně uvolnit prostředky na vyžádání, dříve, než prostředky by být uvolněny, pokud zleva systému uvolňování paměti. Poté, co ho vyčistí nespravované prostředky, <xref:System.IDisposable.Dispose%2A> by měly volat <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> metoda umožňuje systému uvolňování paměti vědět, že <xref:System.Object.Finalize%2A> není k dispozici k volání; tím se eliminuje potřeba další uvolnění paměti a tím Doba života objektu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, implementovat <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, pokud typ neobsahuje odkaz nespravovaný prostředek. V opačném případě nepotlačujte upozornění tohoto pravidla protože neschopnost implementace <xref:System.IDisposable> může způsobit, že budou k dispozici nebo využívané uvolnění nespravovaných prostředků.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který implementuje <xref:System.IDisposable> pro vyčištění nespravovaných prostředků.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Související pravidla
 [CA2115: Volejte GC.KeepAlive při použití nativních zdrojů](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Volejte správně GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: Typy vlastních uvolnitelných polí, které by měly být uvolnitelné](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Viz také:

- [Vymazání nespravovaných prostředků](/dotnet/standard/garbage-collection/unmanaged)
- [Vzor pro metodu Dispose](/dotnet/standard/design-guidelines/dispose-pattern)