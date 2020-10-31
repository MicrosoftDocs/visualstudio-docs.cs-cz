---
title: Příkaz převést if na switch – příkaz nebo výraz
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8e093325ff4a4e6a9f8a2623e7e42f69bb6fa62f
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102529"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Převod příkazu if na příkaz switch nebo výraz switch

Tento refaktoring platí pro:

- C#

**Co:** Převést příkaz if na [příkaz switch](/dotnet/csharp/language-reference/keywords/switch) nebo na [výraz přepínače](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8,0.

**Když:** Chcete převést `if` příkaz na `switch` příkaz nebo `switch` výraz a naopak.

**Proč:** Pokud používáte `if` příkaz, tento refaktoring umožňuje snadnou přechod na `switch` příkazy nebo `switch` výrazy.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do `if` klíčového slova.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Vyberte z následujících dvou možností:

    Vyberte **převést na příkaz switch** .

   ![Příkaz převést if na Switch](media/convert-if-to-switch-statement.png)

    Vyberte **převést na výraz Switch** .

    ![Převést příkaz if na výraz Switch](media/convert-if-to-switch-expression.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
