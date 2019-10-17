---
title: 'CA1501: Vyhněte se nadměrné dědičnosti'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fceabd5487b28d4cf16b5cc0d61cd81de2aeb23a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444157"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Vyhněte se nadměrné dědičnosti

|||
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|Kategorie|Microsoft. udržovatelnost|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Typ je více než čtyři úrovně hluboko v hierarchii dědičnosti.

## <a name="rule-description"></a>Popis pravidla

Hluboce vnořené hierarchie typů může být obtížné sledovat, pochopit a udržovat. Toto pravidlo omezuje analýzu na hierarchie ve stejném modulu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, odvoďte typ ze základního typu, který je méně hluboko v hierarchii dědičnosti, nebo odstraňte některé mezilehlé základní typy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Z tohoto pravidla je bezpečné potlačit upozornění. Údržba kódu však může být obtížnější. Všimněte si, že v závislosti na viditelnosti základních typů může řešení porušení tohoto pravidla vytvořit zásadní změny. Například odebrání veřejných základních typů je zásadní změna.

## <a name="example"></a>Příklad

Následující příklad ukazuje typ, který je v rozporu s pravidlem:

[!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
[!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]
