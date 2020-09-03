---
title: Začínáme s jazykem R – kurz
description: Návod pro použití jazyka R v aplikaci Visual Studio, včetně vytváření projektu, interaktivního okna, úprav kódu a ladění.
ms.date: 06/29/2017
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: be0ba7b32af5247bb0dccccb68d900cb6797cc13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801175"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Začínáme s Nástroje R pro Visual Studio

Po nainstalování Nástroje R pro Visual Studio (RTVS) (viz [instalace](installing-r-tools-for-visual-studio.md)) můžete rychle získat informace o zkušenostech, které tyto nástroje poskytují.

## <a name="create-an-r-project"></a>Vytvořit projekt R

1. Otevřete sadu Visual Studio.
1. Zvolit **soubor**  >  **Nový**  >  **projekt** (**CTRL** + **SHIFT** + **N**)
1. V části **šablony**R vyberte "projekt r"  >  **R**, zadejte název a umístění projektu a vyberte **OK**:

   ![Dialogové okno Nový projekt pro R v aplikaci Visual Studio (RTVS v VS2017)](media/getting-started-01-new-project.png)

1. Po vytvoření projektu se zobrazí následující okna:

    - Napravo je Visual Studio Průzkumník řešení, kde se váš projekt zobrazuje v rámci obsahujícího *řešení*. (Řešení mohou obsahovat libovolný počet projektů různých typů; podrobnosti naleznete v [projektech](r-projects-in-visual-studio.md) .
    - V levém horním rohu je nový soubor R ( `script.R` ), kde můžete upravit zdrojový kód se všemi funkcemi pro úpravy sady Visual Studio.
    - Vlevo dole je **interaktivní R** okno, ve kterém můžete interaktivně vyvíjet a testovat kód.

> [!Note]
> Můžete použít okno **interaktivní R** bez otevřených projektů a dokonce i v případě, že je načten jiný typ projektu. V každém okamžiku stačí vybrat možnost **nástroje R**  >  **Windows**  >  **interaktivní R** Windows.

## <a name="explore-the-interactive-window-and-intellisense"></a>Prozkoumejte interaktivní okno a IntelliSense

1. Otestujte, jestli interaktivní okno funguje, zadáním `3 + 4` a pak **zadáním** zobrazíte výsledek:

    ![Interaktivní R okno v aplikaci Visual Studio 2017 (VS2017)](media/getting-started-02-interactive1.png)

1. Zadejte něco složitějšího `ds <- c(1.5, 6.7, 8.9) * 1:12` a pak zadáním `ds` zobrazíte výsledek:

    ![Další interaktivní příklad pro R v aplikaci Visual Studio](media/getting-started-03-interactive2.png)

1. Zadejte `mean(ds)` , ale Všimněte si, že jakmile zadáte `m` nebo `me` , Visual Studio IntelliSense nabízí možnosti automatického dokončování. Když v seznamu vyberete požadované dokončení, vložíte ho stisknutím klávesy **TAB** . Výběr můžete změnit pomocí kláves se šipkami nebo myši.

    ![Při zadávání kódu se zobrazuje IntelliSense](media/getting-started-04-intellisense1.png)

1. Po dokončení `mean` zadejte levou závorku `(` a Všimněte si, jak vám IntelliSense nabídne vloženou nápovědu pro funkci:

    ![IntelliSense zobrazující nápovědu pro funkci](media/getting-started-05-intellisense2.png)

1. Dokončete řádek `mean(ds)` a stisknutím klávesy ENTER zobrazte výsledek ( `[1] 39.51667` ).

1. Interaktivní okno je integrováno s funkcí Help, takže zadání `?mean` zobrazí nápovědu pro tuto funkci v okně **Nápověda pro R** v aplikaci Visual Studio. Podrobnosti najdete v tématu [help in nástroje R pro Visual Studio](getting-started-help.md).

    ![Okno Nápověda pro R v aplikaci Visual Studio](media/getting-started-06-help.png)

1. Některé příkazy, například `plot(1:100)` , otevřou nové okno v aplikaci Visual Studio, když se výstup nedá zobrazit přímo v interaktivním okně:

    ![Zobrazení grafu v aplikaci Visual Studio](media/getting-started-07-plot-window.png)

Interaktivní okno také umožňuje zkontrolovat historii, načíst a uložit pracovní prostory, připojit se k ladicímu programu a pracovat se soubory zdrojového kódu místo pomocí kopírování a vkládání. Podrobnosti najdete v tématu [práce s interaktivní R oknem](interactive-repl-for-r-in-visual-studio.md) .

## <a name="experience-code-editing-features"></a>Zkušenosti s funkcemi pro úpravu kódu

V krátkém případě interaktivní okno znázorňuje základní funkce pro úpravu, jako je IntelliSense, které fungují i v editoru kódu. Pokud zadáte stejný kód jako předtím, zobrazí se stejné automatické dokončování a zobrazení výzvy IntelliSense, ale ne výstup.

Psaní kódu v *. Soubor R* umožňuje zobrazit celý kód najednou a zjednodušit provádění malých změn a pak rychle zobrazit výsledek spuštěním kódu v interaktivním okně. V projektu můžete také mít tolik souborů, kolik chcete. Když je kód v souboru, můžete ho také spustit v ladicím programu (popsáno dále v tomto článku). Tyto možnosti jsou užitečné při vývoji výpočetních algoritmů a psaní kódu pro manipulaci s jednou nebo více datovými sadami, zejména pokud chcete prošetřit všechny mezilehlé výsledky.

V následujícím příkladu vytvoříte malý kód pro zkoumání [centrálního limitu věta](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipedii). (Tento příklad je přizpůsobený z *R kuchařkau* Paul Teetor.)

1. V `script.R` editoru zadejte následující kód:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Chcete-li rychle zobrazit výsledky, vyberte veškerý kód (**CTRL** + **A**), stiskněte **klávesu CTRL** + **Enter** a potom klikněte pravým tlačítkem myši a vyberte možnost **provést v interaktivním**režimu. Veškerý vybraný kód se spustí v interaktivním okně, jako kdybyste ho zadali přímo, a zobrazí výsledek v okně vykreslení:

    ![Zobrazení grafu v aplikaci Visual Studio](media/getting-started-08-plot1.png)

1. V případě jednoho řádku stačí stisknout **klávesovou zkratku** + **ENTER** , aby se tento řádek spouštěl v interaktivním okně.

> [!Tip]
> Naučte se vytvářet úpravy a stisknout **klávesu CTRL** + **ENTER** (nebo vybrat vše s **klávesou**CTRL + **a** stisknutím klávesy **CTRL** + **ENTER**) a rychle spustit kód. V takovém případě je mnohem efektivnější než použití myši pro stejné operace.
>
> Kromě toho můžete přetáhnout okno vykreslení z rámce sady Visual Studio a umístit ho tam, kde chcete zobrazit. Pak můžete změnit velikost okna grafu na požadované rozměry a pak ho uložit do obrázku nebo souboru PDF.

1. Přidejte několik řádků kódu, které budou zahrnovat druhý graf:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. Stisknutím **kombinace kláves CTRL +** + **A** a **Ctrl** + ENTER znovu spusťte kód a**vydáte** následující výsledek:

    ![Aktualizovaný duální graf v aplikaci Visual Studio](media/getting-started-09-plot2.png)

1. Problémem je, že první graf určuje svislé měřítko, takže druhý diagram (s) nevyhovuje `lines` . Aby bylo možné tento problém vyřešit, musíme pro `ylim` volání nastavit parametr `plot` , ale do toho, aby bylo možné správně vypočítat maximální svislou hodnotu, je nutné přidat kód. Provádění tohoto řádku v interaktivním okně je nepohodlné, protože před voláním je potřeba změnit uspořádání kódu `samp.means` `plot` . V souboru kódu ale můžeme snadno provést příslušné úpravy:

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

1. **CTRL** + **A** **stisknutím klávesy CTRL** + **ENTER** zobrazíte výsledek:

    ![V aplikaci Visual Studio byl aktualizovaný duální graf, správně zvětšen](media/getting-started-10-plot3.png)

V editoru můžete dělat víc. Podrobnosti najdete v tématu [Úprava kódu R](editing-r-code-in-visual-studio.md), [IntelliSense](r-intellisense.md)a [fragmentů kódu](code-snippets-for-r.md).

## <a name="debug-your-code"></a>Ladění kódu

Jednou ze silných klíčů v aplikaci Visual Studio je jeho uživatelské rozhraní pro ladění. RTVS staví na tomto silném základu a přidává inovativní uživatelské rozhraní, jako je [Průzkumník proměnných](variable-explorer.md). V tomto příkladu se podívejme pouze na první pohled na ladění.

1. Začněte tím, že obnovíte aktuální pracovní prostor, abyste mohli vymazat všechno, co jste předtím provedli, pomocí **R Tools**  >  **Session**  >  příkazu nabídky pro**resetování** relace nástroje R. Ve výchozím nastavení se všechno, co v interaktivním okně děláte, rozloží na aktuální relaci, která je pak také používána ladicím programem. Po obnovení relace se ujistěte, že se relace ladění spustí bez stávajících dat. Příkaz pro **obnovení** ale nemá vliv na váš *skript. * Zdrojový soubor R, protože je spravovaný a uložený mimo pracovní prostor.

1. Pomocí *skriptu. *V rámci souboru R vytvořeného v předchozí části nastavte zarážku na řádku, který začíná `pop <-` vložením blikajícího kurzoru na daný řádek, a stisknutím klávesy **F9**nebo výběrem příkazu **ladit**  >  **Přepnout zarážku** . Případně klikněte na levý okraj (nebo hřbet) pro tento řádek, kde se zobrazuje červená zarážka:

    ![Nastavení zarážky v editoru](media/getting-started-11-debug1.png)

1. Spusťte ladicí program s kódem ve *skriptu. R* jedním kliknutím na tlačítko **zdrojový spouštěcí soubor** na panelu nástrojů vyberte **Debug**  >  položky nabídky**zdrojový soubor pro spuštění** ladění nebo stiskněte klávesu **F5**. Visual Studio přejde do režimu ladění a spustí běh kódu. Zastaví se však na řádku, kde jste nastavili zarážku:

    ![Zastavování na zarážce v ladicím programu sady Visual Studio](media/getting-started-12-debug2.png)

1. Během ladění poskytuje Visual Studio možnost krokovat kód řádek po řádku. Můžete také Krokovat s vnořením do funkcí, krokovat je nebo krokovat s voláním kontextu. Tyto možnosti, společně s ostatními, lze nalézt v nabídce **ladění** , místní nabídce v editoru pravým tlačítkem myši a na panelu nástrojů ladění:

    ![Panel nástrojů ladění v sadě Visual Studio](media/getting-started-13-debug3.png)

1. Při zastavení na zarážce můžete prozkoumávat hodnoty proměnných. V aplikaci Visual Studio Najděte okno **Automatické** hodnoty a vyberte kartu podél dolních pojmenovaných **místních**hodnot. Okno **místní** hodnoty zobrazuje místní proměnné v aktuálním bodě programu. Pokud jste na zarážce zastavili předchozí nastavení, uvidíte, že `pop` Proměnná ještě není definovaná. Nyní použijte příkaz **ladit**  >  **Krok over** (**F10**) a zobrazí se hodnota `pop` Zobrazit:

    ![Okno místních hodnot v aplikaci Visual Studio](media/getting-started-14-debug4.png)

1. K prohlédnutí proměnných v různých oborech, včetně globálního oboru a rozsahů balíčků, použijte [Průzkumník proměnných](variable-explorer.md). Průzkumník proměnných také umožňuje přepnout do tabulkového zobrazení s možnostmi seřaditelné sloupce a exportovat data do souboru CSV.

    ![Rozšířené zobrazení Průzkumník proměnných](media/variable-explorer-expanded-results.png)

1. Můžete pokračovat v krokování v programu řádek po řádku nebo vybrat **pokračovat** (**F5**) a spustit ho k dokončení (nebo další zarážku).

Pokud chcete pokračovat, přečtěte si téma [ladění](debugging-r-in-visual-studio.md) a [Průzkumník proměnných](variable-explorer.md).

## <a name="next-steps"></a>Další kroky

V tomto návodu jste se naučili základy projektů jazyka R, pomocí interaktivního okna, úprav kódu a ladění v aplikaci Visual Studio. Chcete-li pokračovat v průzkumu více možností, Projděte si následující články a články uvedené v obsahu:

- [Ukázkové projekty](getting-started-samples.md)
- [Úpravy kódu](editing-r-code-in-visual-studio.md)
- [Ladění](debugging-r-in-visual-studio.md)
- [Pracovní prostory](r-workspaces-in-visual-studio.md)
- [Vizualizace dat](visualizing-data-with-r-in-visual-studio.md)
