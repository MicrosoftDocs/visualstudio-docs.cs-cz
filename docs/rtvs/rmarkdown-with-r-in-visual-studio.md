---
title: R Markdown
description: Postup vytváření R Markdown dokumentů v aplikaci Visual Studio pro tvorbu vysoce kvalitních sestav, prezentací a řídicích panelů.
ms.date: 11/16/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 4e74966e71a7d440aed918e8aa609eeb8e68c355
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851878"
---
# <a name="create-r-markdown-documents"></a>Vytváření dokumentů R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) je formát dokumentu, který slouží k analýze analýz v R na vysoce kvalitní dokumenty, sestavy, prezentace a řídicí panely.

Nástroje R pro Visual Studio (RTVS) poskytuje šablonu R Markdown položky, editor podporuje Editor (včetně IntelliSense pro kód R v editoru), možnosti generování souborů a živý náhled.

## <a name="using-r-markdown"></a>Použití R Markdown

1. Zavřete Visual Studio.
1. (Jednorázově) Nainstalujte `pandoc` z [pandoc.org](https://pandoc.org/installing.html).
1. Restartujte aplikaci Visual Studio, která by měla vyzvednout instalaci pandoc.
1. Nainstalujte `knitr` balíčky a `rmarkdown` , které můžete provést z [interaktivního okna](interactive-repl-for-r-in-visual-studio.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. Vytvořte nový soubor R Markdown pomocí příkazu nabídky **soubor**  >  **Nový**  >  **soubor** a vyberte **R**  >  **R Markdown** ze seznamu. V kontextu projektu klikněte pravým tlačítkem na projekt v Průzkumník řešení a vyberte **Přidat R Markdown** (nebo **Přidat**  >  **novou položku** a vybrat **R Markdown** ze seznamu).

1. Výchozí obsah nového souboru je následující:

    <!-- markdownlint-disable MD048 -->
    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you select the **R Tools | Publish | Preview** button, a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~
    <!-- markdownlint-disable MD048 -->

## <a name="previews"></a>Náhledy

Visual Studio 2017 verze 15,5 a novější automaticky poskytuje živý náhled pro R Markdown. Chcete-li zapnout automatickou synchronizaci mezi editorem a verzí Preview, vyberte možnost **R nástroje**  >  **Markdownu**  >  **Automatická synchronizace** (**CTRL** + **SHIFT** + **Y**). Pokud nepoužíváte automatickou synchronizaci, můžete aktualizovat verzi Preview pomocí **nástrojů R**  >  **Markdownu**  >  **znovu načíst R Markdown Preview**.

Můžete také zobrazit náhled souboru ve formátech HTML, PDF a Microsoft Word tak, že kliknete pravým tlačítkem myši na Editor a vyberete jeden z příkazů ve **verzi Preview** . Stejné příkazy jsou také k dispozici v nabídce Markdownu **nástrojů jazyka R**  >   . (V dřívějších verzích sady Visual Studio tyto příkazy najdete v **nástrojích**  >  jazyka R Nabídka **publikovat** .)

![RMarkdown Live Preview a další příkazy nabídky Preview](media/rmarkdown-live-preview.png)
