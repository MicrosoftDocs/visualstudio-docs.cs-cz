---
title: 'CA1403: typy automatického rozložení by neměly být viditelné modelu COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5f39540cb23d86dda4244604da8a9ff764594e11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661341"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typy automatického rozložení by neměly být viditelné modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Typ hodnoty zobrazený v modelu COM (Component Object Model) je označen atributem <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> nastaveným na hodnotu <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 typy rozložení <xref:System.Runtime.InteropServices.LayoutKind> jsou spravovány modulem CLR (Common Language Runtime). Rozložení těchto typů se může změnit mezi verzemi .NET Framework, což způsobí přerušení klientů modelu COM, kteří očekávají konkrétní rozložení. Všimněte si, že pokud atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> není zadán, C#[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] a C++ kompilátory určují rozložení <xref:System.Runtime.InteropServices.LayoutKind> pro typy hodnot.

 Pokud není určeno jinak, všechny veřejné neobecné typy jsou viditelné pro COM; všechny NonPublic a obecné typy jsou neviditelné v modelu COM. Chcete-li však omezit falešně pozitivní hodnoty, toto pravidlo vyžaduje explicitní zadání viditelnosti typu COM; obsahující sestavení musí být označeno s <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> nastavenou na `false` a typ musí být označený jako <xref:System.Runtime.InteropServices.ComVisibleAttribute> nastavený na `true`.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte hodnotu atributu <xref:System.Runtime.InteropServices.StructLayoutAttribute> na <xref:System.Runtime.InteropServices.LayoutKind> nebo <xref:System.Runtime.InteropServices.LayoutKind>, nebo nastavte typ jako neviditelný na COM.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který porušuje pravidlo a typ, který splňuje pravidlo.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1408: Nepoužívejte AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Viz také
 [Představujeme rozhraní třídy](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [opravňující typy .NET pro](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) spolupráci [s nespravovaným kódem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
