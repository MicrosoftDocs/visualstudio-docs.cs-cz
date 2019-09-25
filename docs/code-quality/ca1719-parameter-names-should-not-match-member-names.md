---
title: 'CA1719: Názvy parametrů by se neměly shodovat s názvy členů'
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
ms.openlocfilehash: 2aa55993758df24346b78eb4d9ad022014d9d81c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233978"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Názvy parametrů by se neměly shodovat s názvy členů

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Kategorie|Microsoft.Naming|
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
[CA1709: Identifikátory by se měly použita správně.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

[CA1708: Identifikátory by se měly lišit o více než malých písmenech](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

[CA1707: Identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)