---
title: 'CA2200: znovu vyvolejte pro zachování podrobností zásobníku | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6d63ef6ff3647742e931fd05f59c66b40059ad00
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546364"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Znovu vyvolejte pro zachování podrobností zásobníku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Výjimka je znovu vyvolána a výjimka je explicitně určena v `throw` příkazu.

## <a name="rule-description"></a>Popis pravidla
 Jakmile je vyvolána výjimka, je součástí informací trasování zásobníku. Trasování zásobníku je seznam hierarchie volání metody, která začíná metodou, která vyvolá výjimku a končí metodou, která výjimku zachytí. Pokud je výjimka znovu vyvolána zadáním výjimky v `throw` příkazu, je trasování zásobníku restartováno v aktuální metodě a seznam volání metody mezi původní metodou, která vyvolala výjimku, a aktuální metodou je ztraceno. Chcete-li zachovat původní informace o trasování zásobníku s výjimkou, použijte `throw` příkaz bez zadání výjimky.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, znovu vyvolejte výjimku bez explicitní specifikace výjimky.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, `CatchAndRethrowExplicitly` , která porušuje pravidlo a metodu, `CatchAndRethrowImplicitly` ,,, který splňuje pravidlo.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
