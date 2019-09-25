---
title: 'CA1820: Testujte prázdné řetězce pomocí délky řetězce'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b197cacc764f1f5472d3eb074ac89199db508408
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233420"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testujte prázdné řetězce pomocí délky řetězce

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategorie|Microsoft. Performance|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Řetězec je porovnán s prázdným řetězcem pomocí <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="rule-description"></a>Popis pravidla

Porovnávání řetězců pomocí <xref:System.String.Length%2A?displayProperty=nameWithType> vlastnosti <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> nebo metody je rychlejší než použití <xref:System.Object.Equals%2A>. Důvodem je to <xref:System.Object.Equals%2A> , že provádí podstatně více instrukcí <xref:System.String.IsNullOrEmpty%2A> jazyka MSIL, než buď, nebo počet instrukcí, které byly <xref:System.String.Length%2A> provedeny pro načtení hodnoty vlastnosti a jejich porovnání na nulu.

Pro řetězce null a <xref:System.Object.Equals%2A> `<string>.Length == 0` chovají se jinak. Pokud se pokusíte získat hodnotu <xref:System.String.Length%2A> vlastnosti u řetězce s hodnotou null, modul CLR (Common Language Runtime) <xref:System.NullReferenceException?displayProperty=fullName>vyvolá výjimku. Pokud provedete porovnání mezi řetězcem s hodnotou null a prázdným řetězcem, modul CLR (Common Language Runtime) nevyvolá `false`výjimku a vrátí. Testování pro hodnotu null nijak významně neovlivňuje relativní výkon těchto dvou přístupů. Při cílení na .NET Framework 2,0 nebo novější použijte <xref:System.String.IsNullOrEmpty%2A> metodu. V opačném případě <xref:System.String.Length%2A> použijte porovnávání = = 0, kdykoli je to možné.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, změňte porovnání na použití <xref:System.String.IsNullOrEmpty%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pokud výkon není problémem, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad

Následující příklad znázorňuje různé techniky, které se používají k vyhledání prázdného řetězce.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]