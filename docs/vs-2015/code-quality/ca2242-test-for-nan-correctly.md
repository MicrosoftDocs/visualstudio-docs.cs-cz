---
title: 'CA2242: test pro správně NaN | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0c832b7eb4a94506c5e15dfa5858bb9f6753912
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546260"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testujte správně NaN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Výraz testuje hodnotu proti <xref:System.Single.NaN?displayProperty=fullName> nebo <xref:System.Double.NaN?displayProperty=fullName> .

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Double.NaN?displayProperty=fullName>, který reprezentuje nečíselný výsledek, je-li aritmetická operace nedefinovaná. Libovolný výraz, který testuje rovnost mezi hodnotou a <xref:System.Double.NaN?displayProperty=fullName> vždy vrátí `false` . Libovolný výraz, který testuje nerovnost mezi hodnotou a <xref:System.Double.NaN?displayProperty=fullName> vždy vrátí `true` .

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla a přesně určit, zda hodnota představuje <xref:System.Double.NaN?displayProperty=fullName> , použijte <xref:System.Single.IsNaN%2A?displayProperty=fullName> nebo <xref:System.Double.IsNaN%2A?displayProperty=fullName> k otestování hodnoty.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dva výrazy, které nesprávně testují hodnotu proti <xref:System.Double.NaN?displayProperty=fullName> a výraz, který je správně použit <xref:System.Double.IsNaN%2A?displayProperty=fullName> k otestování hodnoty.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
