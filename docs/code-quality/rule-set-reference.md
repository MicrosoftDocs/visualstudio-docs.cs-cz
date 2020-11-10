---
title: Referenční dokumentace sady pravidel nástroje Analýza kódu
ms.date: 04/04/2018
description: Přečtěte si o předdefinovaných pravidlech v sadě Visual Studio pro starší verze analýzy kódu. Podívejte se na zdroje informací o sadách pravidel. Zjistěte, jak používat tyto sady v přizpůsobených sadách pravidel.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce5b7f2ecdc854269288c61eaeee6d46b4a74d91
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436976"
---
# <a name="code-analysis-rule-set-reference"></a>Referenční dokumentace sady pravidel nástroje Analýza kódu

Při konfiguraci starší verze analýzy pro projekty spravovaného kódu v sadě Visual Studio můžete vybrat ze seznamu předdefinovaných *sad pravidel*. Některá pravidla jsou součástí více než jedné z předdefinovaných sad pravidel, například sada pravidel základní pravidla správnosti zahrnuje pravidla, která jsou uvedena v sadě pravidel spravovaná doporučená pravidla.

> [!NOTE]
> Sady pravidel v této části se týkají starší verze analýzy. Informace o sadách pravidel dostupných pro balíčky analyzátoru kódu najdete v tématu [použití sad pravidel s analyzátory kódu](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

Můžete použít jednu z těchto předdefinovaných sad pravidel nebo můžete [přizpůsobit sadu pravidel](../code-quality/how-to-create-a-custom-rule-set.md) tak, aby vyhovovala vašim požadavkům na projekt. Pokud zahrnete několik sad pravidel, které obsahují stejné pravidlo, v sadě vlastních pravidel, toto pravidlo se v sadě vlastních pravidel zobrazí jenom jednou.

Témata v této části popisují předdefinované sady pravidel a pravidla (nebo upozornění), která obsahují.

| Sada pravidel | Zahrnutá pravidla |
| - | - |
| [Všechna pravidla](all-rules-rule-set.md) | Obsahuje všechna dostupná spravovaná pravidla a pravidla jazyka C++. |
| [Základní pravidla správnosti](basic-correctness-rules-rule-set-for-managed-code.md) | Zahrnuje spravovaná doporučená pravidla a pravidla pro logické chyby a využití rozhraní. |
| [Rozšířená pravidla správnosti](extended-correctness-rules-rule-set-for-managed-code.md) | Zahrnuje základní pravidla správnosti (včetně spravovaných doporučených pravidel) a další pravidla pro logické chyby a využití rozhraní. |
| [Základní pravidla obecných zásad návrhu](basic-design-guideline-rules-rule-set-for-managed-code.md) | Zahrnuje spravovaná doporučená pravidla a pravidla pro zajištění snadného čtení, pochopení a údržby kódu. |
| [Rozšířená pravidla obecných zásad návrhu](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Zahrnuje základní pravidla obecných zásad návrhu (včetně spravovaných doporučených pravidel) a další pravidla udržovatelnosti, která se zaměřují na pojmenovávání. |
| [Pravidla globalizace](globalization-rules-rule-set-for-managed-code.md) | Zahrnuje pravidla pro problémy globalizace. |
| [Minimální pravidla pro spravovaný kód](managed-minimum-rules-rule-set-for-managed-code.md) | Obsahuje čtyři pravidla pro kritické problémy spravovaného kódu. |
| [Doporučená pravidla pro spravovaný kód](managed-recommended-rules-rule-set-for-managed-code.md) | Zahrnuje spravovaná minimální pravidla a další pravidla pro kritické problémy spravovaného kódu. |
| [Smíšená minimální pravidla](mixed-minimum-rules-rule-set.md) | Zahrnuje pravidla pro kritické problémy v kódu jazyka C++ pro modul CLR. |
| [Smíšená doporučená pravidla](mixed-recommended-rules-rule-set.md) | Zahrnuje smíšená minimální pravidla a další pravidla pro kritické problémy v kódu C++ pro CLR. |
| [Nativní minimální pravidla](native-minimum-rules-rule-set.md) | Zahrnuje pravidla pro kritické problémy v nativním kódu. |
| [Nativní doporučená pravidla](native-recommended-rules-rule-set.md) | Zahrnuje nativní minimální pravidla a další pravidla pro kritické problémy v nativním kódu. |
| [Pravidla zabezpečení](security-rules-rule-set-for-managed-code.md) | Zahrnuje pravidla pro hledání slabých míst zabezpečení. |