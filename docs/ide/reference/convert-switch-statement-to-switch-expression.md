---
title: Převedení příkazu switch na výraz switch
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cc13cffe8352d9fb57f5bb991c3af615eddb2a14
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68740064"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Převedení příkazu switch na výraz switch

Toto refaktoring se vztahuje na:

- C#

**Co:** Převeďte [příkaz switch](/dotnet/csharp/language-reference/keywords/switch) na [výraz přepínače](/dotnet/csharp/whats-new/csharp-8#switch-expressions)jazyka C# 8.0 .

**Kdy:** Chcete převést `switch` příkaz na `switch` výraz a naopak. 

**Proč:** Pokud používáte pouze výrazy, toto refaktoring `switch` umožňuje snadný přechod z tradičních příkazů.

## <a name="how-to"></a>Postupy

1. V souboru projektu [nastavte jazykovou verzi na náhled,](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) protože `switch` výrazy jsou novou funkcí jazyka C# 8.0.
2. Umístěte kurzor `switch` do klíčového slova a stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
3. Vyberte **Převést příkaz switch na výraz**.

   ![Převedení příkazu switch na výraz switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
