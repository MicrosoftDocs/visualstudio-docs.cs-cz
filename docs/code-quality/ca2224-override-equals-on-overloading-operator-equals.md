---
title: 'CA2224: Přepište Equals při přetížení operátoru rovnosti'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72bcf01b9c0613bb390ac9adbbba2fb176db13bd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231219"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Přepište Equals při přetížení operátoru rovnosti

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Veřejný typ implementuje operátor rovnosti, ale nepřepisuje <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla

Operátor rovnosti má být syntakticky pohodlný způsob, jak získat přístup k funkcím <xref:System.Object.Equals%2A> metody. Při implementaci operátoru rovnosti musí být jeho logika shodná s <xref:System.Object.Equals%2A>vlastností.

C# Kompilátor vydá upozornění, pokud váš kód narušuje toto pravidlo.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, měli byste buď odebrat implementaci operátoru rovnosti, nebo přepsat <xref:System.Object.Equals%2A> a mít dvě metody vracet stejné hodnoty. Pokud operátor rovnosti nezavádí nekonzistentní chování, můžete opravit porušení poskytnutím implementace <xref:System.Object.Equals%2A> , která <xref:System.Object.Equals%2A> volá metodu v základní třídě.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Je bezpečné potlačit upozornění z tohoto pravidla, pokud operátor rovnosti vrací stejnou hodnotu jako zděděná implementace <xref:System.Object.Equals%2A>. Příklady v tomto článku zahrnují typ, který by mohl bezpečně potlačit upozornění od tohoto pravidla.

## <a name="examples-of-inconsistent-equality-definitions"></a>Příklady nekonzistentních definic rovnosti

Následující příklad ukazuje typ s nekonzistentními definicemi rovnosti. `BadPoint`změní význam rovnosti tím, že poskytuje vlastní implementaci operátoru rovnosti, ale nepřepisuje <xref:System.Object.Equals%2A> tak, aby se choval stejně.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

Následující kód testuje chování `BadPoint`.

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

Následující příklad ukazuje typ, který je technicky v rozporu s tímto pravidlem, ale nepracuje nekonzistentním způsobem.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

Následující kód testuje chování `GoodPoint`.

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

Následující příklad ukazuje třídu (odkazový typ), která toto pravidlo porušuje.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

Následující příklad opravuje porušení pomocí přepsání <xref:System.Object.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Příklad struktury

Následující příklad ukazuje strukturu (typ hodnoty), která porušuje toto pravidlo:

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

Následující příklad opravuje porušení pomocí přepsání <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Související pravidla

[CA1046: Nepřetížit operátor přetížení se rovná na odkazových typech](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Přetížení operátoru mají pojmenované alternativy.](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226 Operátory by měly mít symetrické přetížení](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218: Přepsat GetHashCode při přepsání Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: Operátor přetížení se rovná přepisování ValueType. Equals.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)