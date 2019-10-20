---
title: 'CA2140: transparentní kód nesmí odkazovat na položky kritické pro zabezpečení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c3e624e4210e59406fd1d5955cd37c2e83ed79a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602871"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

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
 Prvek kódu označený atributem <xref:System.Security.SecurityCriticalAttribute> je kritický pro zabezpečení. Transparentní metoda nemůže použít prvek kritický pro zabezpečení. Pokud se transparentní typ pokusí použít typ, který je kritický pro zabezpečení, je vyvolána <xref:System.TypeAccessException>, <xref:System.MethodAccessException> nebo <xref:System.FieldAccessException>.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, proveďte jednu z následujících akcí:

- Označte prvek kódu, který používá kód kritický pro zabezpečení s atributem <xref:System.Security.SecurityCriticalAttribute>.

     \- nebo-

- Odeberte atribut <xref:System.Security.SecurityCriticalAttribute> z prvků kódu, které jsou označeny jako kritické pro zabezpečení, a místo toho je označte atributem <xref:System.Security.SecuritySafeCriticalAttribute> nebo <xref:System.Security.SecurityTransparentAttribute>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 V následujících příkladech transparentní metoda se pokusí odkázat na kritickou obecnou kolekci zabezpečení, pole kritické pro zabezpečení a kritickou metodu zabezpečení.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.Security.SecurityTransparentAttribute><xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
