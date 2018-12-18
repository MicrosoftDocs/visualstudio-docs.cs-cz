---
title: 'CA2141: transparentní metody nesmějí vyhovovat LinkDemands | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3e5e34f0b207bc89b4f8928bff999c71f5d6c403
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939310"
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
 Transparentní metoda zabezpečení volá metodu v sestavení, který není označen atributem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA), nebo transparentní metoda zabezpečení splňuje požadavky <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` pro typ nebo metodu.

## <a name="rule-description"></a>Popis pravidla
 Nesplňujete LinkDemand je citlivé operace zabezpečení, což může způsobit nechtěné zvýšení oprávnění. Kód transparentní pro zabezpečení nesmějí vyhovovat LinkDemands, protože není v souladu s stejné požadavky auditu zabezpečení jako kritický kód pro zabezpečení. Transparentní metody v sestaveních úrovně 1 sadu pravidel zabezpečení způsobí, že všechny LinkDemands splňují převést na úplné požadavky v době běhu, což může způsobit problémy s výkonem. V sestavení pro úrovně 2 sady pravidel zabezpečení se nezdaří transparentní metody sestavení v kompilátor just-in-time (JIT) v případě podobného pokusu splňují LinkDemand.

 V sestavení vyvolá tuto usee zabezpečení úrovně 2, pokusy o transparentní metoda zabezpečení k splňuje pravidlo LinkDemand nebo volat metodu v sestavení sestavení APTCA <xref:System.MethodAccessException>; v sestaveních úrovně 1 LinkDemand stane úplný požadavek.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, označte přistupující metodu s <xref:System.Security.SecurityCriticalAttribute> nebo <xref:System.Security.SecuritySafeCriticalAttribute> atribut, nebo odeberte LinkDemand metodou používaná.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 V tomto příkladu transparentní metoda pokusí volat metodu, která má LinkDemand. Toto pravidlo bude platit pro tento kód.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]



