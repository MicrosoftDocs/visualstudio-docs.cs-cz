---
title: 'CA1712: Nezačínejte hodnoty výčtu s názvem typu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9bf4d7d2ee0df2a6c5330fcfb8fe6bd168e318c9
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72439395"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: Nezačínejte hodnoty výčtu s názvem typu

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Kategorie|Microsoft. pojmenování|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Výčet obsahuje člena, jehož název začíná názvem typu výčtu.

## <a name="rule-description"></a>Popis pravidla
Názvy členů výčtu nejsou uvozeny názvem typu, protože informace o typu se mají poskytnout pomocí vývojářských nástrojů.

Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zkracuje čas potřebný k tomu, abyste se seznámili s novou softwarovou knihovnou a zvyšovali si riziko, že knihovna byla vyvinutá někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, odeberte ze člena výčtu předponu názvu typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje nesprávně pojmenovaný výčet následovaný opravenou verzí.

[!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
[!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
[!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA1711: Identifikátory by neměly mít nesprávnou příponu](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

[CA1027: Označte výčty pomocí FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

[CA2217: Neoznačujte výčty pomocí FlagsAttribute](../code-quality/ca2217.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Enum?displayProperty=fullName>
