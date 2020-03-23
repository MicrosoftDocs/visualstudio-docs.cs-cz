---
title: R Markdown
description: Jak vytvořit dokumenty R Markdown v sadě Visual Studio pro vytváření vysoce kvalitních sestav, prezentací a řídicích panelů.
ms.date: 11/16/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 32cfabfe61a8c1dc8f04cd2d024b07a92b1eb7e2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72888562"
---
# <a name="create-r-markdown-documents"></a>Vytvoření dokumentů R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) je formát dokumentu, který mění analýzu v R na vysoce kvalitní dokumenty, sestavy, prezentace a řídicí panely.

Nástroje R pro Visual Studio (RTVS) poskytuje šablonu položky R Markdown, podporu editoru (včetně kódu IntelliSense for R v editoru), možnosti generování souborů a živý náhled.

## <a name="using-r-markdown"></a>Použití R Markdown

1. Zavřete Visual Studio.
1. (Pouze jednou) Instalace `pandoc` z [pandoc.org](https://pandoc.org/installing.html).
1. Restartujte visual studio, které by mělo vyzvednout instalaci pandoc.
1. Nainstalujte `knitr` `rmarkdown` a balíčky, které můžete udělat z [interaktivního okna](interactive-repl-for-r-in-visual-studio.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. Vytvořte nový soubor R Markdown pomocí příkazu nabídky **Soubor** > **nový** > **soubor** a vyberte ze seznamu **r** > **R Markdown.** V kontextu projektu klikněte pravým tlačítkem myši na projekt v Průzkumníku řešení a vyberte **přidat R Markdown** (nebo **Přidat** > **novou položku** a vybrat **R Markdown** ze seznamu).

1. Výchozí obsah nového souboru je následující:

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~

## <a name="previews"></a>Náhledy

Visual Studio 2017 verze 15.5 a novější automaticky poskytují živý náhled pro R Markdown. Chcete-li zapnout automatickou synchronizaci mezi editorem a náhledem, vyberte **možnost R Tools** > **Markdown** > **Automatic Sync** **(Ctrl**+**Shift**+**Y).** Pokud nepoužíváte automatickou synchronizaci, můžete náhled aktualizovat pomocí **nástroje R** > **Markdown** > **Znovu načíst R Markdown Preview**.

Můžete také zobrazit náhled souboru ve formátech HTML, PDF a Microsoft Word kliknutím pravým tlačítkem myši do editoru a výběrem jednoho z příkazů **náhledu.** Stejné příkazy jsou k dispozici také v nabídce **R Tools** > **Markdown.** (V dřívějších verzích sady Visual Studio se tyto příkazy nacházejí v nabídce**Publikování** **nástrojů** > Jazyka R.)

![Živý náhled RMarkdown a další příkazy nabídky náhledu](media/rmarkdown-live-preview.png)
