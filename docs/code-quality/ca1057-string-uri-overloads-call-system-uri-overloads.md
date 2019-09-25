---
title: 'CA1057: Přetížení řetězce identifikátoru URI volají přetížení System.Uri'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e6bd77a49690979ea7ab3c4619fdd578a80bb77c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235513"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Přetížení řetězce identifikátoru URI volají přetížení System.Uri

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Typ deklaruje přetížení metod, které se liší pouze nahrazením řetězcového parametru <xref:System.Uri?displayProperty=fullName> parametrem a přetížení, které přijímá řetězcový parametr, nevolá přetížení, které <xref:System.Uri> přijímá parametr.

## <a name="rule-description"></a>Popis pravidla
Vzhledem k tomu, že přetížení se liší pouze řetězcem <xref:System.Uri> nebo parametrem, předpokládá se, že řetězec představuje identifikátor URI (Uniform Resource Identifier). Řetězcová reprezentace identifikátoru URI je náchylná k chybám analýzy a kódování a může vést k ohrožení bezpečnosti. <xref:System.Uri> Třída poskytuje tyto služby bezpečným a bezpečným způsobem. Chcete-li těžit výhody <xref:System.Uri> třídy, přetížení řetězce by mělo <xref:System.Uri> volat přetížení pomocí řetězcového argumentu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Znovu Implementujte metodu, která používá řetězcovou reprezentaci identifikátoru URI, aby vytvořila instanci <xref:System.Uri> třídy pomocí řetězcového argumentu a poté <xref:System.Uri> předá objekt přetížení, které má <xref:System.Uri> parametr.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Pokud parametr řetězce nepředstavuje identifikátor URI, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
Následující příklad ukazuje správně implementované přetížení řetězce.

[!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
[!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
[!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA2234: Předejte objekty System. URI místo řetězců.](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

[CA1056: Vlastnosti identifikátoru URI by neměly být řetězce](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1054: Parametry identifikátoru URI by neměly být řetězce](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

[CA1055: Návratové hodnoty identifikátoru URI by neměly být řetězce](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)