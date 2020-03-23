---
title: Dělení a slučování příkazů if
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a3b42f83faacda6be34b282150cf4fb4c0f379f1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093671"
---
# <a name="split-or-merge-if-statements"></a>Dělení a slučování příkazů if

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co: Co:** **What:** Rozdělit nebo sloučit, [pokud](/dotnet/csharp/language-reference/keywords/if-else) příkazy.

**Kdy:** Chcete `if` rozdělit příkaz, který `&&` používá `||` operátory nebo `if` do vnořeného příkazu, `if` nebo sloučit příkaz s vnějším `if` příkazem.

**Proč:** Je to otázka preference stylu.  

## <a name="how-to"></a>Postupy

Pokud chcete rozdělit `if` příkaz:

1. Umístěte kurzor `if` do příkazu operátorem `&&` nebo. `||`

2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**

    ![Rozdělit, pokud prohlášení](../media/split-if-statement.png)

3. Vyberte **Rozdělit do vnořených if příkazů**.

    ![Rozdělit, pokud je výkaz dokončen](../media/split-if-statement-complete.png)

Pokud chcete sloučit `if` vnitřní příkaz `if` s vnějším příkazem: 

1. Umístěte kurzor do `if` vnitřního klíčového slova.

2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**

    ![Sloučit, pokud prohlášení](../media/merge-if-statement.png)

3. Vyberte **Sloučit s vnějším příkazem if**.

    ![Sloučit, pokud je příkaz dokončen](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)