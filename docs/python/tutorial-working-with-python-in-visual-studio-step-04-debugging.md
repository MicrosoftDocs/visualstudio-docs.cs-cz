---
title: Python v kurzu Visual Studia krok 4, ladění
titleSuffix: ''
description: Krok 4 základního návodu možností Pythonu v sadě Visual Studio, který popisuje, jak spustit kód Pythonu v ladicím programu.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3f6464986cb94ffa3ab3cc9264ab818112046ea9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "63002796"
---
# <a name="step-4-run-code-in-the-debugger"></a>Krok 4: Spuštění kódu v ladicím programu

**Předchozí krok: [Použití interaktivního okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Kromě správy projektů, poskytování bohaté možnosti úprav a **interaktivní** okno, Visual Studio poskytuje plně doporučené ladění kódu Pythonu. V ladicím programu můžete spustit kód krok za krokem, včetně každé iterace smyčky. Program můžete také pozastavit, kdykoli jsou splněny určité podmínky. Kdykoli, když je program pozastaven v ladicím programu, můžete zkontrolovat celý stav programu a změnit hodnotu proměnných. Tyto akce jsou nezbytné pro sledování chyb programu, a také poskytují velmi užitečné pomůcky pro pečlivé sledování přesný tok programu.

1. Nahraďte kód v *PythonApplication1.py* souboru následujícím. Tato varianta kódu `make_dot_string` se rozbalí, takže můžete prozkoumat jeho diskrétní kroky v ladicím programu. Také umístí `for` smyčky do `main` funkce a spustí explicitně voláním této funkce:

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

1. Zkontrolujte, zda kód funguje správně stisknutím **klávesy F5** nebo výběrem **příkazu** > nabídky Ladění**spouštět** ladění. Tento příkaz spustí kód v ladicím programu, ale protože jste neudělali nic pozastavit program, zatímco je spuštěn, pouze vytiskne vlnový vzor pro několik iterací. Stisknutím libovolné klávesy zavřete výstupní okno.

    > [!Tip]
    > Chcete-li po dokončení programu automaticky zavřít výstupní okno, vyberte příkaz**Příkaz y možnosti** **nástroje,** > rozbalte uzel **Pythonu,** vyberte **Ladění**a zrušte zaškrtnutí políčka Čekat **na vstup, když proces normálně ukončí**:
    >
    > ![Možnost ladění pythonu pro zavření výstupního okna při normálním ukončení programu](media/vs-getting-started-python-22-debugging5.png)

1. Nastavte zarážku `for` na příkaz u c) jednou v šedém okraji tímto řádkem nebo umístěním stříšky do tohoto řádku a použitím příkazu **Ladění** > **přepínání zarážky** (**F9**). Na šedém okraji se zobrazí červená tečka označující zarážku (jak je uvedeno v následující šipky):

    ![Nastavení zarážky](media/vs-getting-started-python-18-debugging1.png)

1. Spusťte ladicí program znovu (**F5**) a uvidíte, že spuštění kódu se zastaví na řádku s tou zarážkou. Zde můžete zkontrolovat zásobník volání a zkoumat proměnné. Proměnné, které jsou v oboru, se zobrazí v okně Autos, když jsou **definovány;** Můžete také přepnout do zobrazení **Locals** v dolní části tohoto okna a zobrazit všechny proměnné, které sada Visual Studio najde v aktuálním oboru (včetně funkcí), ještě předtím, než jsou definovány:

    ![Prostředí uživatelského prostředí zarážky pro Python](media/vs-getting-started-python-19-debugging2b.png)

