---
title: 'CA1013: Přetižte operátor rovnosti společně s přetížením operátorů sčítání a odečítání'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2bb5fd5c0e68b5dcffc212af03294d94d04d2abe
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236338"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Přetižte operátor rovnosti společně s přetížením operátorů sčítání a odečítání

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Veřejný nebo chráněný typ implementuje operátory sčítání a odčítání, aniž by implementoval operátor rovnosti.

## <a name="rule-description"></a>Popis pravidla
V případě, že instance typu lze kombinovat pomocí operací, jako je sčítání a odčítání, byste měli téměř vždy definovat rovnost, která `true` se vrátí pro všechny dvě instance, které mají stejné hodnoty prvků.

Nelze použít výchozí operátor rovnosti v přetížené implementaci operátoru rovnosti. Uděláte to tak, že dojde k přetečení zásobníku. K implementaci operátoru rovnosti použijte metodu Object. Equals v implementaci. Podívejte se na téma v následujícím příkladu.

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, implementujte operátor rovnosti tak, aby byl matematicky konzistentní s operátory sčítání a odčítání.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
V případě, že výchozí implementace operátoru rovnosti poskytuje správné chování pro typ, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
Následující příklad definuje typ (`BadAddableType`), který porušuje toto pravidlo. Tento typ by měl implementovat operátor rovnosti, aby všechny dvě instance, které mají stejné hodnoty polí `true` , byly testovány pro rovnost. Typ `GoodAddableType` zobrazuje opravenou implementaci. Všimněte si, že tento typ také implementuje operátor nerovnosti a <xref:System.Object.Equals%2A> přepsání pro splnění dalších pravidel. Bude implementována <xref:System.Object.GetHashCode%2A>i kompletní implementace.

[!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>Příklad
Následující příklad testuje rovnost pomocí instancí typů, které byly dříve definovány v tomto tématu, k ilustraci výchozího a správného chování operátoru rovnosti.

[!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

Tento příklad vytvoří následující výstup:

```txt
Bad type:  {2,2} {2,2} are equal? No
Good type: {3,3} {3,3} are equal? Yes
Good type: {3,3} {3,3} are == ?   Yes
Bad type:  {2,2} {9,9} are equal? No
Good type: {3,3} {9,9} are == ?   No
```

## <a name="see-also"></a>Viz také:

- [Operátory rovnosti](/dotnet/standard/design-guidelines/equality-operators)