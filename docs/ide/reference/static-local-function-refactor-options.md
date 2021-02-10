---
title: Možnosti refaktoringu statických lokálních funkcí
description: Naučte se, jak pomocí nabídky rychlé akce a refaktoringu vytvořit místní funkci jako statickou a předat proměnné definované mimo funkci do deklarace a volání funkce.
ms.custom: SEO-VS-2020
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 050ce5e90d9141892ff65602ca560d0add83da5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967186"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Refaktoring statických místních funkcí a rychlé akce

Tento článek popisuje dvě funkce produktivity související se statickými místními funkcemi. Jedním z nich je refaktoring, který vytváří místní funkci staticky a druhá je rychlá akce, která generuje kód pro předání proměnných do statické místní funkce.

## <a name="make-local-function-static"></a>Nastavit místní funkci jako statickou

Tento refaktoring platí pro:

- C#

**Co:** Převede místní funkci na statickou a předá proměnné definované mimo funkci do deklarace a volání funkce.

**Když:** Chcete, aby byla místní funkce statická a aby byly definovány všechny proměnné v rozsahu funkce.

**Proč:** Statická lokální funkce vylepšuje čitelnost: víte, že konkrétní kód je izolovaný, usnadňuje pochopení, opětovné čtení a opakované použití. Statické místní funkce také poskytují rozsah, který brání znečištění třídy statickou funkcí, která je volána pouze v jediné metodě.

### <a name="how-to"></a>Postupy

1. Umístěte blikající kurzor na název místní funkce.

2. Stiskněte klávesu **CTRL** + **.** (tečka) pro aktivaci nabídky **rychlé akce a refaktoringu** .

   ![Nastavit místní funkci jako statickou](media/make-local-function-static.png)

3. Vyberte možnost **nastavit místní funkci static.**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Předat proměnnou explicitně do statické místní funkce

Tato rychlá akce platí pro:

- C#

**Co:** Předává proměnnou explicitně do místní statické funkce.

**Když:** Chcete, aby lokální funkce byla statická, ale nadále používá proměnné inicializované mimo ni.

**Proč:** Použití statických lokálních funkcí poskytuje uživatelům objasnění, protože ví, že je možné deklarovat a volat pouze v určitém kontextu programu. Poskytuje flexibilitu pro definování proměnných mimo tento kontext, ale je možné je dál předat jako argumenty statické místní funkce.

### <a name="how-to"></a>Postupy

1. Umístěte blikající kurzor na proměnnou, kde se používá ve statické místní funkci.

2. Stiskněte klávesu **CTRL** + **.** (tečka) pro aktivaci nabídky **rychlé akce a refaktoringu** .

   ![Předat proměnnou explicitně ve statické lokální funkci](media/pass-variable-explicitly-static-local-function.png)

3. Vyberte **Předat proměnnou explicitně v místní statické funkci**.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)