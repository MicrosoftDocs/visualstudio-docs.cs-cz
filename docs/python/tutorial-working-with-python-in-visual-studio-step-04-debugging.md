---
title: Python v kurzu Visual Studio – Krok 4, ladění
titleSuffix: ''
description: Krok 4 základního návodu k funkcím Pythonu v aplikaci Visual Studio, který pokryje, jak spustit kód Pythonu v ladicím programu.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8cb9143057bf0cfda85c835131204c6641199b48
ms.sourcegitcommit: 10cb0b68f8cef219ea08eff9bc5f0afe1545c825
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699327"
---
# <a name="step-4-run-code-in-the-debugger"></a>Krok 4: spuštění kódu v ladicím programu

**Předchozí krok: [použití interaktivního okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Kromě správy projektů, poskytování bohatých možností úprav a **interaktivního** okna, nabízí Visual Studio plnohodnotné ladění pro kód Pythonu. V ladicím programu můžete spustit kód krok za krokem, včetně všech iterací smyčky. Můžete také pozastavit program vždy, když jsou splněné určité podmínky. Kdykoli je program pozastaven v ladicím programu, můžete kontrolovat celý stav programu a změnit hodnotu proměnných. Tyto akce jsou nezbytné pro sledování chyb programů a také poskytují velmi užitečné pomůcky pro pečlivý průběh přes přesný tok programu.

1. Nahraďte kód v souboru *PythonApplication1.py* následujícím kódem. Tato variace kódu se rozbalí `make_dot_string` , takže můžete prozkoumávat jeho samostatné kroky v ladicím programu. Také umístí `for` smyčku do `main` funkce a spustí ji explicitně voláním této funkce:

    ```python
    from math import cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(rad) + 20)          # scale to 0-40 spaces
        st = ' ' * numspaces + 'o'                   # place 'o' after the spaces
        return st

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. Stiskněte klávesu **F5** a vyberte   >  příkaz nabídky **Spustit ladění** pro ladění, zda kód správně funguje. Tento příkaz spustí kód v ladicím programu, ale vzhledem k tomu, že jste neudělali žádnou akci, abyste program zastavili, když je spuštěný, pouze vytiskne vzorek Wave pro několik iterací. Stisknutím libovolné klávesy zavřete okno výstup.

    > [!Tip]
    > Chcete-li po dokončení programu zavřít okno výstup automaticky, vyberte   >  příkaz nabídky **Možnosti** nástrojů, rozbalte uzel **Python** , vyberte možnost **ladění** a potom zrušte zaškrtnutí políčka **při normálním ukončení procesu počkat na vstup**:
    >
    > ![Možnost ladění Pythonu pro zavření okna výstupu při normálním ukončení programu](media/vs-getting-started-python-22-debugging5.png)

1. Nastavte zarážku pro `for` příkaz tak, že kliknete jednou na šedé okraj na tento řádek nebo umístíte blikající kurzor na tento řádek a použijete příkaz **ladit**  >  **přepínací zarážku** (**F9**). Na šedém okraji se zobrazí červená tečka pro indikaci zarážky (jak je uvedeno u šipky níže):

    ![Nastavení zarážky](media/vs-getting-started-python-18-debugging1.png)

1. Spusťte ladicí program znovu (**F5**) a podívejte se, že běh kódu se na řádku s touto zarážkou zastaví. Tady můžete zkontrolovat zásobník volání a prozkoumat proměnné. Proměnné, které jsou v oboru, se zobrazí v okně **Automatické** hodnoty, když jsou definovány. v dolní části tohoto okna můžete také přepnout na zobrazení **místních** hodnot, aby se zobrazily všechny proměnné, které Visual Studio najde v aktuálním oboru (včetně funkcí), a to i před jejich definováním:

    ![Prostředí uživatelského rozhraní zarážky pro Python](media/vs-getting-started-python-19-debugging2b.png)

1. Sledujte panel nástrojů ladění (viz níže) v horní části okna sady Visual Studio. Tento panel nástrojů poskytuje rychlý přístup k nejběžnějším příkazům ladění (které lze také najít v nabídce **ladění** ):

    ![Základní tlačítka panelu nástrojů ladění](media/vs-getting-started-python-20-debugging3.png)

    Tlačítka zleva doprava následujícím způsobem:
    - **Pokračovat** (**F5**) spustí program až do další zarážky nebo do ukončení programu.
    - **Break All** (**CTRL** + **ALT** + **Break**) pozastaví dlouhotrvající program.
    - **Zastavit ladění** (**SHIFT** + **F5**) zastaví program bez ohledu na to, a ukončí ladicí program.
    - **Restart** (**CTRL** + **SHIFT** + **F5**) zastaví program bez ohledu na jeho činnost a restartuje jej od začátku v ladicím programu.
    - **Zobrazit další příkaz** (**ALT** + **NUM** **&#42;**) přepne na další řádek kódu, který se má spustit. To je nejužitečnější při procházení kódu během relace ladění a chcete se rychle vrátit do bodu, ve kterém je ladicí program pozastaven.
    - **Krok dovnitř** (**F11**) spustí další řádek kódu, který se zadává do volaných funkcí.
    - **Krok za** (**F10**) spustí další řádek kódu bez zadání do volaných funkcí.
    - **Krok ven** (**SHIFT** + **F11**) spustí zbytek aktuální funkce a pozastaví se v volajícím kódu.

1. Krok nad `for` příkazem pomocí **kroku over**. *Krokování* znamená, že ladicí program spustí aktuální řádek kódu, včetně všech volání funkcí, a pak se okamžitě pozastaví. Všimněte si, jak `i` je proměnná nyní definovaná v oknech **místní** hodnoty a **Automatické** hodnoty.

1. Krokovat s dalším řádkem kódu, který volá `make_dot_string` a pozastavuje. **Krokovat** se sem přímo znamená, že ladicí program spustí celý `make_dot_string` a při návratu se pozastaví. Ladicí program se v této funkci nezastaví, pokud tam neexistuje samostatná zarážka.

1. Pokračujte v krokování kódu několikrát a sledujte, jak se hodnoty v okně **místní** hodnoty nebo **Automatické** změny mění.

1. V okně **místní** **hodnoty** nebo **Automatické** hodnoty dvakrát klikněte ve sloupci hodnota pro `i` proměnné nebo pro `s` úpravu hodnoty. Chcete-li použít změny, stiskněte klávesu **ENTER** nebo klikněte na libovolnou oblast mimo tuto hodnotu.

1. Pokračujte v procházení kódu pomocí **kroku into**. **Krok do** znamená, že ladicí program vstoupí do libovolného volání funkce, pro které obsahuje informace o ladění, jako je například `make_dot_string` . Jednou v rámci můžete `make_dot_string` prozkoumávat své místní proměnné a krokovat kód podle vlastního kódu.

1. Pokračujte v krokování s **krokem do** a Všimněte si, že když se dostanete ke konci `make_dot_string` , další krok se vrátí do `for` smyčky s novou návratovou hodnotou v `s` proměnné. Až se znovu pokusíte o `print` příkaz, Všimněte si, že **Krok dovnitř** v aplikaci `print` nevstoupí do této funkce. Důvodem je to `print` , že není napsaný v Pythonu, ale je nativní kód uvnitř modulu runtime Pythonu.

1. Dál používejte **Krok do** , dokud se znovu nezablokuje do `make_dot_string` . Pak použijte **Krok ven** a Všimněte si, že se vrátíte do `for` smyčky. V **kroku out** ladicí program spustí zbytek funkce a pak automaticky pozastaví volání v kódu volajícího. To je velmi užitečné, pokud jste procházeli částmi zdlouhavé funkce, kterou chcete ladit, ale nemusíte procházet celým a nechcete nastavit explicitní zarážku v kódu volajícího.

1. Chcete-li pokračovat v používání programu až do další zarážky, použijte **pokračovat** (**F5**). Vzhledem k tomu, že ve smyčce máte zarážku `for` , přerušíte u další iterace.

1. Krokování do stovek iterací smyčky může být zdlouhavé, takže Visual Studio umožňuje přidat *podmínku* na zarážku. Ladicí program pak pozastaví program na zarážce pouze v případě, že je podmínka splněna. Například můžete použít podmínku se zarážkou v `for` příkazu tak, že se pozastaví pouze v případě, že hodnota `i` přesahuje 1600. Tuto podmínku nastavíte tak, že kliknete pravým tlačítkem myši na červenou zarážku a vyberete **podmínky** (**ALT** + **F9**  >  **C**). V místní nabídce **nastavení zarážek** , která se zobrazí, zadejte `i > 1600` jako výraz a vyberte **Zavřít**. Pokračujte stisknutím klávesy **F5** a sledujte, že program spouští mnoho iterací před dalším přerušením.

    ![Nastavení podmínky zarážky](media/vs-getting-started-python-21-debugging4.png)

1. Chcete-li spustit program k dokončení, zakažte zarážku kliknutím pravým tlačítkem myši na tečku na okraji a výběrem možnosti **Zakázat zarážku** (**CTRL** + **F9**). Pak vyberte **pokračovat** (nebo stiskněte klávesu **F5**) a program spusťte. Po ukončení programu Visual Studio zastaví svou relaci ladění a vrátí do režimu úprav. Všimněte si, že můžete také odstranit zarážku, a to tak, že vyberete její tečku nebo kliknutím pravým tlačítkem na tečku a vyberete **Odstranit zarážku**, ale tím odstraníte také všechny nastavené podmínky.

> [!Tip]
> V některých situacích, jako je například selhání při spuštění vlastního interpretu Pythonu, se může okno výstup zobrazit jenom krátce a pak se automaticky zavřít bez možnosti zobrazit chybové zprávy. Pokud k tomu dojde, klikněte pravým tlačítkem myši na projekt v **Průzkumník řešení**, vyberte možnost **vlastnosti**, vyberte kartu **ladění** a poté přidejte `-i` do pole **argumenty interpretu** . Tento argument způsobí, že překladač přejde do interaktivního režimu po dokončení programu, takže okno zůstane otevřené, dokud nezadáte **klávesu CTRL** + **Z**  >  **ENTER** k ukončení.

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Instalace balíčků do prostředí Pythonu](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Ladění](debugging-python-in-visual-studio.md)
- [Ladění v sadě Visual Studio](../debugger/debugger-feature-tour.md) poskytuje úplnou dokumentaci k funkcím ladění sady Visual Studio.
