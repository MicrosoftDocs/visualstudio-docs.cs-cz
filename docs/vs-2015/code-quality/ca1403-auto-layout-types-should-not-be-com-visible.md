---
title: 'CA1403: Typy automatického rozložení by neměly být viditelné modelu COM | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e6f675c2d13efbf029aa515402be4bf75bad867e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816845"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typy automatického rozložení by neměly být viditelné modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategorie|Microsoft.Interoperability|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Typ hodnoty viditelné modelu COM (Component Object) je označena <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> atribut nastaven na <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Runtime.InteropServices.LayoutKind> modul common language runtime spravuje typy rozložení. Mezi verzemi rozhraní .NET Framework, což naruší klienty modulu COM, které očekávají specifické rozložení můžete změnit rozložení těchto typů. Všimněte si, že pokud <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut není zadán, C#, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], a zadejte kompilátory C++ <xref:System.Runtime.InteropServices.LayoutKind> rozložení pro typy hodnot.

 Pokud není označen jinak, jsou viditelné modelu COM; všechny veřejné neobecné typy všechny neveřejné a obecné typy nejsou viditelná modelu COM. Ale snížil počet falešných poplachů, toto pravidlo vyžaduje typ, který má být explicitně uvedena; viditelnost modelu COM musí být označené obsahující sestavení <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> nastavena na `false` a typ musí být označeny pomocí <xref:System.Runtime.InteropServices.ComVisibleAttribute> nastavena na `true`.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte hodnotu <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut <xref:System.Runtime.InteropServices.LayoutKind> nebo <xref:System.Runtime.InteropServices.LayoutKind>, nebo skrytí typu modelu COM.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který porušuje pravidla a typ, který splňuje pravidlo.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1408: Nepoužívejte AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Viz také
 [Představení rozhraní třídy](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024) [kvalifikace typů .NET pro spolupráci](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [spolupráce pomocí nespravovaného kódu](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



