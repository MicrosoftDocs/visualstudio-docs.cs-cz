---
title: 'CA1804: Odeberte nepoužívané lokální hodnoty'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0a83d0afffc50c7697fad98c4dc49e31770d63d4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233754"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Odeberte nepoužívané lokální hodnoty

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Kategorie|Microsoft. Performance|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Metoda deklaruje místní proměnnou, ale nepoužívá proměnnou, kromě toho, že se může jednat o příjemce příkazu přiřazení. Pro analýzu podle tohoto pravidla musí být testované sestavení sestaveno s ladicími informacemi a přidružený soubor databáze programu (PDB) musí být k dispozici.

## <a name="rule-description"></a>Popis pravidla
Nepoužívané místní proměnné a zbytečná přiřazení zvětšují velikost sestavení a snižují výkon.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, odeberte nebo použijte místní proměnnou.

> [!NOTE]
> C# Kompilátor odebere nepoužívané místní proměnné, pokud `optimize` je povolena možnost.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačí upozornění z tohoto pravidla, pokud byla proměnná vyvolána kompilátorem. Je také bezpečné potlačit upozornění z tohoto pravidla nebo zakázat pravidlo, pokud není výkon a údržba kódu primárními aspekty.

## <a name="example"></a>Příklad
Následující příklad ukazuje několik nepoužitých místních proměnných.

[!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
[!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA1809: Vyhněte se nadměrným lokálním hodnotám](../code-quality/ca1809-avoid-excessive-locals.md)

[CA1811: Vyhněte se nevolanému privátnímu kódu](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Vyhněte se nevytváření instancí vnitřních tříd](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Zkontrolovat nepoužité parametry](../code-quality/ca1801-review-unused-parameters.md)