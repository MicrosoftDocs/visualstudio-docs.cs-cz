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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531914"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Pro výrazy lambda použít text výrazu nebo text bloku

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje Refaktorovat výraz lambda, aby používal tělo výrazu nebo tělo bloku.

**Když:** Preferujete výrazy lambda pro použití těla výrazu nebo těla bloku.

**Proč:** Výrazy lambda lze Refaktorovat, aby se zlepšila čitelnost v závislosti na vašich uživatelských preferencích.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refaktoring těla výrazu lambda nebo bloku

1. Umístěte kurzor na pravé straně operátoru lambda.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

  ![Použít lambda výraz/tělo bloku](media/block-body-lambda.png)

3. Vyberte možnost **použít text bloku pro výrazy lambda** nebo **použijte tělo výrazu pro výrazy lambda**.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře na platformě .NET](../csharp-developer-productivity.md)