---
title: 'CA2131: Typy kritické pro zabezpečení se nesmí účastnit ekvivalence typů'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 802442a71eed3267a71fad9a5a208c9ee82cb556
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232352"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Typy kritické pro zabezpečení se nesmí účastnit ekvivalence typů

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Typ se účastní rovnocennosti typu a buď samotný typ, nebo člen nebo pole typu, je označen <xref:System.Security.SecurityCriticalAttribute> atributem.

## <a name="rule-description"></a>Popis pravidla
Toto pravidlo je vyvoláno pro všechny kritické typy nebo typy obsahující kritické metody nebo pole, která se účastní porovnávání typů. Když CLR takový typ detekuje, nenačte ho <xref:System.TypeLoadException> za běhu za běhu. Obvykle ke spuštění tohoto pravidla dochází pouze v případě, že uživatel implementuje porovnávání typů ručně a nepřenechává porovnávání typů na nástroji tlbimp a kompilátorech.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, odeberte atribut SecurityCritical.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklady ukazují rozhraní, metodu a pole, které způsobí, že se toto pravidlo aktivuje.

[!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]

## <a name="see-also"></a>Viz také:
[Kód transparentní pro zabezpečení, úroveň 2](/dotnet/framework/misc/security-transparent-code-level-2)