1. Sledujte panel nástrojů ladění (viz níže) v horní části okna sady Visual Studio. Tento panel nástrojů poskytuje rychlý přístup k nejběžnějším příkazům ladění (které lze nalézt také v nabídce **Ladění):**

    ![Základní ladění tlačítek panelu nástrojů](media/vs-getting-started-python-20-debugging3.png)

    Tlačítka zleva doprava:
    - **Continue** **(F5)** spustí program až do další zarážky nebo do dokončení programu.
    - **Break All** **(Ctrl**+**Alt**+**Break)** pozastaví dlouhotrvající program.
    - **Zastavit ladění** **(Shift**+**F5**) zastaví program, ať je kdekoli, a ukončí ladicí program.
    - **Restart** **(Ctrl**+**Shift**+**F5)** zastaví program, ať je kdekoli, a restartuje jej od začátku v ladicím programu.
    - **Zobrazit další příkaz** (**Alt**+**Num** **&#42;**) přepne na další řádek kódu ke spuštění. To je velmi užitečné při procházení v rámci kódu během relace ladění a chcete rychle vrátit do bodu, kde je pozastavenladicí program.
    - **Krok do** (**F11**) spustí další řádek kódu, zadání mj.
    - **Krok přes** (**F10**) spustí další řádek kódu bez zadání do volaných funkcí.
    - **Krok ven** **(Shift**+**F11)** spustí zbytek aktuální funkce a pozastaví v volajícím kódu.

1. Krok přes `for` příkaz pomocí **Krok přes**. *Krokování* znamená, že ladicí program spustí aktuální řádek kódu, včetně všech volání funkce a okamžitě pozastaví znovu. Všimněte si, jak je proměnná `i` nyní definována v oknech **Locals** a **Autos.**

1. Krok přes další řádek kódu, `make_dot_string` který volá a pozastaví. **Krok tady** konkrétně znamená, že ladicí `make_dot_string` program spustí celý a pozastaví, když se vrátí. Ladicí program se nezastaví uvnitř této funkce, pokud existuje samostatná zarážka.

1. Pokračujte krokování přes kód ještě několikrát a sledovat, jak se mění hodnoty v locals **nebo** **Autos** okna.

1. V okně **Místní** nebo **Autos** poklepejte na sloupec `i` `s` **Hodnota** pro proměnnou nebo pro úpravu hodnoty. Stisknutím **klávesy Enter** nebo kliknutím mimo tuto hodnotu použijete všechny změny.

1. Pokračovat krokování kódu pomocí **Krok do**. **Krok do** znamená, že ladicí program zadá uvnitř jakékoli volání funkce, `make_dot_string`pro které má ladicí informace, například . Jakmile `make_dot_string` jste uvnitř, můžete prozkoumat jeho místní proměnné a konkrétně procházet jeho kód.

1. Pokračujte krokování s **Krok do** a všimněte si, že když se dostanete `make_dot_string`na konec , další krok se vrátí do `for` smyčky s novou vrácenou hodnotu v `s` proměnné. Při kroku znovu `print` do příkazu, všimněte si, že **krok do** na `print` nevstoupí do této funkce. Důvodem `print` je, že není napsán v Pythonu, ale je spíše nativní kód uvnitř runtime Pythonu.

1. Pokračujte v používání **funkce Krok do,** dokud nebudete opět na částečný úvazek. `make_dot_string` Pak použijte **Krok ven** a všimněte si, že se vrátíte do `for` smyčky. Pomocí **programu Step Out**ladicí program spustí zbývající část funkce a poté se automaticky pozastaví v volajícím kódu. To je velmi užitečné, když jste prošli některé části zdlouhavé funkce, které chcete ladit, ale není nutné krokovat zbytek a nechcete nastavit explicitní zarážku v volajícím kódu.

1. Chcete-li pokračovat v běhu programu, dokud není dosaženo další zarážky, použijte **pokračovat** **(F5).** Protože máte zarážku `for` ve smyčce, přerušíte na další iteraci.

1. Krokování stovky iterací smyčky může být únavné, takže Visual Studio umožňuje přidat *podmínku* zarážky. Ladicí program pak pozastaví program na zarážky pouze v případě, že je splněna podmínka. Můžete například použít podmínku s zarážkou na `for` příkaz tak, aby `i` se pozastaví pouze v případě, že hodnota přesahuje 1600. Chcete-li tuto podmínku nastavit, klepněte pravým tlačítkem myši na červenou tečku zarážky a vyberte možnost **Podmínky** (**Alt**+**F9** > **C**). V rozbalovacím panelu Nastavení `i > 1600` **zarážky** zadejte jako výraz a vyberte **Zavřít**. Stisknutím **klávesy F5** pokračujte a sledujte, že program před další přestávkou spustí mnoho iterací.

    ![Nastavení podmínky zarážky](media/vs-getting-started-python-21-debugging4.png)

1. Chcete-li spustit program až do konce, zakažte zarážku klepnutím pravým tlačítkem myši a výběrem **příkazu Zakázat zarážku** (**Ctrl**+**F9**). Potom vyberte **Pokračovat** (nebo stisknutím **klávesy F5**) program spusťte. Po ukončení programu Visual Studio zastaví relaci ladění a vrátí se do režimu úprav. Všimněte si, že můžete také odstranit zarážku kliknutím na jeho tečku, ale to také odstraní všechny podmínky, které jste nastavili.

> [!Tip]
> V některých situacích, jako je například selhání spuštění samotného interpretu Pythonu, se výstupní okno může zobrazit pouze krátce a pak se automaticky zavře, aniž byste měli možnost zobrazit zprávy o chybách. Pokud k tomu dojde, klepněte pravým tlačítkem myši na projekt v `-i` **Průzkumníku řešení**, vyberte **vlastnosti**, vyberte kartu **Ladění** a přidejte ji do pole **Argumenty interpretu.** Tento argument způsobí, že interpret přejde do interaktivního režimu po dokončení programu, čímž se okno ponechá otevřené, dokud nezadáte **klávesu Ctrl**+**Z** > **Enter.**

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Instalace balíčků v prostředí Pythonu](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [ladění](debugging-python-in-visual-studio.md)
- [Ladění v sadě Visual Studio](../debugger/debugger-feature-tour.md) poskytuje úplnou dokumentaci funkcí ladění sady Visual Studio.
