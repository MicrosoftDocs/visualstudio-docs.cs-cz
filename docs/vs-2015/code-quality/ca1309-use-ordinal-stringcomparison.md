---
title: 'CA1309: použijte ordinální StringComparison | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: be60d2a1dcb769a0b7a8574984de3d288bf57af4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538876"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Použijte řadový StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Operace porovnání řetězců, která je nelingvistická, nenastavuje <xref:System.StringComparison> parametr buď na **ordinální** , nebo na **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Popis pravidla
 Mnohé řetězcové operace, nejdůležitější <xref:System.String.Compare%2A?displayProperty=fullName> metody a <xref:System.String.Equals%2A?displayProperty=fullName> , nyní poskytují přetížení, které přijímá <xref:System.StringComparison?displayProperty=fullName> hodnotu výčtu jako parametr.

 Když zadáte buď **StringComparison. Ordinal** nebo **StringComparison. OrdinalIgnoreCase**, porovnávání řetězců bude nelingvistická. To znamená, že funkce, které jsou specifické pro přirozený jazyk, se při rozhodování o porovnávání ignorují. To znamená, že rozhodnutí jsou založena na jednoduchých porovnáních bajtů a ignorují tabulky malých a velkých písmen nebo rovnocenných tabulek, které jsou parametrizované podle jazykové verze. V důsledku toho explicitním nastavením parametru buď na **StringComparison. Ordinal** nebo **StringComparison. OrdinalIgnoreCase**, váš kód často získává rychlost, zvyšuje správnost a je spolehlivější.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte metodu porovnání řetězců na přetížení, které přijímá <xref:System.StringComparison?displayProperty=fullName> výčet jako parametr, a zadejte buď **pořadové číslo** nebo **OrdinalIgnoreCase**. Například změňte `String.Compare(str1, str2)` na `String.Compare(str1, str2, StringComparison.Ordinal)` .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, je-li knihovna nebo aplikace určena pro omezené místní cílovou skupinu nebo v případě, že by měla být použita sémantika aktuální jazykové verze.

## <a name="see-also"></a>Viz také
 [Upozornění globalizace](../code-quality/globalization-warnings.md) [CA1307: zadejte StringComparison.](../code-quality/ca1307-specify-stringcomparison.md)
