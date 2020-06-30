---
title: 'CA1802: Použijte literály, kde je to vhodné | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dc8019c97d3c561000f1c6a8d083bee6253face3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544401"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Použijte literály, kde je to vhodné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategorie|Microsoft. Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Pole je deklarováno `static` a `readonly` ( `Shared` a `ReadOnly` v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) a je inicializováno s hodnotou, která je COMPUTE v době kompilace.

## <a name="rule-description"></a>Popis pravidla
 Hodnota `static``readonly` pole je vypočítána za běhu při volání statického konstruktoru pro deklarující typ. Pokud je `static``readonly` pole inicializováno, když je deklarováno a statický konstruktor není deklarován explicitně, kompilátor vygeneruje statický konstruktor pro inicializaci pole.

 Hodnota `const` pole je vypočítána v době kompilace a uložena v metadatech, což zvyšuje výkon modulu runtime při porovnání s `static``readonly` polem.

 Vzhledem k tomu, že hodnota přiřazená cílovému poli je COMPUTE v době kompilace, změňte deklaraci na `const` pole tak, aby se hodnota vypočítala v době kompilace namísto za běhu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nahraďte modifikátory `static` a `readonly` `const` modifikátorem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění nebo pravidlo zakázat, pokud výkon nebudete mít obavy.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, `UseReadOnly` , který porušuje pravidlo a typ, `UseConstant` , který splňuje pravidlo.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
