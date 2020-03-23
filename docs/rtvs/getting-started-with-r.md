---
title: Začínáme s kurzem R
description: Návod použití Jazyka R v sadě Visual Studio včetně vytváření projektu, interaktivního okna, úprav kódu a ladění.
ms.date: 06/29/2017
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: df46a2731f9923d85a16082f96c44947099db592
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "63000475"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Začínáme s nástroji R pro Visual Studio

Jakmile máte nainstalovánnástroje R Tools for Visual Studio (RTVS) (viz [Instalace](installing-r-tools-for-visual-studio.md)), můžete rychle získat chuť prostředí, které tyto nástroje poskytují.

## <a name="create-an-r-project"></a>Vytvoření projektu R

1. Otevřete sadu Visual Studio.
1. Zvolte **Nový projekt** > **New** > **souboru** **(Ctrl**+**Shift**+**N)**
1. V části **Šablony** > **R**vyberte možnost "Projekt R" , pojmenujte projekt a vyberte **OK**:

   ![Dialogové okno Nový projekt pro R v sadě Visual Studio (RTVS ve VS2017)](media/getting-started-01-new-project.png)

1. Po vytvoření projektu se zobrazí následující okna:

    - Na pravé straně je Visual Studio Průzkumník řešení, kde se zobrazí váš projekt uvnitř obsahující *řešení*. (Řešení mohou obsahovat libovolný počet projektů různých typů; podrobnosti naleznete v tématu [Projekty.](r-projects-in-visual-studio.md)
    - V levém horním rohu je`script.R`nový soubor R ( ), kde můžete upravit zdrojový kód se všemi funkcemi pro úpravy sady Visual Studio.
    - V levém dolním rohu je interaktivní okno **R,** ve kterém můžete interaktivně vyvíjet a testovat kód.

> [!Note]
> Můžete použít **interaktivní** okno R bez otevření projektů a i při načtení jiného typu projektu. Stačí kdykoli vybrat **nástroj R Nástroje** > **Windows** > **R Interactive.**

## <a name="explore-the-interactive-window-and-intellisense"></a>Prozkoumejte interaktivní okno a technologie IntelliSense

1. Otestujte, zda interaktivní okno `3 + 4` funguje zadáním a **zadáním** výsledku:

    ![Interaktivní okno R v Sadě Visual Studio 2017 (VS2017)](media/getting-started-02-interactive1.png)

1. Zadejte něco trochu `ds <- c(1.5, 6.7, 8.9) * 1:12`složitější, , `ds` a zadejte vidět výsledek:

    ![Další interaktivní příklad pro R v sadě Visual Studio](media/getting-started-03-interactive2.png)

1. Zadejte, `mean(ds)` ale všimněte si, že jakmile zadáte `m` nebo `me`, Visual Studio IntelliSense poskytuje možnosti automatického dokončování. Pokud je v seznamu vybráno požadované dokončení, vložte jej stisknutím **klávesy Tab.** můžete změnit výběr pomocí šipek nebo myši.

    ![Technologie IntelliSense se zobrazuje při zadávání kódu](media/getting-started-04-intellisense1.png)

1. Po `mean`dokončení zadejte otevírací závorku `(` a poznamenejte si, jak vám technologie IntelliSense poskytuje inline nápovědu pro funkci:

    ![Technologie IntelliSense zobrazující nápovědu k funkci](media/getting-started-05-intellisense2.png)

1. Dokončete řádek `mean(ds)` a stisknutím`[1] 39.51667`klávesy Enter zobrazíte výsledek ( ).

1. Interaktivní okno je integrováno s `?mean` nápovědou, takže zadání masívní ho zobrazí nápovědu pro tuto funkci v okně **nápovědy R** v sadě Visual Studio. Podrobnosti naleznete [v nápovědě k nástrojům R pro sady Visual Studio](getting-started-help.md).

    ![Okno nápovědy R v sadě Visual Studio](media/getting-started-06-help.png)

1. Některé příkazy, `plot(1:100)`například , otevřou nové okno v sadě Visual Studio, když výstup nelze zobrazit přímo v interaktivním okně:

    ![Zobrazení vykreslení v sadě Visual Studio](media/getting-started-07-plot-window.png)

Interaktivní okno také umožňuje zkontrolovat historii, načíst a uložit pracovní prostory, připojit se k ladicímu programu a pracovat se soubory zdrojového kódu namísto použití copy-paste. Podrobnosti naleznete [v části Práce s interaktivním oknem R.](interactive-repl-for-r-in-visual-studio.md)

## <a name="experience-code-editing-features"></a>Zkušenosti s úpravami kódu

Stručná práce s interaktivním oknem ukazuje základní funkce úprav, jako je Technologie IntelliSense, které fungují také v editoru kódu. Pokud zadáte stejný kód jako dříve, zobrazí se stejné výzvy automatického dokončování a technologie IntelliSense, nikoli však výstup.

Psaní kódu v *. Soubor R* umožňuje zobrazit veškerý kód najednou a usnadňuje provádění malých změn a pak rychle zobrazit výsledek spuštěním kódu v interaktivním okně. Můžete také mít tolik souborů, kolik chcete v projektu. Pokud je kód v souboru, můžete jej také spustit krok za krokem v ladicím programu (popsaném dále v tomto článku). Tyto funkce jsou užitečné při vývoji výpočetních algoritmů a psaní kódu pro manipulaci s jednou nebo více datovými sadami, zejména pokud chcete prozkoumat všechny průběžné výsledky.

Například následující kroky vytvoří malý kód k prozkoumání [centrální limitní teoretové](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipedie). (Tento příklad je převzat z *Kuchařky R* Paulem Teetorem.)

1. V `script.R` editoru zadejte následující kód:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Chcete-li rychle zobrazit výsledky, vyberte veškerý kód (**Ctrl**+**A**), stiskněte **klávesu Ctrl**+**Enter** nebo klepněte pravým tlačítkem myši a vyberte Spustit **v interaktivním**. Veškerý vybraný kód je spuštěn v interaktivním okně, jako byste jej zadali přímo, zobrazující výsledek v okně vykreslení:

    ![Zobrazení vykreslení v sadě Visual Studio](media/getting-started-08-plot1.png)

1. U jednoho řádku stačí kdykoli stisknout **klávesu Ctrl**+**Enter** a spustit tento řádek v interaktivním okně.

> [!Tip]
> Naučte se vzor provádění úprav a stisknutím **klávesctrl**+**enter** (nebo výběrem vše s **Ctrl**+**A** a pak stisknutím **Ctrl**+**Enter**) rychle spustit kód. To je mnohem efektivnější než použití myši pro stejné operace.
>
> Kromě toho můžete přetáhnout okno vykreslení z rámce sady Visual Studio a umístit jej kdykoli jiného na displeji. Potom můžete změnit velikost okna vykreslení na požadované rozměry a pak ho uložit do obrazu nebo souboru PDF.

1. Přidejte několik dalších řádků kódu, které obsahují druhý obrázek:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. Dalším stisknutím **kláves Ctrl**+**A** a **Ctrl**+**Enter** spusťte kód a výsledkem je následující:

    ![Aktualizováno duální vykreslení v sadě Visual Studio](media/getting-started-09-plot2.png)

1. Problém je v tom, že první obrázek určuje svislé měřítko, takže druhý obrázek (s) `lines`se nevejde. Chcete-li tento problém vyřešit, musíme nastavit `ylim` parametr při `plot` volání, ale to, že správně musíme přidat kód pro výpočet maximální svislé hodnoty. Dělat to řádek po řádku v interaktivním okně je nepohodlné, protože `samp.means` musíme změnit uspořádání kódu použít před voláním `plot`. V souboru kódu však můžeme snadno provést příslušné úpravy:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. **Stisknutím kláves**+**Ctrl** A a **Ctrl**+**enter** zobrazíte výsledek znovu:

    ![Aktualizováno duální vykreslení v sadě Visual Studio, správně škálované](media/getting-started-10-plot3.png)

V editoru je toho víc, co můžete udělat. Podrobnosti naleznete v [tématech Úprava kódu R](editing-r-code-in-visual-studio.md), [Technologie IntelliSense](r-intellisense.md)a [Fragmenty kódu](code-snippets-for-r.md).

## <a name="debug-your-code"></a>Ladění kódu

Jednou z klíčových předností visual studia je jeho ladění ui. RTVS staví na tomto silném základu a přidává inovativní uI, jako je [Variable Explorer](variable-explorer.md). Zde, pojďme se podívat na ladění.

1. Chcete-li začít, resetujte aktuální pracovní plochu, abyste vyčistili vše, co jste dosud udělali, pomocí příkazu nabídky**Obnovení** **relace** >  **nástrojů R.** >  Ve výchozím nastavení vše, co děláte v interaktivním okně, napočírá na aktuální relaci, která je pak také používána ladicím programem. Obnovením relace zajistíte, že relace ladění začíná bez existujících dat. Příkaz **Obnovit** však nemá vliv na *váš skript. R* zdrojový soubor, protože je spravován a uložen mimo pracovní prostor.

1. Se *scénářem. Soubor R* vytvořený v předchozí části nastavte zarážku `pop <-` na řádku, která začíná umístěním stříšky na tento řádek a stisknutím **klávesy F9**nebo výběrem **příkazu** > nabídky Ladění**přepínání zarážky.** Případně jednoduše klikněte na levý okraj (nebo okap) pro tento řádek, kde se objeví červená tečka zarážky:

    ![Nastavení zarážky v editoru](media/getting-started-11-debug1.png)

1. Spusťte ladicí program s kódem ve *skriptu. R* buď výběrem tlačítka **Zdroj ový spouštěcí soubor** na panelu nástrojů, výběrem položky nabídky**spouštěcísoubor** **zdroje ladění** > nebo stisknutím **klávesy F5**. Visual Studio přejde do režimu ladění a spustí kód. Zastaví se však na řádku, kde nastavíte zarážku:

    ![Zastavení na zarážku v ladicím programu sady Visual Studio](media/getting-started-12-debug2.png)

1. Během ladění Visual Studio poskytuje možnost krokovat kód řádek po řádku. Můžete také krok do funkce, krok přes ně, nebo krok z nich do kontextu volání. Tyto funkce spolu s ostatními najdete v nabídce **Ladění,** v kontextové nabídce po kliknutí pravým tlačítkem myši v editoru a na panelu nástrojů Ladění:

    ![Panel nástrojů ladění v sadě Visual Studio](media/getting-started-13-debug3.png)

1. Při zastavení na zarážky, můžete zkontrolovat hodnoty proměnných. Vyhledejte okno **Autos** v sadě Visual Studio a vyberte kartu v dolní části s názvem **Locals**. Okno **Locals** zobrazuje místní proměnné v aktuálním bodě programu. Pokud jste zastaveni na zarážku nastavit `pop` dříve, uvidíte, že proměnná ještě není definována. Nyní použijte příkaz **Ladění** > **kroku přes** (**F10**) `pop` a zobrazí se hodnota pro zobrazení:

    ![Okno Místní chotin v sadě Visual Studio](media/getting-started-14-debug4.png)

1. Chcete-li prozkoumat proměnné v různých oborech, včetně globálního oboru a oborů balíčků, použijte [Průzkumník proměnných](variable-explorer.md). Průzkumník proměnných také umožňuje přepnout do tabulkového zobrazení se seřaditelnými sloupci a exportovat data do souboru CSV.

    ![Rozšířené zobrazení Průzkumníka proměnných](media/variable-explorer-expanded-results.png)

1. Můžete pokračovat krokování programu řádek po řádku, nebo vyberte **Pokračovat** **(F5)** spustit až do dokončení (nebo další zarážka).

Chcete-li jít hlouběji, naleznete [v tématu ladění](debugging-r-in-visual-studio.md) a [proměnné Explorer](variable-explorer.md).

## <a name="next-steps"></a>Další kroky

V tomto návodu jste se naučili základy r projektů pomocí interaktivního okna, úpravy kódu a ladění v sadě Visual Studio. Chcete-li pokračovat ve zkoumání dalších funkcí, přečtěte si následující články a články uvedené v obsahu:

- [Ukázkové projekty](getting-started-samples.md)
- [Úpravy kódu](editing-r-code-in-visual-studio.md)
- [ladění](debugging-r-in-visual-studio.md)
- [Pracovní prostory](r-workspaces-in-visual-studio.md)
- [Vizualizace dat](visualizing-data-with-r-in-visual-studio.md)
