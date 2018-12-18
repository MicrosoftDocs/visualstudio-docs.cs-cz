---
title: Začít kurz jazyka R
description: Návod k využití R v sadě Visual Studio včetně vytváření projektu, interaktivní okno kódu úprav a ladění.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 88387485b952bf201a222741a6b3d02861df186c
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238376"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Začínáme s nástroji R pro Visual Studio

Jakmile budete mít nástroje R pro Visual Studio (RTVS) nainstalovaná (naleznete v tématu [instalace](installing-r-tools-for-visual-studio.md)), můžete rychle získat představu o tom, které poskytují tyto nástroje prostředí. 

## <a name="create-an-r-project"></a>Vytvoření projektu jazyka R

1. Spusťte sadu Visual Studio.
1. Zvolte **souboru** > **nové** > **projektu** (**Ctrl**+**Shift** + **N**)
1. Vyberte "projekt R" v rámci **šablony** > **R**, dejte projektu název a umístění a pak vyberte **OK**:

   ![Dialogové okno Nový projekt pro R v sadě Visual Studio (RTVS v VS2017)](media/getting-started-01-new-project.png)

1. Po vytvoření projektu se zobrazí následující okna:

    - Na pravé straně je Průzkumníku řešení Visual Studio, kde se zobrazí váš projekt uvnitř obsahujícího *řešení*. (Řešení může obsahovat libovolný počet různých typů projektů, naleznete v tématu [projekty](r-projects-in-visual-studio.md) podrobnosti.
    - V levém horním rohu se nový soubor R (`script.R`) ve kterém můžete upravit zdrojový kód se všemi sady Visual Studio je funkce úprav.
    - V levém dolním je **interaktivní R** okno, ve kterém můžete interaktivně vyvíjet a testovat kód.

> [!Note]
> Můžete použít **interaktivní R** okno bez nutnosti všechny projekty otevřít a dokonce i když se načte jiný typ projektu. Stačí vybrat **nástroje R** > **Windows** > **interaktivní R** kdykoli.

## <a name="explore-the-interactive-window-and-intellisense"></a>Prozkoumat interaktivní okno a technologie IntelliSense

1. Test, který interaktivní okno funguje tak, že zadáte `3 + 4` a potom **Enter** k zobrazení výsledku:

    ![Interaktivní okno R v sadě Visual Studio 2017 (VS2017)](media/getting-started-02-interactive1.png)

1. Zadejte něco o něco složitější, `ds <- c(1.5, 6.7, 8.9) * 1:12`a pak zadejte `ds` k zobrazení výsledku:

    ![Další příklad, interaktivní R v sadě Visual Studio](media/getting-started-03-interactive2.png)

1. Zadejte `mean(ds)` , ale Všimněte si, že nejdříve zadáte `m` nebo `me`, poskytuje možnosti automatického dokončování IntelliSense ve Visual Studio. Po dokončení chcete, aby se v seznamu vyberete, stisknutím klávesy **kartu** k vložení; můžete změnit výběr pomocí kláves se šipkami nebo myši.

    ![Povolí, nebude při zadávání kódu technologie IntelliSense](media/getting-started-04-intellisense1.png)

1. Po dokončení `mean`, zadejte levou závorku `(` a Všimněte si, jak technologie IntelliSense umožňuje vložená Nápověda pro funkci:

    ![Technologie IntelliSense zobrazuje nápovědu pro funkci](media/getting-started-05-intellisense2.png)

1. Dokončení řádku `mean(ds)` a stiskněte klávesu Enter k zobrazení výsledku (`[1] 39.51667`).

1. Interaktivní okno je integrovaná s nápovědou, takže zadávání `?mean` zobrazí nápovědu pro tuto funkci v **nápovědy** okna v sadě Visual Studio. Podrobnosti najdete v tématu [nápovědu v nástroje jazyka R pro Visual Studio](getting-started-help.md).

    ![Okno Nápověda jazyka R v sadě Visual Studio](media/getting-started-06-help.png)

1. Některé příkazy, jako například `plot(1:100)`, otevřete nové okno v sadě Visual Studio, když výstup nelze zobrazit přímo v interaktivním okně:

    ![Zobrazení diagramů v sadě Visual Studio](media/getting-started-07-plot-window.png)

Interaktivní okno také umožňuje zkontrolovat historii, načíst a uložit pracovní prostory, připojit ladicí program a interakci s souborů se zdrojovým kódem místo pomocí kopírování a vkládání. Zobrazit [práce s interaktivním okně R](interactive-repl-for-r-in-visual-studio.md) podrobnosti.

## <a name="experience-code-editing-features"></a>Funkce pro úpravu kódu prostředí

Práce s oknem interaktivní stručně ukazuje základních funkcí pro úpravy jako například IntelliSense, které fungují také v editoru kódu. Pokud zadáte stejný kód jako dříve, se zobrazí stejné automatického dokončování a výzev technologie IntelliSense, ale ne ve výstupu.

Psaní kódu v *. R* soubor si můžete najednou zobrazit veškerý kód a usnadňuje dělat malé změny a pak se krátce zobrazit výsledek spuštěním kódu v interaktivním okně. Je také možné tolik souborů v projektu. Pokud je kód v souboru, můžete ho spustit také podrobné v ladicím programu (popsáno dále v tomto článku). Tyto funkce jsou užitečné při vývoji výpočetní algoritmy a psaní kódu pro manipulaci s jeden nebo více datových sad, zejména v případě, že chcete prozkoumat všechny mezilehlé výsledky.

Jako příklad, následujícím postupem se vytvoří pár kódu [centrální Limit věta](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipedia). (V tomto příkladu jsou upraveny z *R kuchařka* podle Paul Teetor.)

1. V `script.R` editoru zadejte následující kód:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Pokud chcete rychle zobrazit výsledky, vyberte veškerý kód (**Ctrl**+**A**), stiskněte klávesu **Ctrl**+**Enter** nebo Klikněte pravým tlačítkem a vyberte **provést v Interactive**. Všechny vybrané kód spuštěný v interaktivním okně, jako kdyby jste ho zadali přímo, v okně diagram zobrazující výsledek:

    ![Zobrazení diagramů v sadě Visual Studio](media/getting-started-08-plot1.png)

1. Pro jeden řádek, stačí stisknout kombinaci kláves **Ctrl**+**Enter** kdykoli spustit tento řádek v interaktivním okně.

> [!Tip]
> Další vzor úpravou a stisknutím **Ctrl**+**Enter** (nebo výběr všechno, co s **Ctrl**+**A** a stisknutím klávesy **Ctrl**+**Enter**) rychlé spuštění kódu. To je mnohem efektivnější než pomocí myši pro stejné operace.
> 
> Kromě toho lze přetáhnout a rozevírací okno diagramů mimo rámec sady Visual Studio a umístěte ho jinak můžete kdykoli na obrazovce. Pak můžete změnit velikost okna diagramů dimenzím chcete a uložte ho do obrazu nebo souboru PDF.

1. Přidejte několik další řádky kódu, které zahrnují druhý graf:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. Stisknutím klávesy **Ctrl**+**A** a **Ctrl**+**Enter** znovu pro spuštění kódu, vytváření následující výsledky:

    ![Aktualizované duální diagramů v sadě Visual Studio](media/getting-started-09-plot2.png)

1. Problém je, že první graf určuje vertikální škálování, tak druhá vykreslení (s `lines`) nevejde. Chcete-li tento problém, musíme nastavit `ylim` parametru u `plot` volat, ale udělat tak, aby správně potřebujeme přidat kód pro výpočet svislé maximální hodnoty. Provádění tento řádek po řádku v interaktivním okně je nevhodné, protože potřebujeme k uspořádání kódu pro použití `samp.means` před voláním `plot`. V souboru kódu ale snadno bychom mohli příslušné úpravy:

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

1. **CTRL**+**A** a **Ctrl**+**Enter** znovu, abyste viděli výsledek:

    ![Aktualizované duální diagramů v sadě Visual Studio správně škálovat](media/getting-started-10-plot3.png)

Existuje více, které vám pomůžou v editoru. Podrobnosti najdete v tématu [kódu jazyka R upravit](editing-r-code-in-visual-studio.md), [IntelliSense](r-intellisense.md), a [fragmenty kódu](code-snippets-for-r.md).

## <a name="debug-your-code"></a>Ladění kódu

Jednou z klíčových předností sady Visual Studio je jeho ladění uživatelského rozhraní. RTVS sestavení na tomto silné a přidá inovativní uživatelského rozhraní, jako [Průzkumníka proměnných](variable-explorer.md). Tady stačí Pojďme se první pohled na ladění.

1. Pokud chcete začít, resetování aktuálního pracovního prostoru všechno, co jste provedli zatím pomocí zrušte **nástroje R** > **relace** > **resetování** příkazu nabídky. Ve výchozím nastavení všechno, co dělat v interaktivním okně běžné u aktuální relace, který potom slouží také ladicím programem. Resetováním relace, zajistíte tím, že ladicí relace začíná žádná existující data. **Resetování** příkazu, ale nemá vliv na vaše *skriptu. R* zdrojového souboru, protože, který obsahuje spravované a uložili mimo pracovní prostor.

1. S *skriptu. R* vytvoří soubor v předchozí části, nastavit zarážku na řádek, který začíná `pop <-` umístěním blikající kurzor na tomto řádku a stisknutím klávesy **F9**, nebo jeho výběru **ladění**  >  **Přepnout zarážku** příkazu nabídky. Stačí klikněte v levém okraji (nebo ovládací prvek) pro tento řádek, ve kterém se zobrazí červený zarážku tečka:

    ![Nastavením zarážky v editoru](media/getting-started-11-debug1.png)

1. Spuštění ladicího programu s kódem v *skriptu. R* tak, že vyberete **zdrojový soubor spouštěcí** tlačítko na panelu nástrojů, vyberete **ladění** > **zdrojový soubor spouštěcí** položky nabídky nebo stisknutím klávesy **F5**. Visual Studio přejde do režimu její ladění a spuštění kódu. Zastaví, ale na řádku, kde nastavit zarážku:

    ![Probíhá zastavení na zarážce v ladicím programu sady Visual Studio](media/getting-started-12-debug2.png)

1. Během ladění, Visual Studio poskytuje možnost Procházet kódem řádek po řádku. Můžete také Krokovat s vnořením funkce, krok nad nich, nebo krok z nich na kontext volání. Tyto možnosti společně s ostatními, můžete najít na **ladění** nabídky, klikněte pravým tlačítkem na místní nabídky v editoru a panelu nástrojů ladění:

    ![Panel nástrojů v sadě Visual Studio pro ladění](media/getting-started-13-debug3.png)

1. Při zastavení na zarážce, můžete zkoumat hodnoty proměnné. Vyhledejte **automatické hodnoty** okna v sadě Visual Studio a zvolte kartu v dolní části s názvem **lokální**. **Lokální** okno zobrazuje lokální proměnné do aktuálního místa v programu. Pokud jste zastavení na zarážce, sady použili náhodnost, uvidíte, že `pop` ještě není definována proměnná. Teď použijte **ladění** > **Krokovat s přeskočením** příkazu (**F10**), a zobrazí hodnotu `pop` zobrazí:

    ![Okno místních hodnot v sadě Visual Studio](media/getting-started-14-debug4.png)

1. Chcete-li zkontrolovat proměnné v různých oborech, včetně globální obor a balíček obory, použijte [Průzkumníka proměnných](variable-explorer.md). Průzkumník proměnných také poskytuje schopnost přepínat zobrazení na tabulkové zobrazení s řazení sloupců a export dat do souboru CSV.

    ![Rozšířené zobrazení Průzkumníka proměnných](media/variable-explorer-expanded-results.png)

1. Můžete pokračovat v krokování programem řádek po řádku, nebo vyberte **pokračovat** (**F5**) ke spuštění dokončení (nebo k další zarážce).

Seznamte se blíž, najdete v článku [ladění](debugging-r-in-visual-studio.md) a [Průzkumníka proměnných](variable-explorer.md).

## <a name="next-steps"></a>Další kroky

V tomto návodu jste se naučili základy projekty v R, používání interaktivního okna, úpravy a ladění v sadě Visual Studio code. Pokračujte ve zkoumání další možnosti, naleznete následující články také články, které jsou uvedené v tabulce obsah:

- [Ukázkové projekty](getting-started-samples.md)
- [Úpravy kódu](editing-r-code-in-visual-studio.md)
- [Ladění](debugging-r-in-visual-studio.md)
- [Pracovní prostory](r-workspaces-in-visual-studio.md)
- [Vizualizace dat](visualizing-data-with-r-in-visual-studio.md)
