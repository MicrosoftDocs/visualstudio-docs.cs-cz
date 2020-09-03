---
title: 'CA2130: konstanty kritické pro zabezpečení by měly být transparentní | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4439e7b520232b71c16d3f3c6b4afb3a4ba35f21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534599"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Konstanty kritické pro zabezpečení musí být transparentní
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Pole konstanty nebo člen výčtu je označeno atributem <xref:System.Security.SecurityCriticalAttribute> .

## <a name="rule-description"></a>Popis pravidla
 Pro konstantní hodnoty není vynucována transparentnost, protože kompilátory vkládají konstantní hodnoty do kódu, aby za běhu programu nebylo zapotřebí žádné vyhledávání. Konstantní pole by měla být transparentní z pohledu zabezpečení, aby kontroloři kódu nepředpokládali, že transparentní kód nemůže ke konstantě přistoupit.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte atribut SecurityCritical z pole nebo hodnoty.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 V následujících příkladech je hodnota výčtu `EnumWithCriticalValues.CriticalEnumValue` a konstanta `CriticalConstant` vyvolána tímto upozorněním. Chcete-li tyto problémy vyřešit, odeberte `SecurityCritical` atribut [], aby byly jeho zabezpečení transparentní.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2130.constantsshouldbetransparent/cs/ca2130 - constantsshouldbetransparent.cs#1)]
