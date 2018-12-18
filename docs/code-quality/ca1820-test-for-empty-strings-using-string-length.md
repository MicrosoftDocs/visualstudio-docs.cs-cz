---
title: 'CA1820: Testujte prázdné řetězce pomocí délky řetězce'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c6c25f48ecd628d3d6c32bb235180f91e750cdf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847771"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testujte prázdné řetězce pomocí délky řetězce

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategorie|Microsoft.Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Řetězec je ve srovnání s prázdný řetězec s použitím <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 Porovnání řetězců pomocí <xref:System.String.Length%2A?displayProperty=fullName> vlastnost nebo <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> metoda je mnohem rychlejší než použití <xref:System.Object.Equals%2A>. Důvodem je, že <xref:System.Object.Equals%2A> provádí výrazně více instrukcí jazyka MSIL než buď <xref:System.String.IsNullOrEmpty%2A> nebo počet instrukcí provést k načtení <xref:System.String.Length%2A> vlastnost hodnotu a porovnat ho na hodnotu nula.

 Byste měli vědět, který <xref:System.Object.Equals%2A> a <xref:System.String.Length%2A> == 0 chovat jinak pro řetězce s hodnotou null. Pokud se pokusíte získat hodnotu <xref:System.String.Length%2A> vlastnost na řetězec s hodnotou null, modul common language runtime vyvolá <xref:System.NullReferenceException?displayProperty=fullName>. Pokud provádíte srovnání řetězec s hodnotou null a prázdné řetězce, modul common language runtime nevyvolá výjimku. Porovnání vrátí `false`. Testování pro null neovlivní výrazně relativní výkon tyto dvě metody. Při cílení na [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], použijte <xref:System.String.IsNullOrEmpty%2A> metody. Jinak použijte <xref:System.String.Length%2A> == porovnání, kdykoli je to možné.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte porovnání pro použití <xref:System.String.Length%2A> vlastnost a testování pro řetězec s hodnotou null. Pokud je zaměřen na [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], použijte <xref:System.String.IsNullOrEmpty%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, pokud výkon není problém.

## <a name="example"></a>Příklad
 Následující příklad ukazuje různé techniky, které se používají k vyhledání prázdný řetězec.

 [!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]