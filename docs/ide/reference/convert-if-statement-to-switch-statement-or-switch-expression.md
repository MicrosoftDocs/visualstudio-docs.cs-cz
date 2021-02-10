---
title: Příkaz převést if na switch – příkaz nebo výraz
description: Naučte se, jak pomocí nabídky rychlé akce a refaktoring převést příkaz if na příkaz switch nebo výraz přepínače C# 8,0.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0d857338eb1c9b5bb66ccb89e20e6f892944d608
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936826"
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

    Vyberte **převést na příkaz switch**.

   ![Příkaz převést if na Switch](media/convert-if-to-switch-statement.png)

    Vyberte **převést na výraz Switch**.

    ![Převést příkaz if na výraz Switch](media/convert-if-to-switch-expression.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
