---
title: 'CA2224: Přepište Equals při přetížení operátoru rovnosti'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4cbb4c6ea167dd06328c3cce513f42cdfcf3c7a1
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546415"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Přepište Equals při přetížení operátoru rovnosti

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

Veřejný typ implementuje operátor rovnosti, ale nepřepisuje <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla

Operátor rovnosti má být syntakticky pohodlný způsob, jak přistupovat k funkcím <xref:System.Object.Equals%2A> metody. Pokud se rozhodnete implementovat operátor rovnosti, musí být shodná s svou logikou <xref:System.Object.Equals%2A>.

Kompilátor jazyka C# vyvolá upozornění, pokud váš kód poruší toto pravidlo.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, buď odstranit implementace operátoru rovnosti, nebo přepsat <xref:System.Object.Equals%2A> a mít dvě metody vrací stejné hodnoty. Pokud operátor rovnosti nezavádí nekonzistentní chování, porušení zásad můžete vyřešit tím, že poskytuje implementace <xref:System.Object.Equals%2A> , která volá <xref:System.Object.Equals%2A> metodu v základní třídě.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Je bezpečné potlačit upozornění tohoto pravidla, je-li operátor rovnosti vrací stejnou hodnotu jako zděděná implementace metody <xref:System.Object.Equals%2A>. Příklady v tomto článku zahrnují typ, který může bezpečně potlačit upozornění tohoto pravidla.

## <a name="examples-of-inconsistent-equality-definitions"></a>Příklady definice nekonzistentní rovnosti

Následující příklad ukazuje typ s nekonzistentní definice rovnosti. `BadPoint` Změní význam rovnosti poskytnutím vlastní implementace operátoru rovnosti, ale nepřepisuje <xref:System.Object.Equals%2A> tak, aby se chová stejně.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

Následující kód testy chování `BadPoint`.

[!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

Tento příklad vytvoří následující výstup:

```txt
a =  ([0] 1,1) and b = ([1] 2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? No
b == bcopy ? Yes
```

Následující příklad ukazuje typ, který technicky poruší toto pravidlo, ale nechová nekonzistentní způsobem.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

Následující kód testy chování `GoodPoint`.

[!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

Tento příklad vytvoří následující výstup:

```txt
a =  (1,1) and b = (2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? Yes
b == bcopy ? Yes
```

## <a name="class-example"></a>Příklad třídy

Následující příklad ukazuje třídu (odkaz), který porušuje tato pravidla.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

V následujícím příkladu řeší porušení zásady tak, že přepíšete <xref:System.Object.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Příklad struktury

Následující příklad ukazuje strukturu (typ hodnoty), který porušuje tato pravidla:

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

V následujícím příkladu řeší porušení zásady tak, že přepíšete <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Související pravidla

[CA1046: Nepřetěžujte operátory rovnosti na odkazových typech](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Přetížení operátoru mají pojmenované alternativy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Operátory by měly mít symetrické přetížení](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218: Přepište GetHashCode při přepsání Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: Přetižte operátor equals při přepsání ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)