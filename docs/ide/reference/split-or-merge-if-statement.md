---
title: Dělení a slučování příkazů if
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring rozdělit nebo sloučit příkazy if.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f72c6c2ed1cfdd1c8ea4471976d6a4980dfe422f
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479924"
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