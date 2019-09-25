---
title: 'CA1802: Použijte literály, kde je to vhodné'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 435eb5a9fd7e41a69c873df4c728e42551734a37
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253369"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Použijte literály, kde je to vhodné

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategorie|Microsoft. Performance|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Pole je deklarováno `static` a `readonly` (`Shared` a `ReadOnly` v Visual Basic) a je inicializováno s hodnotou, která je COMPUTE v době kompilace.

Ve výchozím nastavení toto pravidlo vypadá pouze v externě viditelných polích, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Hodnota `static readonly` pole je vypočítána v době běhu při volání statického konstruktoru pro deklarující typ. Pokud je `static readonly` pole inicializováno, když je deklarováno a statický konstruktor není deklarován explicitně, kompilátor vygeneruje statický konstruktor pro inicializaci pole.

Hodnota `const` pole je vypočítána v době kompilace a uložena v metadatech, což zvyšuje výkon za běhu při porovnání `static readonly` s polem.

Vzhledem k tomu, že hodnota přiřazená cílovému poli je COMPUTE v době kompilace, změňte deklaraci `const` na pole tak, aby se hodnota vypočítala v době kompilace místo v době běhu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, nahraďte `static` modifikátory a `readonly` `const` modifikátorem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Z tohoto pravidla je bezpečné potlačit upozornění nebo pravidlo zakázat, pokud výkon nebudete mít obavy.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1802.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (výkon). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje typ, `UseReadOnly`, který porušuje pravidlo a `UseConstant`typ,, který splňuje pravidlo.

[!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
[!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]