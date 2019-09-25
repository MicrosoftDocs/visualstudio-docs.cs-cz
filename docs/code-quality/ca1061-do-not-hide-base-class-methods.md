---
title: 'CA1061: Neskrývejte metody základní třídy'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eacd20dee0758ff481b259807ba52bb78b26f5d2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235392"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Neskrývejte metody základní třídy

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Odvozený typ deklaruje metodu se stejným názvem a se stejným počtem parametrů jako jedna z jejích základních metod; jeden nebo více parametrů je základní typ odpovídajícího parametru v základní metodě; a všechny zbývající parametry mají typy, které jsou stejné jako odpovídající parametry v základní metodě.

## <a name="rule-description"></a>Popis pravidla
Metoda v základním typu je skryta v odvozeném typu v případě, že signatura parametru Derived Method se liší pouze typy, které jsou méně slabě odvozené než odpovídající typy v signatuře parametru základní metody.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, odeberte nebo přejmenujte metodu, nebo změňte signaturu parametru tak, aby metoda neskryla základní metodu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje metodu, která porušuje pravidlo.

[!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]