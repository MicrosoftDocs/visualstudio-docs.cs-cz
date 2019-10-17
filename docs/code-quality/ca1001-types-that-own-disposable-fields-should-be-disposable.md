---
title: 'CA1001: Typy, které vlastní uvolnitelné pole by měly být uvolnitelné'
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
ms.openlocfilehash: f49624e4e39bb0b3c1a0c1be7f32e797536d30eb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431791"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typy, které vlastní uvolnitelné pole by měly být uvolnitelné

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategorie|Microsoft. Design|
|Zásadní změna|Bez přerušení – Pokud typ není viditelný vně sestavení.<br /><br /> Přerušení – Pokud je typ viditelný mimo sestavení.|

## <a name="cause"></a>příčina
Třída deklaruje a implementuje pole instance, které je typu <xref:System.IDisposable?displayProperty=fullName> a třída neimplementuje <xref:System.IDisposable>.

## <a name="rule-description"></a>Popis pravidla
Třída implementuje rozhraní <xref:System.IDisposable> pro uvolnění nespravovaných prostředků, které vlastní. Pole instance, které je typu <xref:System.IDisposable> označuje, že pole vlastní nespravovaný prostředek. Třída, která deklaruje pole <xref:System.IDisposable> nepřímo vlastní nespravovaný prostředek a má implementovat rozhraní <xref:System.IDisposable>. Pokud třída přímo nevlastní žádné nespravované prostředky, neměli byste implementovat finalizační metodu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, implementujte <xref:System.IDisposable> a z metody <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> volejte metodu <xref:System.IDisposable.Dispose%2A> pole.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje třídu, která porušuje pravidlo a třídu, která splňuje pravidlo pomocí implementace <xref:System.IDisposable>. Třída neimplementuje finalizační metodu, protože třída přímo nevlastní žádné nespravované prostředky.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA2213: Uvolnitelné pole by mělo být uvolněno](../code-quality/ca2213.md)

[CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216.md)

[CA2215: Metody Dispose by měly volat uvolnění třídy Base](../code-quality/ca2215.md)

[CA1049: Typy, které vlastní nativní prostředky by měly být uvolnitelné](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
