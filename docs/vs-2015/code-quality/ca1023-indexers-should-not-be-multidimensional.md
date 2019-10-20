---
title: 'CA1023: indexery by neměly být multidimenzionální | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1b7c4c82add8644a1c2c213536c2ad3c0097c3a6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661981"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Indexery by neměly být multidimenzionální
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ obsahuje veřejný nebo chráněný indexer, který používá více než jeden index.

## <a name="rule-description"></a>Popis pravidla
 Indexery, tj. indexované vlastnosti, by měly používat jeden index. Multidimenzionální indexery můžou významně snížit použitelnost knihovny. Pokud návrh vyžaduje více indexů, je třeba znovu zvážit, zda typ představuje logické úložiště dat. V takovém případě použijte metodu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte návrh tak, aby používal celé číslo jedinou nebo index řetězce, nebo použijte metodu místo indexeru.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla až po pečlivém zvážení nutnosti nestandardního indexeru.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, `DayOfWeek03` s multidimenzionálním indexerem, který porušuje pravidlo. Indexer se může zobrazit jako typ převodu, a proto je lépe přístupný jako metoda. Typ je přepracován v `RedesignedDayOfWeek03` pro splnění pravidla.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1043: Použijte celočíselný nebo řetězcový argument pro indexery](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Použijte vlastnosti, kde je to vhodné](../code-quality/ca1024-use-properties-where-appropriate.md)
