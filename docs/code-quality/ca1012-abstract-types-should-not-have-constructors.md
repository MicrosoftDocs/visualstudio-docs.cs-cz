---
title: 'CA1012: Abstraktní typy by neměly mít konstruktory'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6ba7a88e2167f5e67eb5cefe706bfc2cf1abfccd
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441663"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: Abstraktní typy by neměly mít konstruktory

|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|Kategorie|Microsoft. Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Typ je abstraktní a má konstruktor.

Ve výchozím nastavení toto pravidlo vyhledává pouze externě viditelné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Konstruktory abstraktních typů mohou být volány pouze odvozenými typy. Protože veřejné konstruktory vytvoří instance typu a nemůžete vytvořit instance abstraktního typu, abstraktní typ, který má veřejný konstruktor, je nesprávně navržený.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, buď zajistěte, aby byl konstruktor chráněn, nebo Nedeklarujte typ jako abstraktní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo. Abstraktní typ má veřejný konstruktor.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1012.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (návrh). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Příklad

Následující fragment kódu obsahuje abstraktní typ, který toto pravidlo porušuje.

[!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
[!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]

Následující fragment kódu opravuje předchozí porušení změnou dostupnosti konstruktoru z `public` na `protected`.

[!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
[!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]
