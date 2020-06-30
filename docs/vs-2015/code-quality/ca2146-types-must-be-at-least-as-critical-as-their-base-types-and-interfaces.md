---
title: 'CA2146: typy musí být alespoň tak kritické jako jejich základní typy a rozhraní | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2316d6e555fa091d26392aee71b774489c81a379
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546390"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Typy musí být alespoň tak kritické, jako jejich základní typy a rozhraní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Transparentní typ je odvozen z typu, který je označen jako <xref:System.Security.SecuritySafeCriticalAttribute> nebo <xref:System.Security.SecurityCriticalAttribute> , nebo typ, který je označen <xref:System.Security.SecuritySafeCriticalAttribute> atributem, je odvozen z typu, který je označen <xref:System.Security.SecurityCriticalAttribute> atributem.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo je vyvoláno, když má odvozený typ atribut transparentnosti zabezpečení, který není tak kritický jako jeho základní typ nebo implementované rozhraní. Pouze kritické typy lze odvodit z kritických základních typů nebo mohou implementovat kritická rozhraní a pouze kritické typy nebo bezpečně kritické typy mohou být odvozeny ze základních bezpečně kritických typů nebo mohou implementovat bezpečně kritická rozhraní. Porušení tohoto pravidla v důsledku transparentnosti úrovně 2 <xref:System.TypeLoadException> pro odvozený typ.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li toto porušení opravit, označte odvozený nebo implementující typ s atributem transparentnosti, který je nejméně tak důležitý jako základní typ nebo rozhraní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]
