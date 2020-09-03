---
title: 'CA2111: Ukazatelé by neměli být viditelné | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7429251a66ce2fe22a825a153cb90248faabb9fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544362"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Ukazatele by neměly být viditelné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Veřejné nebo chráněné <xref:System.IntPtr?displayProperty=fullName> pole nebo <xref:System.UIntPtr?displayProperty=fullName> pole není jen pro čtení.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.IntPtr> a <xref:System.UIntPtr> jsou typy ukazatelů, které se používají pro přístup k nespravované paměti. Pokud ukazatel není privátní, interní nebo jen pro čtení, škodlivý kód může změnit hodnotu ukazatele, potenciálně umožnit přístup k libovolnému umístění v paměti nebo způsobit selhání aplikace nebo systému.

 Pokud máte v úmyslu zabezpečit přístup k typu, který obsahuje pole s ukazatelem, přečtěte si téma [CA2112: zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Zabezpečte ukazatel tak, že ho nastavíte jako jen pro čtení, interní nebo soukromý.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění z tohoto pravidla, pokud nespoléháte na hodnotu ukazatele.

## <a name="example"></a>Příklad
 Následující kód ukazuje ukazatele, které porušují a splňují pravidlo. Všimněte si, že neprivátní ukazatele také porušují pravidlo [CA1051: Nedeklarujte viditelná pole instance](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2112: Zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: Nedeklarujte viditelná pole instance](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Viz také
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>
