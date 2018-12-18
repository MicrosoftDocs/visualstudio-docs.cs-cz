---
title: R Tools for Visual Studio
description: Nástroje R pro Visual Studio (RTVS) je zdarma, open source rozšíření, která poskytuje mnoho funkcí jazyka, včetně IntelliSense, ladění a vzdálené pracovní prostory.
ms.date: 11/13/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 05ffd249be3d7734979f3a131a3a10423b76cb9d
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35667012"
---
# <a name="work-with-r-in-visual-studio"></a>Práce s R v sadě Visual Studio

R je vysoce rozšiřitelný jazyk a prostředí pro statistické výpočty a grafiku. Je distribuován zdarma v rámci licence GNU General Public, požívá silná podpora komunity a je známá schopnost vytvářet kvalitní publikace vykreslení včetně symboly matematické vzorce. Další informace o jazyce R na [r-project.org](https://www.r-project.org/about.html) a [Úvod do jazyka R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

Nástroje R pro Visual Studio (RTVS) je bezplatná, [open source](https://github.com/microsoft/RTVS) rozšíření pro Visual Studio 2017 a Visual Studio 2015 s aktualizací Update 3 (nebo vyšší), vydáno v rámci licence MIT. (Druhý opensourcové komponenty volá [RHost](https://github.com/microsoft/R-Host), které odkazuje na binární soubory interpret R, je vydávaný v rámci licence V2 veřejné GNU.)

> [!Note]
> RTVS se v současné době podporuje pouze v sadě Visual Studio ve Windows a nikoli Visual Studio pro Mac.

Chcete-li prostředí R v sadě Visual Studio:

- [Instalace nástrojů R](installing-r-tools-for-visual-studio.md).
- Postupujte podle [Začínáme](getting-started-with-r.md) průvodce, stejně jako [ukázky](getting-started-samples.md) a [získání pomoci](getting-started-help.md) článků.

Potom postupujte podle níže odkazy, které další informace o funkce související s R a také obecné možnosti samotnou sadu Visual Studio.

| Funkce | Popis | Dokumentace ke službě Visual Studio – Obecné |
| --- | --- | --- |
| [Systém projektů Visual Studia](r-projects-in-visual-studio.md) | Organizovat a spravovat související soubory ve struktuře pohodlný a využijte užitečné šablony pro položky jako kód R, dokumentace R, R Markdown, dotazů SQL a uložených procedur. Také využijte [Správce balíčků](r-package-manager-in-visual-studio.md) a [systému SQL Server integration](integrating-sql-server-with-r.md).  | [Řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Pracovní prostor](r-workspaces-in-visual-studio.md) | RTVS můžete svázat do místních a vzdálených pracovních prostorů umožňuje vývoj kódu R místně s menší sady dat, pak snadno spouštět kód na výkonnější počítače založené na cloudu s mnohem větších datových sad. | není k dispozici |
| [Možnosti nástrojů jazyka R](options-for-r-tools-in-visual-studio.md) | Ovládat různé aspekty RTVS. | [Dialogové okno Možnosti](../ide/reference/options-dialog-box-visual-studio.md) |
| [Bohaté možnosti úprav, technologie IntelliSense a fragmentů kódu](editing-r-code-in-visual-studio.md) | Zahrnuje obarvení syntaxe [IntelliSense](r-intellisense.md) napříč všemi váš kód a knihoven, formátování, podpisů kódu přejít k definici, najít všechny odkazy [fragmenty kódu](code-snippets-for-r.md)a provádění dalších akcí. | [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | R Markdown dokumenty usnadňují sdílení výsledky vašich dat pomocí integrovaného kód R uvnitř bloků kódu v markdownu. | není k dispozici |
| [Interaktivní okno](interactive-repl-for-r-in-visual-studio.md) | Poskytuje úplné prostředí REPL pro R umožňuje snadné spouštění kódu ve zdrojovém souboru v interaktivním okně. | není k dispozici |
| [Vizualizace dat](visualizing-data-with-r-in-visual-studio.md) | Vykreslení je nedílnou součástí prostředí R a RTVS podporuje více, okna diagramů nezávislé, každá má své vlastní historie a možnost přesunout vykreslí mezi okny. Vykreslení můžete uložit do rastrový obrázek a soubory PDF nebo zkopírován do schránky jako rastrový obrázek nebo metasouboru.  | není k dispozici |
| [Průzkumník proměnných](variable-explorer.md) | Zkontrolujte proměnné v oborech globální nebo specifický pro balíček s možností zobrazení seřaditelné tabulky a export do souboru CSV. | není k dispozici |
| [Plně vybavené ladění](debugging-r-in-visual-studio.md) | Zahrnuje integraci s interaktivním okně. | [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md) |

Viz také [– nejčastější dotazy](faq.md).

|   |   |
|---|---|
| ![Ikona filmové kamery pro video](../install/media/video-icon.png "Sledovat video") | [Podívejte se na video (webu youtube.com)](https://www.youtube.com/watch?v=dll3IS1bfWQ) přehledné informace o R Tools for Visual Studio (12 min 36s). Viz také [další videa o R Tools](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio). |

## <a name="send-us-your-feedback"></a>Pošlete nám svůj názor!

1. **Problémy s úložištěm GitHub**: je nejlepší způsob, jak kontaktovat tým RTVS [založením problému v Githubu](https://github.com/Microsoft/RTVS/issues), nebo pomocí **nástroje R** > **zpětnou vazbu** nabídky.

1. **Poslat smajlíka / Oblouček nahoru**: **nástroje R** > **zpětnou vazbu** nabídky je rychlý způsob, jak odeslat zpětnou vazbu a připojení souborů protokolu RTVS pro pomoc s diagnostikou problému. (Protokoly se zapisují do *%temp%/RTVSlogs.zip* v případě, že se mají posílat je zvlášť.) Protokolování je zakázaná, pokud si nepřejete mimo telemetrická data sady Visual Studio prostřednictvím **pomáhají** > **zpětnou vazbu** > **nastavení** příkaz nabídky nebo během instalace.

1. **E-mailu**: můžete poslat přímý zpětnou vazbu týmu na *rtvsuserfeedback (adrese)*.
