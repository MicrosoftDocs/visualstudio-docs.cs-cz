---
title: 'CA2111: Ukazatelé by neměli být viditelné'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a08d15ec491bb78c2d9398c8e689015c9523a3c1
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546821"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Ukazatelé by neměli být viditelné

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný <xref:System.IntPtr?displayProperty=fullName> nebo <xref:System.UIntPtr?displayProperty=fullName> pole není jen pro čtení.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.IntPtr> a <xref:System.UIntPtr> jsou typy ukazatelů, které se používají pro přístup k nespravované paměti. Pokud ukazatel není soukromý, interní nebo jen pro čtení, škodlivý kód může změnit hodnotu ukazatele, potenciálně umožňuje přístup k libovolného umístění v paměti nebo může způsobit selhání aplikace nebo systému.

 Pokud máte v úmyslu zabezpečený přístup k typu, který obsahuje pole, ukazatel, přečtěte si téma [CA2112: zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Ukazatel Zabezpečte tím, že je jen pro čtení, interní nebo privátní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění tohoto pravidla, pokud nelze spoléhat na hodnotu ukazatele.

## <a name="example"></a>Příklad
 Následující kód ukazuje ukazatele, které porušují a splňovat pravidla. Všimněte si, že nesoukromých ukazatelů také porušovat pravidla [CA1051: nedeklarujte viditelná pole instance](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Související pravidla
 [CA2112: Zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: Nedeklarujte viditelná pole instance](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Viz také:

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>