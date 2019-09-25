---
title: 'CA1011: Zvažte předání základních typů jako parametrů'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dcb5937f58088684e7bfc204ab4143434b0684ae
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236399"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Zvažte předání základních typů jako parametrů

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Deklarace metody obsahuje formální parametr, který je odvozeným typem, a metoda volá pouze členy základního typu parametru.

## <a name="rule-description"></a>Popis pravidla

Je-li v deklaraci metody zadán jako parametr základní typ, lze jako příslušný argument k metodě předat kterýkoliv typ odvozený z tohoto základního typu. Pokud je argument použit uvnitř těla metody, konkrétní metoda, která je spuštěna, závisí na typu argumentu. Pokud nejsou vyžadovány další funkce, které jsou poskytovány odvozeným typem, použití základního typu umožňuje širší použití metody.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, změňte typ parametru na jeho základní typ.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Z tohoto pravidla je bezpečné potlačit upozornění.

- Pokud metoda vyžaduje konkrétní funkce, které jsou poskytovány odvozeným typem

     \- nebo –

- aby bylo možné vyhovět, že pouze odvozený typ nebo více odvozený typ, je předán metodě.

V těchto případech bude kód robustnější z důvodu kontroly silného typu, který je poskytován kompilátorem a modulem runtime.

## <a name="example"></a>Příklad

Následující příklad ukazuje metodu, `ManipulateFileStream`, která se dá použít jenom <xref:System.IO.FileStream> s objektem, který porušuje toto pravidlo. Druhá metoda `ManipulateAnyStream`, splňuje pravidlo tím, že <xref:System.IO.FileStream> nahradí parametr pomocí <xref:System.IO.Stream>.

[!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
[!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
[!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Související pravidla

[CA1059: Členové by neměli zveřejňovat určité konkrétní typy](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)