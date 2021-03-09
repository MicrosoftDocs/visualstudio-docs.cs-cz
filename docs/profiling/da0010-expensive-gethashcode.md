---
title: DA0010 – nákladný GetHashCode | Microsoft Docs
description: Volání metody GetHashCode typu jsou významným podílem dat profilování nebo metoda přiděluje paměť.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5d44c998cabd3611e2ed393be0ad7df20e1ac49c
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469921"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Náročná funkce GetHashCode

|Položka|Hodnota|
|-|-|
|ID pravidla|DA0010|
|Kategorie|Využití .NET Framework|
|Metody profilace|Vzorkování<br /><br /> Paměť .NET|
|Zpráva|Funkce GetHashCode by měly být levné a nesmí přidělit žádnou paměť. Pokud je to možné, snižte složitost funkce kódu hash.|
|Typ zprávy|Upozornění|

## <a name="cause"></a>Příčina
 Volání metody GetHashCode typu jsou významným podílem dat profilování nebo metoda přiděluje paměť.

## <a name="rule-description"></a>Popis pravidla
 Hashing je technika, jak rychle vyhledat konkrétní položku ve velké kolekci. Vzhledem k tomu, že tabulky hash můžou být velké a musí podporovat velmi vysoké míry přístupu, měly by být efektivní tabulky hash. Nemnožení tohoto požadavku je, že metody GetHashCode v .NET Framework by neměly přidělit paměť. Přidělování paměti zvyšuje zatížení systému uvolňování paměti a zpřístupňuje metodu potenciálním zpožděním, pokud bude nutné spustit uvolňování paměti v důsledku žádosti o přidělení.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Snižte složitost metody.
