---
title: 'CA1027: označte výčty pomocí FlagsAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 774279dd05bd14c34df7f1d450f00599812d6a5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544505"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Označte výčty pomocí FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Hodnoty veřejného výčtu jsou mocninami dvou nebo jsou kombinací jiných hodnot, které jsou definovány ve výčtu, a atribut není k <xref:System.FlagsAttribute?displayProperty=fullName> dispozici. Pro snížení falešně pozitivních hodnot toto pravidlo neoznamuje porušení výčtů, které mají sousedící hodnoty.

## <a name="rule-description"></a>Popis pravidla
 Výčet je typ hodnoty, který definuje množinu souvisejících pojmenovaných konstant. Platí <xref:System.FlagsAttribute> pro výčet, pokud se jeho pojmenované konstanty dají smysluplně kombinovat. Představte si například výčet dnů v týdnu v aplikaci, který uchovává přehled o dostupných prostředcích. Pokud je dostupnost každého prostředku kódována pomocí výčtu, který je k <xref:System.FlagsAttribute> dispozici, lze reprezentovat libovolnou kombinaci dnů. Bez atributu lze reprezentovat pouze jeden den v týdnu.

 Pro pole, která ukládají kombinovatelné výčty, jsou jednotlivé hodnoty výčtu považovány za skupiny bitů v poli. Proto se tato pole někdy označují jako *Bitová pole*. Pro kombinování hodnot výčtu pro úložiště v bitovém poli použijte logické podmíněné operátory. Chcete-li otestovat bitové pole k určení, zda je zadána konkrétní hodnota výčtu, použijte logické logické operátory. Pro bitové pole pro uložení a načtení kombinovaných hodnot výčtu správně musí být každá hodnota, která je definována ve výčtu, Mocnina dvou. Pokud to tak není, logické operátory logických operátorů nebudou moci extrahovat jednotlivé hodnoty výčtu, které jsou uloženy v poli.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte <xref:System.FlagsAttribute> do výčtu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud nechcete, aby hodnoty výčtu byly možné, potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 V následujícím příkladu `DaysEnumNeedsFlags` je výčet, který splňuje požadavky na použití <xref:System.FlagsAttribute> , ale nemá je. `ColorEnumShouldNotHaveFlag`Výčet nemá hodnoty, které jsou mocninou dvou, ale nesprávně určuje <xref:System.FlagsAttribute> . To porušuje pravidlo [CA2217: neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Viz také
 <xref:System.FlagsAttribute?displayProperty=fullName>
