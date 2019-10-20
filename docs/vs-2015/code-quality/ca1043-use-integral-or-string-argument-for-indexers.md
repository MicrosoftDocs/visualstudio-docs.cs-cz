---
title: 'CA1043: Použijte celočíselný nebo řetězcový argument pro indexery | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 528b3a1f301544ccb20cfa6bddc31c0a5c50d1ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668293"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Použijte celočíselný nebo řetězcový argument pro indexery
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ obsahuje veřejný nebo chráněný indexer, který používá jiný typ indexu než <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName> nebo <xref:System.String?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 Indexery, tj. indexované vlastnosti, by měly pro index používat celočíselné nebo řetězcové typy. Tyto typy jsou obvykle používány pro indexování datových struktur a zvyšují použitelnost knihovny. Použití typu <xref:System.Object> by mělo být omezeno na ty případy, kde konkrétní celé číslo nebo typ řetězce nelze zadat v době návrhu. Pokud návrh vyžaduje jiné typy pro index, je třeba znovu zvážit, zda typ představuje logické úložiště dat. Pokud nepředstavuje logické úložiště dat, použijte metodu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte index na celé číslo nebo typ řetězce nebo použijte metodu místo indexeru.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla až po pečlivém zvážení nutnosti nestandardního indexeru.

## <a name="example"></a>Příklad
 Následující příklad ukazuje indexer, který používá index <xref:System.Int32>.

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1023: Indexery by neměly být multidimenzionální](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: Použijte vlastnosti, kde je to vhodné](../code-quality/ca1024-use-properties-where-appropriate.md)
