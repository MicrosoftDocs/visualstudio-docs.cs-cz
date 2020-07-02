---
title: 'CA2131: typy kritické pro zabezpečení se nemusí účastnit rovnosti typů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ccd556a5929e56597de678ad4ad8ea6c101b7c7f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535886"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Typy kritické pro zabezpečení se nesmí účastnit ekvivalence typů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Typ se účastní rovnocennosti typu a buď samotný typ, nebo člen nebo pole typu, je označen <xref:System.Security.SecurityCriticalAttribute> atributem.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo je vyvoláno pro všechny kritické typy nebo typy obsahující kritické metody nebo pole, která se účastní porovnávání typů. Když CLR takový typ detekuje, nenačte ho za <xref:System.TypeLoadException> běhu za běhu. Obvykle ke spuštění tohoto pravidla dochází pouze v případě, že uživatel implementuje porovnávání typů ručně a nepřenechává porovnávání typů na nástroji tlbimp a kompilátorech.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte atribut SecurityCritical.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklady ukazují rozhraní, metodu a pole, které způsobí, že se toto pravidlo aktivuje.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2131.criticaltypesmustnotparticipateintypeequivalence/cs/ca2131 - criticaltypesmustnotparticipateintypeequivalence.cs#1)]

## <a name="see-also"></a>Viz také
 [Transparentní kód pro zabezpečení, úroveň 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
