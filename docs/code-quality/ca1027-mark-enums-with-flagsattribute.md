---
title: 'CA1027: Označte výčty pomocí FlagsAttribute'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8375d2096417948b19a228d8a4f02accac7c0b5f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236117"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Označte výčty pomocí FlagsAttribute

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Hodnoty výčtu jsou mocninami dvou nebo jsou kombinací jiných hodnot, které jsou definovány ve výčtu, a <xref:System.FlagsAttribute?displayProperty=fullName> atribut není k dispozici. Pro snížení falešně pozitivních hodnot toto pravidlo neoznamuje porušení výčtů, které mají sousedící hodnoty.

Ve výchozím nastavení toto pravidlo vyhledává pouze veřejné výčty, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Výčet je typ hodnoty, který definuje množinu souvisejících pojmenovaných konstant. Platí <xref:System.FlagsAttribute> pro výčet, pokud se jeho pojmenované konstanty dají smysluplně kombinovat. Představte si například výčet dnů v týdnu v aplikaci, který uchovává přehled o dostupných prostředcích. Pokud je dostupnost každého prostředku kódována pomocí výčtu, který <xref:System.FlagsAttribute> je k dispozici, lze reprezentovat libovolnou kombinaci dnů. Bez atributu lze reprezentovat pouze jeden den v týdnu.

Pro pole, která ukládají kombinovatelné výčty, jsou jednotlivé hodnoty výčtu považovány za skupiny bitů v poli. Proto se tato pole někdy označují jako *Bitová pole*. Pro kombinování hodnot výčtu pro úložiště v bitovém poli použijte logické podmíněné operátory. Chcete-li otestovat bitové pole k určení, zda je zadána konkrétní hodnota výčtu, použijte logické logické operátory. Pro bitové pole pro uložení a načtení kombinovaných hodnot výčtu správně musí být každá hodnota, která je definována ve výčtu, Mocnina dvou. Pokud to tak není, logické operátory logických operátorů nebudou moci extrahovat jednotlivé hodnoty výčtu, které jsou uloženy v poli.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, přidejte <xref:System.FlagsAttribute> do výčtu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pokud nechcete, aby hodnoty výčtu byly možné, potlačit upozornění od tohoto pravidla.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1027.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (návrh). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Příklad

V následujícím příkladu `DaysEnumNeedsFlags` je výčet, který splňuje požadavky na použití <xref:System.FlagsAttribute> , ale nemá je. Výčet nemá hodnoty, které jsou mocninou dvou, ale nesprávně určují <xref:System.FlagsAttribute>. `ColorEnumShouldNotHaveFlag` To porušuje CA2217 [pravidla: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

[!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>Související pravidla

- [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Viz také:

- <xref:System.FlagsAttribute?displayProperty=fullName>