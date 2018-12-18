---
title: 'CA1027: Označte výčty pomocí FlagsAttribute | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b8cebc05fa58c589f07beed70ab222d31bc8553a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879217"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Označte výčty pomocí FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Veřejný výčet hodnoty mocniny dvou nebo kombinací jiné hodnoty, které jsou definovány ve výčtu, a <xref:System.FlagsAttribute?displayProperty=fullName> atribut není k dispozici. Pokud chcete snížit počet falešně pozitivních výsledků, toto pravidlo sestavu porušení pro výčty, které mají souvislých hodnot.

## <a name="rule-description"></a>Popis pravidla
 Výčet je typ hodnoty, který definuje množinu souvisejících pojmenovaných konstant. Použít <xref:System.FlagsAttribute> výčtu když mohou být pojmenované konstanty smysluplně kombinovány. Představte si třeba výčet dny v týdnu v aplikaci, která uchovává informace o den, které prostředky jsou k dispozici. Pokud je dostupnost každého prostředku zakódován pomocí výčtu, která má <xref:System.FlagsAttribute> můžou být vyjádřeny současné libovolnou kombinací těchto dnů. Bez atributu může být reprezentován jenom jeden den v týdnu.

 U polí, které ukládají combinable – výčty hodnot jednotlivých výčtu jsou považovány za skupin bitů v poli. Proto tato pole jsou někdy označovány jako *bitová pole*. Chcete-li kombinace hodnot výčtu pro úložiště v bitové pole, použijte logická podmíněných operátorů. K otestování bitové pole. k určení, zda hodnota konkrétní výčtu není k dispozici, použijte logické logické operátory. Jednotlivé hodnoty, které je definováno ve výčtu bitové pole k ukládání a načítání hodnot výčtu kombinované správně, musí být mocninou čísla 2. Pokud to není tak logické logické operátory nebude možné extrahovat hodnoty jednotlivých výčtu, které jsou uloženy v poli.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte <xref:System.FlagsAttribute> do výčtu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění tohoto pravidla, pokud nechcete, aby výčtu hodnoty, které mají být kombinovatelných.

## <a name="example"></a>Příklad
 V následujícím příkladu `DaysEnumNeedsFlags` je výčet, který splňuje požadavky na používání <xref:System.FlagsAttribute>, ale nejsou dostupné. `ColorEnumShouldNotHaveFlag` Výčet nemá žádné hodnoty, které jsou pro mocniny dvou ale nesprávně určuje <xref:System.FlagsAttribute>. To porušuje pravidlo [CA2217: neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Viz také
 <xref:System.FlagsAttribute?displayProperty=fullName>



