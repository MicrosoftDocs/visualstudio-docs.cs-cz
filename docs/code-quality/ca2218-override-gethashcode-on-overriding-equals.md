---
title: 'CA2218: Přepište GetHashCode při přepsání Equals'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8699e3434dc9c4cf9d3eccc37916c20ff7f34015
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231189"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: Přepište GetHashCode při přepsání Equals

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Veřejný typ přepisuje <xref:System.Object.Equals%2A?displayProperty=fullName> , ale nepřepisuje <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Object.GetHashCode%2A>Vrátí hodnotu založenou na aktuální instanci, která je vhodná pro algoritmy hash a datové struktury, jako je zatřiďovací tabulka. Dva objekty, které jsou stejného typu a jsou rovny, musí vracet stejný kód hash, aby bylo zajištěno, že instance následujících typů fungují správně:

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- Typy, které implementují<xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, Poskytněte implementaci <xref:System.Object.GetHashCode%2A>. Pro pár objektů stejného typu je nutné zajistit, aby implementace vrátila stejnou hodnotu, pokud vaše implementace <xref:System.Object.Equals%2A> vrátí `true` pro dvojici.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="class-example"></a>Příklad třídy

### <a name="description"></a>Popis
Následující příklad ukazuje třídu (odkazový typ), která toto pravidlo porušuje.

### <a name="code"></a>Kód
[!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]

### <a name="comments"></a>Komentáře
Následující příklad opravuje porušení pomocí přepsání <xref:System.Object.GetHashCode>.

### <a name="code"></a>Kód
[!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]

## <a name="structure-example"></a>Příklad struktury

### <a name="description"></a>Popis
Následující příklad ukazuje strukturu (typ hodnoty), která toto pravidlo porušuje.

### <a name="code"></a>Kód
[!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]

### <a name="comments"></a>Komentáře
Následující příklad opravuje porušení pomocí přepsání <xref:System.Object.GetHashCode>.

### <a name="code"></a>Kód
[!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]

## <a name="related-rules"></a>Související pravidla
[CA1046: Nepřetížit operátor přetížení se rovná na odkazových typech](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Přetížení operátoru mají pojmenované alternativy.](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226 Operátory by měly mít symetrické přetížení](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2224: Přepište Equals při přetížení operátoru Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

[CA2231: Operátor přetížení se rovná přepisování ValueType. Equals.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Operátory rovnosti](/dotnet/standard/design-guidelines/equality-operators)