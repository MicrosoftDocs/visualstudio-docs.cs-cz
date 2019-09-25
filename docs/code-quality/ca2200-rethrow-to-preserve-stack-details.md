---
title: 'CA2200: Znovu vyvolejte pro zachování podrobností zásobníku'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5cf7fc6e31b9250392fc3ea447a5b91225640a50
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231898"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Znovu vyvolejte pro zachování podrobností zásobníku

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Výjimka je znovu vyvolána a výjimka je explicitně určena v `throw` příkazu.

## <a name="rule-description"></a>Popis pravidla

Jakmile je vyvolána výjimka, je součástí informací trasování zásobníku. Trasování zásobníku je seznam hierarchie volání metody, která začíná metodou, která vyvolá výjimku a končí metodou, která výjimku zachytí. Pokud je výjimka znovu vyvolána zadáním výjimky v `throw` příkazu, je trasování zásobníku restartováno v aktuální metodě a seznam volání metody mezi původní metodou, která vyvolala výjimku, a aktuální metodou je ztraceno. Chcete-li zachovat původní informace o trasování zásobníku s výjimkou, `throw` použijte příkaz bez zadání výjimky.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, znovu vyvolejte výjimku bez explicitní specifikace výjimky.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad

Následující příklad ukazuje metodu, `CatchAndRethrowExplicitly`, která porušuje pravidlo a metodu, `CatchAndRethrowImplicitly`,,, který splňuje pravidlo.

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]