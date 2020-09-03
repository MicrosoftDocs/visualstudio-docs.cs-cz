---
title: 'CA1034: vnořené typy by neměly být viditelné | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04a982c993ffbb04a3e7600dfb93a00e80727b84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542165"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Vnořené typy by neměly být viditelné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Externě viditelný typ obsahuje deklaraci externě viditelného typu. Vnořené výčty a chráněné typy jsou z tohoto pravidla vyloučeny.

## <a name="rule-description"></a>Popis pravidla
 Vnořený typ je typ deklarovaný v oboru jiného typu. Vnořené typy jsou užitečné pro zapouzdření údajů o privátní implementaci nadřazeného typu. Jsou-li vnořené typy používány za tímto účelem, neměly by být externě viditelné.

 Nepoužívejte externě viditelné vnořené typy pro logické seskupení nebo pro zamezení kolizí názvů; místo toho použijte obory názvů.

 Vnořené typy zahrnují pojem přístupnost členů, které někteří programátoré nerozumí jasně.

 Chráněné typy lze použít v podtřídách a vnořených typech ve scénářích přizpůsobení předem.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pokud nechcete, aby byl vnořený typ externě viditelný, změňte přístupnost typu. V opačném případě odeberte vnořený typ z jeho nadřazeného typu. Pokud je účel vnoření zařazen do kategorie vnořeného typu, použijte místo toho obor názvů k vytvoření hierarchie.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který je v rozporu s pravidlem.

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]
