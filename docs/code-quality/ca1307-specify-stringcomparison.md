---
title: 'CA1307: Určete StringComparison'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e352eea1b7fcf82cb948315affeae6e30690a4aa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234977"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Určete StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategorie|Microsoft.Globalization|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Operace porovnání řetězců používá přetížení metody, které nenastavuje <xref:System.StringComparison> parametr.

## <a name="rule-description"></a>Popis pravidla
Mnoho řetězcových operací, nejdůležitější <xref:System.String.Compare%2A> metody a <xref:System.String.Equals%2A> , poskytují přetížení, které přijímá <xref:System.StringComparison> hodnotu výčtu jako parametr.

Pokaždé, když existuje přetížení, <xref:System.StringComparison> které přijímá parametr, měl by být použit místo přetížení, které tento parametr nevyužívá. Explicitním nastavením tohoto parametru je váš kód často jasný a je snazší ho udržovat.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, změňte metody porovnání řetězců na přetížení, které přijímají <xref:System.StringComparison> výčet jako parametr. Například: změnit `String.Compare(str1, str2)` na `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
V případě, že je knihovna nebo aplikace určena pro omezené místní cílovou skupinu a nebude proto lokalizována, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="see-also"></a>Viz také:

- [Upozornění globalizace](../code-quality/globalization-warnings.md)
- [CA1309: Použít ordinální StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)