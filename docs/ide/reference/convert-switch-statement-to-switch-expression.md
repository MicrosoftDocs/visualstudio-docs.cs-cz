---
title: Převedení příkazu switch na výraz switch
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring převést příkaz switch na výraz přepínače C# 8,0.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 56a1b20854cdd2c1821490bb4972d67bbe912056
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919671"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Převedení příkazu switch na výraz switch

Tento refaktoring platí pro:

- C#

**Co:** Převod [příkazu switch](/dotnet/csharp/language-reference/keywords/switch) na [výraz přepínače](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8,0.

**Když:** Chcete převést `switch` příkaz na `switch` výraz a naopak. 

**Proč:** Pokud používáte pouze výrazy, tento refaktoring umožňuje snadnou přechod z tradičních `switch` příkazů.

## <a name="how-to"></a>Postupy

1. V souboru projektu [nastavte jazykovou verzi Preview](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) , protože `switch` výrazy představují novou funkci C# 8,0.
2. Umístěte kurzor do `switch` klíčového slova a stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Vyberte **převést příkaz switch na výraz**.

   ![Převedení příkazu switch na výraz switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
