---
title: Ladění kódu R
description: Sada Visual Studio poskytuje úplné ladicí prostředí pro R, včetně zarážek, připojení, zásobníku volání a kontrol proměnných.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: e3696cac00c726cffb76f29a1da2c503a15af2bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885817"
---
# <a name="debug-r-in-visual-studio"></a>Ladění R v aplikaci Visual Studio

Nástroje R pro Visual Studio (RTVS) se integruje s plným prostředím ladění sady Visual Studio (viz [ladění v aplikaci Visual Studio](../debugger/debugger-feature-tour.md). Tato podpora zahrnuje zarážky, připojení ke spuštěným procesům, kontrolu a sledování proměnných a kontrolu zásobníku volání. Tento článek popisuje tyto aspekty ladění, které jsou jedinečné pro R a RTVS.

Spuštění ladicího programu pro spouštěcí soubor r v projektu r je stejné jako u jiných typů projektů **: pomocí ladění**  >  **Spustit ladění**, klávesy **F5** nebo **zdrojového spouštěcího souboru** na panelu nástrojů ladění:

![Tlačítko pro spuštění ladicího programu pro R](media/debugger-start-button.png)

Chcete-li změnit spouštěcí soubor, klikněte pravým tlačítkem myši na soubor v Průzkumník řešení a vyberte možnost **nastavit jako spouštěcí skript jazyka R**.

Ve všech případech spustí ladicí program "sources" soubor v interaktivním okně, což znamená, že ho načte a spustí, jak je znázorněno ve výstupu interaktivního okna:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Všimněte si, že `rtvs::debug_source` funkce se používá ke zdroji skriptu. Tato funkce je povinná, protože RTVS potřebuje upravit kód v přípravě pro ladění. Při použití libovolného RTVS zdroje a připojeného ladicího programu Visual Studio automaticky používá `rtvs::debug_source` .

Ladicí program můžete také ručně připojit z interaktivního okna přímo pomocí příkazu jazyka **R**  >    >  **připojit ladicí program** k příkazu, příkaz **ladit**  >  **připojit k interaktivní R** nebo příkaz **připojit ladicí program** na panelu nástrojů interaktivního okna. Až to uděláte, je vaše zodpovědnost za zdroj souborů, které chcete ladit. Pokud chcete soubory vytvořit ručně, ujistěte se, že používáte `rtvs::debug_source` a ne běžný `source` příkaz v jazyce R.

Toto připojení mezi ladicím programem a interaktivním oknem usnadňuje provádění akcí, jako je volání (a ladění) funkce s různými hodnotami parametrů. Předpokládejme například, že máte následující funkci ve zdrojovém souboru (to znamená, že je načten do relace):

```R
add <- function(x, y) {
    return(x + y)
}
```

Potom nastavíte zarážku na `return` příkaz. V interaktivním okně teď, když vstoupí na `add(4,5)` zarážku, zastavuje ladicí program.

## <a name="environment-browser-in-the-interactive-window"></a>Prohlížeč prostředí v interaktivním okně

Když jste v ladicím programu zastavili, zastaví se také v okně [interaktivní okno](interactive-repl-for-r-in-visual-studio.md)s výzvou v prohlížeči prostředí. Zobrazí se výzva, `Browse[n]>` kde n je číslo.

Prohlížeč prostředí podporuje řadu speciálních příkazů:

| Příkaz | Popis |
| --- | --- |
| n | Další: spustí další příkaz v souboru kódu (totéž jako krok over). |
| s | Krok do: spustí další příkaz v souboru kódu, krokování do oboru funkce, pokud je dalším příkazem volání funkce. |
| f | dokončit: spustí zbytek aktuálního rozsahu funkcí a vrátí volajícímu (stejné jako krok ven). |
| c, pokračování | pokračovat: spustí program na další zarážku. |
| Q | konec: ukončí relaci ladění. |
| kde: | Zobrazit zásobník: zobrazí zásobník volání v interaktivním okně. |
| Nápověda | Zobrazit Help: zobrazí dostupné příkazy v interaktivním okně. |
| &lt;výrazu&gt; | vyhodnotit výraz *ve výrazu*. |

![Prohlížeč prostředí v interaktivním okně](media/debugger-environment-browser.png)
