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
ms.openlocfilehash: 8433ac081a45e3dbab80ffcd6f96e6d1db914337
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672008"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testujte správně NaN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Výraz testuje hodnotu od <xref:System.Single.NaN?displayProperty=fullName> nebo <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Double.NaN?displayProperty=fullName>, který představuje nečíselný výsledek, vrátí výsledky, pokud není definována aritmetická operace. Libovolný výraz, který testuje rovnost mezi hodnotou a <xref:System.Double.NaN?displayProperty=fullName> vždy vrátí `false`. Libovolný výraz, který testuje nerovnost mezi hodnotou a <xref:System.Double.NaN?displayProperty=fullName> vždy vrátí `true`.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla a přesně určit, zda hodnota představuje <xref:System.Double.NaN?displayProperty=fullName>, použijte k otestování hodnoty <xref:System.Single.IsNaN%2A?displayProperty=fullName> nebo <xref:System.Double.IsNaN%2A?displayProperty=fullName>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dva výrazy, které nesprávně testují hodnotu proti <xref:System.Double.NaN?displayProperty=fullName> a výraz, který správně používá <xref:System.Double.IsNaN%2A?displayProperty=fullName> k otestování hodnoty.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
