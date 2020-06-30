---
title: 'CA1714: výčty příznaků by měly mít plurální názvy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 74e93a9644f365120117bd247d2ea8b9d43608cb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548184"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Výčty příznaků by neměly mít názvy v množném čísle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Veřejný výčet má <xref:System.FlagsAttribute?displayProperty=fullName> a jeho název nekončí na ' '.

## <a name="rule-description"></a>Popis pravidla
 Typy, které jsou označeny s <xref:System.FlagsAttribute> názvy, které jsou plural, protože atribut označuje, že lze zadat více než jednu hodnotu. Například výčet, který definuje dny v týdnu, může být určen pro použití v aplikaci, kde můžete zadat více dní. Tento výčet by měl mít <xref:System.FlagsAttribute> operátor a mohl by být pojmenovaný ' days '. Podobný výčet, který umožňuje zadat pouze jeden den, by neměl mít atribut a mohl by být označován za "Day".

 Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zmenší výuková křivka, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Nastavte název výčtu v množném čísle, nebo odeberte <xref:System.FlagsAttribute> atribut, pokud by neměl být zadán více hodnot výčtu současně.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit porušení, pokud je název plurální slovo, ale nekončí na '. Například pokud je výpis více dní popsaný dříve pojmenován ' DaysOfTheWeek ', může to porušovat logiku pravidla, ale ne jeho záměr. Tato porušení by se měla potlačit.

## <a name="related-rules"></a>Související pravidla
 [CA1027: Označte výčty pomocí FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Viz také
 <xref:System.FlagsAttribute?displayProperty=fullName>[Návrh výčtu](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
