---
title: Zjednodušit výraz LINQ
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 04485d6ce67c822fd0620bd63f3557851db6dbb9
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2020
ms.locfileid: "88251301"
---
# <a name="simplify-linq-expression"></a>Zjednodušit výraz LINQ

Tento refaktoring platí pro:

- C#

**Co:** Refaktorické instance `SomeEnumerableType.Where(<LambdaExpression>).Single()` do `SomeEnumerable.Single(<LambdaExpression>)` pro pro `Enumerable.Single()` a jsou následující vyčíslitelné metody: `SingleOrDefault()` , `Last()` , `LastOrDefault()` , `Any()` , `Count()` , `First()` a `FirstOrDefault()` .

**Když:**  Všechny instance, kde metoda volá `Single()` , `SingleOrDefault()` a tak dále, nemá žádné argumenty a předchází `Where()` výraz. Vstup `Where()` výrazu nelze sestavit jako strom výrazu.

**Proč:** Odebrání nepotřebného volání výčtového pro `.Where()` metodu zvyšuje výkon a čitelnost.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do `SomeEnumerableType.Where(<LambdaExpression>).Single()` instance v sadě Visual Studio.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Vybrat **zjednodušený výraz LINQ**

   ![Převést typeof na nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
