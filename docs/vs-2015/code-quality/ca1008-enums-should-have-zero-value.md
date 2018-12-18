---
title: 'CA1008: Výčty by měly mít nulovou hodnotu | Dokumentace Microsoftu'
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
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 69e60b0f2ee8106b04507722f1b3094e1bbdbbc8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874823"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Výčty by měly mít nulovou hodnotu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategorie|Microsoft.Design|
|Narušující změna|Bez konce – po zobrazení výzvy k přidání **žádný** hodnotu výčtu bez příznaku. Zásadní – po zobrazení výzvy k přejmenujte nebo odeberte všechny hodnoty výčtu.|

## <a name="cause"></a>příčina
 Výčet bez použité <xref:System.FlagsAttribute?displayProperty=fullName> nedefinuje člena, který má hodnotu nula; nebo výčet, který má použité <xref:System.FlagsAttribute> definuje člen s hodnotou nula, ale jeho název není 'None' nebo výčet definuje více s nulovou hodnotou členy.

## <a name="rule-description"></a>Popis pravidla
 Výchozí hodnota neinicializovaného výčtu je stejně jako jiné hodnotové typy, je nula. Výčet bez flags−attributed by měl definovat člen, který má hodnotu nula, tak, aby výchozí hodnota je platná hodnota výčtu. V případě potřeby, název člena 'None'. V opačném případě přiřadíte nulový nejčastěji používané člena. Všimněte si, že ve výchozím nastavení, pokud hodnota první člen výčtu není nastavená v deklaraci, její hodnota je nula.

 Pokud výčet, který má <xref:System.FlagsAttribute> použít definuje člen s nulovou hodnotou, její název by měl být "Žádný" k označení, že ve výčtu byly nastaveny žádné hodnoty. Použití člena s nulovou hodnotou pro jakékoli jiné účely bylo v rozporu s použití <xref:System.FlagsAttribute> , AND a bitové operátory jsou zbytečné s členem. Z toho vyplývá, že pouze jednoho člena by měla být přiřazena hodnota nula. Všimněte si, že pokud více členů, které mají nulovou hodnotu Probíhá s atributy příznaků výčtu, `Enum.ToString()` vrátí nesprávné výsledky pro členy, kteří nejsou nula.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla pro výčty bez flags−attributed, definujte člen, který má hodnotu nula; Jedná se o změnu pevné. Pro výčty příznaků s atributy, které definovat člen s hodnotou nula název tohoto člena 'None' a odstranit všechny členy, které mají hodnotu nula; Toto je zásadní změnu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění tohoto pravidla s výjimkou s atributy příznaky výčty, které byly dříve součástí.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dva výčty, které splňují pravidla a výčet, `BadTraceOptions`, který porušuje pravidla.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Nepojmenovávejte výčty hodnot Reserved](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Nezačínejte hodnoty výčtu s názvem typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Úložiště výčtu by měl být Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: Označte výčty pomocí FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Viz také
 <xref:System.Enum?displayProperty=fullName>



