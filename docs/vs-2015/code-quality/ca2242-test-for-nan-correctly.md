---
title: 'CA2242: Testujte správně NaN | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d7cd2d6d823dfb13c86ad3f2cc4ef001e854955c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842479"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testujte správně NaN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Výraz testuje hodnotu proti <xref:System.Single.NaN?displayProperty=fullName> nebo <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Double.NaN?displayProperty=fullName>, který představuje not a number, vznikne, když není definován aritmetické operace. Libovolný výraz, který testuje rovnost mezi hodnotou a <xref:System.Double.NaN?displayProperty=fullName> vždy vrátí `false`. Libovolný výraz, který testuje nerovnost mezi hodnotou a <xref:System.Double.NaN?displayProperty=fullName> vždy vrátí `true`.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla a přesně určit, zda hodnota představuje <xref:System.Double.NaN?displayProperty=fullName>, použijte <xref:System.Single.IsNaN%2A?displayProperty=fullName> nebo <xref:System.Double.IsNaN%2A?displayProperty=fullName> pro testování hodnot.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dva výrazy, které testují nesprávné hodnoty s <xref:System.Double.NaN?displayProperty=fullName> a výraz, který používá správně <xref:System.Double.IsNaN%2A?displayProperty=fullName> pro testování hodnot.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]



