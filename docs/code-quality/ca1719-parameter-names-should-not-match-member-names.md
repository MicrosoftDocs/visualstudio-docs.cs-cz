---
title: 'CA1719: Názvy parametrů by neměly odpovídat názvům členů'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86e9fe7b06f16474376d3cc672607bb2ef54746a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72438963"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Názvy parametrů by neměly odpovídat názvům členů

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Kategorie|Microsoft. pojmenování|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Název externě viditelných shod členů, v porovnání s rozlišováním velkých a malých písmen, název jednoho z jeho parametrů.

## <a name="rule-description"></a>Popis pravidla
Název parametru by měl sdělit význam parametru a název členu by měl sdělit význam členu. Byl by to vzácný návrh, pokud by byly stejné. Stejné pojmenování parametru i jeho členu je neintuitivní a činí knihovnu obtížně použitelnou.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Vyberte název parametru, který se neshoduje s názvem člena.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Pro nový vývoj se nevyskytují žádné známé scénáře, kdy je nutné potlačit upozornění od tohoto pravidla. U přenosných knihoven možná budete muset potlačit upozornění od tohoto pravidla.

## <a name="related-rules"></a>Související pravidla
[CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

[CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

[CA1707: Identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
