---
title: 'CA1720: Identifikátory by neměly obsahovat názvy typů'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2677c2ef5342b795bb684f3ab06bc7cf5195cf7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233899"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Identifikátory by neměly obsahovat názvy typů

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Kategorie|Microsoft.Naming|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Název parametru v členu obsahuje název datového typu.

-nebo-

Název členu obsahuje název datového typu specifický pro jazyk.

Ve výchozím nastavení toto pravidlo vypadá pouze u externě viditelných členů, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Názvy parametrů a členů jsou lépe použity ke sdělení jejich významu, než aby bylo možné popsat jejich typ, který je třeba poskytnout pomocí vývojářských nástrojů. V případě názvů členů, pokud je třeba použít název datového typu, použijte název nezávislá na jazyce, nikoli na konkrétní jazyk. Například namísto názvu C# `int`typu použijte název datového typu nezávislý na jazyku,. `Int32`

Všechny diskrétní tokeny v názvu parametru nebo členu jsou zkontrolovány proti následujícím jazykově specifickým názvům datových typů při nerozlišování velkých a malých písmen:

- Bool
- WChar
- Int8
- UInt8
- Krátké
- UShort
- Int
- UInt
- Integer
- UInteger –
- Dlouhé
- ULong
- Celé
- Podpisy
- Float
- Float32
- Float64

Kromě toho názvy parametrů jsou také zkontrolovány proti následujícím jazykově nezávislým názvům datových typů při nerozlišování velkých a malých písmen:

- Objekt
- Objektu
- Boolean
- Char
- String
- SByte
- Byte
- UByte
- Int16
- UInt16
- Int32
- UInt32
- Int64
- UInt64
- IntPtr
- střed
- Ukazatele
- UInptr
- UPtr
- UPointer
- Single
- Double
- Desetinné číslo
- Guid

## <a name="how-to-fix-violations"></a>Jak opravit porušení

**Je-li aktivováno proti parametru:**

Nahraďte identifikátor datového typu v názvu parametru výrazem, který lépe popisuje svůj význam nebo obecnější výraz, jako je hodnota.

**Při vyvolání proti členovi:**

Nahraďte identifikátor datového typu specifický pro jazyk v názvu člena termínem, který lépe popisuje svůj význam, ekvivalent nezávislého jazyka nebo obecnější výraz, jako je hodnota.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Příležitostné použití parametrů založených na typu a názvů členů může být vhodné. Pro nový vývoj ale nedochází k žádným známým scénářům, kdy byste měli potlačit upozornění od tohoto pravidla. U knihoven, které byly dřív dodány, možná budete muset potlačit upozornění od tohoto pravidla.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1720.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (pojmenování). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Související pravidla

- [CA1709: Identifikátory by se měly použita správně.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identifikátory by se měly lišit o více než malých písmenech](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719: Názvy parametrů by neměly odpovídat názvům členů](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)