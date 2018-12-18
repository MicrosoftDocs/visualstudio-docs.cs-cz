---
title: Projekty v R
description: Jak vytvořit projekty v R správce v sadě Visual Studio obsahuje vlastnosti, projekt příkazů a šablony.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: f91d105d1c7b5b60d74dae2f9669a18f8ec064c8
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248280"
---
# <a name="create-r-projects-in-visual-studio"></a>Vytvořit projekty v R v sadě Visual Studio

Projekt R ( *.rxproj* souboru) identifikuje všechny zdroje a soubory obsahu přidružené k projektu. Také obsahuje informace o sestavení pro každý soubor, udržuje informace o integraci se systémy správy zdrojového kódu a pomáhá s uspořádáním do logické součásti vaší aplikace. Pracovního prostoru související informace, jako je v seznamu nainstalovaných balíčků, ale jsou udržovány odděleně v pracovní prostor.

Projekty jsou vždy spravované v rámci sady Visual Studio *řešení*, který může obsahovat libovolný počet projektů, které lze odkazovat navzájem. Zobrazit [používat více typů projektů v sadě Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Vytvoření nového projektu R

1. Spusťte Visual Studio.
1. Zvolte **soubor > Nový > projekt...** (**Ctrl**+**Shift**+**N**)
1. Vyberte "projekt R" v rámci **šablony > R**, dejte projektu název a umístění a pak vyberte **OK**:

    ![Dialogové okno Nový projekt pro R v sadě Visual Studio (RTVS v VS2017)](media/getting-started-01-new-project.png)

Tento příkaz vytvoří projekt s prázdnou *skriptu. R* soubor je otevřen v editoru. Všimněte si také v **Průzkumníka řešení** existují dva další soubory v projektu:

![Obsah R projektu ze šablony](media/projects-template-results.png)

*. Rhistory* libovolné příkazy po uzavření [interaktivní R](interactive-repl-for-r-in-visual-studio.md) okna. Můžete otevřít okno vyhrazené historie s **nástroje R** > **Windows** > **historie** příkazu. Toto okno obsahuje položky panelu nástrojů tlačítko a kontextové nabídky vymazat obsah historie.

*Rproject.rproj* souboru udržuje určitá nastavení projektu R konkrétní, které jinak nejsou spravovány nástrojem Visual Studio:

| Vlastnost | Výchozí | Popis |
| --- | --- | --- |
| Version | 1.0 | Verze nástrojů R pro Visual Studio používá k vytvoření projektu. |
| RestoreWorkspace | Výchozí | Automaticky načíst předchozí proměnné pracovního prostoru z `.RData` soubor v adresáři projektu. |
| SaveWorkspace | Výchozí | Uložit aktuální pracovní prostor proměnné `.RData` soubor do adresáře projektu při zavření projektu. |
| AlwaysSaveHistory | Výchozí | Uložit aktuální interaktivní okno historie `.RHistory` soubor do adresáře projektu při zavření projektu. |
| EnableCodeIndexing | Ano | Určuje, jestli se má spustit úlohu na pozadí indexing urychlení vyhledávání kódu. |
| UseSpacesForTab | Ano | Určuje, jestli se má vložit mezery (Ano) nebo znak tabulátoru (žádné) v případě **kartu** stisknutí klávesy v editoru. |
| NumSpacesForTab | 2 | Počet mezer pro vložení Pokud UseSpacesForTab je Ano. |
| Kódování | UTF-8 | Výchozí kódování pro `.R` soubory. |
| RnwWeave | Sweave | Balíček pro použití při tkaní Rnw souboru. |
| LaTeX | pdfLaTeX | Knihovna má použít při převodu RMarkdwon do formátu PDF. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Převod složky souborů do projektu jazyka R

Pokud máte existující složky *. R* soubory, které chcete spravovat v projektu, proveďte následující kroky:

1. Vytvoření nového projektu v sadě Visual Studio jako v předchozí části.
1. Zkopírujte soubory do složky projektu.
1. V Průzkumníku řešení Visual Studio, klikněte pravým tlačítkem na projekt, vyberte **přidat** > **ukončení položky**a přejděte k souborům, které chcete přidat. Tyto soubory se zobrazí ve stromu vašeho projektu po výběru **OK**.
1. Chcete-li uspořádat kód do podsložky, klikněte pravým tlačítkem na projekt, vyberte **přidat** > **novou složku** nejprve pak zkopírujte soubory do této složky a přidat tyto existující položky v kroku 3.

## <a name="project-properties"></a>Vlastnosti projektu

K otevření stránek vlastností projektu, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **vlastnosti**, nebo vyberte **projektu > vlastnosti (název projektu)** nabídky položka. Otevřeném okně zobrazí vlastnosti projektu:


| Tabulátor | Vlastnost | Popis | 
| --- | --- | --- | 
| Spustit | Spouštěcí soubor | Název souboru, který se spustí s **zdrojový soubor spouštěcí** příkazu **F5**, **ladění** > **spustit ladění**, nebo  **Ladění** > **spustit bez ladění**. Pravým tlačítkem soubor v projektu a výběrem **nastavit jako spouštěcí skript jazyka R** také nastaví jako spouštěcí soubor. | 
| | Resetovat při spuštění interaktivní R | Vymaže všechny proměnné z pracovního prostoru interaktivní okno při spuštění projektu. To provedete tak záruky existuje není žádný obsah pracovního prostoru plyne ze zbytkových zkontrolují běhů. | 
| | Cesta vzdáleného projektu | Cesta k vzdálený pracovní prostor. | 
| | Přenos souborů při spuštění | Určuje, zda soubory projektu, v souladu s filtr na **soubory k přesunu**, jsou zkopírovány do vzdálené pracovní prostor se každé spuštění. | 
| | Soubory k přesunu | Názvy souborů a zástupné znaky označující konkrétní soubory ke zkopírování do vzdáleného pracovního prostoru, pokud **přenos souborů při spuštění** zaškrtnuto. | 
| Nastavení | (Soubor Settings.R) | Nastavení projektu R pochází *Settings.R* nebo **. Settings.R* soubory, které jsou umístěné uvnitř projektu. Pokud není dostupný žádný soubor nastavení, můžete přidat proměnné, uložit na stránku a výchozí *Settings.R* soubor se vytvoří za vás. Můžete také přidat soubor nastavení projektu prostřednictvím **souboru** > **přidat novou položku** příkazu nabídky. <br/> Nastavení se ukládají jako kód R a soubor lze použít jako zdroj před spuštěním dalších modulů, tedy předem naplnění prostředí s předdefinovanými nastaveními. | 

## <a name="r-specific-project-commands"></a>Příkazy jazyka R specifický pro projekt

Projektů sady Visual Studio podporují několik obecných příkazů pomocí místní nabídky a **projektu** nabídky. Podrobnosti o těchto obecných možností naleznete v tématu [řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). Mějte na paměti, ale, že přidá do místní nabídky pro projekt R počet vlastní příkazy nástroje R pro Visual Studio (RTVS) a také soubory a složky v rámci projektu.

| Příkaz | Popis |
| --- | --- |
| Sada zde pracovní adresář | Nastaví R interaktivní okno pracovní adresář na složku projektu, který můžete použít také na všechny podsložky v rámci projektu. |
| Otevřít nadřazenou složku | Otevře se Průzkumník Windows v umístění vybraný soubor. |
| Přidat skript jazyka R | Vytvoří a otevře se nový *. R* s výchozím názvem souboru. Můžete také použít **přidat** > **nová položka** příkaz pro vytvoření *. R* soubory a také řadu dalších typů souborů. Zobrazit [šablony položek specifické pro R](#r-specific-item-templates). |
| Přidat R Markdown | Vytvoří a otevře se nové *.rmd* dokument s výchozím názvem. Můžete také použít **přidat** > **nová položka** příkaz pro vytvoření *.rmd* soubory a také řadu dalších typů souborů. Zobrazit [šablony položek specifické pro R](#r-specific-item-templates).  |
| Publikovat uložené procedury | Zahájí proces publikování žádné uložené procedury, které jsou součástí skripty jazyka R. Zobrazit [pracovat uložených procedur SQL serveru](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures). | 

## <a name="r-specific-item-templates"></a>Šablony položek specifické pro R

RTVS obsahuje několik šablon pro určité typy souborů. Přístup k šablony pravým tlačítkem myši projekt R a výběrem **přidat** > **nová položka**, tak, že vyberete **projektu**  >   **Přidat novou položku**, nebo pomocí **souboru** > **nový** > **souboru** a vyberete **R** kartu. Nejlepší způsob, jak prozkoumat šablony je vytvořit nový projekt a vložit soubory každého typu.

> [!Note]
> **Přidat** > **nová položka** příkazy také zobrazit typy obecné souborů, které nejsou uvedené v tabulce; **souboru** > **nový**   >  **Souboru** tyto typy jsou obsaženy místo toho na **Obecné** kartu.

| Typ souboru | Popis |
| --- | --- |
| Skript jazyka R | Textový soubor, který obsahuje stejné příkazy, které mohou být zadány v příkazovém řádku R. |
| R Markdown | Soubor obsahující [R Markdown](rmarkdown-with-r-in-visual-studio.md) dokumentu. |
| Nastavení jazyka R | Soubor, který obsahuje nastavení aplikace r. | 
| Dokumentace R | Obecný soubor dokumentace R obsahující pouze název, aliasu a názvu pole. |
| Dokumentace R (funkce) | Soubor dokumentace R obsahující velký počet polí s komentáři pro popis funkce. |
| Dokumentace R (datová sada) | Soubor dokumentace R obsahující velký počet polí s komentáři popisující datové sady. |
| Příkaz jazyka SQL | A prázdné *.sql* souboru. Zobrazit [fungují s SQL serverem a R](integrating-sql-server-with-r.md). |
| Uložená procedura s jazykem R | Soubor R s podřízený dotaz SQL a podřízené uložené procedury souboru šablony. Zobrazit [fungují s SQL serverem a R](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Použití více typů projektů v sadě Visual Studio

Řešení sady Visual Studio poskytují vhodné místo pro shromažďování a řídit související projekty na jednom místě logický. Řešení zajistit, aby byl váš kód uspořádané a usnadňuje spolupráci v rámci týmů.

V následujícím příkladu řešení obsahuje projekt R s modelem vytvořené pomocí R a Azure Machine Learning, projektu Pythonu, scikit informace, projekt C++ obsahující moduly pro náročné na výpočetní prací, projektu pro správu dat na SQL a Python/Bottle projekt pro web, který publikuje výsledek:

![Visual Studio Průzkumník řešení zobrazující několik souvisejících projektů v řešení](media/projects-polyglot.png)

Zvýrazněná tučné písmo projekt je projekt "spuštění" pro řešení; Chcete-li ji změnit, klikněte pravým tlačítkem na jiný projekt a vyberte **nastavit jako spouštěný projekt**.

> [!Note]
> V současné době není k dispozici žádné explicitní R C#/C++ jazyková integrace na místě (jako je Python, naleznete v tématu [vytvoření rozšíření C++ pro Python](../python/working-with-c-cpp-python-in-visual-studio.md)).  Existují ale knihoven, které poskytují C# a C++ přemostění pro jazyk R.

Další informace o správě obecně projekty a řešení, najdete v části [řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).
