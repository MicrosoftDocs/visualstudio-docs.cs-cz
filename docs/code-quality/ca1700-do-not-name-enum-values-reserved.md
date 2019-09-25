---
title: 'CA1700: Nejmenujte rezervované hodnoty &#39;výčtu&#39;'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5171123827481c99bbc35c10b04aaf942a15fabb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234392"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Nejmenujte rezervované hodnoty &#39;výčtu&#39;

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Kategorie|Microsoft.Naming|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Název členu výčtu obsahuje slovo "rezervované".

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo předpokládá, že člen výčtu, který má název obsahující výraz „reserved“, není aktuálně používán, ale je zástupným symbolem k přejmenování nebo odstranění v budoucí verzi. Přejmenování nebo odstranění členu je narušující změna. Neměli byste očekávat, že uživatelé budou ignorovat člena, protože jeho název obsahuje "rezervované", ani vám nemůžete spoléhat na to, že se v dokumentaci budou číst nebo přidržet. Vzhledem k tomu, že se rezervované členy zobrazují v prohlížečích objektů a inteligentních vývojových prostředích, mohou způsobit nejasnost o tom, které členy jsou skutečně používány.

Místo použití rezervovaného člena přidejte do výčtu v budoucí verzi nového člena. Ve většině případů není přidání nového člena zásadní změnou, pokud sčítání nezpůsobí změnu hodnot původních členů.

V omezeném počtu případů je přidání člena zásadní změnou, i když původní hodnoty zachovají původní členové. Primárně nemůže být nový člen vrácen z existujících cest kódu bez přerušení, které používají `switch` příkaz (`Select` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) na vrácené hodnotě, která zahrnuje celý seznam členů a který vyvolal výjimku v Výchozí velikost písmen. Sekundárním problémem je, že klientský kód nemusí zpracovávat změnu v chování z metod reflexe, <xref:System.Enum.IsDefined%2A?displayProperty=fullName>jako je. V případě, že by se měl nový člen vrátit z existujících metod nebo dojde k nekompatibilitě známé aplikace z důvodu nedostatečného využití reflexe, jediného nepřerušeného řešení je:

1. Přidejte nový výčet, který obsahuje původní a nové členy.

2. Označte původní výčet <xref:System.ObsoleteAttribute?displayProperty=fullName> atributem.

   Použijte stejný postup pro všechny externě viditelné typy nebo členy, které zveřejňují původní výčet.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, odeberte nebo přejmenujte člena.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Z tohoto pravidla je bezpečné potlačit upozornění pro člena, který se právě používá, nebo pro knihovny, které byly dřív dodány.

## <a name="related-rules"></a>Související pravidla

[CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

[CA1712: Neprefixovat hodnoty výčtu s názvem typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

[CA1028: Úložiště výčtu by měl být Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

[CA1008 Výčty by měly mít nulovou hodnotu](../code-quality/ca1008-enums-should-have-zero-value.md)

[CA1027: Označení výčtů pomocí FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)