---
title: 'CA1702: složená slova by se měla použita správně | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f9dc15cec4012d2b63eb5f21c25bd709961c95c8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544076"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Malá a velká písmena složených slov by měla být použita správně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio naleznete v tématu [CA1702: složená slova by měla být použita správně](/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly).

|Položka|Hodnota|
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Přerušení – při vyvolání na sestavení.<br /><br /> Bez přerušení – při vyvolání v parametrech typu.|

## <a name="cause"></a>Příčina
 Název identifikátoru obsahuje více slov a nejméně jedno z těchto slov se jeví jako složené slovo, které není správně použita.

## <a name="rule-description"></a>Popis pravidla
 Název identifikátoru je rozdělen na slova, která jsou založena na velikosti písmen. Každá souvislá kombinace dvou slov je kontrolována knihovnou kontroly pravopisu společnosti Microsoft. Pokud je rozpoznáno, identifikátor vytvoří porušení pravidla. Příklady složených slov, která způsobují porušení, jsou "kontrolní součet" a "MultiPart", které by měly být použita jako "kontrolní součet" a "multipart". Kvůli předchozímu běžnému využití jsou do pravidla integrována několik výjimek a několik jednoduchých slov je označeno jako "panel nástrojů" a "filename", které by se měly použita jako dvě odlišná slova (v tomto případě "panel nástrojů" a "FileName").

 Zásady vytváření názvů poskytují běžný vzhled pro knihovny, které cílí na modul CLR (Common Language Runtime). Tím se zmenší výuková křivka, která je požadována pro nové knihovny softwaru, a zvyšuje důvěru zákazníků, že knihovna byla vyvinuta někým, kdo má zkušenosti s vývojem spravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Změňte název tak, aby byl použita správně.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění, pokud slovník pravopisu rozpozná obě části složeného slova a záměr je použít dvě slova.

## <a name="related-rules"></a>Související pravidla
 [CA1701: Malá a velká písmena složených slov řetězců prostředků by měla být použita správně](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Viz také
 [Zásady vytváření názvů](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) – [konvence psaní velkých písmen](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
