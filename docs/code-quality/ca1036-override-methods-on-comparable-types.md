---
title: 'CA1036: Přepište metody u srovnatelných typů'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be340314afe36f3a930474f345715965f566b2d4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235995"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Přepište metody u srovnatelných typů

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Typ implementuje <xref:System.IComparable?displayProperty=fullName> rozhraní a nepřepisuje <xref:System.Object.Equals%2A?displayProperty=fullName> ani nepřetěžují operátor specifický pro jazyk pro rovnost, nerovnost, menší než nebo větší než. Pravidlo neoznamuje porušení, pokud typ dědí pouze implementaci rozhraní.

Ve výchozím nastavení toto pravidlo vyhledává pouze veřejné a chráněné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Typy, které definují vlastní pořadí řazení implementují <xref:System.IComparable> rozhraní. <xref:System.IComparable.CompareTo%2A> Metoda vrátí celočíselnou hodnotu, která označuje správné pořadí řazení pro dvě instance typu. Toto pravidlo identifikuje typy, které nastaví pořadí řazení. Nastavení pořadí řazení znamená, že se běžný význam rovnosti, nerovnosti, menší než a větší než neaplikuje. Pokud zadáte implementaci <xref:System.IComparable>, je nutné obvykle také přepsat <xref:System.Object.Equals%2A> , aby vracely hodnoty, které jsou konzistentní s <xref:System.IComparable.CompareTo%2A>. Pokud přepíšete <xref:System.Object.Equals%2A> a budete kódovat v jazyce, který podporuje přetížení operátoru, měli byste také zadat operátory, které jsou konzistentní <xref:System.Object.Equals%2A>s.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Pokud chcete opravit porušení tohoto pravidla, přepište <xref:System.Object.Equals%2A>. Pokud váš programovací jazyk podporuje přetížení operátora, zadejte následující operátory:

- op_Equality
- op_Inequality
- op_LessThan
- op_GreaterThan

V C#nástroji tokeny, které se používají k reprezentování těchto operátorů, jsou následující:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Je bezpečné potlačit upozornění z pravidla CA1036, pokud je porušení způsobeno chybějícími operátory a váš programovací jazyk nepodporuje přetížení operátoru, stejně jako případ s Visual Basic. Pokud určíte, že implementace operátorů nemá smysl v kontextu vaší aplikace, je také bezpečné potlačit upozornění z tohoto pravidla, je-li aktivováno v operátorech rovnosti jiných než op_Equality. Při přepisování <xref:System.Object.Equals%2A?displayProperty=nameWithType>byste ale měli vždycky přepsat op_Equality a operátor = =.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1036.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (návrh). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="examples"></a>Příklady

Následující kód obsahuje typ, který je správně implementován <xref:System.IComparable>. Komentáře kódu identifikují metody, které odpovídají různým pravidlům, která <xref:System.Object.Equals%2A> se vztahují <xref:System.IComparable> k a rozhraní.

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

Následující kód aplikace testuje chování <xref:System.IComparable> implementace, která se zobrazila dříve.

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Viz také:

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operátory rovnosti](/dotnet/standard/design-guidelines/equality-operators)