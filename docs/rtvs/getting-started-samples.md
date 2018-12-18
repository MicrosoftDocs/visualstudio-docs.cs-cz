---
title: Ukázkové R projekty
description: Index kolekce ukázky začít pracovat s R a Visual Studio.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: adb26b3cf6097d830c899ef4ef251d2066b81a38
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238326"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>R Tools pro Visual Studio ukázkové projekty

Tato kolekce ukázek získá vám pomohou s R, R nástrojů pro Visual Studio (RTVS) a Microsoft Machine Learning Server:

1. Stažení [soubor zip ukázky](https://github.com/Microsoft/RTVS-docs/archive/master.zip) a extrahovat do složky podle svého výběru.
1. Otevřete `examples/Examples.sln` zobrazíte dvě složky v projektu:

    - *První pohled na R* dává jemného Úvod pro nové uživatele do R.
    - *Paní a Machine Learning* jsou uvedeny příklady použití R a Microsoft Machine Learning Server pro machine learning.

## <a name="a-first-look-at-r"></a>První pohled na R

Tato ukázka obsahuje podrobný Úvod do R prostřednictvím rozsáhlé komentáře ve dvou zdrojové soubory. Pro nejlepší prostředí, umístěte kurzor na začátek souboru a stiskněte klávesu Ctrl + Enter k odeslání kódu řádku podle polohu na **R interaktivní** okno. (Řádky, které instalují balíčky může trvat minutu nebo dvě k dokončení.)

- `1-Getting Started with R.R` Popisuje mnoho základy R, včetně použití balíčků, načítání a analýza dat a vykreslení.

    ![Příklad výstupu z 1 – Začínáme s ukázkou R.R](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` představuje grafické balíček ggplot2 známé pro jeho přitažlivé pozemcích a jednoduché syntaxe. Tento příklad vizualizuje zemětřesení data z Fiji.

    ![Příklad výstupu z 2úvod k ggplot2. Ukázka R](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Server Microsoft Machine Learning a Machine Learning

Tato kolekce příklady ukazuje, jak používat R k vytváření modelů machine learning a chcete využít výhod [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

Jako s všechny příklady, otevřete soubor, přesuňte kurzor na začátek a poté procházet kód řádek po řádku s **Ctrl**+**Enter**. Soubory markdown v každé složky také obsahují další podrobnosti.

- `Benchmarks` Získá počet algebra lineární náročné, paralelní výpočty zobrazíte výkonu, které spouští je možné prostřednictvím Microsoft R otevřené a knihovny pro jádra matematické Intel (MKL). Simulované daty srovnávací testy konkrétně porovnat výpočty matice na jedno vlákno versus dva.

    ![Příklad srovnávacího testu vykreslení.](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` Vytvoří model vyžádání předpovědi pro kolo pronájem na základě historických dat sady, pomocí Microsoft ML Server. 

- `Data_Exploration` obsahuje tři skriptů:

  - `Import Data from URL.R` ukazuje, jak načíst adresa URL identifikuje data do R.
  - `Import Data from URL to xdf.R` ukazuje, jak načíst adresa URL identifikuje data do Microsoft ML Server jako xdf.
  - `Using ggplot2.R` je rozšířením `A First Look at R/2-Introduction to ggplot2.R` vzorku, s rozsáhlejší prohlídku funkcí na ggplot2 včetně interaktivní 3D vykreslení.

      ![Výstup pomocí ggplot2. Příklad R](media/samples-3d-interactive.png)

- `Datasets` obsahuje tři *.csv* soubory používané Další ukázky
- `Flight_Delays_Prediction_with_R` a `Flight_Delays_Prediction_with_MRS` ukazuje, jak k předvídání zpoždění letů pomocí machine learning, která, počasí data a historie výkonu na čas a R. 
- `Machine learning` obsahuje tři ukázky kurzů k předvídání zpoždění letů, ustájení ceny a pronájem kolo. Společně tyto ukázky ukazují použití R a Microsoft ML Server skutečných problémů. Budou také ukazují, jak můžete použít několik oblíbených machine learning modely a nasadit jako k webové služby Azure pomocí [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/) pracovního prostoru.

- `R_MRO_MRS_Comparison` je součástí půl porovnání, které se zobrazuje podobnosti a rozdíly mezi R, Microsoft R otevřete a Microsoft ML Server příkazy, syntaxe, konstrukce a výkonu.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>Co je speciální o Microsoft R otevřete a Microsoft ML Server?

[Microsoft R otevřete](http://aka.ms/rtvs-r-open), se liší od společnosti Microsoft distribuce R, [CRAN r.](https://cran.r-project.org/) důležité dvěma způsoby:

1. [Vyšší výpočetní výkon](https://mran.revolutionanalytics.com/rro/#intelmkl1) při použití s [Intel matematické jádra knihovny](https://software.intel.com/intel-mkl). Knihovny jsou k dispozici jako zdarma ke stažení od společnosti Microsoft pro použití s Microsoft R otevřete.

1. [Sada nástrojů reprodukovatelnou R](https://mran.revolutionanalytics.com/rro/#reproducibility) zajistí, že knihovny, které jste použili k vytvoření vašeho programu R jsou vždy k dispozici jiným uživatelům, které mají vaši práci reprodukovat.

[ML serveru Microsoft (MLS)](/machine-learning-server/what-is-machine-learning-server) je rozšířením R, která umožňuje zpracovávat další data a zpracovat je rychlejší. Nabízí výkonné R dvě možnosti:

1. Větší datové sady bez omezení paměti RAM. ML Server může zpracovat z důvodu nedostatku paměti data z různých zdrojů, včetně clusterů Hadoop, databáze a datových skladů.

1. Více jader, paralelní zpracování. MLS můžete efektivně distribuovat výpočetní mezi všechny výpočetní prostředky, které má k dispozici. Na pracovní stanici osobní nebo vzdáleného clusteru získá MLS rychlejší odpověď.

Toto porovnání ukazuje, že MLS a MRO s MKL mají výrazně lepší výpočetní výkon související se určité matice výpočtu než R a MRO bez MKL. Simulované data se používají v tohoto výpočtu:

![Porovnání MLS a MRO s MKL r a MRO bez MKL](media/samples-speed-comparison.png)

Technické porovnání R s MRO a MLS, podívejte se na [Lixun Potokar podrobné diskusní](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) v tomto tématu.

Následující obrázek pak porovná uplynulý čas v sekundách použít při vytváření modelů Logistic Regression k předvídání zpoždění letů delší než 15 minut.  Uplynulý čas použít v CRAN r. zvyšuje výrazně zvýšit malý počet řádků, zatímco MLS zvyšuje pouze přibližně dvakrát. Podrobnosti o této srovnávacího testu, podívejte se *srovnávacích testů/rxGlm_benchmark. R* příklad.

![rxGlm srovnávacího testu](media/samples-rxGLM-benchmark.png)
