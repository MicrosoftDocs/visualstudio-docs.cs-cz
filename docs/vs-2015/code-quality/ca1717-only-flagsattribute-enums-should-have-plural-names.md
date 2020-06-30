---
title: 'CA1717: pouze výčty FlagsAttribute by měly mít plurální názvy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c58c218991226a954185853097dc81da36c69ed6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543686"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Pouze výčty FlagsAttribute by měly mít názvy v množném čísle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Název externě viditelného výčtu končí v množném čísle a výčet není označen <xref:System.FlagsAttribute?displayProperty=fullName> atributem.

## <a name="rule-description"></a>Popis pravidla
 Zásady vytváření názvů určují, že plurální název pro výčet označuje, že lze zadat více než jednu hodnotu výčtu současně. <xref:System.FlagsAttribute>Říká kompilátorům, že by měl být výčet zpracován jako bitové pole, které umožňuje bitové operace na výčtu.

 Pokud lze současně zadat pouze jednu hodnotu výčtu, název výčtu by měl být jednotné slovo. Například výčet, který definuje dny v týdnu, může být určen pro použití v aplikaci, kde můžete zadat více dní. Tento výčet by měl mít <xref:System.FlagsAttribute> operátor a mohl by být pojmenovaný ' days '. Podobný výčet, který umožňuje zadat pouze jeden den, by neměl mít atribut a mohl by být označován za "Day".

 Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zkracuje čas potřebný k učení nové softwarové knihovny a zvyšuje se důvěra zákazníků, že knihovna byla vyvinutá někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Nastavte název výčtu na jednotné slovo nebo přidejte <xref:System.FlagsAttribute> .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z pravidla, pokud název končí v jednotném slově.

## <a name="related-rules"></a>Související pravidla
 [CA1714: Výčty příznaků by neměly mít názvy v množném čísle](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: Označte výčty pomocí FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Viz také
 <xref:System.FlagsAttribute?displayProperty=fullName>[Návrh výčtu](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
