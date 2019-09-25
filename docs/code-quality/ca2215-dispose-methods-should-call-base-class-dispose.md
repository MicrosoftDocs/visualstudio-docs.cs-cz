---
title: 'CA2215: Metody Dispose by měly volat uvolnění základní třídy'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 468b63ca554ea126bbd621a2502e54540e6ed068
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231284"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Metody Dispose by měly volat uvolnění základní třídy

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Typ, který implementuje <xref:System.IDisposable?displayProperty=fullName> dědí z typu, který také implementuje <xref:System.IDisposable>. Metoda dědění typu nevolá <xref:System.IDisposable.Dispose%2A> metodu nadřazeného typu. <xref:System.IDisposable.Dispose%2A>

## <a name="rule-description"></a>Popis pravidla
Pokud typ dědí z typu na jedno použití, musí volat <xref:System.IDisposable.Dispose%2A> metodu základního typu v rámci své vlastní <xref:System.IDisposable.Dispose%2A> metody. Volání metody Dispose základní typ zajistí, že budou uvolněny všechny prostředky vytvořené základním typem.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, zavolejte `base`.<xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable.Dispose%2A> v metodě.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
V případě volání metody `base`je bezpečné potlačit upozornění od tohoto pravidla.<xref:System.IDisposable.Dispose%2A> nastane na hlubší úrovni volání než kontroly pravidla.

## <a name="example"></a>Příklad
Následující příklad ukazuje typ `TypeA` , který implementuje. <xref:System.IDisposable>

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Příklad
Následující příklad ukazuje typ `TypeB` , který dědí z typu `TypeA` a správně volá jeho <xref:System.IDisposable.Dispose%2A> metodu.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Viz také:

- <xref:System.IDisposable?displayProperty=fullName>
- [Vzor pro metodu Dispose](/dotnet/standard/design-guidelines/dispose-pattern)