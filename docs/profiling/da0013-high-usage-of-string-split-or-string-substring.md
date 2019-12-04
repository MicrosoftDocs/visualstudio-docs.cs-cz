---
title: 'DA0013: vysoké použití String. Split nebo String. substring | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d42469ac5236a41eda96af5d1fe896a5ed84a321
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779400"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Vysoké použití String.Split nebo String.Substring

|||
|-|-|
|Id pravidla|DA0013|
|Kategorie|Pokyny k použití .NET Framework|
|Metody profilace|Kontrol|
|Zpráva|Zvažte snížení využití funkcí String. Split a String. substring.|
|Typ pravidla|Upozornění|

## <a name="cause"></a>příčina
 Volání metod System. String. Split nebo System. String. substring představují významnou část dat profilace. Zvažte použití System. String. IndexOf nebo System. String. IndexOfAny, pokud testujete existenci podřetězce v řetězci.

## <a name="rule-description"></a>Popis pravidla
 Metoda Split pracuje na objektu String a vrací nové pole řetězců, které obsahuje podřetězce originálu. Funkce přiděluje paměť pro vrácený objekt Array a přidělí objekt New String pro každý prvek pole, který najde. Podobně metoda substr funguje na objektu String a vrátí nový řetězec, který je ekvivalentní požadovanému podřetězci.

 Pokud je Správa přidělení paměti ve vaší aplikaci kritická, zvažte použití alternativ pro metody String. Split a String. substr. Například můžete použít metodu IndexOf nebo IndexOfAny k vyhledání konkrétního podřetězce v rámci řetězce znaků bez vytvoření nové instance třídy String.

## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění
 Dvakrát klikněte na zprávu v okně **Seznam chyb** , abyste přešli na [zobrazení podrobností o funkcích](../profiling/function-details-view.md) profilu vzorkování. Zkontrolujte volání funkcí a vyhledejte části programu, které usnadňují použití metod System. String. Split nebo System. String. substr. Pokud je to možné, použijte metodu IndexOf nebo IndexOfAny k vyhledání konkrétního podřetězce v rámci řetězce znaků bez vytvoření nové instance třídy String.
