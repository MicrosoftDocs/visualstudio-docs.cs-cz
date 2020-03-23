---
title: Možnosti refaktoringu statických lokálních funkcí
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c297457c910c484c05c974c581e89c75e0ad44e5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77144840"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Statické místní funkce refaktoringy a rychlé akce

Tento článek popisuje dva funkce produktivity související se statickými místními funkcemi. Jedním z nich je refaktoring, který dělá místní funkce statické a druhý je rychlá akce, která generuje kód předat proměnné do statické místní funkce.

## <a name="make-local-function-static"></a>Nastavit místní funkci jako statickou

Toto refaktoring se vztahuje na:

- C#

**Co:** Vytvoří místní funkci statickou a předá proměnné definované mimo funkci deklaraci a volání funkce.

**Kdy:** Chcete, aby místní funkce byla statická a aby byly definovány všechny proměnné v rozsahu funkce.

**Proč:** Statické místní funkce zlepšuje čitelnost: s vědomím, že konkrétní kód je izolován usnadňuje pochopení, opětovné čtení a opětovné použití. Statické místní funkce také poskytují obor, aby se zabránilo znečištění třídy statickou funkcí, která je volána pouze v jedné metodě.

### <a name="how-to"></a>Postupy

1. Umístěte stříšku na název místní funkce.

2. Stiskněte **klávesu Ctrl**+**.** (tečka) pro spuštění nabídky **Rychlé akce a Refaktorings.**

   ![Nastavit místní funkci jako statickou](media/make-local-function-static.png)

3. Vyberte **Vytvořit místní funkci "statickou".**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Předat proměnnou explicitně ve statické místní funkci

Tato rychlá akce se vztahuje na:

- C#

**Co:** Předává proměnnou explicitně do místní statické funkce.

**Kdy:** Chcete, aby místní funkce byla statická, ale stále používáte proměnné inicializované mimo ni.

**Proč:** Použití statické místní funkce poskytuje vysvětlení pro čtenáře, protože vědí, že může být deklarována a volána pouze v určitém kontextu programu. Poskytuje flexibilitu definovat proměnné mimo tento kontext, ale stále je možné předat jako argumenty statické místní funkce.

### <a name="how-to"></a>Postupy

1. Umístěte stříšku na proměnnou, kde se používá ve statické místní funkce.

2. Stiskněte **klávesu Ctrl**+**.** (tečka) pro spuštění nabídky **Rychlé akce a Refaktorings.**

   ![Předat proměnnou explicitně ve statické místní funkci](media/pass-variable-explicitly-static-local-function.png)

3. Vyberte **Předat proměnnou explicitně v místní statické funkci**.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)