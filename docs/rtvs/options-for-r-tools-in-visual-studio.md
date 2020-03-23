---
title: Možnosti nástrojů R
description: Odkaz na možnosti v sadě Visual Studio pro jazyk R a přidružené funkce.
ms.date: 12/04/2017
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: c7c2cb57dc96d7bb0df09248eb7a877820e50521
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302705"
---
# <a name="r-tools-for-visual-studio-options"></a>Nástroje R pro možnosti sady Visual Studio

K nastavení se přistupuje prostřednictvím nabídky**Možnosti** **nástrojů** > R nebo pomocí**nástrojů** **A** > nástrojů a posouváním na **nástroje R**:

  ![Dialogové okno Možnosti pro nástroje R](media/options-dialog.png)

Možnosti a nastavení specifické pro R jsou přístupné pomocí níže uvedených metod. Chcete-li zobrazit všechny tyto oddíly, musíte v dolní části dialogového okna **Možnosti** vybrat pole **Zobrazit všechna nastavení.**

- Možnosti formátování kódu (viz [Možnosti editoru](editing-r-code-in-visual-studio.md#editor-options): Nabídka**Možnosti** **nástroje** > a pak vyberte **Text Editor** > **R** > **Formátování**
- Volby linter (viz [Linting](linting-r-code.md)): Nabídka**Možnosti** **nástrojů** > a pak vyberte **Textový editor** > **R** > **Lint**
- Upřesnit možnosti editoru ([popsané v tomto článku](#text-editor--r--advanced-options)): Nabídka**Možnosti** **nástrojů** > a pak vyberte **Textový editor** > **R** > **Upřesnit**
- Možnosti chování ([popsané v tomto článku](#r-tools--advanced-options)): Nabídka**Možnosti** **nástroje** > R nebo **Možnosti nástrojů** > **Options**a potom přejděte na **položku Nástroje R**.

Příkaz Nastavení**datové vědy** **nástroje R** > ovlivňuje také řadu různých nastavení v sadě Visual Studio celkově. Tento příkaz je popsán v další části.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>Nástroje R > nastavení datové vědy

R **Nástroje > Nastavení datové vědy položky** nabídky konfiguruje Visual Studio IDE s rozložením, který je optimalizovaný pro potřeby datových vědců. Tato možnost konkrétně otevře okna [Interaktivní](interactive-repl-for-r-in-visual-studio.md), [Průzkumník proměnných](variable-explorer.md)a [Pracovní prostory:](r-workspaces-in-visual-studio.md)

![Rozložení okna datových vědců v sadě Visual Studio](media/installation-data-scientist-layout-result.png)

Chcete-li se později vrátit k dalším nastavením sady Visual Studio, **nejprve** > použijte příkaz**Nástroje importu a nastavení exportu,** vyberte **Exportovat vybraná nastavení prostředí**a zadejte název souboru. Chcete-li tato nastavení obnovit, použijte stejný příkaz a vyberte **Importovat vybraná nastavení prostředí**. Můžete také použít stejné příkazy, pokud změníte rozložení datových vědců a chcete se k němu později vrátit, nikoli přímo pomocí příkazu **Nastavení datové vědy.**

## <a name="text-editor--r--advanced-options"></a>Textový editor > R > upřesnit možnosti

Tyto možnosti řídí chování formátování, technologie IntelliSense, osnovy, odsazení a kontroly syntaxe pro R.

![Dialogové okno Možnosti pro rozšířené volby textového editoru R](media/options-dialog-advanced-text-editor.png)

Každá možnost je nastavena na zapnutí nebo vypnutí pro řízení chování v otázce. Podrobnosti o tom, co jednotlivé možnosti ovlivňují, nalézáte v podokně nápovědy v dolní části dialogového okna. Všimněte si, že můžete přetáhnout horní části podokna nápovědy nahoru, aby se podokno zvětšilo.

![Rozbalené podokno nápovědy v dialogovém okně rozšířených možností textového editoru R](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>Nástroje R > rozšířené možnosti

Příkaz Příkaz **Možnosti** > **nástrojů** R otevře dialogové okno **Možnosti** na volby R:

  ![Dialogové okno Možnosti pro nástroje R](media/options-dialog.png)

Následující části popisují různé možnosti, které jsou k dispozici na této stránce.

### <a name="debugging"></a>ladění

Tyto možnosti řídí způsob zpracování hodnot v [Průzkumníku proměnných](variable-explorer.md) a v oknech ladicího programu, jako je Watch a Locals (viz [Kód Ladění R).](debugging-r-in-visual-studio.md)

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Vyhodnocení aktivních vazeb | `True` | When `True`, zajišťuje, že při kontrole proměnných a vlastností vždy uvidíte nejaktuálnější hodnotu. Riziko je, že hodnocení výrazy může způsobit vedlejší účinky, v závislosti na tom, jak byly implementovány. |
| Zobrazit tečkové předponou proměnné | `False` | Určuje, zda budou zobrazeny proměnné s `.` předponou. |

### <a name="grid-view"></a>Zobrazení mřížky

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Dynamické vyhodnocení | `False` | Ve výchozím `View(<expression>)` nastavení funkce pořídí snímek dat jako datový rámec, který může spotřebovat značnou paměť s velkými datovými sadami. Nastavení této `True` možnosti znamená, že výraz je vyhodnocen, když se mřížka aktualizuje, aby se načítaly pouze ta data, která se zobrazí. Pokud se však výraz změní, změní se také data, což může být nevhodné pro výrazy dplyr pip. |

### <a name="help"></a>Nápověda

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Webový prohlížeč F1 | `Internal` | Určuje způsob zobrazení nápovědy při hledání termínu pomocí **klávesctrl**+**f1**. Pokud je `Internal`nastavena na , nápověda je vykreslena v okně nástroje v sadě Visual Studio. Pokud je `External`nastavena na , zobrazí se nápověda ve výchozím webovém prohlížeči. |
| F1 vyhledávací řetězec webu | `R site:stackoverflow.com` | Určuje, jak jsou vyhledávací termíny předávány do vašeho vyhledávače, když stisknete **kombinaci kláves**+**YF1** na termínu v editoru. Ve výchozím nastavení `R site:stackoverflow.com`je řetězec `R` , který se připojí k hledaný mů e-termín. Je `site:stackoverflow.com` direktiva pro vyhledávač, který mu říká, `stackoverflow.com` že rozsah hledání na stránky v rámci domény. |
| R Prohlížeč nápovědy | `Automatic` | Určuje, jak se nápověda zobrazuje při prohledávání dokumentace jazyka R pomocí **f1**, **? nebo** **??**. Pokud je `Automatic`nastavena na , nápověda vykreslí v příslušném okně. Nápověda HTML se například zobrazí v okně nástroje Visual Studio, zatímco pdf se zobrazí ve výchozím programu PDF. Pokud je `External`nastavena na , nápověda je vykreslena ve výchozím webovém prohlížeči. |

### <a name="history"></a>Historie

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Vždy ukládat historii | `True` | Určuje, zda rtvs zapíše historii příkazů do *. RHistory* v pracovním adresáři při každém zavření projektu. K uložení historie dojde i v případě, že projekt před ukončením neuložíte. |
| Obnovit vyhledávací filtr | `True` | Určuje, zda může okno Historie filtrovat historii příkazů tak, aby zobrazovalo pouze příkazy, které odpovídají termínu filtru v dialogovém okně Historie R. Toto nastavení určuje, zda chcete obnovit filtr vyhledávání historie při každém spuštění nového příkazu nebo přepnout na nový projekt, který spustí zatížení jiného *. RHistory* soubor. Výchozí nastavení `True` minimalizuje překvapení při spuštění příkazu se sadou filtrů a divíte se, proč se příkaz, který jste právě spustili, neobjevil v historii. |
| Použít víceřádkový výběr | `True` | Určuje, zda můžete jedním kliknutím vybrat víceřádkový příkaz v historii. Také umožňuje navigaci šipkou nahoru/dolů v interaktivním systému Windows podle příkazů, nikoli podle řádků. |

### <a name="html"></a>HTML

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Prohlížeč stránek HTML | `External` | Určuje, kde je `ggvis` vykreslen obsah, `shiny` například obrázek nebo aplikace. `Internal`zobrazuje výstup HTML v okně nástroje v sadě Visual Studio; `External` zobrazí výstup HTML ve výchozím prohlížeči. |

### <a name="logging"></a>Protokolování

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Protokolovat události | `Normal` | Řídí podrobnost protokolování používaného pro diagnostiku RTVS. Výchozí nastavení `Normal` vytvoří soubor protokolu `TEMP` v adresáři. Pokud je `Traffic`nastavena na , RTVS protokoly všechny příkazy a odpovědi ve vaší relaci. Tyto soubory protokolu nikdy opustit počítač, ale může být užitečné pro diagnostiku problémů v RTVS. |

### <a name="markdown"></a>Markdown

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Prohlížeč náhledu Markdownu | `External` | Určuje, kde se zobrazí výstup RMarkdown HTML. `Internal`zobrazí dokument HTML RMarkdown v okně nástroje v sadě Visual Studio; `External` zobrazí RMarkdown HTML pomocí výchozího prohlížeče. |

### <a name="r-engine"></a>R Motor

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Znaková stránka | `(OS Default)` | Nastaví znakovou stránku (národní prostředí) pro R. Ve výchozím nastavení používá základní národní prostředí operačního systému. |
| CRAN Zrcadlo | `(Use .Rprofile)` | Nastaví výchozí zrcadlo CRAN pro instalace balíčků. Výchozí nastavení `Use .Rprofile` respektuje nastavení CRAN Mirror ve vašem *. RProfile.* |

### <a name="workspace"></a>Pracovní prostor

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Načíst pracovní prostor při otevření projektu | `No` | Nastavení `Yes` umožňuje načítání dat relace z *. RData* do globálního prostředí při otevření projektu. |
| Výzva k uložení pracovního prostoru při resetování | `Yes` | Nastavení `No` zakáže zobrazení výzvy k uložení pracovního prostoru po klepnutí na tlačítko Obnovit v interaktivním okně. |
| Uložení pracovního prostoru při zavření projektu | `No` | Nastavení `Yes` umožňuje uložení globálního prostředí do *oblasti . RData* soubor při zavření projektu. |
| Zobrazit dialogové okno potvrzení před přepnutím pracovních prostorů | `Yes` | Nastavení `No` zakázat výzvu uživateli k potvrzení při přepínání mezi různými pracovními prostory. Viz [Přepínání mezi pracovními plochami](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Zobrazit indikátor zatížení stroje | `False` | Řídí viditelnost indikátoru zatížení PROCESOR/Paměť/Síť ve stavovém řádku. Vzhledem k tomu, že indikátor vzniká síťový `False` provoz, je užitečné zachovat tento ve scénářích vzdáleného účtovaného podle objemu dat. Změna této možnosti vyžaduje restartování sady Visual Studio. |
