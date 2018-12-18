---
title: R Markdown
description: Postup vytvoření R Markdownu dokumenty v sadě Visual Studio k vytvoření vysoce kvalitní sestav, prezentací a řídicí panely.
ms.date: 11/16/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 1bb6779e0e8174dd10f209d9825ffb861d00455d
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238320"
---
# <a name="create-r-markdown-documents"></a>Vytváření dokumentů R Markdownu

[R Markdownu](https://rmarkdown.rstudio.com/) je dokument formátu, který se zobrazí analýzy v R vysoce kvalitní dokumentů, sestav, prezentací a řídicí panely.

R Tools pro Visual Studio (RTVS) poskytuje šablony položky R Markdownu, editor podporují (včetně IntelliSense pro R kódu v editoru), možnosti generování souboru a live preview.

## <a name="using-r-markdown"></a>Pomocí Markdownu R

1. Zavřete Visual Studio.
1. (Pouze jednou) Nainstalujte `pandoc` z [pandoc.org](http://pandoc.org/installing.html).
1. Restartujte Visual Studio, který by měl vyzvednutí pandoc instalace.
1. Nainstalujte `knitr` a `rmarkdown` balíčků, které můžete provést z [interaktivních okna](interactive-repl-for-r-in-visual-studio.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Vytvoření nového souboru Markdownu R pomocí **soubor** > **nový** > **soubor** příkazu v nabídce a výběrem **R**  >  **R Markdownu** ze seznamu. V kontextu projektu, klikněte pravým tlačítkem na projekt v Průzkumníku řešení a vyberte **přidat Markdownu R** (nebo **přidat** > **novou položku** a výběrem **R Markdownu** ze seznamu).

1. Výchozí hodnotou tohoto nového souboru jsou následující:

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

## <a name="previews"></a>Preview verze

Visual Studio 2017 verze 15,5 a novější automaticky získávat živém náhledu pro R Markdownu. Chcete-li zapnout automatickou synchronizaci mezi editoru a ve verzi preview, vyberte **R nástroje** > **Markdownu** > **automatické synchronizace** ( **CTRL**+**Shift**+**Y**). Pokud nepoužíváte automatické synchronizace, můžete obnovit pomocí preview **R nástroje** > **Markdownu** > **opětovného načtení R Markdown Preview**.

Můžete také zobrazit náhled souboru ve formátu HTML, PDF, a aplikace Microsoft Word formátuje v editoru pravým tlačítkem myši a výběrem jedné z **Preview** příkazy. Stejné příkazy jsou také k dispozici na **R nástroje** > **Markdownu** nabídky. (V dřívějších verzích sady Visual Studio tyto příkazy se nacházejí na **R nástroje** > **publikovat** nabídky.)

![RMarkdown živém náhledu a další příkazy nabídky preview](media/rmarkdown-live-preview.png)
