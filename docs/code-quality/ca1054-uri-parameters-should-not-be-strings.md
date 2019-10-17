---
title: 'CA1054: Parametry identifikátoru URI by neměly být řetězce'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 79ab405e6019dd93fdb9ffa89b5274f6f3d679e8
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446574"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: Parametry identifikátoru URI by neměly být řetězce

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Kategorie|Microsoft. Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Typ deklaruje metodu s parametrem řetězce, jehož název obsahuje "URI", "URI", "urn", "urn", "URL" nebo "URL" a typ nedeklaruje odpovídající přetížení, které přijímá parametr <xref:System.Uri?displayProperty=fullName>.

Ve výchozím nastavení toto pravidlo vyhledává pouze externě viditelné typy, ale je možné jej [nakonfigurovat](#configurability).

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo rozdělí název parametru na tokeny založené na konvenci ve stylu CamelCase (velká a malá písmena) a zkontroluje, jestli každý token odpovídá "URI", "URI", "urn", "urn", "URL" nebo "URL". Pokud existuje shoda, pravidlo předpokládá, že parametr představuje identifikátor URI (Uniform Resource Identifier). Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. Pokud metoda přijímá řetězcovou reprezentaci identifikátoru URI, měla by být poskytnuta odpovídající přetížená instance, která přebírá instanci třídy <xref:System.Uri>, která poskytuje tyto služby bezpečným a bezpečným způsobem.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, změňte parametr na typ <xref:System.Uri>; Toto je zásadní změna. Případně zadejte přetížení metody, která přijímá parametr <xref:System.Uri>; Tato změna je nevýznamná.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pokud parametr nepředstavuje identifikátor URI, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="configurability"></a>Konfigurovatelnost

Pokud toto pravidlo spouštíte z [analyzátorů FxCop](install-fxcop-analyzers.md) (a ne pomocí starší verze analýzy), můžete nakonfigurovat, které části základu kódu mají spustit toto pravidlo, na základě jejich přístupnosti. Například chcete-li určit, že pravidlo by mělo běžet pouze proti neveřejnému povrchu rozhraní API, přidejte do souboru. editorconfig v projektu následující dvojici klíč-hodnota:

```ini
dotnet_code_quality.ca1054.api_surface = private, internal
```

Tuto možnost můžete nakonfigurovat jenom pro toto pravidlo, pro všechna pravidla nebo pro všechna pravidla v této kategorii (návrh). Další informace najdete v tématu [Konfigurace analyzátorů FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje typ, `ErrorProne`, který porušuje toto pravidlo, a typ `SaferWay`, který splňuje pravidlo.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Související pravidla

- [CA1056: Vlastnosti identifikátoru URI by neměly být řetězce](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1055: Návratové hodnoty identifikátoru URI by neměly být řetězce](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
- [CA2234: Předejte objekty System.Uri namísto řetězců](../code-quality/ca2234.md)
- [CA1057: Řetězcové přetížení identifikátoru URI volá přetížení System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
