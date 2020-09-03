---
title: 'CA1700: Nejmenujte hodnoty výčtu &#39;vyhrazené&#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 57f2a2e5959860a99a921101ff5782f9bce9ace3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545649"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Nejmenujte hodnoty výčtu &#39;vyhrazené&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Název členu výčtu obsahuje slovo "rezervované".

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo předpokládá, že člen výčtu, který má název obsahující výraz „reserved“, není aktuálně používán, ale je zástupným symbolem k přejmenování nebo odstranění v budoucí verzi. Přejmenování nebo odstranění členu je narušující změna. Neměli byste očekávat, že uživatelé budou ignorovat člena, protože jeho název obsahuje "rezervované", ani vám nemůžete spoléhat na to, že se v dokumentaci budou číst nebo přidržet. Vzhledem k tomu, že se rezervované členy zobrazují v prohlížečích objektů a inteligentních vývojových prostředích, mohou způsobit nejasnost o tom, které členy jsou skutečně používány.

 Místo použití rezervovaného člena přidejte do výčtu v budoucí verzi nového člena. Ve většině případů není přidání nového člena zásadní změnou, pokud sčítání nezpůsobí změnu hodnot původních členů.

 V omezeném počtu případů je přidání člena zásadní změnou, i když původní hodnoty zachovají původní členové. Primárně nemůže být nový člen vrácen z existujících cest kódu bez přerušení, které používají `switch` `Select` příkaz (in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) na vrácené hodnotě, která zahrnuje celý seznam členů a který vyvolá výjimku ve výchozím případě. Sekundárním problémem je, že klientský kód nemusí zpracovávat změnu v chování z metod reflexe, jako je <xref:System.Enum.IsDefined%2A?displayProperty=fullName> . V případě, že by se měl nový člen vrátit z existujících metod nebo dojde k nekompatibilitě známé aplikace z důvodu nedostatečného využití reflexe, jediného nepřerušeného řešení je:

1. Přidejte nový výčet, který obsahuje původní a nové členy.

2. Označte původní výčet <xref:System.ObsoleteAttribute?displayProperty=fullName> atributem.

   Použijte stejný postup pro všechny externě viditelné typy nebo členy, které zveřejňují původní výčet.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte nebo přejmenujte člena.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění pro člena, který se právě používá, nebo pro knihovny, které byly dřív dodány.

## <a name="related-rules"></a>Související pravidla
 [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712: Nezačínejte hodnoty výčtu názvem typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Úložiště výčtu by mělo být Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008: Výčty by měly mít nulovou hodnotu](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Označte výčty pomocí FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
