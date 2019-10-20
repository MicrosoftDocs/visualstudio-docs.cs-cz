---
title: 'CA1820: testujte prázdné řetězce pomocí délky řetězce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6711dac907de2777cf892b20269fec7e99d3bd6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657494"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testujte prázdné řetězce pomocí délky řetězce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategorie|Microsoft. Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Řetězec je porovnán s prázdným řetězcem pomocí <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 Porovnávání řetězců pomocí vlastnosti <xref:System.String.Length%2A?displayProperty=fullName> nebo metody <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> je výrazně rychlejší než použití <xref:System.Object.Equals%2A>. Důvodem je to, že <xref:System.Object.Equals%2A> provádí výrazně více instrukcí jazyka MSIL, než buď <xref:System.String.IsNullOrEmpty%2A>, nebo počet instrukcí, které byly provedeny pro načtení hodnoty vlastnosti <xref:System.String.Length%2A> a jejich porovnání na nulu.

 Počítejte s tím, že <xref:System.Object.Equals%2A> a <xref:System.String.Length%2A> = = 0 se chovají jinak pro řetězce s hodnotou null. Pokud se pokusíte získat hodnotu vlastnosti <xref:System.String.Length%2A> u řetězce s hodnotou null, modul CLR (Common Language Runtime) vyvolá <xref:System.NullReferenceException?displayProperty=fullName>. Pokud provedete porovnání mezi řetězcem s hodnotou null a prázdným řetězcem, modul CLR (Common Language Runtime) nevyvolá výjimku. porovnávání vrátí `false`. Testování pro hodnotu null nijak významně neovlivňuje relativní výkon těchto dvou přístupů. Při cílení [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] použijte metodu <xref:System.String.IsNullOrEmpty%2A>. V opačném případě použijte <xref:System.String.Length%2A> = = porovnání, kdykoli je to možné.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte porovnání na použití vlastnosti <xref:System.String.Length%2A> a testování řetězce s hodnotou null. Pokud cílíte [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], použijte metodu <xref:System.String.IsNullOrEmpty%2A>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud se výkon nejedná o problém, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklad znázorňuje různé techniky, které se používají k vyhledání prázdného řetězce.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
