---
title: 'CA1403: Typy automatického rozložení by neměly být viditelné modelu COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8329c51e58478e1902f64232f4f2546418639e34
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440533"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typy automatického rozložení by neměly být viditelné modelu COM

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Typ hodnoty zobrazený v modelu COM (Component Object Model) je označen atributem <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> nastaveným na hodnotu <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla

typy rozložení <xref:System.Runtime.InteropServices.LayoutKind> jsou spravovány modulem CLR (Common Language Runtime). Rozložení těchto typů se může měnit mezi verzemi rozhraní .NET, což přerušuje klienty modelu COM, kteří očekávají konkrétní rozložení. Pokud není zadán atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute>, kompilátor C#, Visual Basic a C++ kompilátory určují [LayoutKind. auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) pro hodnoty typu.

Pokud není uvedeno jinak, jsou všechny veřejné, neobecné typy viditelné modelu COM a všechny neveřejné a obecné typy jsou neviditelné v modelu COM. Chcete-li však omezit falešně pozitivní hodnoty, toto pravidlo vyžaduje explicitní stanovení viditelnosti typu modelu COM. Obsahující sestavení musí být označeno s <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> nastavenou na `false` a typ musí být označený jako <xref:System.Runtime.InteropServices.ComVisibleAttribute> nastavený na `true`.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, změňte hodnotu atributu <xref:System.Runtime.InteropServices.StructLayoutAttribute> na [LayoutKind. Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) nebo [LayoutKind. sekvenční](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>)nebo nastavte typ jako neviditelný na com.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad

Následující příklad ukazuje typ, který porušuje pravidlo a typ, který splňuje pravidlo.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Související pravidla

[CA1408: Nepoužívejte AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Viz také:

- [Kvalifikovat typy .NET pro spoluprovozování](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)
