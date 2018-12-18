---
title: Nepodporované scénáře ladění v Návrháři pracovních postupů
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2b876df1b7d997f3999c119d02abd593a88e6d5e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973067"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Nepodporované scénáře ladění v Návrháři pracovních postupů

Návrháře pracovních postupů v rozhraní .NET Framework 4 přidali mnoho nových funkcí, ale stále existují některé ladění scénáře, které nejsou podporovány.

Tady jsou nepodporované návrháře pracovních postupů ladění scénáře:

-   Provádění nemůže pokračovat, po kód bylo upraveno.

-   Provádění nemůže pokračovat z libovolného bodu v pracovním postupu (nastavit další).

-   Provádění nelze pokračovat, dokud kurzor je dosaženo (Spustit ke kurzoru).

-   Návrhář postupu provádění nelze použít k ladění vytvořených v kódu bez použití návrháře pracovních postupů.

-   Pracovní postupy vytvořené v dřívějších verzích Windows Workflow Foundation (WF) nemůžete ladit v Návrháři rozhraní .NET Framework 4.

-   Zarážky nelze definovat na propojení mezi aktivitami nebo <xref:System.Activities.Statements.Flowchart> uzlů.

-   Během ladění není k dispozici do schránky.

-   Zarážky nezachovají, při aktivity se kopírování a vložení.

-   V okně zásobník volání nelze nastavit zarážky pracovního postupu.

-   Při vytváření zarážky v návrháři **řádku** a **znak** nastavení v **nové zarážek** dialogové okno se nepoužívají.

-   Breakpoint – okno nebo v místní nabídce nepodporuje následující sloupce nebo možnosti pro ladění pracovního postupu:

    -   Podmínka

    -   Počet volání

    -   Při průchodu

    -   Funkce

    -   Data

    -   Proces

    -   Přejděte na zpětný překlad