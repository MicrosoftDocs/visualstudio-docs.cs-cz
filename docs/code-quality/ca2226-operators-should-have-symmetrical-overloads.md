---
title: 'CA2226: Operátory by měly mít symetrická přetížení'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d9e486d4193645335189c475fdd3ca220374d96
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231439"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Operátory by měly mít symetrická přetížení

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Typ implementuje operátor rovnosti nebo nerovnosti a neimplementuje opačný operátor.

Ve výchozím nastavení toto pravidlo vyhledává pouze externě viditelné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Neexistují žádné okolnosti, kdy je rovnost nebo nerovnost pro instance typu a opačný operátor není definován. Typy obvykle implementují operátor nerovnosti vrácením hodnoty negace operátoru rovnosti.

C# Kompilátor vydá chybu pro porušení tohoto pravidla.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, implementujte operátory rovnosti a nerovnosti nebo odeberte tu, která je k dispozici.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo. Pokud tak učiníte, váš typ nebude fungovat způsobem, který je konzistentní s rozhraním .NET.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca2226.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (použití). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Související pravidla

- [CA1046: Nepřetížit operátor přetížení se rovná na odkazových typech](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225: Přetížení operátoru mají pojmenované alternativy.](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2224: Přepište Equals při přetížení operátoru Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Přepsat GetHashCode při přepsání Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: Operátor přetížení se rovná přepisování ValueType. Equals.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)