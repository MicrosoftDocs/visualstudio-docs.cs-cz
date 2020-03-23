---
title: 'DA0010: Drahé GetHashCode | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9ce982c7a98fd12749c66c89e47bd895d2fb6a5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777683"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Náročná metoda GetHashCode

|||
|-|-|
|Id pravidla|DA0010|
|Kategorie|Použití rozhraní .NET Framework|
|Metody profilování|Vzorkování<br /><br /> Paměť .NET|
|Zpráva|GetHashCode funkce by měly být levné a nepřidělovat žádnou paměť. Pokud je to možné, snižte složitost funkce kódu hash.|
|Typ zprávy|Upozornění|

## <a name="cause"></a>Příčina
 Volání GetHashCode metoda typu jsou významnou část data profilování nebo metoda přiděluje paměť.

## <a name="rule-description"></a>Popis pravidla
 Hashing je technika pro rychlé umístění určité položky ve velké kolekci. Vzhledem k tomu, že tabulky hash mohou být velké a musí podporovat velmi vysoké míry přístupu, tabulky hash by měly být efektivní. Důsledkem tohoto požadavku je, že metody GetHashCode v rozhraní .NET Framework by neměly přidělovat paměť. Přidělení paměti zvyšuje zatížení systému uvolňování paměti a zpřístupňuje metodu k potenciálním zpožděním, pokud je nutné spustit uvolňování paměti v důsledku požadavku na přidělení.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Snižte složitost metody.
