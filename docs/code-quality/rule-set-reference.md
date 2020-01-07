---
title: Referenční dokumentace sady pravidel nástroje Analýza kódu
ms.date: 04/04/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d380346b7e049a6ffc4e8d03a5be27983de10249
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587235"
---
# <a name="code-analysis-rule-set-reference"></a>Referenční dokumentace sady pravidel nástroje Analýza kódu

Při konfiguraci starší verze analýzy pro projekty spravovaného kódu v sadě Visual Studio můžete vybrat ze seznamu předdefinovaných *sad pravidel*. Některá pravidla jsou součástí více než jedné z předdefinovaných sad pravidel, například sada pravidel základní pravidla správnosti zahrnuje pravidla, která jsou uvedena v sadě pravidel spravovaná doporučená pravidla.

> [!NOTE]
> Sady pravidel v této části se týkají starší verze analýzy. Informace o sadách pravidel dostupných pro balíčky analyzátoru kódu najdete v tématu [použití sad pravidel s analyzátory kódu](analyzer-rule-sets.md).

Můžete použít jednu z těchto sad předdefinovaných pravidel, nebo se dají [přizpůsobování sady vlastních pravidel](../code-quality/how-to-create-a-custom-rule-set.md) podle svých požadavků projektu. Pokud zahrnete několik sad pravidel, které obsahují stejné pravidlo, v sadě vlastních pravidel, toto pravidlo se v sadě vlastních pravidel zobrazí jenom jednou.

Témata v této části popisují předdefinovaných pravidel sady a pravidel (nebo upozornění), které obsahují.

| Sada pravidel | Zahrnutá pravidla |
| - | - |
| [Všechna pravidla](all-rules-rule-set.md) | Obsahuje všechna dostupná spravovaná a C++ pravidla. |
| [Základní pravidla správnosti](basic-correctness-rules-rule-set-for-managed-code.md) | Zahrnuje spravovaná doporučená pravidla a pravidla pro logické chyby a využití rozhraní. |
| [Rozšířená pravidla správnosti](extended-correctness-rules-rule-set-for-managed-code.md) | Zahrnuje základní pravidla správnosti (včetně spravovaných doporučených pravidel) a další pravidla pro logické chyby a využití rozhraní. |
| [Základní pravidla obecných zásad návrhu](basic-design-guideline-rules-rule-set-for-managed-code.md) | Zahrnuje spravovaná doporučená pravidla a pravidla pro zajištění snadného čtení, pochopení a údržby kódu. |
| [Rozšířená pravidla obecných zásad návrhu](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Zahrnuje základní pravidla obecných zásad návrhu (včetně spravovaných doporučených pravidel) a další pravidla udržovatelnosti, která se zaměřují na pojmenovávání. |
| [Pravidla globalizace](globalization-rules-rule-set-for-managed-code.md) | Zahrnuje pravidla pro problémy globalizace. |
| [Spravovaná minimální pravidla](managed-minimum-rules-rule-set-for-managed-code.md) | Obsahuje čtyři pravidla pro kritické problémy spravovaného kódu. |
| [Spravovaná doporučená pravidla](managed-recommended-rules-rule-set-for-managed-code.md) | Zahrnuje spravovaná minimální pravidla a další pravidla pro kritické problémy spravovaného kódu. |
| [Smíšená minimální pravidla](mixed-minimum-rules-rule-set.md) | Zahrnuje pravidla pro kritické problémy v C++ kódu pro CLR. |
| [Smíšená doporučená pravidla](mixed-recommended-rules-rule-set.md) | Zahrnuje smíšená minimální pravidla a další pravidla pro kritické problémy C++ v kódu pro CLR. |
| [Nativní minimální pravidla](native-minimum-rules-rule-set.md) | Zahrnuje pravidla pro kritické problémy v nativním kódu. |
| [Nativní doporučená pravidla](native-recommended-rules-rule-set.md) | Zahrnuje nativní minimální pravidla a další pravidla pro kritické problémy v nativním kódu. |
| [Pravidla zabezpečení](security-rules-rule-set-for-managed-code.md) | Zahrnuje pravidla pro hledání slabých míst zabezpečení. |
