---
title: Ladění pro Python v sadě Visual Studio kurz – krok 4
titleSuffix: ''
description: Krok 4 Průvodce základní funkce Pythonu v sadě Visual Studio ke spuštění kódu Pythonu v ladicím programu.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5facce6eff378586ece01b5774089e76058615f9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060417"
---
# <a name="step-4-run-code-in-the-debugger"></a>Krok 4: Spuštění kódu v ladicím programu

**Předchozí krok: [použití okna interaktivní okno REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Kromě správy projektů, poskytuje bohaté možnosti, úprav a **interaktivní** okně Visual Studio poskytuje plně vybavené ladění pro kód Python. V ladicím programu můžete spustit váš kód krok za krokem, včetně všech iterací smyčky. Je také možné pozastavit program pokaždé, když jsou splněny určité podmínky. Kdykoli při program je pozastavení v ladicím programu, můžete zkontrolovat stav celého programu a změňte hodnotu proměnné. Tyto akce jsou nezbytné pro sledování chyby v kódu programu a také poskytují velmi užitečné pomůcky pro pečlivě uplatňují přesné programu.

1. Nahraďte kód v *PythonApplication1.py* souboru následujícím kódem. Tuto variaci kód rozšiřuje `make_dot_string` tak, aby můžete zkontrolovat jeho diskrétní kroky v ladicím programu. Zároveň přenáší `for` smyčku do `main` funkce a spustí ji explicitně voláním této funkce:

    ```python
    from math import cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(radians(x)) + 20)   # scale to 0-40 spaces
        st = ' ' * numspaces + 'o'                   # place 'o' after the spaces
        return st

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. Zkontrolujte, jestli kód funguje správně stisknutím kombinace kláves **F5** nebo jeho výběru **ladění** > **spustit ladění** příkazu nabídky. Tento příkaz spustí kód v ladicím programu, ale vzhledem k tomu, že jste ještě nepracovali se pro pozastavení programu, když je spuštěný, stačí vytiskne vlnovky u několika iterací. Stisknutím jakékoli klávesy zavřete okno výstup.

    > [!Tip]
    > Zavřete okno výstup automaticky při dokončení programu, nahraďte `main()` volat s následujícím kódem:
    >
    > ```python
    > if __name__ == "__main__":
    >     sys.exit(int(main() or 0))
    > ```

1. Nastavit zarážku na `for` jedním klepnutím na okraji šedé tento řádek nebo umístěním blikající kurzor na tomto řádku a pomocí příkazu **ladění** > **Přepnout zarážku** příkazu () **F9**). Červená tečka se zobrazí v šedé okraj udávajících zarážky (jak je uvedeno níže šipkou):

    ![Nastavením zarážky](media/vs-getting-started-python-18-debugging1.png)

1. Znovu spusťte ladicí program (**F5**) a podívejte se spuštěnou zastaví kód na řádku s Tato zarážka určena. Tady si můžete prohlédnout volání zásobníku a zkontrolovat proměnné. Proměnné, které jsou v oboru se zobrazí v **automatické hodnoty** okno, když máte definovány; můžete také přepínač tak, aby **lokální** zobrazení v dolní části tohoto okna, chcete-li zobrazit všechny proměnné, které Visual Studio vyhledá v aktuální rozsah (včetně funkce), dokonce i předtím, než se definuje:

    ![Zarážka uživatelské rozhraní pro Python](media/vs-getting-started-python-19-debugging2b.png)

1. Sledujte ladění nástrojů (viz dole) v horní části okna nástroje Visual Studio. Tento panel nástrojů poskytuje rychlý přístup k největší běžné příkazy ladění (které také najdete na **ladění** nabídky):

    ![Základní ladění tlačítka na panelu nástrojů](media/vs-getting-started-python-20-debugging3.png)

    Tlačítka zleva doprava následujícím způsobem:
    - **Pokračovat** (**F5**) spustí program až k další zarážce nebo až do dokončení programu.
    - **Přerušení všech** (**Ctrl**+**Alt**+**přerušit**) dlouho běžící program pozastaví.
    - **Zastavit ladění** (**Shift**+**F5**) program zastaví, bez ohledu na to je a ladicí program se ukončí.
    - **Restartujte** (**Ctrl**+**Shift**+**F5**) program zastaví, bez ohledu na to je a restartuje ho od začátku v ladicí program.
    - **Zobrazit další příkaz** (**Alt**+**Num** **&#42;**) přepne na další řádek kódu ke spuštění. To je nejužitečnější při navigaci v kódu během relace ladění a chcete rychle se vrátit do bodu, kde je pozastavena ladicím programu.
    - **Krokovat s vnořením** (**F11**) spustí další řádek kódu, zadáte do volané funkce.
    - **Krokovat s přeskočením** (**F10**) spustí další řádek kódu bez nutnosti zadávat do volané funkce.
    - **Krokovat s Vystoupením** (**Shift**+**F11**) spustí zbývající část aktuální funkci a pozastaví ve volajícím kódu.

1. Krokovat přes `for` pomocí příkazu **Krokovat s přeskočením**. *Krokování* znamená, že ladicí program spouští aktuální řádek kódu, včetně všechna volání funkce a následně ihned pozastaví znovu. Všimněte si, že jak proměnné `i` je nyní definována ve **lokální** a **automatické hodnoty** systému windows.

1. Krok za další řádek kódu, která volá `make_dot_string` a pozastaví. **Krokovat s přeskočením** tady konkrétně znamená, že ladicí program běží celý `make_dot_string` a pozastaví při vrátí. Ladicí program nezastaví uvnitř této funkce, pokud existuje samostatné zarážku.

1. Pokračovat, krokování přes kód ještě několikrát a podívejte se jak hodnoty v **lokální** nebo **automatické hodnoty** okno změnit.

1. V **lokální** nebo **automatické hodnoty** okna, dvakrát klikněte na v **hodnotu** sloupec pro buď `i` nebo `s` proměnné a příslušnou hodnotu upravte. Stisknutím klávesy **Enter** nebo klikněte na tlačítko mimo tuto hodnotu použít změny.

1. Pokračujte v krokování kódu pomocí **Krokovat s vnořením**. **Krokovat s vnořením** znamená, že ladicí program vstoupí v jakékoli volání funkce, pro které má ladicí informace, jako například `make_dot_string`. Jednou uvnitř `make_dot_string` můžete prozkoumat své místní proměnné a konkrétně projít jeho kód.

1. Krokování s pokračovat **Krokovat s vnořením** a Všimněte si, že při dosažení konce `make_dot_string`, dalším krokem vrátí do `for` smyčky s novou návratovou hodnotou v `s` proměnné. Jako krok znovu na `print` prohlášení, Všimněte si, že **Krokovat s vnořením** na `print` nepřejde do této funkce. Důvodem je, že `print` není napsané v Pythonu, ale je místo toho nativní kód uvnitř modulu runtime Pythonu.

1. Pokračovat v používání **Krokovat s vnořením** až na znovu partway do `make_dot_string`. Pak pomocí **Krokovat s Vystoupením** a Všimněte si, že se vrátíte `for` smyčky. S **Krokovat s Vystoupením**, ladicí program spustí zbývající část funkce a automaticky pozastaví ve volajícím kódu. To je velmi užitečné, když jste prošli část zdlouhavé funkce, kterou chcete ladit, nemusíte krokovat ostatní a není, ale chcete nastavit explicitní zarážky ve volajícím kódu.

1. Chcete-li pokračování ve spouštění programu, dokud nebude dosaženo k další zarážce, použijte **pokračovat** (**F5**). Protože máte zarážku `for` smyčky, přerušíte na další iteraci.

1. Krokování stovky iterací smyčky může být pracná, aby Visual Studio vám umožňuje přidat *podmínku* zarážku. Ladicí program pak pozastaví program na zarážce, pouze pokud je splněna podmínka. Například můžete použít podmínku zarážky, která na `for` příkaz tak, že pozastaví pouze při hodnotu `i` překračuje 1600. Pokud chcete nastavit tuto podmínku, klikněte pravým tlačítkem na tečku red zarážky a vyberte **podmínky** (**Alt**+**F9** > **C**). V **nastavení zarážek** automaticky otevírané okno, které se zobrazí, zadejte `i > 1600` jako výraz a vyberte **Zavřít**. Stisknutím klávesy **F5** pokračovat a podívejte se, že se program spouští více iterací před další přerušení.

    ![Nastavení podmínku zarážky](media/vs-getting-started-python-21-debugging4.png)

1. Spustit program dokončen, zakázat zarážku tak, že kliknete pravým tlačítkem a vyberete **zakázat zarážku** (**Ctrl**+**F9**). Potom vyberte **pokračovat** (nebo stiskněte klávesu **F5**) ke spuštění programu. Při ukončení programu sady Visual Studio ukončí jeho ladicí relace a vrátí jeho režimu úprav. Všimněte si, že zarážka můžete také odstranit klepnutím na jeho tečkou, ale tím se odstraní také všechny podmínky, které jste nastavili.

> [!Tip]
> V některých situacích, jako je například selhání při spuštění interpret Pythonu, může v okně výstupu zobrazí pouze krátce a pak zavřete automaticky bez s možností zobrazíte všechny chybové zprávy. Pokud k tomu dojde, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení**vyberte **vlastnosti**, vyberte **ladění** kartu a pak přidejte `-i` k  **Argumenty pro interpret** pole. Tento argument způsobí, že překladač přejde do interaktivního režimu po dokončení programu, a tím udržování okna otevřete dokud nezadáte **Ctrl**+**Z**  >  **Enter** ukončíte.

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Instalace balíčků ve vašem prostředí Pythonu](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Ladění](debugging-python-in-visual-studio.md)
- [Ladění v sadě Visual Studio](../debugger/debugger-feature-tour.md) poskytuje úplnou dokumentaci sady Visual Studio je funkce ladění.
