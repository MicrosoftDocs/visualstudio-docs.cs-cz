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
ms.openlocfilehash: 4e590514247444d32d0d9a31b2bbc409434cf53c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234823"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typy automatického rozložení by neměly být viditelné modelu COM

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Typ hodnoty zobrazený v modelu COM (Component Object Model) je označen <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> atributem nastaveným na <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>hodnotu.

## <a name="rule-description"></a>Popis pravidla

<xref:System.Runtime.InteropServices.LayoutKind>typy rozložení jsou spravovány modulem CLR (Common Language Runtime). Rozložení těchto typů se může měnit mezi verzemi rozhraní .NET, což přerušuje klienty modelu COM, kteří očekávají konkrétní rozložení. Pokud atribut není C#zadán, kompilátor, Visual Basic a C++ kompilátory určují hodnoty [LayoutKind. auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) pro typy hodnot. <xref:System.Runtime.InteropServices.StructLayoutAttribute>

Pokud není uvedeno jinak, jsou všechny veřejné, neobecné typy viditelné modelu COM a všechny neveřejné a obecné typy jsou neviditelné v modelu COM. Chcete-li však omezit falešně pozitivní hodnoty, toto pravidlo vyžaduje explicitní stanovení viditelnosti typu modelu COM. Obsahující <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> sestavení musí být označeno nastavením na `false` a typ <xref:System.Runtime.InteropServices.ComVisibleAttribute> musí být označen nastavením na `true`.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, změňte hodnotu <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributu na [LayoutKind. Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) nebo [LayoutKind. sekvenční](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>), nebo nastavte typ jako neviditelný na com.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad

Následující příklad ukazuje typ, který porušuje pravidlo a typ, který splňuje pravidlo.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Související pravidla

[CA1408: Nepoužívat AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Viz také:

- [Kvalifikovat typy .NET pro spoluprovozování](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)