---
title: R Tools for Visual Studio
description: Nástroje R pro Visual Studio 2017 (RTVS) je bezplatné opensourcové rozšíření, které nabízí řadu jazykových funkcí včetně IntelliSense, ladění a vzdálených pracovních prostorů.
ms.date: 11/13/2017
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 89aa8b9d1b1f288e19252b8a111666f5b4e3e087
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238709"
---
# <a name="work-with-r-in-visual-studio"></a>Práce s jazykem R v sadě Visual Studio

R představuje vysoce rozšiřitelný jazyk a prostředí pro statistické výpočty a grafy. Distribuuje se v rámci Obecné veřejné licence GNU v.2, nabízí silnou podporu uživatelské komunity a je známý tím, že umí vykreslit vysoce kvalitní diagramy včetně matematických symbolů a vzorců. Další informace o jazyce R najdete na webu [r-project.org](https://www.r-project.org/about.html) a na stránce [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

Nástroje R pro Visual Studio (RTVS) je bezplatné [opensourcové](https://github.com/microsoft/RTVS) rozšíření pro Visual Studio 2017 a Visual Studio 2015 Update 3 (nebo novější verzi), vydané v rámci licence MIT. (Druhá opensourcová komponenta s názvem [RHost](https://github.com/microsoft/R-Host), která odkazuje na binární soubory překladače jazyka R, je vydaná v rámci Obecné veřejné licence GNU v.2.)

> [!Note]
> Rozšíření RTVS je momentálně podporováno jen v sadě Visual Studio 2017 ve Windows, Visual Studio pro Mac ho nepodporuje. Není k dispozici pro Visual Studio 2019.

Když chcete v sadě Visual Studio používat jazyk R:

- [Nainstalujte rozšíření Nástroje R](installing-r-tools-for-visual-studio.md).
- Postupujte podle příručky [Začínáme](getting-started-with-r.md) a také si přečtěte články [Ukázky](getting-started-samples.md) a [Získání nápovědy](getting-started-help.md).

Potom postupujte podle odkazů níže a získejte další informace o funkcích souvisejících s jazykem R a také o obecných funkcích sady Visual Studio.

| Funkce | Popis | Obecná dokumentace sady Visual Studio |
| --- | --- | --- |
| [Projektový systém sady Visual Studio](r-projects-in-visual-studio.md) | Mějte související soubory uspořádané v přehledné struktuře, která usnadní jejich správu, a využívejte efektivní šablony pro kódování v jazyce R, dokumentaci k jazyku R, nástroj R Markdown, příkazy jazyka SQL a uložené procedury. Práci vám usnadní také [správce balíčků](r-package-manager-in-visual-studio.md) a [integrace SQL Serveru](integrating-sql-server-with-r.md).  | [Řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Pracovní prostor](r-workspaces-in-visual-studio.md) | Rozšíření RTVS lze navázat na místní i vzdálené pracovní prostory, takže kód v jazyce R můžete vyvíjet místně pomocí menších datových sad a následně ho spustit na výkonnějších cloudových počítačích a pracovat s výrazně většími datovými sadami. | Není k dispozici |
| [Možnosti rozšíření Nástroje R](options-for-r-tools-in-visual-studio.md) | Mějte pod kontrolou různé aspekty rozšíření RTVS. | [Možnosti – dialogové okno](../ide/reference/options-dialog-box-visual-studio.md) |
| [Široká škála úprav, IntelliSense a fragmenty kódu](editing-r-code-in-visual-studio.md) | Zahrnuje barevné zvýrazňování syntaxe, funkci [IntelliSense](r-intellisense.md) napříč všemi kódy a knihovnami, formátování kódu, nápovědu pro podpis, příkazy Go to Definition (Přejít k definici), Find All References (Vyhledat všechny odkazy) [fragmenty kódu](code-snippets-for-r.md) a další. | [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | Dokumenty nástroje R Markdown vám pomůžou sdílet výsledky práce s daty, včetně integrovaného kódu R uvnitř bloků kódu jazyka Markdown. | Není k dispozici |
| [Okno Interactive](interactive-repl-for-r-in-visual-studio.md) | Poskytuje plnohodnotné prostředí REPL pro jazyk R a umožňuje snadno spustit kód ve zdrojovém souboru v interaktivním okně. | Není k dispozici |
| [Vizualizace dat](visualizing-data-with-r-in-visual-studio.md) | Vykreslení diagramů je nedílnou součástí prostředí jazyka R a rozšíření RTVS podporuje několik nezávislých oken diagramů, z nichž má každé vlastní historii, a umožňuje diagramy mezi nimi přesouvat. Diagramy lze ukládat jako rastrové obrázky nebo do souborů PDF, případně kopírovat do schránky jako rastrové obrázky nebo metasoubory.  | Není k dispozici |
| [Průzkumník proměnných](variable-explorer.md) | Prozkoumejte proměnné v globálním oboru nebo v oboru konkrétního balíčku a využívejte funkce pro zobrazení tabulek s možností třídění a exportu do souboru CSV. | Není k dispozici |
| [Bohaté funkce ladění](debugging-r-in-visual-studio.md) | Zahrnují integraci s oknem Interactive. | [Ladění v sadě Visual Studio](../debugger/debugger-feature-tour.md) |

Přečtěte si [nejčastější dotazy](faq.md).

![ikona filmové kamery pro video](../install/media/video-icon.png "Přehrát video") [Podívejte se na video (na youtube.com)](https://www.youtube.com/watch?v=dll3IS1bfWQ), které představuje Nástroje R pro Visual Studio (12 min 36 s). Podívejte se také na [další videa o nástrojích jazyka R](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio).

## <a name="send-us-your-feedback"></a>Vyjádřete svůj názor.

1. **Problémy GitHubu**: Když potřebujete kontaktovat tým podpory rozšíření RTVS, nejlepší možností je [založit o daném problému vlákno na GitHubu](https://github.com/Microsoft/RTVS/issues), nebo využít nabídku **Nástroje R** > **Názory**.

1. **Poslat smajlíka/zamračeného smajlíka**: Pokud chcete odeslat svůj názor a připojit soubory protokolu rozšíření RTVS, abyste usnadnili diagnostiku problému, rychlou možností je nabídka **Nástroje R** > **Názory**. (Pokud chcete poslat protokoly samostatně, zapisují se do souboru *%temp%/RTVSlogs.zip*.) Pokud jste se při instalaci nebo prostřednictvím příkazu nabídky **Nápověda** > **Názory** > **Nastavení** rozhodli odhlásit z telemetrie sady Visual Studio, protokolování je vypnuté.

1. **E-mail**: Svůj názor můžete napsat týmu přímo na adresu *rtvsuserfeedback (at) microsoft.com*.
