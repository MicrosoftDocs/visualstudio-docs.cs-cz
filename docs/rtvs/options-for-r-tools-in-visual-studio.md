---
title: Možnosti nástrojů R
description: Referenční informace o možnostech v aplikaci Visual Studio pro jazyk R a související funkce.
ms.date: 12/04/2017
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: ed2ee29fb7a0a832dd3076cbd47a7f9cd1414d96
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939471"
---
# <a name="r-tools-for-visual-studio-options"></a>Možnosti Nástroje R pro Visual Studio

K nastavení je možné přistupovat prostřednictvím nabídky možnosti **nástrojů R**  >   nebo prostřednictvím   >  **možností** nástrojů a posouvání na **nástroje r**:

  ![Dialogové okno Možnosti pro nástroje R](media/options-dialog.png)

Možnosti a nastavení specifické pro R jsou dostupné pomocí níže uvedených metod. Aby se zobrazily všechny tyto oddíly, musíte zaškrtnout políčko **Zobrazit všechna nastavení** v dolní části dialogového okna **Možnosti** .

- Možnosti formátování kódu (viz [Možnosti editoru](editing-r-code-in-visual-studio.md#editor-options):   >  nabídka **Možnosti** nástrojů a výběr formátování **textového editoru**  >  **R**  >  
- Linter možnosti (viz [linting](linting-r-code.md)):   >  nabídka **Možnosti** nástrojů a pak vybrat **textový editor**  >  **R**  >  **Lint**
- Rozšířené možnosti editoru ([popsané v tomto článku](#text-editor--r--advanced-options)):   >  nabídka **Možnosti** nástrojů a pak vybrat **textový editor**  >  **R**  >  **Upřesnit**
- Možnosti chování ([popsané v tomto článku](#r-tools--advanced-options)): nabídka **Možnosti nástrojů R**  >   nebo   >  **Možnosti** nástrojů a přechod na **nástroje r**.

Příkaz **nastavení pro datové vědy nástrojů jazyka R**  >   ovlivňuje také celou řadu různých nastavení v aplikaci Visual Studio. Tento příkaz je popsaný v následující části.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>Nástroje R > Nastavení pro datové vědy

Položka nabídky **nástroje R > nastavení pro datové vědy** konfiguruje integrované vývojové prostředí sady Visual Studio s rozložením, které je optimalizováno pro potřeby vědeckých pracovníků dat. Konkrétně tato možnost otevře okna [interaktivní](interactive-repl-for-r-in-visual-studio.md), [Průzkumník proměnných](variable-explorer.md)a [pracovní prostory](r-workspaces-in-visual-studio.md) :

![Rozložení okna pro datový vědecký pracovník v aplikaci Visual Studio](media/installation-data-scientist-layout-result.png)

Pokud se chcete později vrátit k dalším nastavením sady Visual Studio, použijte nejprve příkaz **nástroje** pro  >  **Import a export nastavení** , vyberte **Exportovat vybrané nastavení prostředí** a zadejte název souboru. Chcete-li tato nastavení obnovit, použijte stejný příkaz a vyberte možnost **Importovat vybrané nastavení prostředí**. Stejné příkazy můžete použít také v případě, že změníte rozložení pro odborníky na data a chcete se k němu vrátit později, místo použití příkazu **nastavení pro datové vědy** přímo.

## <a name="text-editor--r--advanced-options"></a>Textový editor > R > pokročilé možnosti

Tyto možnosti řídí chování formátování, technologie IntelliSense, sbalení, odsazení a kontrola syntaxe pro jazyk R.

![Dialogové okno Možnosti pro rozšířené možnosti textového editoru jazyka R](media/options-dialog-advanced-text-editor.png)

Každá možnost je nastavena na hodnotu Zapnuto nebo vypnuto pro řízení daného chování. Podrobnosti o tom, co jednotlivé možnosti ovlivňují, najdete v podokně Help v dolní části dialogového okna. Všimněte si, že je možné přetáhnout horní část okna, aby bylo okno větší.

![Rozšířené podokno s podoknem Help v dialogovém okně Upřesnit možnosti editoru textu R](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>Nástroje R > pokročilé možnosti

Příkaz nabídky možnosti **nástrojů r**  >   otevře dialogové okno **Možnosti** pro možnosti jazyka r:

  ![Dialogové okno Možnosti pro nástroje R](media/options-dialog.png)

V následujících částech jsou popsány různé možnosti, které jsou k dispozici na této stránce.

### <a name="debugging"></a>Ladění

Tyto možnosti určují, jak jsou zpracovávány hodnoty v [Průzkumník proměnných](variable-explorer.md) a v oknech ladicího programu, jako jsou kukátka a lokální hodnoty (viz [ladění R Code](debugging-r-in-visual-studio.md)).

| Možnost | Výchozí hodnota | Description |
| --- | --- | --- |
| Vyhodnotit aktivní vazby | `True` | V případě `True` je zajištěno, že při kontrole proměnných a vlastností vždy uvidíte nejaktuálnější hodnotu. Riziko je, že vyhodnocení výrazů může způsobit vedlejší účinky v závislosti na tom, jak byly implementovány. |
| Zobrazit proměnné s tečkou | `False` | Určuje, zda jsou zobrazeny proměnné s předponou `.` . |

### <a name="grid-view"></a>Zobrazení mřížky

| Možnost | Výchozí hodnota | Description |
| --- | --- | --- |
| Dynamické vyhodnocení | `False` | Ve výchozím nastavení `View(<expression>)` funkce přebírá snímek dat jako datový rámec, což může spotřebovávat značnou paměť s velkými datovými sadami. Nastavení této možnosti `True` znamená, že výraz je vyhodnocen, když se tabulka aktualizuje, aby se načetla pouze data, která se zobrazí. Nicméně pokud výraz změní data i změny, které nemusí být vhodné pro výrazy dplyr PIP. |

### <a name="help"></a>Nápověda

| Možnost | Výchozí hodnota | Description |
| --- | --- | --- |
| Webový prohlížeč F1 | `Internal` | Určuje, jak se zobrazí Nápověda při hledání termínu pomocí **klávesy CTRL** + **F1**. Při nastavení na je v `Internal` aplikaci Visual Studio vykreslena v okně nástroje. Při nastavení na se `External` ve výchozím webovém prohlížeči zobrazí zpráva. |
| Vyhledávání na webu řetězec F1 | `R site:stackoverflow.com` | Určuje, jakým způsobem jsou do vyhledávacího modulu předávány hledané termíny při stisknutí klávesy **CTRL** + **F1** pro termín v editoru. Ve výchozím nastavení je řetězec `R site:stackoverflow.com` , který se připojí `R` k hledanému termínu. `site:stackoverflow.com`Je direktivou pro vyhledávací modul, která dává pokyn pro určení rozsahu hledání na stránky v rámci `stackoverflow.com` domény. |
| Prohlížeč Nápověda pro R | `Automatic` | Určuje, jak se zobrazí Nápověda při hledání v dokumentaci jazyka R pomocí **klávesy F1**, **?** nebo **??**. Pokud je nastaveno na `Automatic` , help vykresluje v příslušném okně. V okně nástroje sady Visual Studio se například zobrazí nápovědu HTML, zatímco soubory PDF se zobrazí ve výchozím programu PDF. Při nastavení na `External` je ve výchozím webovém prohlížeči vykreslena hodnota help. |

### <a name="history"></a>Historie

| Možnost | Výchozí hodnota | Description |
| --- | --- | --- |
| Vždy ukládat historii | `True` | Určuje, zda RTVS zapisuje historii příkazů do *. RHistory* soubor v pracovním adresáři pokaždé, když je projekt uzavřený. Uložení historie se projeví i v případě, že projekt neuložíte předtím, než skončíte. |
| Resetovat vyhledávací filtr | `True` | Určuje, zda okno historie může filtrovat historii příkazů, aby zobrazovalo pouze příkazy, které podřetězec odpovídá termínu filtru v dialogovém okně Historie R. Toto nastavení určuje, zda má být obnoven filtr hledání historie pokaždé, když spustíte nový příkaz nebo přepnete na nový projekt, který aktivuje zatížení jiného *. Soubor RHistory* Výchozí nastavení `True` minimalizuje neočekávaně při spuštění příkazu se sadou filtrů a zajímá Vás, proč se příkaz, který jste právě spustili, nezobrazil v historii. |
| Použít víceřádkový výběr | `True` | Určuje, jestli můžete vybrat víceřádkový příkaz v historii jediným kliknutím. Také umožňuje navigaci pomocí šipky nahoru/dolů v interaktivních oknech podle příkazů místo řádků. |

### <a name="html"></a>HTML

| Možnost | Výchozí hodnota | Description |
| --- | --- | --- |
| Prohlížeč stránek HTML | `External` | Určuje, kde `ggvis` se vykreslí obsah, jako je například vykreslení nebo `shiny` aplikace. `Internal` zobrazuje výstup HTML v rámci okna nástrojů v sadě Visual Studio; `External` zobrazí výstup HTML ve výchozím prohlížeči. |

### <a name="logging"></a>protokolování

| Možnost | Výchozí hodnota | Description |
| --- | --- | --- |
| Události protokolu | `Normal` | Řídí podrobnost protokolování používaného pro diagnostiku RTVS. Ve výchozím nastavení se `Normal` vytvoří soubor protokolu ve vašem `TEMP` adresáři. Když se nastaví na `Traffic` , RTVS zaprotokoluje všechny příkazy a odpovědi ve vaší relaci. Tyto soubory protokolu tento počítač nikdy nenechávají, ale mohou být užitečné při diagnostice problémů v RTVS. |

### <a name="markdown"></a>Markdown

| Možnost | Výchozí hodnota | Description |
| --- | --- | --- |
| Prohlížeč náhledu Markdownu | `External` | Určuje, kde se zobrazí výstup RMarkdown HTML. `Internal` zobrazuje dokument HTML RMarkdown v rámci okna nástrojů v sadě Visual Studio; `External` zobrazí RMARKDOWN HTML s použitím výchozího prohlížeče. |

### <a name="r-engine"></a>Modul R

| Možnost | Výchozí hodnota | Description |
| --- | --- | --- |
| Znaková stránka | `(OS Default)` | Nastaví znakovou stránku (locale) pro R. Ve výchozím nastavení používá základní národní prostředí operačního systému. |
| CRAN zrcadlení | `(Use .Rprofile)` | Nastaví výchozí zrcadlení CRAN pro instalace balíčků. Výchozí nastavení pro `Use .Rprofile` Nastavení zrcadlení Cran ve vašem systému *. Soubor RProfile* |

### <a name="workspace"></a>Pracovní prostor

| Možnost | Výchozí hodnota | Description |
| --- | --- | --- |
| Načíst pracovní prostor při otevření projektu | `No` | Nastavení umožňující `Yes` načtení dat relace z *. RData* soubor do globálního prostředí při otevření projektu. |
| Při resetování vyzvat k uložení pracovního prostoru | `Yes` | Nastavení `No` zakáže zobrazování výzvy k uložení pracovního prostoru po kliknutí na tlačítko Resetovat v interaktivním okně. |
| Uložit pracovní prostor při zavření projektu | `No` | Nastavení na `Yes` povoluje ukládání globálního prostředí do *. RData* soubor při zavření projektu. |
| Před přepnutím pracovních prostorů zobrazit potvrzovací dialog | `Yes` | Nastavení `No` zakáže uživateli zobrazovat výzvy k potvrzení při přepínání mezi různými pracovními prostory. Zobrazit [přepínání mezi pracovními prostory](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Zobrazit indikátor zatížení počítače | `False` | Řídí viditelnost indikátoru zatížení procesoru/paměti/sítě ve stavovém řádku. Vzhledem k tomu, že indikátor vykonává síťový provoz, je vhodné tento postup uchovávat `False` ve vzdálených scénářích s měřením. Změna této možnosti vyžaduje restartování sady Visual Studio. |
