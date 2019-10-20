---
title: 'CA1814: preferovat vícenásobná pole nad multidimenzionální | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f0ac183321bd2a3070b1f1ddc54402b74c8fb823
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668408"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Preferujte vícenásobná pole více než multidimenzionální
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Kategorie|Microsoft. Performance|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Člen je deklarován jako multidimenzionální pole.

## <a name="rule-description"></a>Popis pravidla
 Vícenásobné pole je pole, jehož prvky jsou pole. Pole tvořící prvky mohou být různě velká, což vede k menšímu nevyužitému místu u některých sad dat.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte multidimenzionální pole na vícenásobné pole.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla, pokud multidimenzionální pole nezahrnuje prostor.

## <a name="example"></a>Příklad
 Následující příklad ukazuje deklarace pro zubatá a multidimenzionální pole.

 [!code-csharp[FxCop.Performance.JaggedArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/cs/FxCop.Performance.JaggedArrays.cs#1)]
 [!code-vb[FxCop.Performance.JaggedArrays#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/vb/FxCop.Performance.JaggedArrays.vb#1)]
