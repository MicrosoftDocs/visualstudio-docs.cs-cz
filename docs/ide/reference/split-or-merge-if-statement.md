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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "79093671"
---
# <a name="split-or-merge-if-statements"></a>Dělení a slučování příkazů if

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** **co:** Split nebo Merge příkazy [if](/dotnet/csharp/language-reference/keywords/if-else) .

**Když:** Chcete rozdělit `if` příkaz, který používá `&&` `||` operátory nebo do vnořeného `if` příkazu, nebo sloučit `if` příkaz s vnějším `if` příkazem.

**Proč:** Je to pro styl předvolby.  

## <a name="how-to"></a>Postupy

Pokud chcete rozdělit `if` příkaz:

1. Umístěte kurzor do `if` příkazu pomocí `&&` `||` operátoru OR.

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

    ![Rozdělit if – příkaz](../media/split-if-statement.png)

3. Vyberte **rozdělit do vnořených příkazů if**.

    ![Rozdělit příkaz if dokončen](../media/split-if-statement-complete.png)

Pokud chcete spojit vnitřní `if` příkaz s vnějším `if` příkazem: 

1. Umístěte kurzor do `if` klíčového slova Inner.

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

    ![Sloučit if – příkaz](../media/merge-if-statement.png)

3. Vyberte **Sloučit s vnějším příkazem if**.

    ![Příkaz Merge IF je dokončený.](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)