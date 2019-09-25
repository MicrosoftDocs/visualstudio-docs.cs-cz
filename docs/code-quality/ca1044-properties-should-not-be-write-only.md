---
title: 'CA1044: Vlastnosti by neměly být pouze pro zápis'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0fb424627d88ede6c0677b8c45de4aab487ae498
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235819"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Vlastnosti by neměly být pouze pro zápis

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Vlastnost má přístupový objekt set, ale nikoli přistupující objekt get.

Ve výchozím nastavení toto pravidlo vyhledává pouze veřejné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Přístupové objekty get poskytují přístup pro čtení k vlastnostem a přístup k sadě poskytují přístup pro zápis. Ačkoli je přijatelné a často nezbytné použít vlastnost jen pro čtení, směrnice návrhu zakazují použití vlastností jen pro zápis. Důvodem je skutečnost, že uživatel může nastavit hodnotu a potom zabránit uživateli v zobrazení hodnoty neposkytuje žádné zabezpečení. Taktéž bez přístupu pro čtení není možné zobrazit stav sdílených objektů, což omezuje jejich užitečnost.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, přidejte do vlastnosti přistupující objekt get. Případně, pokud je nezbytné chování vlastnosti jen pro zápis, zvažte převedení této vlastnosti na metodu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Doporučuje se, abyste z tohoto pravidla potlačili upozornění.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1044.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (návrh). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Příklad

V následujícím příkladu `BadClassWithWriteOnlyProperty` je typ s vlastností pouze pro zápis. `GoodClassWithReadWriteProperty`obsahuje opravený kód.

[!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
[!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]