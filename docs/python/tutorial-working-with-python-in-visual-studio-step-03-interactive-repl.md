---
title: Python v výukovém kroku 3 visual studia, interaktivní REPL
titleSuffix: ''
description: Krok 3 základního návodu možností Pythonu v sadě Visual Studio, který pokrývá okno Interaktivní REPL pythonu.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 51723d22cd72de8333fca9b83c1643117a7413e5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "72986217"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Krok 3: Použití interaktivního okna REPL

**Předchozí krok: [Zápis a spuštění kódu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Visual Studio **Interaktivní** okno pro Python poskytuje bohaté čtení vyhodnotit-print-loop (REPL) prostředí, které výrazně zkracuje obvyklý cyklus edit-build-ladění. Interaktivní **Interactive** okno poskytuje všechny možnosti prostředí REPL příkazového řádku Pythonu. Také umožňuje velmi snadnou výměnu kódu se zdrojovými soubory v editoru sady Visual Studio, což je jinak těžkopádné s příkazovým řádkem.

> [!NOTE]
> Problémy s REPL, ujistěte se, že `ipython` a `ipykernel` balíčky nainstalovány, a pomoc s instalací balíčků, viz Python prostředí [balíčky kartu](/en-us/visualstudio/python/python-environments-window-tab-reference#packages-tab).

1. Otevřete **interaktivní** okno kliknutím pravým tlačítkem myši na prostředí Pythonu projektu v **Průzkumníku řešení** (například Python **3.6 (32bitový)** zobrazený v dřívější grafice) a výběrem **možnosti Otevřít interaktivní okno**. Z hlavní nabídky sady Visual Studio můžete střídavě vybrat **zobrazit** > **další** > **interaktivní windowswindows.**

1. Interaktivní **Interactive** okno se otevře pod **>>>** editorem se standardní výzvou Python REPL. Rozevírací seznam **Prostředí** umožňuje vybrat konkrétního interpreta, se kterým chcete pracovat. Často krát také chcete, aby **interaktivní** okno větší, které můžete provést přetažením oddělovač mezi dvěma okny:

    ![Interaktivní okno Pythonu a změna velikosti přetažením](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Velikost všech oken v sadě Visual Studio můžete změnit přetažením oddělovačů okrajů. Okna můžete také přetáhnout bez e-li rámečku sady Visual Studio a uspořádat je v rámci, jak se vám líbí. Úplné podrobnosti naleznete v [tématu Přizpůsobení rozložení oken](../ide/customizing-window-layouts-in-visual-studio.md).

1. Zadejte několik `print("Hello, Visual Studio")` příkazů, jako `123/456` je to se mi líbí a výrazy jako vidět okamžité výsledky:

    ![Okamžité výsledky interaktivního okna pythonu](media/vs-getting-started-python-12-interactive2.png)

1. Když začnete psát víceřádkový příkaz, jako je definice funkce, **interaktivní** okno zobrazuje výzvu **Pythonu ...** pro pokračování řádků, které na rozdíl od příkazového řádku REPL poskytují automatické odsazení:

    ![Interaktivní okno Pythonu s pokračováním příkazu](media/vs-getting-started-python-13-interactive3.png)

1. Interaktivní **Interactive** okno poskytuje úplnou historii všeho, co jste zadali, a vylepšuje příkazový řádek REPL s víceřádkovými položkami historie. Můžete například snadno vyvolat celou definici `f` funkce jako jednu jednotku `make_double`a snadno změnit název na , nikoli znovu vytvořit funkci řádek po řádku.

1. Visual Studio můžete odeslat více řádků kódu z okna **editoru** do interaktivní okno. Tato funkce umožňuje udržovat kód ve zdrojovém souboru a snadno odesílat vybrané části do **interaktivního** okna. Potom můžete pracovat s těmito fragmenty kódu v rychlém prostředí REPL, spíše než muset spustit celý program. Chcete-li zobrazit tuto `for` funkci, nejprve nahraďte smyčku v *souboru PythonApplication1.py* následujícím:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Vyberte `import` `from`příkazy `make_dot_string` , a funkce v souboru *Py,* klepněte pravým tlačítkem myši a vyberte **příkaz Odeslat do interaktivního** (nebo stiskněte **klávesu Ctrl**+**Enter**). Fragment kódu je okamžitě vložen do **interaktivního** okna a spuštěn. Vzhledem k tomu, že kód definoval funkci, můžete tuto funkci rychle otestovat několikanásobným voláním:

    ![Odeslání kódu do interaktivního okna a jeho testování](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Pomocí **klávesy Ctrl**+**Enter** v editoru *bez* výběru spustí aktuální řádek kódu v **interaktivním** okně a automaticky umístí stříška na další řádek. Pomocí této funkce opakovaně stisknutím **klávesctrl**+**enter** poskytuje pohodlný způsob, jak krokovat kód, který není možný pouze s příkazovým řádkem Pythonu. Také umožňuje krokovat kód bez spuštění ladicího programu a bez nutnosti spuštění programu od začátku.

1. Můžete také zkopírovat a vložit více řádků kódu do **interaktivního** okna z libovolného zdroje, jako je například výstřižek níže, což je obtížné dělat s repl příkazového řádku Pythonu. Po vložení spustí **interaktivní** okno tento kód, jako byste ho zadali:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Vložení více řádků kódu pomocí odesílání interaktivních](media/vs-getting-started-python-15-interactive5.png)

1. Jak můžete vidět, tento kód funguje dobře, ale jeho výstup není příliš inspirující. Jiná hodnota kroku `for` ve smyčce by ukázala více kosinusové vlny. Naštěstí, protože celá `for` smyčka je v historii REPL jako jedna jednotka, je snadné se vrátit a provést jakékoli změny, které chcete, a pak znovu otestovat funkci. Stisknutím šipky nahoru nejprve naodvolání smyčky. `for` Poté stisknutím levé nebo pravé šipky začněte v kódu procházet (dokud tak neučiníte, šipky nahoru a dolů budou pokračovat v procházení historie). Přejděte na `range` a `range(0, 360, 12)`změňte specifikaci na . Stisknutím **klávesctrl**+**enter** (kdekoli v kódu) spusťte celý příkaz znovu:

    ![Úprava předchozího příkazu v interaktivním okně](media/vs-getting-started-python-16-interactive6.png)

1. Opakujte postup experimentovat s různými nastaveními kroku, dokud nenajdete hodnotu, která se vám nejvíce líbí. Můžete také provést opakování vlny prodloužením rozsahu, `range(0, 1800, 12)`například .

1. Až budete spokojeni s kódem, který jste napíšete do **interaktivního** okna, vyberte ho, klikněte pravým tlačítkem myši a vyberte **Kopírovat kód** **(Ctrl**+**Shift**+**C**) a vložte ho do editoru. Všimněte si, jak tato speciální funkce sady Visual `>>>` Studio `...` automaticky vynese jakýkoli výstup, stejně jako a výzvy. Například následující obrázek ukazuje pomocí příkazu **Kopírovat kód** u výběru, který obsahuje výzvy a výstup:

    ![Příkaz Interaktivní kód kopírování okna při výběru s výzvami a výstupem](media/vs-getting-started-python-17-interactive7.png)

    Když vložíte do editoru, získáte pouze kód:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Chcete-li zkopírovat přesný obsah **interaktivního** okna, včetně výzev a výstupu, stačí použít standardní příkaz **Kopírovat.**

1. To, co jste právě udělali, je použít rychlé prostředí REPL **interaktivního** okna k vytvoření podrobností pro malý kus kódu, pak pohodlně přidejte tento kód do zdrojového souboru projektu. Když nyní spustíte kód znovu s **Ctrl**+**F5** (nebo **Ladění** > **Start bez ladění**), zobrazí se přesné výsledky, které jste chtěli.

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Spuštění kódu v ladicím programu](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [Použití interaktivního okna](python-interactive-repl-in-visual-studio.md)
- [Použití funkce IPython REPL](interactive-repl-ipython.md)
