---
title: 'CA1804: odebrat nepoužívané národní prostředí | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4bd57d76acd0c46e39bb2c01449146715abc0666
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543881"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Odeberte nepoužívané lokální hodnoty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Kategorie|Microsoft. Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Metoda deklaruje místní proměnnou, ale nepoužívá proměnnou, kromě toho, že se může jednat o příjemce příkazu přiřazení. Pro analýzu podle tohoto pravidla musí být testované sestavení sestaveno s ladicími informacemi a přidružený soubor databáze programu (PDB) musí být k dispozici.

## <a name="rule-description"></a>Popis pravidla
 Nepoužívané místní proměnné a zbytečná přiřazení zvětšují velikost sestavení a snižují výkon.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte nebo použijte místní proměnnou. Všimněte si, že kompilátor jazyka C#, který je součástí nástroje, [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] odebere nepoužívané místní proměnné, pokud `optimize` je tato možnost povolená.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla, pokud byla proměnná vyvolána kompilátorem. Je také bezpečné potlačit upozornění z tohoto pravidla nebo zakázat pravidlo, pokud není výkon a údržba kódu primárními aspekty.

## <a name="example"></a>Příklad
 Následující příklad ukazuje několik nepoužitých místních proměnných.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1809: Vyhněte se nadměrným lokálním hodnotám](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Vyhněte se nevolanému privátnímu kódu](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Vyhněte se nevytvořeným instancím interních tříd](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Zkontrolujte nepoužité parametry](../code-quality/ca1801-review-unused-parameters.md)
