---
title: CA2141:Transparentní metody nesmějí vyhovovat LinkDemands
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0365d82917b8cfbaf291d557a6ac2d95c220562a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232123"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141:Transparentní metody nesmějí vyhovovat LinkDemands

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Transparentní metoda zabezpečení volá metodu v sestavení, které není označeno <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributem (APTCA), nebo transparentní metoda zabezpečení vyhovuje <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` pro typ nebo metodu.

## <a name="rule-description"></a>Popis pravidla
Vyhovující LinkDemand je operace citlivá na zabezpečení, která může způsobit neúmyslné zvýšení oprávnění. Transparentní kód zabezpečení nesmí splňovat LinkDemand, protože nepodléhá stejným požadavkům na audit zabezpečení jako kód kritický pro zabezpečení. Transparentní metody v pravidle zabezpečení nastavené na úrovni 1 sestavení způsobí, že všechny LinkDemands, které vyhovují, budou převedeny na plné požadavky v době běhu, což může způsobit problémy s výkonem. V sestaveních s pravidlem zabezpečení nastaveným na úrovni 2 nebudou transparentní metody zkompilovány v kompilátoru JIT (just-in-time), pokud se pokoušejí vyhovět LinkDemand.

V sestaveních, která používají zabezpečení úrovně 2, pokusy transparentní metody zabezpečení o splnění LinkDemand nebo volání metody v sestavení, které nepatří do sestavení typu <xref:System.MethodAccessException>APTCA, vyvolá; v sestaveních úrovně 1 se jako úplný požadavek na plnou poptávku.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, označte metodu přístupu pomocí <xref:System.Security.SecurityCriticalAttribute> atributu nebo <xref:System.Security.SecuritySafeCriticalAttribute> , nebo odeberte LinkDemand z metody přístupu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
V tomto příkladu se transparentní metoda pokusí zavolat metodu, která má LinkDemand. Toto pravidlo se bude na tomto kódu aktivovat.

[!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]