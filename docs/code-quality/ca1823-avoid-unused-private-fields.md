---
title: 'CA1823: Vyhněte se nepoužitým privátním polím'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f0aa23ff93e193ee06509c1cb635404ec827793
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233366"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Vyhněte se nepoužitým privátním polím

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Kategorie|Microsoft. Performance|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Toto pravidlo je hlášeno, když existuje soukromé pole v kódu, ale není používáno žádnou cestou kódu.

## <a name="rule-description"></a>Popis pravidla
Byla zjištěna soukromá pole, která v rámci sestavení zjevně nejsou přístupná.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, odeberte pole nebo přidejte kód, který ho používá.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Z tohoto pravidla je bezpečné potlačit upozornění.

## <a name="related-rules"></a>Související pravidla
[CA1812: Vyhněte se nevytváření instancí vnitřních tříd](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Zkontrolovat nepoužité parametry](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Odebrat nepoužívané místní hodnoty](../code-quality/ca1804-remove-unused-locals.md)

[CA1811: Vyhněte se nevolanému privátnímu kódu](../code-quality/ca1811-avoid-uncalled-private-code.md)