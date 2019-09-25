---
title: 'CA2111: Ukazatele by neměly být viditelné'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a93f776ac6e133b0ebf79d1dfa56f802ff66e5f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232773"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Ukazatele by neměly být viditelné

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Veřejné nebo chráněné <xref:System.IntPtr?displayProperty=fullName> pole nebo <xref:System.UIntPtr?displayProperty=fullName> pole není jen pro čtení.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.IntPtr>a <xref:System.UIntPtr> jsou typy ukazatelů, které se používají pro přístup k nespravované paměti. Pokud ukazatel není privátní, interní nebo jen pro čtení, škodlivý kód může změnit hodnotu ukazatele, potenciálně umožnit přístup k libovolnému umístění v paměti nebo způsobit selhání aplikace nebo systému.

Pokud máte v úmyslu zabezpečit přístup k typu, který obsahuje pole s ukazatelem [, přečtěte si téma CA2112: Zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Zabezpečte ukazatel tak, že ho nastavíte jako jen pro čtení, interní nebo soukromý.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačit upozornění z tohoto pravidla, pokud nespoléháte na hodnotu ukazatele.

## <a name="example"></a>Příklad
Následující kód ukazuje ukazatele, které porušují a splňují pravidlo. Všimněte si, že neprivátní ukazatele také porušují CA1051 pravidla [: Nedeklarujte viditelná pole](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)instance.

[!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA2112: Zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA1051: Nedeklarujte viditelná pole instance](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Viz také:

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>