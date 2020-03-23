---
title: 'DA0013: Vysoké využití String.Split nebo String.Substring | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779400"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Vysoké použití String.Split nebo String.Substring

|||
|-|-|
|Id pravidla|DA0013 řekl:|
|Kategorie|Pokyny k použití rozhraní .NET Framework|
|Metody profilování|Vzorkování|
|Zpráva|Zvažte snížení použití String.Split a String.Substring funkce.|
|Typ pravidla|Upozornění|

## <a name="cause"></a>Příčina
 Volání metod System.String.Split nebo System.String.Substring jsou významnou částí dat profilování. Zvažte použití System.String.IndexOf nebo System.String.IndexOfAny, pokud testujete existenci podřetězce v řetězci.

## <a name="rule-description"></a>Popis pravidla
 Split Metoda pracuje na String objekt a vrátí nové pole Strings, který obsahuje podřetězce originálu. Funkce přiděluje paměť vráceného objektu pole a přiděluje nový objekt String pro každý prvek pole, který najde. Podobně Substr metoda pracuje na String objekt a vrátí nový String, který je ekvivalentní požadované podřetězec.

 Pokud správa přidělení paměti je důležité ve vaší aplikaci, zvažte použití alternativy string.Split a String.Substr metody. Například můžete použít Metodu IndexOf nebo IndexOfAny k vyhledání určitého podřetězce v rámci znaku String bez vytvoření nové instance třídy String.

## <a name="how-to-investigate-a-warning"></a>Jak prošetřit varování
 Poklepáním na zprávu v okně **Seznam chyb** přejděte do [zobrazení podrobností funkce](../profiling/function-details-view.md) dat profilů vzorkování. Zkontrolujte volající funkce najít části programu, které nejčastěji používají metody System.String.Split nebo System.String.Substr. Pokud je to možné, použijte Metodu IndexOf nebo IndexOfAny k vyhledání určitého podřetězce v rámci znakového řetězce bez vytvoření nové instance třídy String.
