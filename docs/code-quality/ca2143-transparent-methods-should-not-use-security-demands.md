---
title: 'CA2143: Transparentní metody by neměly používat požadavky zabezpečení'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a182beba738e583fad83c3f51d7efa312761906d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231985"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Transparentní metody by neměly používat požadavky zabezpečení

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Typ nebo metoda Tranparent je deklarativně označena <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` poptávkou <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> nebo metoda volá metodu.

## <a name="rule-description"></a>Popis pravidla
Kód transparentní z hlediska zabezpečení by neměl být odpovědný za ověření zabezpečení operace, a proto by neměl požadovat oprávnění. Kód transparentní z hlediska zabezpečení by měl k učinění rozhodnutí o zabezpečení používat úplné požadavky a bezpečně kritický kód by neměl spoléhat na to, že transparentní kód tyto úplné požadavky provede. Jakýkoli kód, který provádí kontroly zabezpečení, jako třeba požadavky na zabezpečení, by měl být místo toho kritický.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Obecně platí, že chcete-li opravit porušení tohoto pravidla, označte metodu <xref:System.Security.SecuritySafeCriticalAttribute> atributem. Můžete také odebrat poptávku.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Soubory pravidla v následujícím kódu, protože transparentní metoda vytvoří deklarativní požadavek zabezpečení.

[!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>Viz také:
[CA2142: Transparentní kód by neměl být chráněn pomocí LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)