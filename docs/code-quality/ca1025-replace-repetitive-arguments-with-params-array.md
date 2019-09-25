---
title: 'CA1025: Nahraďte opakované argumenty polem parametrů'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f65d64dd4e881c41b17cd7cb9dc072a6fe800766
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236137"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Nahraďte opakované argumenty polem parametrů

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Veřejná nebo chráněná metoda ve veřejném typu má více než tři parametry a jejich poslední tři parametry jsou stejného typu.

## <a name="rule-description"></a>Popis pravidla
Použijte pole parametrů namísto opakovaných argumentů, pokud je přesný počet argumentů neznámý a argumenty proměnných jsou stejného typu nebo mohou být předány jako stejný typ. Například <xref:System.Console.WriteLine%2A> metoda poskytuje přetížení pro obecné účely, které používá pole parametrů k přijetí libovolného <xref:System.Object> počtu argumentů.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, nahraďte opakované argumenty polem parametrů.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Z tohoto pravidla je vždycky bezpečné potlačit upozornění. Tento návrh ale může způsobit problémy s použitelností.

## <a name="example"></a>Příklad
Následující příklad ukazuje typ, který je v rozporu s tímto pravidlem.

[!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]