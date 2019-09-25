---
title: 'CA1714: Výčty příznaků by neměly mít názvy v množném čísle'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79585cd9cae31f46a9506085c9c8faf5b5844d44
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234092"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Výčty příznaků by neměly mít názvy v množném čísle

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Kategorie|Microsoft.Naming|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Výčet má <xref:System.FlagsAttribute?displayProperty=fullName> a jeho název nekončí na ' '.

Ve výchozím nastavení toto pravidlo vypadá pouze v externě viditelných výčtech, ale to je [konfigurovatelné](#configurability).

## <a name="rule-description"></a>Popis pravidla

Typy, které jsou označeny <xref:System.FlagsAttribute> s názvy, které jsou plural, protože atribut označuje, že lze zadat více než jednu hodnotu. Například výčet, který definuje dny v týdnu, může být určen pro použití v aplikaci, kde můžete zadat více dní. Tento výčet by měl mít <xref:System.FlagsAttribute> operátor a mohl by být pojmenovaný ' days '. Podobný výčet, který umožňuje zadat pouze jeden den, by neměl mít atribut a mohl by být označován za "Day".

Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zmenší výuková křivka, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Nastavte název výčtu v množném čísle, nebo odeberte <xref:System.FlagsAttribute> atribut, pokud by neměl být zadán více hodnot výčtu současně.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Je bezpečné potlačit porušení, pokud je název plurální slovo, ale nekončí na '. Například pokud je výpis více dní popsaný dříve pojmenován ' DaysOfTheWeek ', může to porušovat logiku pravidla, ale ne jeho záměr. Tato porušení by se měla potlačit.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1714.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (pojmenování). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Související pravidla

- [CA1027: Označení výčtů pomocí FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Viz také:

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Návrh výčtu](/dotnet/standard/design-guidelines/enum)