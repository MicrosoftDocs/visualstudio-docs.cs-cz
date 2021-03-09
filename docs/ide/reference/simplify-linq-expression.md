---
title: Zjednodušení výrazu LINQ
description: Tento refaktoring slouží k odebrání nepotřebných volání výčtu metody WHERE.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 20a3524d786b1f03fc3e221d1b257892d9439a0b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466164"
---
# <a name="simplify-linq-expression"></a>Zjednodušení výrazu LINQ

Tento refaktoring platí pro:

- C#

**Co:** Refaktorické instance `SomeEnumerableType.Where(<LambdaExpression>).Single()` do `SomeEnumerable.Single(<LambdaExpression>)` pro pro `Enumerable.Single()` a jsou následující vyčíslitelné metody: `SingleOrDefault()` , `Last()` , `LastOrDefault()` , `Any()` , `Count()` , `First()` a `FirstOrDefault()` .

**Když:**  Všechny instance, kde metoda volá `Single()` , `SingleOrDefault()` a tak dále, nemá žádné argumenty a předchází `Where()` výraz. Vstup `Where()` výrazu nelze sestavit jako strom výrazu.

**Proč:** Odebrání nepotřebného volání výčtového pro `.Where()` metodu zvyšuje výkon a čitelnost.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do `SomeEnumerableType.Where(<LambdaExpression>).Single()` instance v sadě Visual Studio.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Vybrat **zjednodušený výraz LINQ**

   ![Převedení typeof na nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
