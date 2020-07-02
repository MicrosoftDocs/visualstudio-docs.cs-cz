---
title: 'CA2219: nevyvolává výjimky v klauzulích výjimky | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 960c74625a04b209dc9aa251256e994517a3a52f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538525"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Nevyvolávejte výjimky v klauzulích výjimky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Kategorie|Microsoft. Usage|
|Narušující změna|Nerozdělování, přerušení|

## <a name="cause"></a>Příčina
 Výjimka je vyvolána z `finally` klauzule, Filter nebo Fault.

## <a name="rule-description"></a>Popis pravidla
 Je-li v klauzuli Exception vyvolána výjimka, významně se tím zvyšuje obtížnost ladění.

 Pokud je výjimka vyvolána v `finally` klauzuli nebo chyby, nová výjimka skryje aktivní výjimku, pokud je k dispozici. Tím je původní chybě obtížné detekovat a ladit.

 Pokud je v klauzuli filtru vyvolána výjimka, modul runtime tuto výjimku tiše zachytí a způsobí, že se filtr vyhodnotí jako NEPRAVDA. Neexistuje žádný způsob, jak určit rozdíl mezi filtrem vyhodnoceným na hodnotu false a vyvoláním výjimky z filtru. Díky tomu je obtížné detekovat a ladit chyby v logice filtru.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit toto porušení tohoto pravidla, Nevolejte explicitně výjimku z `finally` klauzule, Filter nebo Fault.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění pro toto pravidlo. Neexistují žádné scénáře, za kterých výjimka vyvolaná v klauzuli Exception poskytuje výhodu pro provádění kódu.

## <a name="related-rules"></a>Související pravidla
 [CA1065: Nevyvolávejte výjimky v neočekávaných umístěních](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Viz také
 [Upozornění návrhu](../code-quality/design-warnings.md)
