---
title: R Tools for Visual Studio
description: Nástroje R pro Visual Studio 2017 (RTVS) je bezplatné rozšíření open source, které poskytuje mnoho funkcí jazyka, včetně IntelliSense, ladění a vzdálených pracovních prostorů.
ms.date: 11/13/2017
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 1132a7a0363e2d508d6eff1026192aad3407fca4
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189251"
---
# <a name="work-with-r-in-visual-studio"></a>Práce s jazykem R v aplikaci Visual Studio

R je vysoce rozšiřitelný jazyk a prostředí pro statistické výpočty a grafiku. Je distribuována zdarma v rámci obecné veřejné licence GNU, nabízí silnou podporu komunity a je známo, že má schopnost vytvářet publikace kvality publikace, včetně matematických symbolů a vzorců. Další informace o jazyce R najdete na adrese [r-Project.org](https://www.r-project.org/about.html) a [Úvod do jazyka r](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

Nástroje R pro Visual Studio (RTVS) je bezplatné [Open Source](https://github.com/microsoft/RTVS) rozšíření pro visual Studio 2017 a visual Studio 2015 Update 3 (nebo vyšší) vydané v rámci licence MIT. (Druhá Open-Source komponenta s názvem [RHost](https://github.com/microsoft/R-Host), která odkazuje na binární soubory překladače R, je vydaná ve veřejné licenci GNU v2.)

> [!Note]
> RTVS je v současné době podporován pouze v aplikaci Visual Studio 2017 ve Windows a Visual Studio pro Mac. Není k dispozici pro Visual Studio 2019.

Pro prostředí jazyka R v aplikaci Visual Studio:

- [Nainstalujte nástroje R](installing-r-tools-for-visual-studio.md).
- Postupujte podle příručky [Začínáme](getting-started-with-r.md) a také [ukázek](getting-started-samples.md) a [načítajících](getting-started-help.md) se článků s nápovědou.

Potom postupujte podle odkazů níže a získejte další informace o funkcích souvisejících s R a také o obecných funkcích aplikace Visual Studio.

| Funkce | Popis | Obecná dokumentace k sadě Visual Studio |
| --- | --- | --- |
| [Systém projektu sady Visual Studio](r-projects-in-visual-studio.md) | Uspořádejte a spravujte související soubory ve vhodné struktuře a využijte výhod užitečných šablon pro položky, jako je kód R, dokumentace R, R Markdown, dotazy SQL a uložené procedury. Také užívejte [Správce balíčků](r-package-manager-in-visual-studio.md) a [SQL Server integraci](integrating-sql-server-with-r.md).  | [Řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Stejných](r-workspaces-in-visual-studio.md) | RTVS se může navazovat na místní a vzdálené pracovní prostory, což vám umožní vyvíjet kód R místně s menšími datovými sadami a potom snadno spustit kód v výkonnějších cloudových počítačích s mnohem většími datovými sadami. | není k dispozici |
| [Možnosti nástrojů R](options-for-r-tools-in-visual-studio.md) | Řízení různých aspektů RTVS. | [Dialogové okno Možnosti](../ide/reference/options-dialog-box-visual-studio.md) |
| [Bohatě upravené úpravy, technologie IntelliSense a fragmenty kódu](editing-r-code-in-visual-studio.md) | Zahrnuje barevné zvýrazňování syntaxe, [IntelliSense](r-intellisense.md) napříč celým kódem a knihovnami, formátování kódu, help signatura, přejít na definici, najít všechny odkazy, [fragmenty kódu](code-snippets-for-r.md)a další. | [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | R Markdown dokumenty vám pomůžou sdílet výsledky dat s integrovaným kódem R uvnitř bloků kódu Markdownu. | není k dispozici |
| [Interaktivní okno](interactive-repl-for-r-in-visual-studio.md) | Poskytuje plnohodnotné prostředí REPL pro R s možností snadného spuštění kódu ve zdrojovém souboru v interaktivním okně. | není k dispozici |
| [Vizualizace dat](visualizing-data-with-r-in-visual-studio.md) | Vykreslení je nedílnou součástí prostředí jazyka R a RTVS podporuje několik nezávislých oken vykreslení, z nichž každá má svou vlastní historii a možnost přesouvat zobrazení mezi okny. Vykreslení lze uložit do rastrových souborů a souborů PDF nebo zkopírovat do schránky jako rastrový obrázek nebo metasoubor.  | není k dispozici |
| [Průzkumník proměnných](variable-explorer.md) | Prohlédněte si proměnné v globálním nebo specifickém oboru pro konkrétní balíčky a možnost zobrazit tabulky s možností řazení a exportovat do sdíleného svazku clusteru. | není k dispozici |
| [Plně funkční ladění](debugging-r-in-visual-studio.md) | Zahrnuje integraci s interaktivním oknem. | [Ladění v sadě Visual Studio](../debugger/debugger-feature-tour.md) |

Seznamte se také s [nejčastějšími dotazy](faq.md).

|   |   |
|---|---|
| ![ikona filmové kamery pro video](../install/media/video-icon.png "Přehrát video") | [Podívejte se na video (YouTube.com)](https://www.youtube.com/watch?v=dll3IS1bfWQ) , kde můžete zobrazit přehled nástroje R pro Visual Studio (12m 36s). Podívejte se také na [Další videa k nástrojům R](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio). |

## <a name="send-us-your-feedback"></a>Pošlete nám svůj názor.

1. **Problémy GitHubu**: nejlepší způsob, jak se spojit s týmem RTVS, je nahlásit [problém na GitHubu](https://github.com/Microsoft/RTVS/issues)nebo pomocí nabídky **nástroje R** > **Zpětná vazba** .

1. **Odeslat smajlíka/zamračení**: nabídka **R nástroje** > **Zpětná vazba** představuje rychlý způsob, jak odeslat zpětnou vazbu a připojit soubory protokolu RTVS, které vám pomůžou diagnostikovat váš problém. (Protokoly se zapisují do *% TEMP%/RTVSlogs.zip* pro případ, že je budete chtít poslat samostatně.) Protokolování je zakázané, pokud **jste se k** telemetrie sady Visual Studio rozhodli prostřednictvím příkazu nabídky **Nastavení** >  > **Feedback** nebo během instalace.

1. **E-mail**: můžete poslat přímý názor týmu na adrese *rtvsuserfeedback (at) Microsoft.com*.
