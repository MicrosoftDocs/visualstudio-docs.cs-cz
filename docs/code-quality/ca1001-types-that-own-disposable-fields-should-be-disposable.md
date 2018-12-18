---
title: 'CA1001: Typy, které vlastní uvolnitelné pole by měly být uvolnitelné'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a73acee1c01aba7a638d27c0e772e4fbf5e19384
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546933"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typy, které vlastní uvolnitelné pole by měly být uvolnitelné

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategorie|Microsoft.Design|
|Narušující změna|Bez konce – Pokud typ není viditelný mimo sestavení.<br /><br /> Rozdělení – typ je viditelný mimo sestavení.|

## <a name="cause"></a>příčina
 Třída deklaruje a implementuje pole instance, která je <xref:System.IDisposable?displayProperty=fullName> typ a třída neimplementuje <xref:System.IDisposable>.

## <a name="rule-description"></a>Popis pravidla
 Třída implementuje <xref:System.IDisposable> rozhraní k uvolnění nespravovaných prostředků, které vlastní. Pole instance, která je <xref:System.IDisposable> označuje, že pole vlastní nespravovaný zdroj. Třída, která deklaruje <xref:System.IDisposable> pole nepřímo vlastní nespravovaný zdroj a měla by implementovat <xref:System.IDisposable> rozhraní. Pokud třída není přímo vlastníkem jakýchkoliv nespravovaných prostředků, neměly by implementovat finalizační metodu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, implementovat <xref:System.IDisposable> z a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> volání metody <xref:System.IDisposable.Dispose%2A> metoda pole.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje třídu, která porušuje pravidlo a třídy, která splňuje pravidlo implementací <xref:System.IDisposable>. Třída neimplementuje finalizační metodu, protože třída není přímo vlastníkem jakýchkoliv nespravovaných prostředků.

 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Související pravidla
 [CA2213: Uvolnitelné pole by mělo být uvolněno](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: Metody Dispose by měly volat uvolnění třídy Base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: Typy, které vlastní nativní prostředky by měly být uvolnitelné](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)