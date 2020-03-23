---
title: Ladění kódu R
description: Visual Studio poskytuje úplné ladění prostředí pro R, včetně zarážky, připojit, zásobník volání a kontrolu proměnných.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 5efa0a32f51e1f5060474a0d277bfca7f1e7d548
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189252"
---
# <a name="debug-r-in-visual-studio"></a>Ladění R v sadě Visual Studio

Nástroje R pro visual studio (RTVS) integruje s úplné ladění prostředí Visual Studio (viz [ladění v sadě Visual Studio](../debugger/debugger-feature-tour.md). Tato podpora zahrnuje zarážky, připojení ke spuštěným procesům, kontrolu a sledování proměnných a kontrolu zásobníku volání. Tento článek pak zkoumá ty aspekty ladění, které jsou jedinečné pro R a RTVS.

Spuštění ladicího programu pro spouštěcí soubor R v projektu R je stejné jako u jiných typů projektů: **použijte** > ladění**ladění start**, klíč **F5** nebo **zdrojový spouštěcí soubor** na panelu nástrojů ladění:

![Tlačítko start ladicího programu pro R](media/debugger-start-button.png)

Chcete-li změnit spouštěcí soubor, klepněte pravým tlačítkem myši na soubor v Průzkumníku řešení a vyberte **příkaz Nastavit jako skript spuštění r**.

Ve všech případech spuštění ladicího programu "zdroje" soubor v interaktivním okně, což znamená, že jeho načtení a spuštění tam, jak je znázorněno ve výstupu interaktivního okna:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Všimněte `rtvs::debug_source` si, že funkce se používá ke zdroji skriptu. Tato funkce je vyžadována, protože RTVS potřebuje upravit kód v rámci přípravy na ladění. Při použití libovolného příkazu zdroje RTVS a je připojen `rtvs::debug_source`ladicí program, Visual Studio automaticky používá .

Ladicí program můžete také ručně připojit z interaktivního okna přímo pomocí příkazu R **Tools** > **Session** > **Attach Debugger, příkazu** **Debug** > **Attach to R Interactive** nebo **příkazu Připojit ladicí program** na panelu nástrojů interaktivního okna. Jakmile tak stanete, je vaší odpovědností zdroj souborů, které chcete ladit. Pokud chcete ručně zdroj souborů, ujistěte se, že `rtvs::debug_source` `source` používáte a ne pravidelný příkaz v R.

Toto připojení mezi ladicím programem a interaktivním oknem usnadňuje provádění funkcí, jako je volání (a ladění) funkce s různými hodnotami parametrů. Předpokládejme například, že máte ve zdrojovém souboru následující funkci (což znamená, že byla načtena do relace):

```R
add <- function(x, y) {
    return(x + y)
}
```

Potom nastavíte zarážku na `return` příkaz. Nyní v interaktivním okně `add(4,5)` zadání zastaví ladicí program na zarážky.

## <a name="environment-browser-in-the-interactive-window"></a>Prohlížeč prostředí v interaktivním okně

Když jste v ladicím programu zastaveni, zastavíte se také na výzvu Prohlížeče prostředí v [interaktivním okně](interactive-repl-for-r-in-visual-studio.md). Výzva se `Browse[n]>` zobrazí jako kde n je číslo.

Prohlížeč prostředí podporuje řadu speciálních příkazů:

| Příkaz | Popis |
| --- | --- |
| n | další: spustí další příkaz v souboru kódu (stejně jako krok přes). |
| s | krok do: spustí další příkaz v souboru kódu, krokování do oboru funkce, pokud další příkaz je volání funkce. |
| f | finish: spustí zbývající část aktuálního rozsahu funkce a vrátí volajícímu (stejně jako krok ven). |
| c, cont | pokračovat: spustí program na další zarážku. |
| Q | ukončí: ukončí relaci ladění. |
| where | zobrazit zásobník: zobrazí zásobník volání v interaktivním okně. |
| Nápověda | zobrazit nápovědu: zobrazí dostupné příkazy v interaktivním okně. |
| &lt;Výraz&gt; | vyhodnocovat výraz v *expr*. |

![Prohlížeč prostředí v interaktivním okně](media/debugger-environment-browser.png)
