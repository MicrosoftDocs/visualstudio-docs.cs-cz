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
ms.openlocfilehash: 296eb6407e3ce63b0eb28ff86c215c12ec724ce9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545311"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testujte prázdné řetězce pomocí délky řetězce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategorie|Microsoft. Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Řetězec je porovnán s prázdným řetězcem pomocí <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Popis pravidla
 Porovnávání řetězců pomocí této <xref:System.String.Length%2A?displayProperty=fullName> vlastnosti nebo <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> metody je výrazně rychlejší než použití <xref:System.Object.Equals%2A> . Důvodem je to <xref:System.Object.Equals%2A> , že provádí podstatně více instrukcí jazyka MSIL, než buď, <xref:System.String.IsNullOrEmpty%2A> nebo počet instrukcí, které byly provedeny pro načtení <xref:System.String.Length%2A> hodnoty vlastnosti a jejich porovnání na nulu.

 Je třeba si uvědomit, že <xref:System.Object.Equals%2A> a <xref:System.String.Length%2A> = 0 se chová jinak u řetězců s hodnotou null. Pokud se pokusíte získat hodnotu <xref:System.String.Length%2A> vlastnosti u řetězce s hodnotou null, modul CLR (Common Language Runtime) vyvolá výjimku <xref:System.NullReferenceException?displayProperty=fullName> . Pokud provedete porovnání mezi řetězcem s hodnotou null a prázdným řetězcem, modul CLR (Common Language Runtime) nevyvolá výjimku. porovnání se vrátí `false` . Testování pro hodnotu null nijak významně neovlivňuje relativní výkon těchto dvou přístupů. Při cílení [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] použijte <xref:System.String.IsNullOrEmpty%2A> metodu. V opačném případě použijte <xref:System.String.Length%2A> porovnávání = =, kdykoli je to možné.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte porovnání tak, aby se použila <xref:System.String.Length%2A> vlastnost a test pro řetězec s hodnotou null. Pokud cílíte [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , použijte <xref:System.String.IsNullOrEmpty%2A> metodu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud se výkon nejedná o problém, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklad znázorňuje různé techniky, které se používají k vyhledání prázdného řetězce.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
