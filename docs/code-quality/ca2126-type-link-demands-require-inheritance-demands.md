---
title: 'CA2126: Požadavky na propojení typů vyžadují požadavky na dědičnost'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4f01ba5af7640521333093e4bba1f36a95363b60
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232467"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Požadavky na propojení typů vyžadují požadavky na dědičnost

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Veřejný nezapečetěný typ je chráněn s požadavkem propojení, má přepsatelné metody a ani typ ani metoda není chráněna pomocí požadavku dědičnosti.

## <a name="rule-description"></a>Popis pravidla
Požadavek propojení na metodu nebo jeho deklarující typ vyžaduje bezprostředního volajícího metody, že má zadané oprávnění. Požadavek dědičnosti na metodu vyžaduje přepsání metody, která má zadané oprávnění. Požadavek dědičnosti na typ vyžaduje, aby odvozená třída měla zadané oprávnění.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, zabezpečte typ nebo metodu pomocí požadavku dědičnosti pro stejné oprávnění, jako je požadavek propojení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje typ, který je v rozporu s pravidlem.

[!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
[!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
[!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA2108: Kontrola deklarativních zabezpečení na hodnotových typech](../code-quality/ca2108-review-declarative-security-on-value-types.md)

[CA2112: Zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA2122: Nezveřejňujte nepřímo metody s požadavky propojení](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

[CA2123: Požadavky na přepsání odkazu by měly být shodné se základem](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](/dotnet/standard/security/secure-coding-guidelines)
- [Požadavky propojení](/dotnet/framework/misc/link-demands)