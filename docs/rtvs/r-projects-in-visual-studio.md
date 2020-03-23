---
title: Projekty v R
description: Jak vytvořit projekty správce R v sadě Visual Studio včetně vlastností, příkazů projektu a šablon.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: bcdef95935c0522c8b93a972d7f44fbd7632c53b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302691"
---
# <a name="create-r-projects-in-visual-studio"></a>Vytvoření r projektů v sadě Visual Studio

Projekt R (soubor *Rxproj)* identifikuje všechny zdrojové a obsahové soubory přidružené k projektu. Obsahuje také informace o sestavení pro každý soubor, udržuje informace pro integraci se systémy správy zdrojového kódu a pomáhá uspořádat aplikaci do logických součástí. Informace související s pracovním prostorem, jako je například seznam nainstalovaných balíčků, jsou však udržovány samostatně v samotném pracovním prostoru.

Projekty jsou vždy spravovány v rámci *řešení*sady Visual Studio , které mohou obsahovat libovolný počet projektů, které mohou odkazovat na sebe. Viz [Použití více typů projektů v sadě Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Vytvoření nového projektu R

1. Otevřete sadu Visual Studio.
1. Zvolte **soubor > nový projekt >** **(Ctrl**+**Shift**+**N)**
1. V části **Šablony** > **R**vyberte možnost "Projekt R" , pojmenujte projekt a vyberte **OK**:

    ![Dialogové okno Nový projekt pro R v sadě Visual Studio (RTVS ve VS2017)](media/getting-started-01-new-project.png)

Tento příkaz vytvoří projekt s prázdným *skriptem. R* soubor otevřít v editoru. Všimněte si také v **Průzkumníku řešení** existují dva další soubory v projektu:

![Obsah projektu R vytvořeného ze šablony](media/projects-template-results.png)

V *. Rhistory* zaznamenává všechny příkazy, které zadáte do interaktivního okna [R.](interactive-repl-for-r-in-visual-studio.md) Pomocí příkazu **R Tools** > **Windows** > **History** můžete otevřít vyhrazené okno historie. Toto okno obsahuje tlačítko panelu nástrojů a položky kontextové nabídky pro vymazání obsahu historie.

Soubor *rproject.rproj* udržuje určitá nastavení projektu specifické pro R, která jinak nejsou spravována visual studio:

| Vlastnost | Výchozí | Popis |
| --- | --- | --- |
| Version | 1.0 | Verze Nástroje R pro Visual Studio slouží k vytvoření projektu. |
| Obnovit pracovní prostor | Výchozí | Automaticky načte předchozí proměnné `.RData` pracovního prostoru ze souboru v adresáři projektu. |
| Uložit pracovní prostor | Výchozí | Při ukončování projektu `.RData` uložte aktuální proměnné pracovního prostoru do souboru v adresáři projektu. |
| AlwaysSaveHistory | Výchozí | Při zavírání projektu `.RHistory` uložte aktuální historii interaktivních oken do souboru v adresáři projektu. |
| EnableCodeIndexing | Ano | Určuje, zda má být spuštěna úloha indexování na pozadí, aby se urychlilo vyhledávání kódu. |
| UseSpacesForTab | Ano | Určuje, zda se mají při stisknutí klávesy **Tab** v editoru vložit mezery (Ano) nebo znak tabulátoru (Ne). |
| Karta NumspacesFor | 2 | Počet mezer, které chcete vložit, pokud je funkce UseSpacesForTab ano. |
| Kódování | UTF-8 | Výchozí kódování pro `.R` soubory. |
| RnwWeave | Svit | Balíček pro použití při tkaní souboru Rnw. |
| Latex | pdfLaTeX | Knihovna, která se použije při převodu RMarkdownu do PDF. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Převod složky souborů na projekt R

Pokud máte existující složku *aplikace . R* soubory, které chcete spravovat v projektu, postupujte takto:

1. Vytvořte nový projekt v sadě Visual Studio jako v předchozí části.
1. Zkopírujte soubory do složky projektu.
1. V Průzkumníku řešení Visual Studia klikněte pravým tlačítkem myši na projekt, vyberte **Přidat** > **existující položku**a vyhledejte soubory, které chcete přidat. Tyto soubory se zobrazí ve stromu projektu po výběru **OK**.
1. Chcete-li kód uspořádat do podsložek, klepněte pravým tlačítkem myši na projekt, nejprve vyberte **Přidat** > **novou složku,** potom zkopírujte soubory do této složky a přidejte tyto existující položky v kroku 3.

## <a name="project-properties"></a>Vlastnosti projektu

Chcete-li otevřít stránky vlastností projektu, klepněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a vyberte **příkaz Vlastnosti**nebo vyberte položku **nabídky vlastností vlastností project > (název projektu).** Okno, které se otevře, zobrazí vlastnosti projektu:

| Karta | Vlastnost | Popis |
| --- | --- | --- |
| Spusťte | Spouštěcí soubor | Název souboru, který je spuštěn s **příkazem Zdrojový spouštěcí soubor,** **F5**, **Ladění** > **Start ladění**nebo **Ladění** > Start bez**ladění**. Klepnutí pravým tlačítkem myši na soubor v projektu a výběrem **možnosti Nastavit jako spouštěcí skript R** jej také nastaví jako spouštěcí soubor. |
| | Obnovit r interaktivní při běhu | Vymaže všechny proměnné z pracovního prostoru interaktivního okna při spuštění projektu. Tím zaručujete, že neexistuje žádný zbytkový obsah pracovního prostoru z pervious spuštění. |
| | Vzdálená cesta k projektu | Cesta ke vzdálenému pracovnímu prostoru. |
| | Přenos souborů při běhu | Označuje, zda mají být soubory projektu, s výhradou filtru v **souborech k přenosu**, zkopírovány do vzdáleného pracovního prostoru při každém spuštění. |
| | Soubory k přenosu | Názvy souborů a zástupné znaky označující konkrétní soubory, které se mají kopírovat do vzdáleného pracovního prostoru, pokud je **vybrána možnost Přenést soubory při spuštění.** |
| Nastavení | (Soubor Settings.R) | Nastavení projektu R pochází z *Nastavení.R* nebo **. Settings.R* soubory, které jsou umístěny uvnitř projektu. Pokud není k dispozici žádný soubor nastavení, můžete přidat proměnné, uložit stránku a vytvořit pro vás výchozí soubor *Settings.R.* Soubor nastavení můžete také přidat do projektu pomocí příkazu nabídky **Přidat** > **novou položku.** <br/> Nastavení jsou uložena jako R kód a soubor může být získáván před spuštěním jiných modulů, čímž se předvyplnění prostředí s předdefinovaným nastavením. |

## <a name="r-specific-project-commands"></a>Příkazy projektu specifické pro R

Projekty sady Visual Studio podporují řadu obecných příkazů prostřednictvím nabídky po kliknutí pravým tlačítkem myši i nabídky **Projekt.** Podrobnosti o těchto obecných funkcích naleznete [v tématu Řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). Mějte však na paměti, že nástroje R pro sady Visual Studio (RTVS) přidá několik vlastních příkazů do nabídky po kliknutí pravým tlačítkem myši pro projekt R a také soubory a složky v rámci projektu.

| Příkaz | Popis |
| --- | --- |
| Nastavit pracovní adresář zde | Nastaví pracovní adresář interaktivního okna R na složku projektu, kterou lze také použít v libovolné podsložce v rámci projektu. |
| Otevřít obsahující složku | Otevře Průzkumníka Windows v umístění vybraného souboru. |
| Přidat skript R | Vytvoří a otevře nový *. Soubor R* s výchozím názvem. Můžete také vytvořit příkaz **Přidat** > **novou položku** *. R* soubory, stejně jako řada dalších typů souborů. Viz [Šablony položek specifických pro R](#r-specific-item-templates). |
| Přidat R Markdown | Vytvoří a otevře nový dokument *.rmd* s výchozím názvem. Příkaz **Přidat** > **novou položku** můžete také použít k vytvoření souborů *RMD* a řady dalších typů souborů. Viz [Šablony položek specifických pro R](#r-specific-item-templates).  |
| Publikovat uložené procedury | Spustí proces publikování všech uložených procedur obsažených ve skriptech R. Viz [Práce s SQL Server uložené procedury](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures). |

## <a name="r-specific-item-templates"></a>Šablony položek specifických pro R

RTVS obsahuje řadu šablon pro konkrétní typy souborů. K šablonám se dostanete klepnutím pravým tlačítkem myši na projekt R a výběrem možnosti **Přidat** > **novou položku**, výběrem **možnosti Přidat** > **novou položku**aplikace Project nebo použitím **souboru** > **Nový** > **soubor** a výběrem karty **R.** Nejlepší způsob, jak prozkoumat šablonu, je vytvořit nový projekt a vložit soubory každého typu.

> [!Note]
> Příkazy **Přidat** > **novou položku** také zobrazují obecné typy souborů, které nejsou uvedeny v tabulce. s **file new** > **New** > **file** tyto typy jsou obsaženy místo toho na kartě **Obecné.**

| Typ souboru | Popis |
| --- | --- |
| Skript jazyka R | Textový soubor obsahující stejné příkazy, které lze zadat na příkazovém řádku R. |
| R Markdown | Soubor obsahující dokument [R Markdown.](rmarkdown-with-r-in-visual-studio.md) |
| Nastavení R | Soubor, který obsahuje nastavení aplikace R. |
| R Dokumentace | Obecný soubor dokumentace R obsahující pouze název, alias a název pole. |
| R Dokumentace (funkce) | Soubor dokumentace R obsahující mnoho polí s komentáři pro popis funkce. |
| R Dokumentace (datová sada) | Soubor dokumentace R obsahující mnoho polí s komentáři pro popis datové sady. |
| Dotaz SQL | Prázdný soubor *.sql.* Viz [Práce se servery SQL Server a R](integrating-sql-server-with-r.md). |
| Uložená procedura s R | Soubor R s podřízeným dotazem SQL Query a podřízeným uloženým souborem šablony procedury. Viz [Práce se servery SQL Server a R](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Použití více typů projektů v sadě Visual Studio

Řešení Sady Visual Studio poskytují vhodné místo pro shromažďování a správu souvisejících projektů na jednom logickém místě. Řešení pomáhají udržovat váš kód uspořádaný a usnadňují spolupráci v rámci týmů.

V níže uvedeném příkladu obsahuje řešení projekt R s modelem vytvořeným pomocí R a Azure Machine Learning, projekt Python/scikit-learn, projekt C++ obsahující moduly pro intenzivní výpočetní práci, projekt SQL pro správu dat a projekt Python/Bottle pro web, který publikuje výsledek:

![Průzkumník řešení Visual Studio zobrazující více souvisejících projektů v řešení](media/projects-polyglot.png)

Projekt zvýrazněný boldface je "startup" projekt pro řešení; chcete-li jej změnit, klepněte pravým tlačítkem myši na jiný projekt a vyberte možnost **Nastavit jako spouštěcí projekt**.

> [!Note]
> V současné době neexistuje žádná explicitní integrace jazyka R až C#/C++ na místě (jako je tomu v [Pythonu, viz Vytvoření rozšíření C++ pro Python).](../python/working-with-c-cpp-python-in-visual-studio.md)  Existují však knihovny k dispozici, které poskytují C# a C++ mosty pro R.

Další informace o správě projektů a řešení obecně naleznete v [tématu Řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).
