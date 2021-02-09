---
title: DA0013 – vysoké použití String. Split nebo String. substring | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5d5ec92544809a83825451494b01fd62a0868ee4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916796"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Vysoký výskyt použití String.Split nebo String.Substring

|Položka|Hodnota|
|-|-|
|ID pravidla|DA0013|
|Kategorie|Pokyny k použití .NET Framework|
|Metody profilace|Vzorkování|
|Zpráva|Zvažte snížení využití funkcí String. Split a String. substring.|
|Typ pravidla|Upozornění|

## <a name="cause"></a>Příčina
 Volání metod System. String. Split nebo System. String. substring představují významnou část dat profilace. Zvažte použití System. String. IndexOf nebo System. String. IndexOfAny, pokud testujete existenci podřetězce v řetězci.

## <a name="rule-description"></a>Popis pravidla
 Metoda Split pracuje na objektu String a vrací nové pole řetězců, které obsahuje podřetězce originálu. Funkce přiděluje paměť pro vrácený objekt Array a přidělí objekt New String pro každý prvek pole, který najde. Podobně metoda substr funguje na objektu String a vrátí nový řetězec, který je ekvivalentní požadovanému podřetězci.

 Pokud je Správa přidělení paměti ve vaší aplikaci kritická, zvažte použití alternativ pro metody String. Split a String. substr. Například můžete použít metodu IndexOf nebo IndexOfAny k vyhledání konkrétního podřetězce v rámci řetězce znaků bez vytvoření nové instance třídy String.

## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění
 Dvakrát klikněte na zprávu v okně **Seznam chyb** , abyste přešli na [zobrazení podrobností o funkcích](../profiling/function-details-view.md) profilu vzorkování. Zkontrolujte volání funkcí a vyhledejte části programu, které usnadňují použití metod System. String. Split nebo System. String. substr. Pokud je to možné, použijte metodu IndexOf nebo IndexOfAny k vyhledání konkrétního podřetězce v rámci řetězce znaků bez vytvoření nové instance třídy String.
