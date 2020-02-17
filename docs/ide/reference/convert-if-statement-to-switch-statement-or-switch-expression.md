---
title: Příkaz převést if na Switch nebo switch Expression
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cb0c06fe0493f973ea9cf0a566ffda45a49eeeff
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77280780"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Příkaz převést if na Switch nebo switch Expression

Tento refaktoring platí pro:

- C#

**Co:** Převést příkaz if na [příkaz switch](/dotnet/csharp/language-reference/keywords/switch) nebo na C# [výraz přepínače](/dotnet/csharp/whats-new/csharp-8#switch-expressions)8,0.

**Když:** Chcete převést příkaz `if` na příkaz `switch` nebo výraz `switch` a naopak. 

**Proč:** Pokud používáte příkaz `if`, tento refaktoring umožňuje snadnou přechod na příkazy `switch` nebo `switch` výrazy.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do klíčového slova `if`.
2. Stiskněte klávesu **Ctrl**+ **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Vyberte **převést na příkaz switch**.

   ![Příkaz převést if na Switch nebo switch Expression](media/convert-if-statement-to-switch-statement-or-switch-expression.png) 

## <a name="see-also"></a>Viz také

- [Refaktoring](../refactoring-in-visual-studio.md)
