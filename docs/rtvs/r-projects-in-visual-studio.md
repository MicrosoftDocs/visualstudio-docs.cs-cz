---
title: Projekty v R
description: Jak v aplikaci Visual Studio vytvořit projekty správce R, včetně vlastností, příkazů projektu a šablon.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: bcdef95935c0522c8b93a972d7f44fbd7632c53b
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409635"
---
# <a name="create-r-projects-in-visual-studio"></a>Vytváření projektů R v aplikaci Visual Studio

Projekt R (soubor *. RXPROJ* ) identifikuje všechny zdrojové a obsahové soubory přidružené k vašemu projektu. Obsahuje také informace o sestavení pro každý soubor, uchovává informace pro integraci se systémy správy zdrojového kódu a pomáhá organizovat aplikace do logických komponent. Informace související s pracovním prostorem, jako je například seznam nainstalovaných balíčků, se ale uchovávají samostatně v samotném pracovním prostoru.

Projekty jsou vždy spravovány v rámci *řešení*sady Visual Studio, které mohou obsahovat libovolný počet projektů, které mohou odkazovat na sebe navzájem. Viz [použití více typů projektů v aplikaci Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Vytváří se nový projekt R.

1. Otevřete sadu Visual Studio.
1. Zvolit **soubor > nový > projekt** (**Ctrl**+**SHIFT**+**N**)
1. V části **šablony** > **r**vyberte "projekt r", zadejte název a umístění projektu a vyberte **OK**:

    ![Dialogové okno Nový projekt pro R v aplikaci Visual Studio (RTVS v VS2017)](media/getting-started-01-new-project.png)

Tento příkaz vytvoří projekt s prázdným *skriptem. Soubor R* otevřený v editoru. Všimněte si také **Průzkumník řešení** v projektu existují dva další soubory:

![Obsah projektu R vytvořeného z šablony](media/projects-template-results.png)

Rozhraní *. Rhistory* zaznamenává jakékoli příkazy, které zadáte do okna [interaktivní R](interactive-repl-for-r-in-visual-studio.md) . Můžete otevřít vyhrazené okno historie pomocí **nástrojů R** > příkazu **Windows** > **history** . Toto okno má tlačítko panelu nástrojů a položky kontextové nabídky k vymazání obsahu historie.

Soubor *rproject. rproj* uchovává určitá nastavení projektu specifická pro R, která nejsou jinak spravovaná pomocí sady Visual Studio:

| Vlastnost | Výchozí | Popis |
| --- | --- | --- |
| Verze | 1.0 | Verze Nástroje R pro Visual Studio použitá k vytvoření projektu. |
| RestoreWorkspace | Výchozí | Automaticky načte předchozí proměnné pracovního prostoru ze souboru `.RData` v adresáři projektu. |
| SaveWorkspace | Výchozí | Uloží aktuální proměnné pracovního prostoru do souboru `.RData` v adresáři projektu při zavření projektu. |
| AlwaysSaveHistory | Výchozí | Při zavření projektu uloží aktuální interaktivní historii okna do souboru `.RHistory` v adresáři projektu. |
| EnableCodeIndexing | Ano | Určuje, zda se má spustit úloha indexování na pozadí, aby se urychlilo vyhledávání v kódu. |
| UseSpacesForTab | Ano | Určuje, zda mají být při stisknutí klávesy **TAB** v editoru vloženy mezery (Ano) nebo znak tabulátoru (ne). |
| NumSpacesForTab | 2 | Počet mezer, které se mají vložit, pokud je UseSpacesForTab Ano |
| Kódování | UTF-8 | Výchozí kódování pro soubory `.R`. |
| RnwWeave | Sweave | Balíček, který se má použít při tkaní souboru RNW |
| LaTeX | pdfLaTeX | Knihovna, která se má použít při převodu RMarkdown do formátu PDF |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Převod složky souborů na projekt R

Máte-li existující složku *. Soubory R* , které chcete spravovat v projektu, proveďte následující kroky:

1. V aplikaci Visual Studio vytvořte nový projekt jako v předchozí části.
1. Zkopírujte soubory do složky projektu.
1. V aplikaci Visual Studio Průzkumník řešení klikněte pravým tlačítkem myši na projekt, vyberte **přidat** > **existující položku**a vyhledejte soubory, které chcete přidat. Tyto soubory se zobrazí ve stromové struktuře projektu po výběru **OK**.
1. Chcete-li organizovat kód do podsložek, klikněte pravým tlačítkem myši na projekt, vyberte možnost **přidat** > **novou složku** a potom zkopírujte soubory do této složky a přidejte tyto existující položky v kroku 3.

## <a name="project-properties"></a>Vlastnosti projektu

Chcete-li otevřít stránky vlastností projektu, klikněte pravým tlačítkem myši na projekt v **Průzkumník řešení** a vyberte možnost **vlastnosti**, nebo vyberte položku nabídky **Vlastnosti projektu > (název projektu)** . Okno, které se otevře, zobrazí vlastnosti projektu:

| Tabulátor | Vlastnost | Popis |
| --- | --- | --- |
| Spusťte | Spouštěcí soubor | Název souboru, který se spouští s příkazem **zdrojového spouštěcího souboru** , **F5**, **ladění** > **Spustit ladění**nebo **ladění** > **Spustit bez ladění**. Kliknutím pravým tlačítkem myši na soubor v projektu a výběrem možnosti **nastavit jako spouštěcí skript R** se nastaví také jako spouštěcí soubor. |
| | Resetovat Interaktivní R při spuštění | Vymaže všechny proměnné z pracovního prostoru interaktivního okna při spuštění projektu. Tím zajistíte, že nebudete mít k dispozici žádný reziduální obsah pracovního prostoru z zkontrolují. |
| | Cesta ke vzdálenému projektu | Cesta ke vzdálenému pracovnímu prostoru. |
| | Přenos souborů při spuštění | Označuje, zda jsou soubory projektu, které podléhají filtru v **souborech k přenosu**, zkopírovány do vzdáleného pracovního prostoru s každým spuštěním. |
| | Soubory k přenosu | Názvy souborů a zástupné znaky označující konkrétní soubory, které se mají zkopírovat do vzdáleného pracovního prostoru, pokud je vybraná možnost **přenést soubory při spuštění** . |
| Nastavení | (Soubor nastavení. R) | Nastavení projektu r přichází z *nastavení. r* nebo * *. Soubory. R nastavení* , které se nacházejí v projektu. Pokud není k dispozici žádný soubor nastavení, můžete přidat proměnné, Uložit stránku a výchozí *nastavení. soubor R* se vytvoří. Soubor nastavení můžete do projektu přidat také pomocí příkazu **soubor** > **Přidat novou položku** nabídky. <br/> Nastavení se ukládají jako kód R a soubor se dá před spuštěním jiných modulů naplnit, takže se předem naplní prostředí s předdefinovaným nastavením. |

## <a name="r-specific-project-commands"></a>Příkazy projektu specifické pro R

Projekty sady Visual Studio podporují několik obecných příkazů prostřednictvím nabídky po kliknutí pravým tlačítkem myši a nabídky **projekt** . Podrobnosti o těchto obecných možnostech naleznete v tématu [řešení a projekty v aplikaci Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). Nezapomeňte však, že Nástroje R pro Visual Studio (RTVS) přidá do nabídky po kliknutí pravým tlačítkem myši mnoho vlastních příkazů pro projekt R a také soubory a složky v rámci projektu.

| Příkaz | Popis |
| --- | --- |
| Sem nastavte pracovní adresář. | Nastaví pracovní adresář okna Interaktivní R do složky projektu, která se dá použít i na jakékoli podsložce v rámci projektu. |
| Otevřít nadřazenou složku | Otevře Průzkumníka Windows v umístění vybraného souboru. |
| Přidat skript jazyka R | Vytvoří a otevře nový *. Soubor R* s výchozím názvem. K vytvoření můžete použít také příkaz **přidat** > **novou položku** *. Soubory R* a také mnoho dalších typů souborů. Viz [šablony položek specifické pro jazyk R](#r-specific-item-templates). |
| Přidat R Markdown | Vytvoří a otevře nový dokument *. rmd* s výchozím názvem. Pomocí příkazu **přidat** > **novou položku** můžete také vytvářet soubory *. rmd* a také řadu dalších typů souborů. Viz [šablony položek specifické pro jazyk R](#r-specific-item-templates).  |
| Publikovat uložené procedury | Spustí proces publikování všech uložených procedur obsažených ve skriptech jazyka R. Viz [práce s uloženými procedurami SQL Server](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures). |

## <a name="r-specific-item-templates"></a>Šablony položek specifické pro R

RTVS obsahuje několik šablon pro konkrétní typy souborů. Přistupujete k šablonám kliknutím pravým tlačítkem myši na projekt R a vybráním možnosti **přidat** > **novou položku**, vybráním možnosti **projekt** > **Přidat novou položku**nebo pomocí **souboru** > **Nový** **soubor** > a výběrem karty **R** . Nejlepším způsobem, jak prozkoumat šablonu, je vytvořit nový projekt a vložit soubory každého typu.

> [!Note]
> Příkazy **přidat** > **nové položky** zobrazují také obecné typy souborů, které nejsou uvedeny v tabulce. se **souborem** > **Nový** **soubor** > tyto typy jsou obsaženy místo na kartě **Obecné** .

| Typ souboru | Popis |
| --- | --- |
| Skript jazyka R | Textový soubor, který obsahuje stejné příkazy, které lze zadat na příkazovém řádku R. |
| R Markdown | Soubor obsahující dokument [R Markdown](rmarkdown-with-r-in-visual-studio.md) . |
| Nastavení R | Soubor, který obsahuje nastavení aplikace R. |
| Dokumentace R | Obecný soubor dokumentace R obsahující pouze pole název, alias a název. |
| Dokumentace R (funkce) | Soubor dokumentace R obsahující mnoho polí s komentáři pro popis funkce. |
| Dokumentace R (datová sada) | Soubor dokumentace R obsahující mnoho polí s komentáři pro popis datové sady. |
| Dotaz SQL | Prázdný soubor *. SQL* . Viz [práce s SQL Server a R](integrating-sql-server-with-r.md). |
| Uložená procedura s jazykem R | Soubor R s podřízeným dotazem SQL a souborem šablony podřízené uložené procedury. Viz [práce s SQL Server a R](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Použití více typů projektů v aplikaci Visual Studio

Řešení sady Visual Studio poskytují vhodné místo pro shromažďování a správu souvisejících projektů na jednom logickém místě. Řešení pomáhají zajistit organizování kódu a usnadňují spolupráci v rámci týmů.

V následujícím příkladu obsahuje řešení projekt R s modelem sestaveným pomocí R a Azure Machine Learning, projektem Python/scikit-učení, C++ projektem obsahujícím moduly pro náročné výpočetní práci, projekt SQL pro správu dat a projekt Python/láhev pro web, který publikuje výsledek:

![Visual Studio Průzkumník řešení znázorňující více souvisejících projektů v řešení](media/projects-polyglot.png)

Projekt zvýrazněný tučným písmem je "spouštěným" projektem řešení. Pokud ho chcete změnit, klikněte pravým tlačítkem myši na jiný projekt a vyberte **nastavit jako spouštěný projekt**.

> [!Note]
> V současné době není k dispozici žádná explicitní C#integraceC++ R to/Language (protože je pro Python k dispozici), přečtěte si téma [vytvoření C++ rozšíření pro Python](../python/working-with-c-cpp-python-in-visual-studio.md).  Existují však dostupné knihovny, které poskytují C# a C++ předávají mosty pro R.

Další informace o tom, jak obecně spravovat projekty a řešení, naleznete v tématu [řešení a projekty v aplikaci Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).
