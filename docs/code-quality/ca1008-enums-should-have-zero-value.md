---
title: 'CA1008: Výčty by měly mít nulovou hodnotu'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c9b6e48fb82be5a41c420827a32926630bb725ed
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236492"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Výčty by měly mít nulovou hodnotu

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategorie|Microsoft.Design|
|Zásadní změna|Bez přerušení – když se zobrazí výzva k přidání hodnoty **none** do výčtu bez příznaků. Přerušení – když se zobrazí výzva k přejmenování nebo odebrání všech hodnot výčtu.|

## <a name="cause"></a>příčina

Výčet bez aplikovaného <xref:System.FlagsAttribute?displayProperty=fullName> objektu nedefinuje člena, který má nulovou hodnotu. Nebo výčet, který má použit <xref:System.FlagsAttribute> , definuje člena, který má hodnotu nula, ale jeho název není ' None '. Nebo výčet definuje více členů s nulovou hodnotou.

Ve výchozím nastavení toto pravidlo vypadá pouze v externě viditelných výčtech, ale to je [konfigurovatelné](#configurability).

## <a name="rule-description"></a>Popis pravidla

Výchozí hodnota neinicializovaného výčtu, stejně jako jiné typy hodnot, je nula. Výčet bez příznaků musí definovat člen, který má nulovou hodnotu, takže výchozí hodnota je platná hodnota výčtu. V případě potřeby pojmenujte člena ' None '. V opačném případě přiřaďte k nejčastěji používanému členu nulu. Ve výchozím nastavení platí, že pokud hodnota prvního člena výčtu není v deklaraci nastavena, je jeho hodnota nula.

Pokud výčet, který má <xref:System.FlagsAttribute> použit, definuje člena s nulovou hodnotou, jeho název by měl být None, aby označoval, že ve výčtu nebyly nastaveny žádné hodnoty. Použití člena s nulovou hodnotou pro jakýkoliv jiný účel je <xref:System.FlagsAttribute> v rozporu s používáním v tom, že operátory and a nebo jsou nepoužitelné u člena. To znamená, že hodnota nula by měla být přiřazena pouze jednomu členu. Pokud se v výčtu Flags-Attribute vyčísluje více členů, které mají hodnotu `Enum.ToString()` nula, vrátí nesprávné výsledky pro členy, kteří nejsou nula.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla pro výčty s atributy bez příznaků, definujte člena, který má hodnotu nula; Tato změna je nevýznamná. Pro výčty s atributy, které definují člena s nulovou hodnotou, pojmenujte tohoto člena ' None ' a odstraňte všechny ostatní členy, které mají hodnotu nula; Toto je zásadní změna.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačit upozornění z tohoto pravidla s výjimkou výčtů s atributy, které byly odeslány dříve.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1008.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (návrh). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje dva výčty, které splňují pravidlo a výčet, `BadTraceOptions`, který porušuje pravidlo.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Související pravidla

- [CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Nejmenujte hodnoty výčtu ' rezervované '](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Neprefixovat hodnoty výčtu s názvem typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: Úložiště výčtu by měl být Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027: Označení výčtů pomocí FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Enum?displayProperty=fullName>