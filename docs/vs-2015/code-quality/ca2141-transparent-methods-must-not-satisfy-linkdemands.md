---
title: 'CA2141: transparentní metody nesmějí vyhovovat LinkDemands | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5e8e88401a6fbe3ab7dc635dadee9215b049b2d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602846"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141:Transparentní metody nesmějí vyhovovat LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Transparentní metoda zabezpečení volá metodu v sestavení, které není označeno atributem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA), nebo transparentní metoda zabezpečení splňuje <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` pro typ nebo metodu.

## <a name="rule-description"></a>Popis pravidla
 Vyhovujícím LinkDemand je operace citlivá na zabezpečení, která může způsobit neúmyslné zvýšení oprávnění. Transparentní kód zabezpečení nesmí splňovat LinkDemand, protože nepodléhá stejným požadavkům na audit zabezpečení jako kód kritický pro zabezpečení. Transparentní metody v pravidle zabezpečení nastavené na úrovni 1 sestavení způsobí, že všechny LinkDemands, které vyhovují, budou převedeny na plné požadavky v době běhu, což může způsobit problémy s výkonem. V sestaveních s pravidlem zabezpečení nastaveným na úrovni 2 nebudou transparentní metody zkompilovány v kompilátoru JIT (just-in-time), pokud se pokoušejí vyhovět LinkDemand.

 V sestaveních, která Usee zabezpečení úrovně 2, pokusy transparentní metodou zabezpečení pro uspokojení LinkDemand nebo volání metody v sestavení bez APTCA vyvolává <xref:System.MethodAccessException>; v sestaveních úrovně 1 se LinkDemand nastaví na plnou poptávku.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, označte metodu přístupu pomocí atributu <xref:System.Security.SecurityCriticalAttribute> nebo <xref:System.Security.SecuritySafeCriticalAttribute> nebo odeberte LinkDemand z metody přístupu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 V tomto příkladu se transparentní metoda pokusí zavolat metodu, která má LinkDemand. Toto pravidlo se bude na tomto kódu aktivovat.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]
