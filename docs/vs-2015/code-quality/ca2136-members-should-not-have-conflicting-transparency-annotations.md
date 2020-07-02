---
title: 'CA2136: členové by neměli mít konfliktní anotace transparentnosti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3a17a0db7dd4ad1c57d23104a313a78cd1289ed
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547690"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Členy by neměly mít konfliktní poznámky transparentnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Toto pravidlo je vyvoláno, když je člen typu označen <xref:System.Security> atributem zabezpečení, který má odlišnou průhlednost než atribut zabezpečení kontejneru člena.

## <a name="rule-description"></a>Popis pravidla
 Atributy transparentnosti jsou použity z prvků kódu většího rozsahu na prvky menšího rozsahu. Atributy transparentnosti prvků kódu, které mají větší rozsah, mají přednost před atributy transparentnosti prvků kódu, které jsou obsaženy v prvním prvku. Například třída, která je označena <xref:System.Security.SecurityCriticalAttribute> atributem, nesmí obsahovat metodu, která je označena <xref:System.Security.SecuritySafeCriticalAttribute> atributem.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li toto porušení opravit, odeberte atribut zabezpečení z prvku kódu, který má nižší rozsah, nebo změňte jeho atribut tak, aby byl stejný jako element obsahující prvek kódu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění z tohoto pravidla

## <a name="example"></a>Příklad
 V následujícím příkladu je metoda označena <xref:System.Security.SecuritySafeCriticalAttribute> atributem a je členem třídy, která je označena <xref:System.Security.SecurityCriticalAttribute> atributem. Je nutné odebrat atribut zabezpečení Safe.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
