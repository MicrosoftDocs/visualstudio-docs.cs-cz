---
title: 'CA2217: Neoznačujte výčty pomocí FlagsAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12cc5f9fc58ac533d118b693587cf807f44b288f
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031641"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Neoznačujte výčty pomocí FlagsAttribute

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Kategorie|Microsoft.Usage|
|Narušující změna|Bez ukončování řádků|

## <a name="cause"></a>příčina

Externě viditelné výčet je označené jako <xref:System.FlagsAttribute>a obsahuje jeden nebo více hodnot, které nejsou zajišťuje dvě nebo kombinaci dalších definované hodnoty na výčtu.

## <a name="rule-description"></a>Popis pravidla

Výčet by měl mít <xref:System.FlagsAttribute> nachází pouze v případě, že každá hodnota definovaná ve výčtu je druhou mocninou dva nebo jejich kombinaci definované hodnoty.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení toto pravidlo, odeberte <xref:System.FlagsAttribute> z výčtu.

## <a name="when-to-suppress-warnings"></a>Při potlačení upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="example-that-should-not-have-the-attribute"></a>Příklad, který by neměl mít atribut

Následující příklad ukazuje výčet, `Color`, který obsahuje hodnotu 3. 3 není power dvou nebo kombinaci některých definovaných hodnot. `Color` – Výčet by nemělo být označené jako <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>Příklad, který by měl být atribut

Následující příklad ukazuje výčet, `Days`, který splňuje požadavky pro bude označena jako s <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>Související pravidla

[CA1027: Označte výčty pomocí FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Viz také

- <xref:System.FlagsAttribute?displayProperty=fullName>
