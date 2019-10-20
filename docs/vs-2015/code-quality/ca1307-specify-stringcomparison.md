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
ms.openlocfilehash: 111f0b85a601d931ac17bde46f7170fa81e71815
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661400"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Zadejte možnosti StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Operace porovnání řetězců používá přetížení metody, které nenastavuje parametr <xref:System.StringComparison>.

## <a name="rule-description"></a>Popis pravidla
 Mnoho operací s řetězci, nejdůležitější <xref:System.String.Compare%2A> a <xref:System.String.Equals%2A> metody, poskytují přetížení, které přijímá hodnotu výčtu <xref:System.StringComparison> jako parametr.

 Pokaždé, když existuje přetížení, které přijímá parametr <xref:System.StringComparison>, měl by se použít místo přetížení, které tento parametr nevyužívá. Explicitním nastavením tohoto parametru je váš kód často jasný a je snazší ho udržovat.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte metody porovnání řetězců na přetížení, které přijímají výčet <xref:System.StringComparison> jako parametr. Například: Změňte `String.Compare(str1, str2)` na `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 V případě, že je knihovna nebo aplikace určena pro omezené místní cílovou skupinu a nebude proto lokalizována, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="see-also"></a>Viz také
 [Upozornění globalizace](../code-quality/globalization-warnings.md) [CA1309: použijte ordinální StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)
