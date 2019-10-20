---
title: 'CA1049: typy, které vlastní nativní prostředky by měly být na jedno použití | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aaaf95346c51e2cb5cadb01a39e482bb508bc764
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668910"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typy, které vlastní nativní prostředky by měly být uvolnitelné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Typ odkazuje na pole <xref:System.IntPtr?displayProperty=fullName>, pole <xref:System.UIntPtr?displayProperty=fullName> nebo pole <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, ale neimplementuje <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo předpokládá, že pole <xref:System.IntPtr>, <xref:System.UIntPtr> a <xref:System.Runtime.InteropServices.HandleRef> ukládají ukazatele na nespravované prostředky. Typy, které přidělují nespravované prostředky, by měly implementovat <xref:System.IDisposable>, aby volající mohli tyto prostředky uvolnit na vyžádání a zkrátit životnost objektů, které uchovávají prostředky.

 Doporučený návrhový vzor pro vyčištění nespravovaných prostředků je poskytnout implicitní a explicitní způsob, jak uvolnit tyto prostředky pomocí metody <xref:System.Object.Finalize%2A?displayProperty=fullName> a metody <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, v uvedeném pořadí. Systém uvolňování paměti volá metodu <xref:System.Object.Finalize%2A> objektu v neurčitém čase po zjištění, že je objekt již dostupný. Po volání <xref:System.Object.Finalize%2A> se vyžaduje další uvolnění paměti pro uvolnění objektu. Metoda <xref:System.IDisposable.Dispose%2A> umožňuje volajícímu explicitně uvolnit prostředky na vyžádání, a to dříve, než budou prostředky uvolněny, pokud se nachází v systému uvolňování paměti. Po vyčištění nespravovaných prostředků by <xref:System.IDisposable.Dispose%2A> měla zavolat metodu <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>, aby systém uvolňování paměti mohl zjistit, že <xref:System.Object.Finalize%2A> již není nutné volat; Tím se eliminuje nutnost dalšího uvolňování paměti a zkrátí životnost objektu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, implementujte <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud typ neodkazuje na nespravovaný prostředek, je bezpečné potlačit upozornění od tohoto pravidla. V opačném případě nedoporučujeme potlačit upozornění z tohoto pravidla, protože selhání implementace <xref:System.IDisposable> může způsobit, že nespravované prostředky nebudou dostupné nebo nepoužívané.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který implementuje <xref:System.IDisposable> pro vyčištění nespravovaného prostředku.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2115: Volejte GC.KeepAlive při použití nativních zdrojů](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Volejte správně GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: Typy vlastních uvolnitelných polí, které by měly být uvolnitelné](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Viz také
  [Vzor pro metodu Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
