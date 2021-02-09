---
title: Dělení a slučování příkazů if
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring rozdělit nebo sloučit příkazy if.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 30ec77382cf404bc74f2ff5fed71cff360b9f28e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893383"
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