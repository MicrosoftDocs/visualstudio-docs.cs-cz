---
title: Zjednodušení výrazu LINQ
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 006fc0fe84b11573ece98019a4446d83de52d62c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957553"
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
