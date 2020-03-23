---
title: Převod příkazu if na příkaz switch nebo výraz switch
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 93ad96809c77d5644b13e6221a41f0b182fb448f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094158"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Převod příkazu if na příkaz switch nebo výraz switch

Toto refaktoring se vztahuje na:

- C#

**Co:** Převeďte příkaz if na [příkaz switch](/dotnet/csharp/language-reference/keywords/switch) nebo na [výraz přepínače](/dotnet/csharp/whats-new/csharp-8#switch-expressions)Jazyka C# 8.0 .

**Kdy:** Chcete převést `if` příkaz na `switch` příkaz `switch` nebo výraz a naopak. 

**Proč:** Pokud používáte `if` příkaz, toto refaktoring umožňuje `switch` snadný `switch` přechod na příkazy nebo výrazy.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor `if` do klíčového slova.
2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
3. Vyberte z následujících dvou možností: 

    Vyberte **Příkaz Převést na 'switch'**.

   ![Převést příkaz if na příkaz switch](media/convert-if-to-switch-statement.png) 

    Vyberte **Převést na výraz přepnout**. 

    ![Převést příkaz if pro přepnutí výrazu](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
