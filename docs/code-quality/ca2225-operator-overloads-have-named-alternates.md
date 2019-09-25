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
ms.workload:
- multiple
ms.openlocfilehash: c027bc4581919f814b4d93eacba77248349fdf8b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231089"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Přetížení operátoru mají pojmenované alternativy

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Bylo zjištěno přetížení operátoru a očekávaná pojmenovaná alternativní metoda nebyla nalezena.

Ve výchozím nastavení toto pravidlo vyhledává pouze externě viditelné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Přetížení operátoru umožňuje použít symboly k vyjádření výpočtů pro typ. Například typ, který přetěžuje symbol plus (+) pro sčítání, by měl obvykle alternativní člen s názvem add. Pojmenovaný alternativní člen poskytuje přístup ke stejným funkcím jako operátor a je k dispozici pro vývojáře, kteří programují v jazycích, které nepodporují přetížené operátory.

Toto pravidlo prověřuje operátory uvedené v následující tabulce.

|C#|Visual Basic|C++|Alternativní název|
|---------|------------------|-----------|--------------------|
|+ (binární)|+|+ (binární)|Přidejte|
|+=|+=|+=|Přidejte|
|&|A|&|BitwiseAnd|
|&=|A =|&=|BitwiseAnd|
|&#124;|Nebo|&#124;|Bitový operátor|
|&#124;=|Nebo =|&#124;=|Bitový operátor|
|--|Není k dispozici|--|Snížení|
|/|/|/|Rozdělovací|
|/=|/=|/=|Rozdělovací|
|==|=|==|Je rovno|
|^|XOR|^|XOR|
|^=|XOR =|^=|XOR|
|>|>|>|Porovnat|
|>=|>=|>=|Porovnat|
|++|Není k dispozici|++|Zvětš|
|<>|!=|Je rovno|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|Porovnat|
|<=|<=|\<=|Porovnat|
|&&|Není k dispozici|&&|LogicalAnd|
|&#124;&#124;|Není k dispozici|&#124;&#124;|Logický operátor|
|!|Není k dispozici|!|LogicalNot|
|%|Mod|%|Střední nebo zbytek|
|%=|Není k dispozici|%=|Mod|
|* (binární)|*|*|Hodnotou|
|*=|Není k dispozici|*=|Hodnotou|
|~|Not|~|OnesComplement|
|>>|>>|>>|RightShift|
=|Není k dispozici|>>=|RightShift|
|-(binární)|-(binární)|-(binární)|Odečten|
|-=|Není k dispozici|-=|Odečten|
|true|IsTrue|Není k dispozici|True (vlastnost)|
|– (Unární)|Není k dispozici|-|Negate|
|+ (Unární)|Není k dispozici|+|I|
|false|IsFalse|False|True (vlastnost)|

N/A = = nemůže být přetížený ve vybraném jazyce.

Pravidlo také kontroluje implicitní a explicitní operátory přetypování v typu (`SomeType`) kontrolou metod pojmenovaných `ToSomeType` a `FromSomeType`.

V C#, je-li binární operátor přetížen, je také implicitně přetížen odpovídající operátor přiřazení, je-li nějaký.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, implementujte alternativní metodu pro operátor; pojmenujte ji pomocí doporučeného alternativního názvu.

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