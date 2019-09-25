---
title: 'CA1722: Identifikátory by neměly mít nesprávnou předponu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb41f2ad4548933d10137e7f72cae59643d33043
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233879"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Identifikátory by neměly mít nesprávnou předponu

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Kategorie|Microsoft.Naming|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Identifikátor má nesprávnou předponu.

## <a name="rule-description"></a>Popis pravidla
Podle konvence mají pouze některé programovací prvky názvy začínající určitou předponou.

Názvy typů nemají konkrétní předponu a neměly by být uvozeny znakem "C". Toto pravidlo oznamuje porušení pro názvy typů, jako je například ' CMyClass ', a neoznamuje porušení pro názvy typů, jako je ' cache '.

Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tato konzistence snižuje výukovou křivku, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Odeberte předponu z identifikátoru.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="related-rules"></a>Související pravidla
[CA1715: Identifikátory by měly mít správnou předponu](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)