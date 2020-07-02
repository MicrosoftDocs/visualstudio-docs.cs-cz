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
ms.openlocfilehash: bee810ed938d316e92095ad47062ed5ad9cd456f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546442"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141:Transparentní metody nesmějí vyhovovat LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Transparentní metoda zabezpečení volá metodu v sestavení, které není označeno <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributem (APTCA), nebo transparentní metoda zabezpečení vyhovuje <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` pro typ nebo metodu.

## <a name="rule-description"></a>Popis pravidla
 Vyhovujícím LinkDemand je operace citlivá na zabezpečení, která může způsobit neúmyslné zvýšení oprávnění. Transparentní kód zabezpečení nesmí splňovat LinkDemand, protože nepodléhá stejným požadavkům na audit zabezpečení jako kód kritický pro zabezpečení. Transparentní metody v pravidle zabezpečení nastavené na úrovni 1 sestavení způsobí, že všechny LinkDemands, které vyhovují, budou převedeny na plné požadavky v době běhu, což může způsobit problémy s výkonem. V sestaveních s pravidlem zabezpečení nastaveným na úrovni 2 nebudou transparentní metody zkompilovány v kompilátoru JIT (just-in-time), pokud se pokoušejí vyhovět LinkDemand.

 V sestaveních, která Usee zabezpečení úrovně 2, pokusy transparentní metody zabezpečení o splnění LinkDemand nebo volání metody v sestavení, které nepatří do třídy APTCA, vyvolá. <xref:System.MethodAccessException> v sestaveních úrovně 1 se jako LinkDemand stala úplným požadavkem.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, označte metodu přístupu pomocí <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atributu nebo, nebo odeberte LinkDemand z metody přístupu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 V tomto příkladu se transparentní metoda pokusí zavolat metodu, která má LinkDemand. Toto pravidlo se bude na tomto kódu aktivovat.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]
