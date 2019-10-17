---
title: 'CA1715: Identifikátory by měly mít správnou předponu'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 875e0b4052cdc7287b264899620d4e083ac6b153
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443870"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Identifikátory by měly mít správnou předponu

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Kategorie|Microsoft. pojmenování|
|Zásadní změna|Přerušení – při vyvolání na rozhraní.<br /><br /> Nerozdělitelné – při vyvolání v parametrech obecného typu.|

## <a name="cause"></a>příčina

Název rozhraní nezačíná velkým písmenem "I".

-nebo-

Název [parametru obecného typu](/dotnet/csharp/programming-guide/generics/generic-type-parameters) u typu nebo metody nezačíná velkým písmenem.

Ve výchozím nastavení toto pravidlo vyhledává pouze externě viditelná rozhraní, typy a metody, ale to je [konfigurovatelné](#configurability).

## <a name="rule-description"></a>Popis pravidla

Podle konvence názvy určitých programovacích prvků začínají specifickou předponou.

Názvy rozhraní by měly začínat velkým písmenem "I" následovaným jiným velkým písmenem. Toto pravidlo oznamuje porušení názvů rozhraní, například ' MyInterface ' a ' IsolatedInterface '.

Názvy parametrů obecného typu by měly začínat velkým písmenem t a volitelně může následovat jiné velké písmeno. Toto pravidlo oznamuje porušení názvů parametrů obecného typu, jako jsou například V a typ.

Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zmenší výuková křivka, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části kódu toto pravidlo analyzuje. Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

### <a name="single-character-type-parameters"></a>Parametry typu s jedním znakem

Můžete nakonfigurovat, jestli chcete z tohoto pravidla vyloučit parametry typu s jedním znakem. Například chcete-li určit, že toto pravidlo *by nemělo* analyzovat parametry typu s jedním znakem, přidejte jednu z následujících párů klíč-hodnota do souboru. editorconfig v projektu:

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA1715.exclude_single_letter_type_parameters = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.allow_single_letter_type_parameters = true
```

> [!NOTE]
> Toto pravidlo se nikdy neaktivuje pro parametr typu s názvem `T`, například `Collection<T>`.

### <a name="api-surface"></a>Plocha rozhraní API

Na základě jejich dostupnosti můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1715.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (pojmenování).

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Přejmenujte identifikátor tak, aby byl správně opraven.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="interface-naming-example"></a>Příklad pojmenování rozhraní

Následující fragment kódu ukazuje nesprávně pojmenované rozhraní:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

Následující fragment kódu opravuje předchozí porušení prefixem rozhraní s ' I ':

[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="type-parameter-naming-example"></a>Příklad pojmenovávání parametrů typu

Následující fragment kódu ukazuje nesprávně pojmenovaný parametr obecného typu:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

Následující fragment kódu opravuje předchozí porušení předponou parametru obecného typu s t:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Související pravidla

- [CA1722: Identifikátory by neměly mít nesprávnou předponu](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)
