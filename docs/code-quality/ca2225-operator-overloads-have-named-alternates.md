---
title: 'CA2225: Přetížení operátoru mají pojmenované alternativy'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.openlocfilehash: b4db3074d334fe32f95c4d1b8446921c4e4d47ba
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481777"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Přetížení operátoru mají pojmenované alternativy

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Category|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>Příčina

Bylo zjištěno přetížení operátoru a očekávaná pojmenovaná alternativní metoda nebyla nalezena.

Ve výchozím nastavení toto pravidlo vyhledává pouze externě viditelné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Přetížení operátoru umožňuje použít symboly k vyjádření výpočtů pro typ. Například typ, který přetěžuje symbol plus `+` pro přidání by měl obvykle alternativní člen s názvem `Add`. Pojmenovaný alternativní člen poskytuje přístup ke stejným funkcím jako operátor. Je k dispozici pro vývojáře, kteří programují v jazycích, které nepodporují přetížené operátory.

Toto pravidlo prověřuje:

- Implicitní a explicitní operátory přetypování v typu vyhledají metody s názvem `To<typename>` a `From<typename>`.

- Operátory uvedené v následující tabulce:

|C#|Visual Basic|C++|Alternativní název metody|
|-|-|-|-|
|+ (binární)|+|+ (binární)|Přidat|
|+=|+=|+=|Přidat|
|&|A|&|BitwiseAnd|
|&=|A =|&=|BitwiseAnd|
|&#124;|Nebo|&#124;|Bitový operátor|
|&#124;=|Nebo =|&#124;=|Bitový operátor|
|--|neuvedeno|--|Snížení|
|/|/|/|Rozdělovací|
|/=|/=|/=|Rozdělovací|
|==|=|==|Je rovno|
|^|XOR|^|XOR|
|^=|XOR =|^=|XOR|
|>|>|>|CompareTo nebo Compare|
|>=|>=|>=|CompareTo nebo Compare|
|++|neuvedeno|++|Zvětš|
|!=|<>|!=|Je rovno|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|CompareTo nebo Compare|
|<=|<=|\<=|CompareTo nebo Compare|
|&&|neuvedeno|&&|LogicalAnd|
|&#124;&#124;|neuvedeno|&#124;&#124;|Logický operátor|
|!|neuvedeno|!|LogicalNot|
|%|Mod|%|Střední nebo zbytek|
|%=|neuvedeno|%=|Mod|
|* (binární)|*|*|Hodnotou|
|*=|neuvedeno|*=|Hodnotou|
|~|Not|~|OnesComplement|
|>>|>>|>>|RightShift|
=|neuvedeno|>>=|RightShift|
|-(binární)|-(binární)|-(binární)|Odečten|
|-=|neuvedeno|-=|Odečten|
|true|IsTrue|neuvedeno|True (vlastnost)|
|– (Unární)|neuvedeno|-|Negate|
|+ (Unární)|neuvedeno|+|I|
|false|IsFalse|False|True (vlastnost)|

\* N/A znamená, že operátor nemůže být přetížen ve vybraném jazyce.

> [!NOTE]
> V C#, je-li binární operátor přetížen, je také implicitně přetížen odpovídající operátor přiřazení, je-li nějaký.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, implementujte alternativní metodu pro operátor. Pojmenujte ji pomocí doporučeného alternativního názvu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačit upozornění z tohoto pravidla, Pokud implementujete sdílenou knihovnu. Aplikace mohou ignorovat upozornění od tohoto pravidla.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca2225.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (použití). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Příklad

Následující příklad definuje strukturu, která porušuje toto pravidlo. Chcete-li opravit příklad, přidejte do `Add(int x, int y)` struktury veřejnou metodu.

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Související pravidla

- [CA1046: Nepřetížit operátor přetížení se rovná na odkazových typech](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226 Operátory by měly mít symetrické přetížení](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224: Přepište Equals při přetížení operátoru Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Přepsat GetHashCode při přepsání Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: Operátor přetížení se rovná přepisování ValueType. Equals.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)