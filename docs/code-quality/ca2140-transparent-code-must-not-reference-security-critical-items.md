---
title: 'CA2140: Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4f02938aed7456762f1ef51da716b6b96bdf437
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232150"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Transparentní metoda:

- zpracovává typ výjimky zabezpečení kritické pro zabezpečení.

- má parametr, který je označený jako typ kritický pro zabezpečení

- má obecný parametr s omezeními kritickými pro zabezpečení

- má místní proměnnou typu, který je kritický pro zabezpečení.

- odkazuje na typ, který je označený jako kritický pro zabezpečení.

- volá metodu, která je označena jako kritická pro zabezpečení

- odkazuje na pole, které je označeno jako kritické pro zabezpečení

- Vrátí typ, který je označený jako kritický pro zabezpečení.

## <a name="rule-description"></a>Popis pravidla

Prvek kódu, který je označen <xref:System.Security.SecurityCriticalAttribute> atributem, je kritický pro zabezpečení. Transparentní metoda nemůže použít prvek kritický pro zabezpečení. Pokud se transparentní typ pokusí použít typ a <xref:System.TypeAccessException>, nebo je vyvolán, <xref:System.MethodAccessException> nebo <xref:System.FieldAccessException> .

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, proveďte jednu z následujících akcí:

- Označte prvek kódu, který používá kód kritický pro zabezpečení s <xref:System.Security.SecurityCriticalAttribute> atributem.

     \- nebo –

- Odeberte atribut z prvků kódu, které jsou označeny jako kritické pro zabezpečení a místo toho je <xref:System.Security.SecuritySafeCriticalAttribute> označte atributem <xref:System.Security.SecurityTransparentAttribute>OR. <xref:System.Security.SecurityCriticalAttribute>

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad

V následujících příkladech transparentní metoda se pokusí odkázat na kritickou obecnou kolekci zabezpečení, pole kritické pro zabezpečení a kritickou metodu zabezpečení.

[!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]

## <a name="see-also"></a>Viz také:

- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityCriticalAttribute>
- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityTreatAsSafeAttribute>
- <xref:System.Security?displayProperty=fullName>