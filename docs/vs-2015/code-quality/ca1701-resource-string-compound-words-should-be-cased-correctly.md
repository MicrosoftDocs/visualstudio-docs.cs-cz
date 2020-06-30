---
title: 'CA1701: složená slova řetězce prostředků by se měla použita správně | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7c1c3b0fd6cf3a25d5db9e3039d4dc5d8364a18e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544102"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Malá a velká písmena složených slov řetězců prostředků by měla být použita správně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Řetězec prostředku obsahuje složené slovo, které zřejmě není správně použita.

## <a name="rule-description"></a>Popis pravidla
 Každé slovo v řetězci prostředku je rozděleno na tokeny, které jsou založeny na velikosti písmen. Každá kombinace dvou sousedících tokenů je zkontrolována knihovnou kontroly pravopisu společnosti Microsoft. Je-li kombinace rozpoznána, způsobí slovo porušení pravidla. Příklady složených slov, která způsobují porušení, jsou "kontrolní součet" a "MultiPart", které by měly být použita jako "kontrolní součet" a "multipart". Kvůli předchozímu běžnému využití jsou do pravidla integrována několik výjimek a několik jednoduchých slov je označeno jako "panel nástrojů" a "filename", které by se měly použita jako dvě odlišná slova. V tomto příkladu by byl označený příznak "panel nástrojů" a "FileName".

 Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zmenší výuková křivka, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Změňte slovo tak, aby se použita správně.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění, pokud slovník pravopisu rozpozná obě části složeného slova a záměr je použít dvě slova.

 Pro kontrolu pravopisu můžete také přidat složená slova do vlastního slovníku. Slova ve vlastním slovníku nezpůsobují porušení. Další informace najdete v tématu [Postup: přizpůsobení slovníku analýzy kódu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Související pravidla
 [CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Viz také
 [Pokyny pro pojmenování](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) [konvencí psaní velkých písmen](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
