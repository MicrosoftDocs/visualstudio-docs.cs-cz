---
title: 'CA1307: zadejte StringComparison | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 033d8f0e22ec040ffb10821993a5a9c647ee401e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538915"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Určete StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Operace porovnání řetězců používá přetížení metody, které nenastavuje <xref:System.StringComparison> parametr.

## <a name="rule-description"></a>Popis pravidla
 Mnoho řetězcových operací, nejdůležitější <xref:System.String.Compare%2A> metody a <xref:System.String.Equals%2A> , poskytují přetížení, které přijímá <xref:System.StringComparison> hodnotu výčtu jako parametr.

 Pokaždé, když existuje přetížení, které přijímá <xref:System.StringComparison> parametr, měl by být použit místo přetížení, které tento parametr nevyužívá. Explicitním nastavením tohoto parametru je váš kód často jasný a je snazší ho udržovat.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte metody porovnání řetězců na přetížení, které přijímají <xref:System.StringComparison> výčet jako parametr. Například: změnit `String.Compare(str1, str2)` na `String.Compare(str1, str2, StringComparison.Ordinal)` .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 V případě, že je knihovna nebo aplikace určena pro omezené místní cílovou skupinu a nebude proto lokalizována, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="see-also"></a>Viz také
 [Upozornění globalizace](../code-quality/globalization-warnings.md) [CA1309: použijte ordinální StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)
