---
title: Ukázkové projekty R
description: Index kolekce vzorků, které můžete začít s R a Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: ef3316d929b00203815918a656568f75571e954e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75843824"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>Nástroje R pro ukázkové projekty sady Visual Studio

Tato kolekce ukázek vás spustí na R, R Tools for Visual Studio (RTVS) a Microsoft Machine Learning Server:

1. Stáhněte si [ukázky zip soubor](https://github.com/Microsoft/RTVS-docs/archive/master.zip) a extrahovat do složky dle vašeho výběru.
1. Chcete-li `examples/Examples.sln` zobrazit dvě složky v projektu, otevřete:

    - *První pohled na R* dává jemný úvod pro nováčky do R.
    - *MRS a Machine Learning* uvádí příklady, jak používat R a Microsoft Machine Learning Server pro strojové učení.

## <a name="a-first-look-at-r"></a>První pohled na R

Tato ukázka poskytuje podrobný úvod do R prostřednictvím rozsáhlé komentáře ve dvou zdrojových souborů. Chcete-li dosáhnout nejlepšího přístupu, umístěte kurzor do horní části souboru a stisknutím kombinace kláves Ctrl+Enter odešlete kód řádek po lži do okna **Interaktivní R.** (Řádky, které instalují balíčky, mohou trvat minutu nebo dvě.)

- `1-Getting Started with R.R`zahrnuje mnoho základů R, včetně použití balíčků, načítání a analýzy dat a vykreslování.

    ![Příklad výstupu z ukázky 1-Začínáme s r.r.](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R`představuje grafický balíček ggplot2 známý svými vizuálně přitažlivými obrázky a jednoduchou syntaxí. Tento příklad vizualizuje data zemětřesení z Fidži.

    ![Příklad výstupu z 2-Úvod na ggplot2. Ukázka R](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Microsoft Machine Learning Server a Machine Learning

Tato kolekce příkladů ukazuje, jak pomocí r vytvořit modely strojového učení a využít microsoft [machine learning server](/machine-learning-server/what-is-machine-learning-server).

Stejně jako u všech příkladů otevřete soubor, umístěte kurzor nahoře a potom krokujte kódem řádek po řádku s **klávesou Ctrl**+**Enter**. Soubory markdownu v každé složce také obsahují další podrobnosti.

- `Benchmarks`spustí řadu intenzivních, paralelních výpočtů lineární algebry, které ukazují zvýšení výkonu, které jsou možné pomocí Microsoft R Open a Knihovny jádra Intel Math (MKL). U simulovaných dat benchmarky konkrétně porovnávají maticové výpočty na jednom vlákně oproti dvěma.

    ![Příklad srovnávacího grafu](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS`vytvoří model prognózy poptávky pro zapůjčení jízdních kol na základě historické sady dat pomocí serveru Microsoft ML Server.

- `Data_Exploration`obsahuje tři skripty:

  - `Import Data from URL.R`ukazuje, jak načíst datový soubor označený adresou URL do R.
  - `Import Data from URL to xdf.R`ukazuje, jak načíst datový soubor označený adresou URL do serveru Microsoft ML Server jako xdf.
  - `Using ggplot2.R`je rozšíření `A First Look at R/2-Introduction to ggplot2.R` vzorku, což poskytuje rozsáhlejší prohlídku funkce ggplot2 včetně interaktivního 3D vykreslování.

      ![Výstup použití ggplot2. Příklad R](media/samples-3d-interactive.png)

- `Datasets`obsahuje tři *soubory .csv* používané jinými ukázkami
- `Flight_Delays_Prediction_with_R`a `Flight_Delays_Prediction_with_MRS` ukazuje, jak předpovědět zpoždění letů pomocí R, strojového učení a historických údajů o výkonu a počasí v čase.
- `Machine learning`obsahuje tři ukázky pro učení předpovědět zpoždění letů, ceny bydlení a půjčovny kol. Společně tyto ukázky ukazují použití R a Microsoft ML Server na skutečné problémy. Také vám ukážou, jak používat několik oblíbených modelů strojového učení a nasadit je jako webovou službu Azure pomocí pracovního prostoru [Azure Machine Learning.](https://azure.microsoft.com/services/machine-learning/)

- `R_MRO_MRS_Comparison`je šestidílné porovnání, které ukazuje podobnosti a rozdíly R, Microsoft R Open a Microsoft ML Server s příkazy, syntaxe, konstrukce a výkon.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>Co je zvláštního na microsoft r open a microsoft ml server?

[Microsoft R Open](https://mran.revolutionanalytics.com/download/), Microsoft distribuce R, se liší od [CRAN R](https://cran.r-project.org/) dvěma důležitými způsoby:

1. [Lepší výpočetní výkon](https://mran.revolutionanalytics.com/rro/#intelmkl1) při použití s [knihovnami intel math jádra](https://software.intel.com/intel-mkl). Knihovny jsou k dispozici ke stažení zdarma od společnosti Microsoft pro použití s Microsoft R Open.

1. [Reprodukovatelný R Toolkit](https://mran.revolutionanalytics.com/rro/#reproducibility) zajišťuje, že knihovny, které jste použili k sestavení programu R jsou vždy k dispozici ostatním, kteří chtějí reprodukovat vaši práci.

[Microsoft ML Server (MLS)](/machine-learning-server/what-is-machine-learning-server) je rozšíření R, které umožňuje zpracovávat více dat a zpracovat je rychleji. To dává R dvě výkonné schopnosti:

1. Větší datové sady bez omezení paměti RAM. ML Server může zpracovávat data z různých zdrojů, včetně clusterů Hadoop, databází a datových skladů.

1. Paralelní vícejádrové zpracování. MLS může efektivně distribuovat výpočty mezi všechny výpočetní prostředky, které má k dispozici. Na vaší osobní pracovní stanici nebo vzdáleném clusteru mls dostane odpověď rychleji.

Následující srovnání ukazuje, že MLS a MRO s MKL mají výrazně lepší výpočetní výkon související s určitým výpočtem matice než R a MRO bez MKL. V tomto výpočtu se používají simulovaná data:

![Porovnání MLS a MRO s MKL s R a MRO bez MKL](media/samples-speed-comparison.png)

Pro technické srovnání R s MRO a MLS, podívejte se [lixun Zhang je podrobná diskuse](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) na toto téma.

Následující obrázek pak porovná uplynulý čas v sekundách použitých při vytváření logistických regresní modelů, aby předpověděl zpoždění letu větší než 15 minut.  Uplynulý čas použitý v CRAN R se dramaticky zvyšuje při zvýšení malého počtu řádků, zatímco MLS se zvyšuje pouze přibližně dvakrát. Podrobnosti o tomto benchmarku najdete v *benchmarkech/rxGlm_benchmark. Příklad R.*

![rxGlm benchmark](media/samples-rxGLM-benchmark.png)
