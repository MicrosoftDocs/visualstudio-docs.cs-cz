---
title: 'CA1505: Vyhněte se neudržovatelnému kódu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3ba027ef2e663870d0af50bc6d2154133f7980c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234547"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Vyhněte se neudržovatelnému kódu

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Kategorie|Microsoft. udržovatelnost|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Typ nebo metoda má nízkou hodnotu indexu udržovatelnosti.

## <a name="rule-description"></a>Popis pravidla

Index udržovatelnosti se počítá pomocí následujících metrik: řádků kódu, programu Volume a cyklomatická složitosti. Objem programu je míra obtížnosti porozumění typu nebo metodě, která je založena na počtu operátorů a operandů v kódu. Složitosti cyklomatická je míra strukturální složitosti typu nebo metody. Další informace o metrikách kódu najdete v [části míry složitosti a udržovatelnosti spravovaného kódu](../code-quality/code-metrics-values.md).

Nízký index udržovatelnosti indikuje, že typ nebo metoda je pravděpodobně obtížné udržovat a že by bylo dobrým kandidátem na přepracování.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li toto porušení opravit, změňte návrh typu nebo metodu a pokuste se ji rozdělit na menší a více zaměřené typy nebo metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Toto upozornění můžete potlačit, pokud typ nebo metodu nelze rozdělit nebo je považována za udržovatelnou bez ohledu na její velkou velikost.

## <a name="see-also"></a>Viz také:

- [Upozornění udržovatelnosti](../code-quality/maintainability-warnings.md)
- [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/code-metrics-values.md)