---
title: 'CA1008: výčty by měly mít nulovou hodnotu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ca58938a55330243315529e9c7990b59d1a6fe5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548340"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Výčty by měly mít nulovou hodnotu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategorie|Microsoft. Design|
|Narušující změna|Bez přerušení – když se zobrazí výzva k přidání hodnoty **none** do výčtu bez příznaků. Přerušení – když se zobrazí výzva k přejmenování nebo odebrání všech hodnot výčtu.|

## <a name="cause"></a>Příčina
 Výčet bez aplikované <xref:System.FlagsAttribute?displayProperty=fullName> definice nedefinuje člen, který má hodnotu nula; nebo výčet, který má použit, <xref:System.FlagsAttribute> definuje člen, který má hodnotu nula, ale jeho název není None nebo výčet definuje více členů s nulovou hodnotou.

## <a name="rule-description"></a>Popis pravidla
 Výchozí hodnota neinicializovaného výčtu, stejně jako jiné typy hodnot, je nula. Výčet s atributem − bez příznaků by měl definovat člen, který má nulovou hodnotu, takže výchozí hodnota je platná hodnota výčtu. V případě potřeby pojmenujte člena ' None '. V opačném případě přiřaďte k nejčastěji používanému členu nulu. Všimněte si, že ve výchozím nastavení, pokud hodnota prvního člena výčtu není nastavena v deklaraci, je jeho hodnota nula.

 Pokud výčet, který má <xref:System.FlagsAttribute> použit, definuje člena s nulovou hodnotou, jeho název by měl být None, aby označoval, že ve výčtu nebyly nastaveny žádné hodnoty. Použití člena s nulovou hodnotou pro jakýkoliv jiný účel je v rozporu s používáním <xref:System.FlagsAttribute> v tom, že operátory and a nebo jsou nepoužitelné u člena. To znamená, že hodnota nula by měla být přiřazena pouze jednomu členu. Všimněte si, že pokud se v výčtu Flags-Attribute vyčísluje více členů, které mají hodnotu nula, `Enum.ToString()` vrátí nesprávné výsledky pro členy, kteří nejsou nula.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla pro výčty s atributy, které nejsou Flags, definujte člena, který má hodnotu nula; Tato změna je nevýznamná. Pro výčty s atributy, které definují člena s nulovou hodnotou, pojmenujte tohoto člena ' None ' a odstraňte všechny ostatní členy, které mají hodnotu nula; Toto je zásadní změna.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění z tohoto pravidla s výjimkou výčtů s atributy, které byly odeslány dříve.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dva výčty, které splňují pravidlo a výčet, `BadTraceOptions` , který porušuje pravidlo.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Nepojmenovávejte výčty hodnot 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Nezačínejte hodnoty výčtu názvem typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Úložiště výčtu by mělo být Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: Označte výčty pomocí FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Viz také
 <xref:System.Enum?displayProperty=fullName>
