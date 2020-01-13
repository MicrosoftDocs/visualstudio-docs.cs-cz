---
title: Ukázkové projekty R
description: Index kolekce ukázek, které vám pomohou začít s R a sadou Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: ef3316d929b00203815918a656568f75571e954e
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75843824"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>Ukázkové projekty Nástroje R pro Visual Studio

Tato kolekce ukázek vám pomůže začít pracovat s R, Nástroje R pro Visual Studio (RTVS) a Microsoft Machine Learning Server:

1. Stáhněte si [soubor zip s ukázkami](https://github.com/Microsoft/RTVS-docs/archive/master.zip) a extrahujte ho do složky podle vašeho výběru.
1. Otevřete `examples/Examples.sln` pro zobrazení dvou složek v projektu:

    - *První pohled na r* poskytuje mírné představení Newcomers do jazyka r.
    - *Paní a Machine Learning* poskytuje příklady použití R a Microsoft Machine Learning Server pro Machine Learning.

## <a name="a-first-look-at-r"></a>První pohled na R

Tato ukázka poskytuje podrobný Úvod k R prostřednictvím rozsáhlých komentářů ve dvou zdrojových souborech. Pro dosažení co nejlepších výsledků umístěte kurzor do horní části souboru a stisknutím kombinace kláves CTRL + ENTER odešlete řádek kódu do okna **interaktivní R** . (Řádky, které instalují balíčky, mohou trvat minutu nebo dvě.)

- `1-Getting Started with R.R` pokrývá mnoho základních základů jazyka R, včetně použití balíčků, načítání a analýzy dat a vykreslování.

    ![Příklad výstupu z 1 Začínáme s ukázkou R.R](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` zavádí ggplot2 grafický balíček známý pro jeho vizuální odvolání a jednoduchou syntaxi. Tento příklad vizualizuje zemětřesení data ze Fidži.

    ![Příklad výstupu z 2 – Úvod do ggplot2. Ukázka R](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Microsoft Machine Learning Server a Machine Learning

V této kolekci příkladů se dozvíte, jak pomocí jazyka R vytvořit modely strojového učení a využít výhod [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

Stejně jako ve všech příkladech otevřete soubor, umístěte kurzor do horní části a poté proveďte krok kódu řádek po řádku se **stisknutou klávesou Ctrl**+**ENTER**. Soubory Markdownu v každé složce také obsahují další podrobnosti.

- `Benchmarks` spouští spoustu náročných a paralelních výpočtů algebraický, které znázorňují zvýšení výkonu, které je možné díky použití Microsoft R Open a knihovny Intel Math kernel Library (MKL). U simulovaných dat srovnávací testy specificky porovnávají výpočty matice na jednom vlákně oproti dvěma.

    ![Ukázkový srovnávací diagram](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` vytvoří model předpovědi poptávky pro nájemné za kolo na základě historické sady dat pomocí Microsoft ML Server.

- `Data_Exploration` obsahuje tři skripty:

  - `Import Data from URL.R` ukazuje, jak načíst datový soubor označený adresou URL do jazyka R.
  - `Import Data from URL to xdf.R` ukazuje, jak načíst datový soubor identifikovaný adresou URL do Microsoft ML Server jako XDF.
  - `Using ggplot2.R` je rozšíření `A First Look at R/2-Introduction to ggplot2.R` Sample a poskytuje komplexnější přehled funkcí ggplot2's, včetně interaktivního vykreslování 3D.

      ![Výstup s použitím ggplot2. Příklad R](media/samples-3d-interactive.png)

- `Datasets` obsahuje tři soubory *. csv* používané jinými ukázkami.
- `Flight_Delays_Prediction_with_R` a `Flight_Delays_Prediction_with_MRS` ukazují, jak předpovědět zpoždění letů pomocí R, strojového učení a historických dat o počasí v čase.
- `Machine learning` obsahuje tři ukázky pro učení, jak předpovědět zpoždění letů, ceny za ubytování a nájemné za kolo. Tyto ukázky společně ukazují aplikaci R a Microsoft ML Server k problémům v reálném světě. Také ukazují, jak používat několik oblíbených modelů strojového učení a nasazovat je jako webovou službu Azure pomocí [Azure Machine Learningho](https://azure.microsoft.com/services/machine-learning/) pracovního prostoru.

- `R_MRO_MRS_Comparison` je porovnání šesti částí, které zobrazuje podobnosti a rozdíly v R, Microsoft R Open a Microsoft ML Server s příkazy, syntaxí, konstrukcemi a výkonem.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>Co je zvláštní informace o Microsoft R Open a Microsoft ML Server?

[Microsoft r Open](https://mran.revolutionanalytics.com/download/), distribuce r od Microsoftu se liší od [Cran r](https://cran.r-project.org/) dvěma důležitými způsoby:

1. [Lepší výpočetní výkon](https://mran.revolutionanalytics.com/rro/#intelmkl1) při použití s [knihovnami pro matematické jádro Intel](https://software.intel.com/intel-mkl) Knihovny jsou k dispozici jako bezplatné stažení od Microsoftu pro použití s Microsoft R Open.

1. [Reprodukovatelné sady r Toolkit](https://mran.revolutionanalytics.com/rro/#reproducibility) zajistí, že knihovny, které jste použili k sestavení programu r, jsou vždy k dispozici ostatním uživatelům, kteří chtějí reprodukovat svou práci.

[Microsoft ml Server (MLS)](/machine-learning-server/what-is-machine-learning-server) je rozšíření jazyka R, které umožňuje zpracovávat více dat a urychlit jejich zpracování. Poskytuje R dvě výkonné možnosti:

1. Větší datové sady bez omezení paměti RAM. ML Server může zpracovávat data z různých zdrojů, včetně clusterů Hadoop, databází a datových skladů.

1. Paralelní zpracování více jader. MLS může efektivně distribuovat výpočty ve všech výpočetních prostředcích, které jsou k dispozici. V osobní pracovní stanici nebo ve vzdáleném clusteru MLS získá odpověď rychleji.

Následující porovnání znázorňuje, že MLS a MRO s MKL významně lepší výpočetní výkon, který souvisí s určitým výpočtem matrice než R a MRO bez MKL. V tomto výpočtu se používají Simulovaná data:

![Porovnávání MLS a MRO s MKL a MRO bez MKL](media/samples-speed-comparison.png)

Pro účely technického porovnání jazyka R s MRO a MLS si Projděte [podrobný popis Lixun Zhang](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) v tématu.

Následující obrázek porovná uplynulý čas v sekundách, který se používá při vytváření logistických regresních modelů pro předpověď zpoždění letu, který je větší než 15 minut.  Uplynulý čas používaný v CRAN R se výrazně zvyšuje při zvýšení malého počtu řádků, zatímco MLS se zvyšuje jenom přibližně dvakrát. Podrobnosti o tomto srovnávacím testu najdete na základě *srovnávacích testů/rxGlm_benchmark. Příklad R* .

![srovnávací rxGlm](media/samples-rxGLM-benchmark.png)
