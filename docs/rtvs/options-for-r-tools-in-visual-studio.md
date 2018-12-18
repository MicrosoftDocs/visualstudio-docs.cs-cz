---
title: Možnosti nástrojů jazyka R
description: Referenční informace pro možnosti v sadě Visual Studio pro jazyk R a související funkce.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: a40ed2fd72862bde3494edd0c74aebcca6b55711
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250956"
---
# <a name="r-tools-for-visual-studio-options"></a>Nástroje R pro Visual Studio možnosti

Nastavení jsou přístupné prostřednictvím **nástroje R** > **možnosti** nabídky, nebo prostřednictvím **nástroje** > **možnosti** a posouvání, aby mohl **nástroje R**:

  ![Dialogové okno Možnosti pro nástroje jazyka R](media/options-dialog.png)

Možnosti a nastavení specifická pro R jsou přístupné pomocí níže uvedených metod. Musíte vybrat **zobrazit všechna nastavení** políčko v dolní části **možnosti** dialogové okno pro všechny tyto oddíly se zobrazí.

- Možnosti formátování kódu (naleznete v tématu [možnosti editoru](editing-r-code-in-visual-studio.md#editor-options): **nástroje** > **možnosti** nabídce pak vyberte **textový Editor**  >  **R** > **formátování**
- Možnosti linter (naleznete v tématu [Linting](linting-r-code.md)): **nástroje** > **možnosti** nabídce pak vyberte **textový Editor**  >   **R** > **Lint**
- Rozšířené možnosti editoru ([popsaných v tomto článku](#text-editor--r--advanced-options)): **nástroje** > **možnosti** nabídce pak vyberte **textový Editor**  >  **R** > **Advanced**
- Chování možnosti ([popsaných v tomto článku](#r-tools--advanced-options)): **nástroje R** > **možnosti** nabídky, nebo **nástroje**  >  **Možnosti**, přejděte k položce **nástroje R**.

**Nástroje R** > **nastavení pro datové vědy** příkaz ovlivňuje také celou řadu různých nastavení v sadě Visual Studio celkové. Tento příkaz je popsané v další části.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>Nástroje R > Nastavení pro datové vědy

**R Tools > Nastavení pro datové vědy** položky nabídky nakonfiguruje integrovaném vývojovém prostředí sady Visual Studio s rozložením, která je optimalizovaná pro potřeby odborníci přes data. Konkrétně tato volba otevře [interaktivní](interactive-repl-for-r-in-visual-studio.md), [Průzkumníka proměnných](variable-explorer.md), a [pracovní prostory](r-workspaces-in-visual-studio.md) windows:

![Rozložení okna mezi odborníky přes data v sadě Visual Studio](media/installation-data-scientist-layout-result.png)

Chcete-li později vrátit k jiné nastavení sady Visual Studio, nejprve pomocí **nástroje** > **nastavení importu a exportu** příkaz select **exportovat vybrané nastavení prostředí**a zadejte název souboru. Obnovení těchto nastavení, použijte stejný příkaz a vyberte **importovat vybrané nastavení prostředí**. Můžete také použít stejné příkazy, pokud změníte rozložení mezi odborníky přes data a chcete se vrátit později místo použití **nastavení pro datové vědy** přímo příkazu.

## <a name="text-editor--r--advanced-options"></a>Textový Editor > R > Upřesnit možnosti

Tyto možnosti určují chování formátování, technologie IntelliSense, sbalování, odsazení a pro R. Kontrola syntaxe

![Dialogové okno Možnosti pro R text editor pokročilé možnosti](media/options-dialog-advanced-text-editor.png)

Každá možnost nastavená na zapnuto nebo vypnuto můžete řídit chování dotyčný. Podrobnosti o jednotlivých možností na podívejte se na podokno Nápověda v dolní části dialogového okna. Všimněte si, že můžete přetáhnout horní části tohoto podokna nápovědy až zkontrolujte podokno větší.

![Rozbalit podokno Nápověda v dialogovém okně R text editor pokročilé možnosti](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>Nástroje R > Upřesnit možnosti

**Nástroje R** > **možnosti** otevře příkazu nabídky **možnosti** dialogové okno Možnosti R:

  ![Dialogové okno Možnosti pro nástroje jazyka R](media/options-dialog.png)

Následující části popisují různé možnosti, které jsou k dispozici na této stránce.

### <a name="debugging"></a>Ladění

Tyto možnosti určují způsob zpracování hodnot v [Průzkumníka proměnných](variable-explorer.md) a v oknech ladicího programu, jako je sledovat a místní hodnoty (naleznete v tématu [kód ladit R](debugging-r-in-visual-studio.md)).

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Vyhodnotit aktivní vazby | `True` | Když `True`, zajistí, že vždycky vidíte aktuální hodnotu při kontrole proměnných a vlastností. Riziko se tohoto vyhodnocení výrazů může způsobit vedlejší účinky, v závislosti na tom, jak jsou implementované. |
| Ukazovat proměnné začínající tečkou | `False` | Určuje, zda proměnné s předponou `.` jsou uvedeny. |

### <a name="grid-view"></a>Zobrazení mřížky

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Dynamické vyhodnocení | `False` | Ve výchozím nastavení `View(<expression>)` funkce pořídí snímek dat jako datový rámec, který může spotřebovat značnou paměť s velkými datovými sadami. Tuto volbu nastavíte `True` znamená, že je výraz vyhodnocen při mřížky aktualizuje k načtení jenom data, která se zobrazí. Nicméně pokud výraz změny dat také změní, které mohou být vhodný pro výrazy pip dplyr. |

### <a name="help"></a>Nápověda

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Webový prohlížeč na F1 | `Internal` | Určuje, jak nápovědy se zobrazí, když se hledaný termín pomocí **Ctrl**+**F1**. Pokud je nastavena na `Internal`, pomoc se vykreslí v rámci panelu nástrojů v sadě Visual Studio. Pokud je nastavena na `External`, nápovědy se zobrazí ve výchozím webovém prohlížeči. |
| F1 Řetězec webového vyhledávání | `R site:stackoverflow.com` | Určuje, jak hledané výrazy jsou předány na vyhledávací web při stisknutí **Ctrl**+**F1** platností v editoru. Ve výchozím nastavení je řetězec `R site:stackoverflow.com`, která připojí `R` pro hledaný termín. `site:stackoverflow.com` Představuje direktivu na vyhledávací web, že má obor hledání stránky v rámci `stackoverflow.com` domény. |
| Prohlížeč nápovědy pro R | `Automatic` | Určuje způsob zobrazení nápovědy při hledání pomocí dokumentace R **F1**, **?**, nebo **??** . Pokud je nastavena na `Automatic`, pomoc se vykreslí v příslušné okno. Nápověda HTML se například zobrazí v rámci panelu nástrojů sady Visual Studio, že se soubory PDF ve svém programu výchozí PDF. Pokud je nastavena na `External`, pomoc se vykreslí ve výchozím webovém prohlížeči. |

### <a name="history"></a>Historie

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Vždycky uložit historii | `True` | Určuje, zda RTVS zapisuje do historie příkazů *. RHistory* soubor ve svém pracovním adresáři při každém zavření projektu. Ukládá se do historie se stane, i v případě, že nechcete uložit projekt před ukončením. |
| Resetovat vyhledávací filtr | `True` | Určuje, zda okno Historie můžete filtrovat historie příkazů zobrazíte jenom příkazy, které dílčí řetězec porovnání podmínky filtru v okně historie R. Toto nastavení určuje, jestli se má resetovat vyhledávací filtr historie při každém spuštění nového příkazu nebo přepnout na nový projekt, který aktivuje zatížení u různých *. RHistory* souboru. Ve výchozím nastavení `True` minimalizuje překvapením, že když spustíte příkaz s sadu filtrů a můžete divit, proč neměli jste spustili příkaz zobrazí v historii. |
| Použít Víceřádkový výběr | `True` | Určuje, zda můžete vybrat více řádků příkazu v historii jediným kliknutím. Taky umožňuje směrem nahoru nebo dolů šipku navigace ve Windows Interaktivní příkazy spíše než řádky. |

### <a name="html"></a>HTML

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Prohlížeč stránek HTML | `External` | Určuje, kde je obsah, jako `ggvis` diagram, nebo `shiny` vykreslením aplikaci. `Internal` zobrazuje výstup ve formátu HTML v rámci panelu nástrojů v sadě Visual Studio; `External` zobrazí výstupu protokolu HTML ve vašem výchozím prohlížeči. |

### <a name="logging"></a>protokolování

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Události protokolu | `Normal` | Určuje úroveň podrobností protokolování použít k diagnostice RTVS. Ve výchozím nastavení `Normal` vytvoří soubor protokolu v vaše `TEMP` adresáře. Pokud je nastavena na `Traffic`, RTVS zaznamenává všechny příkazy a odpovědí v relaci. Tyto soubory protokolu se nikdy opustit váš počítač, ale můžou být užitečné při diagnostikování problémů v RTVS. |

### <a name="markdown"></a>Markdown

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Prohlížeč náhledu markdownu | `External` | Určuje, kde se zobrazí výstup ve formátu RMarkdown HTML. `Internal` Zobrazí dokument RMarkdown HTML v rámci panelu nástrojů v sadě Visual Studio; `External` zobrazí RMarkdown HTML pomocí výchozí prohlížeč. |

### <a name="r-engine"></a>Modul pro R

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Znaková stránka | `(OS Default)` | Nastaví znakovou stránku (národní prostředí) pro R. Ve výchozím nastavení používá základní národní prostředí operačního systému. |
| Zrcadlový server CRAN | `(Use .Rprofile)` | Nastaví výchozí zrcadlový server CRAN pro instalace balíčků. Ve výchozím nastavení `Use .Rprofile` respektuje zrcadlový server CRAN nastavení ve vašich *. RProfile* souboru. |

### <a name="workspace"></a>Pracovní prostor

| Možnost | Výchozí hodnota | Popis |
| --- | --- | --- |
| Načíst pracovní prostor při otevření projektu | `No` | Nastavení na hodnotu `Yes` umožňuje načítání dat relace *. RData* souboru do globálního prostředí při otevření projektu. |
| Vyzvat k uložení pracovního prostoru na resetovat | `Yes` | Nastavení na `No` zakáže výzvy k potvrzení uložení pracovního prostoru, když kliknete na tlačítko Obnovit v interaktivním okně. |
| Uložit pracovní prostor při zavření projektu | `No` | Nastavení na hodnotu `Yes` umožňuje uložení globální prostředí tak, aby *. RData* souboru při zavření projektu. |
| Před přepnutím pracovních prostorů zobrazit potvrzovací dialogové okno | `Yes` | Nastavení na `No` zakáže výzvy k potvrzení při přepínání mezi různé pracovní prostory. Zobrazit [přepínání mezi pracovními prostory](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Zobrazit indikátor zatížení počítače | `False` | Řídí viditelnost indikátorů zatížení procesoru/paměti/sítě na stavovém řádku. Protože indikátor vyvolává síťový provoz, je to užitečné `False` ve scénářích vzdáleného monitorovaný. Změnou této možnosti vyžaduje restartování sady Visual Studio. |
