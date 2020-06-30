---
title: 'CA1505: Vyhněte se neudržovatelnému kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f2f731b1ac0d87b59c7690d0cf57ade3570ed5f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547820"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Vyhněte se neudržovatelnému kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Kategorie|Microsoft. udržovatelnost|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Typ nebo metoda má nízkou hodnotu indexu udržovatelnosti.

## <a name="rule-description"></a>Popis pravidla
 Index udržovatelnosti se počítá pomocí následujících metrik: řádků kódu, programu Volume a cyklomatická složitosti. Objem programu je míra obtížnosti porozumění typu nebo metodě, která je založena na počtu operátorů a operandů v kódu. Složitosti cyklomatická je míra strukturální složitosti typu nebo metody. Můžete získat další informace o metrikách kódu při [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Nízký index udržovatelnosti indikuje, že typ nebo metoda je pravděpodobně obtížné udržovat a že by bylo dobrým kandidátem na přepracování.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li toto porušení opravit, změňte návrh typu nebo metodu a pokuste se ji rozdělit na menší a více zaměřené typy nebo metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Vylučte toto upozornění, pokud je typ nebo metoda stále považována za udržovatelnou bez ohledu na její velkou velikost nebo když typ nebo metodu nelze rozdělit.

## <a name="see-also"></a>Viz také
 [Upozornění na udržovatelnost](../code-quality/maintainability-warnings.md) při [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
