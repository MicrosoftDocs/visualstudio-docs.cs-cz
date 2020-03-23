---
title: Použití výrazu lambda nebo textu bloku
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5c46506e81e5334efea9060e957269e92e9d49cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531914"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Použití těla výrazu nebo těla bloku pro výrazy lambda

Toto refaktoring se vztahuje na:

- C#

**Co:** Umožňuje refaktorovat výraz lambda tak, aby používal tělo výrazu nebo tělo bloku.

**Kdy:** Upřednostňujete lambda výrazy použít tělo výrazu nebo tělo bloku.

**Proč:** Lambda výrazy mohou být refaktorovány ke zlepšení čitelnosti podle vašich uživatelských preferencí.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Lambda výraz tělo nebo blok tělo refaktoring

1. Umístěte kurzor na pravé straně provozovatele lambda.
2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**

  ![Použití těla výrazu/bloku lambda](media/block-body-lambda.png)

3. Vyberte **Použít tělo bloku pro výrazy lambda** nebo Použít tělo **výrazu pro výrazy lambda**.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře rozhraní .NET](../csharp-developer-productivity.md)