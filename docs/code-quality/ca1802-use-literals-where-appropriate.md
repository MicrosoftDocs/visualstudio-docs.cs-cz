---
title: 'CA1802: Použijte literály, kde je to vhodné'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 13cfc8b090d289173975b0ef2ee55562955de0c8
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548741"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Použijte literály, kde je to vhodné

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategorie|Microsoft.Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Pole je deklarován `static` a `readonly` (`Shared` a `ReadOnly` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) a je inicializován s hodnotou, kterou lze vypočítat v době kompilace.

## <a name="rule-description"></a>Popis pravidla
 Hodnota `static``readonly` pole je vypočítán za běhu při volání statického konstruktoru pro deklarujícího typu. Pokud `static``readonly` pole je inicializováno při deklaraci a statický konstruktor není explicitně deklarované, kompilátor vydává statický konstruktor k inicializaci pole.

 Hodnota `const` pole je vypočítána v době kompilace a uložená v metadatech, což zvyšuje výkon modulu runtime srovnání s `static``readonly` pole.

 Protože hodnotu přiřazenou cílovému poli je nelze vypočítat v době kompilace, změňte deklaraci do `const` pole tak, aby hodnota byla vypočítána v době kompilace místo za běhu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nahraďte `static` a `readonly` modifikátory `const` modifikátor.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla nebo zakázat pravidlo, pokud výkon není žádný problém.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, `UseReadOnly`, který porušuje pravidla a typ, `UseConstant`, vyhovující pravidlo.

 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]