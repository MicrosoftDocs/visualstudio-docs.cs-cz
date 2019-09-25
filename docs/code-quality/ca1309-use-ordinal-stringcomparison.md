---
title: 'CA1309: Použijte řadový StringComparison'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eff846cfacb30d97c28cadd14b86f7724b1d2ce4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234927"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Použijte řadový StringComparison

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategorie|Microsoft.Globalization|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Operace porovnání řetězců, která je nelingvistická, nenastavuje <xref:System.StringComparison> parametr buď na **ordinální** , nebo na **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Popis pravidla
Mnohé řetězcové operace, nejdůležitější <xref:System.String.Compare%2A?displayProperty=fullName> metody a <xref:System.String.Equals%2A?displayProperty=fullName> , nyní poskytují přetížení, které přijímá <xref:System.StringComparison?displayProperty=fullName> hodnotu výčtu jako parametr.

Když zadáte buď **StringComparison. Ordinal** nebo **StringComparison. OrdinalIgnoreCase**, porovnávání řetězců je nelingvistické. To znamená, že funkce, které jsou specifické pro přirozený jazyk, se při rozhodování o porovnávání ignorují. Ignorování funkcí přirozeného jazyka znamená, že rozhodnutí jsou založena na jednoduchých porovnáních bajtů, nikoli v tabulkách s použitím malých a velkých písmen nebo rovnocenných hodnot, které jsou parametrizované pomocí jazykové V důsledku toho explicitním nastavením parametru buď na **StringComparison. Ordinal** nebo **StringComparison. OrdinalIgnoreCase**, váš kód často získává rychlost, zvyšuje správnost a je spolehlivější.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, změňte metodu porovnání řetězců na přetížení, které přijímá <xref:System.StringComparison?displayProperty=fullName> výčet jako parametr, a zadejte buď **pořadové číslo** nebo **OrdinalIgnoreCase**. Například změňte `String.Compare(str1, str2)` na `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Je bezpečné potlačit upozornění z tohoto pravidla, je-li knihovna nebo aplikace určena pro omezené místní cílovou skupinu, nebo pokud by měla být použita sémantika aktuální jazykové verze.

## <a name="see-also"></a>Viz také:

- [Upozornění globalizace](../code-quality/globalization-warnings.md)
- [CA1307: Zadat StringComparison](../code-quality/ca1307-specify-stringcomparison.md)