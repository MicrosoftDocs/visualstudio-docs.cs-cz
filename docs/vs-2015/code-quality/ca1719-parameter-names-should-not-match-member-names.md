---
title: 'CA1719: názvy parametrů by neměly odpovídat názvům členů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5024d2ddb7f31593c8eaedfc2fb421b4a0e9b0a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545363"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Názvy parametrů by se neměly shodovat s názvy členů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Název externě viditelných shod členů, v porovnání s rozlišováním velkých a malých písmen, název jednoho z jeho parametrů.

## <a name="rule-description"></a>Popis pravidla
 Název parametru by měl sdělit význam parametru a název členu by měl sdělit význam členu. Byl by to vzácný návrh, pokud by byly stejné. Stejné pojmenování parametru i jeho členu je neintuitivní a činí knihovnu obtížně použitelnou.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Vyberte název parametru, který se neshoduje s názvem člena.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pro nový vývoj se nevyskytují žádné známé scénáře, kdy je nutné potlačit upozornění od tohoto pravidla. U přenosných knihoven možná budete muset potlačit upozornění od tohoto pravidla.

## <a name="related-rules"></a>Související pravidla
 [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
