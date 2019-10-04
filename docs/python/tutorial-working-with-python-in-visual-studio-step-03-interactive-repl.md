---
title: Python v sadě Visual Studio kurz – krok 3, interaktivní okno REPL
titleSuffix: ''
description: Krok 3 průvodce základní funkce Pythonu v sadě Visual Studio, pokrývající okno REPL interaktivní Python.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 15e0b45fd77096ba2227391736aad5c895014d1c
ms.sourcegitcommit: 0554b59a2a251661e56824fb9cd6e9b1f326cef1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71831874"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Krok 3: Používání interaktivního okna REPL

**Předchozí krok: [Zápis a spuštění kódu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Visual Studio **interaktivní** okna pro jazyk Python poskytuje bohaté čtení vyhodnocení print-loop (REPL) prostředí, který výrazně zkracuje obvykle cyklem editovat sestavit ladit. **Interaktivní** okno nabízí všechny funkce prostředí REPL pro Python příkazového řádku. Také umožňuje velmi snadno vyměňovat kódu s zdrojové soubory v sadě Visual Studio editor, který je jinak náročné s příkazovým řádkem.

> [!NOTE]
> V případě problémů s REPL se ujistěte, že máte nainstalované balíčky `ipython` a `ipykernel` a nápovědu k instalaci balíčků najdete na [kartě balíčky prostředí Python](https://docs.microsoft.com/en-us/visualstudio/python/python-environments-window-tab-reference#packages-tab).

1. Otevřít **interaktivní** okno kliknutím pravým tlačítkem myši prostředí projektu Pythonu v **Průzkumníku řešení** (například **Python 3.6 (32bitová verze)** ukazuje předchozí obrázek) a Výběr **otevřít interaktivní okno**. Můžete také vybrat **zobrazení** > **ostatní Windows** > **Windows interaktivní Python** z hlavní nabídky sady Visual Studio.

1. **Interaktivní** níže se standardem editoru se otevře okno **>>>** řádku REPL pro Python. **Prostředí** rozevíracího seznamu můžete vybrat konkrétní interpret pro práci s. Často budete chtít také zajistit **interaktivní** okno větší, což lze provést tak, že přetáhnete oddělovač mezi dvěma okny:

    ![Interaktivní okno Pythonu a tažením změnit velikost](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Všechna okna v sadě Visual Studio můžete nastavit velikost přetažením příhraničních oddělovače. Lze také přetáhnout windows nezávisle na rámci sady Visual Studio a změnit jejich pořadí, ale chcete v rámci. Úplné podrobnosti najdete v tématu [přizpůsobení rozložení oken](../ide/customizing-window-layouts-in-visual-studio.md).

1. Zadejte několik příkazů jako `print("Hello, Visual Studio")` a výrazy, jako jsou `123/456` okamžitou výsledky:

    ![Okamžitou výsledky interaktivní okno Pythonu](media/vs-getting-started-python-12-interactive2.png)

1. Když začnete psát víceřádkové příkazu, jako jsou definice funkce, **interaktivní** okno zobrazuje Python **...**  výzva k pokračování řádků, které na rozdíl od příkazového řádku REPL, poskytuje automatické odsazení:

    ![Interaktivní okno Pythonu s pokračováním – příkaz](media/vs-getting-started-python-13-interactive3.png)

1. **Interaktivní** okno poskytuje úplnou historii všechno, co jste zadali a dále to vylepšuje REPL příkazového řádku s položkami víceřádkové historie. Například můžete snadno odvolat celou definici `f` fungovala jako jeden celek a snadno změnit název, který má `make_double`, ne znovu vytvořit funkci řádek po řádku.

1. Visual Studio můžete odeslat více řádků kódu v okně editoru pro **interaktivní** okna. Tato funkce umožňuje udržovat kódu ve zdrojovém souboru a snadno odesílat vybírat části tak, **interaktivní** okno. Pak můžete pracovat s tyto fragmenty kódu v rychlé prostředí REPL namísto nutnosti spuštění celého programu. Pokud chcete zobrazit tuto funkci, nejprve nahraďte `for` smyčky v *PythonApplication1.py* souboru následujícím kódem:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. V souboru *. py* vyberte příkazy funkce `import`, `from` a `make_dot_string`, klikněte pravým tlačítkem myši a vyberte **Odeslat do interaktivního** (nebo stiskněte klávesu @no__t **CTRL**-6**ENTER**). Fragment kódu se okamžitě vloží do **interaktivní** okno a spustit. Teď vyberte `make_dot_string` fungovat a zopakujte stejný příkaz, který se znovu spouští tento fragment kódu. Protože kód definuje funkci, můžete rychle otestovat tuto funkci voláním párkrát:

    ![Odeslání kódu do interaktivního okna a jeho otestování.](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Pomocí **Ctrl**+**Enter** v editoru *bez* spouští aktuální řádek kódu ve výběru **interaktivní** okno a automaticky umístí blikající kurzor na další řádek. Díky této funkci klávesy **Ctrl**+**Enter** opakovaně poskytuje pohodlný způsob, jak procházet kódem, který není možné z Pythonu příkazového řádku. Také umožňuje procházet kódem bez spuštění ladicího programu a bez nutně od začátku spuštění programu.

1. Můžete také zkopírovat a vložit více řádků kódu do **interaktivní** okno z jakéhokoli zdroje, jako je například následující fragment kódu, které je obtížné provést pomocí příkazového řádku REPL. Pythonu Při vložení, **interaktivní** okna ICT tento kód, jako kdyby měl ji v zadali:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Vložením několika řádků kódu pomocí odesílání interaktivní](media/vs-getting-started-python-15-interactive5.png)

1. Jak je vidět, tento kód funguje správně, ale není velmi inspirující svůj výstup. Hodnotu do jiné kroku `for` smyčky, který by zobrazil informace kosinus wave. Naštěstí protože celý `for` smyčky je v historii REPL jako celek, lze snadno vrátit a jakékoli změny můžete chtít a k testování funkce znovu. Stisknutím klávesy šipka nahoru první odvolání `for` smyčky. Pak pomocí šipek doleva nebo doprava start navigace v kódu (dokud Uděláte to tak, nahoru a dolů šipkami nadále cyklicky procházet historii). Přejít na a změnit `range` specifikace `range(0, 360, 12)`. Stiskněte klávesu **Ctrl**+**Enter** (kdekoli v kódu) pro spuštění celý příkaz znovu:

    ![Úpravy předchozí příkaz v interaktivním okně](media/vs-getting-started-python-16-interactive6.png)

1. Postupujte stejně jako můžete experimentovat s nastavením jiné kroku až do nalezení hodnoty, které vám nejvíc vyhovuje. Můžete provést také vlny opakování prodlužte rozsahu, například `range(0, 1800, 12)`.

1. Až budete spokojeni s tím jsou napsaná v kódu **interaktivní** okna, vyberte ho, klikněte pravým tlačítkem a vyberte **kopírování kódu** (**Ctrl** + **Shift**+**C**) a vložte do editoru. Všimněte si, jak tato speciální funkce sady Visual Studio automaticky vynechá jakýkoli výstup, jakož i `>>>` a `...` zobrazí výzvu. Například následující obrázek ukazuje použití **kopírování kódu** na výběr, který zahrnuje výzvy a výstup příkazu:

    ![Interaktivní okno kopírování kódu příkaz na výběru s výzvami a výstup](media/vs-getting-started-python-17-interactive7.png)

    Když vložíte do editoru, získáte jenom kód:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Pokud chcete zkopírovat obsah **interaktivní** okna, včetně pokynů a výstup, stačí použít standardní **kopírování** příkazu.

1. Co jste právě provedli je použít rychlé prostředí REPL **interaktivní** okno umožní zjistit podrobné informace o malou část kódu, potom pohodlně přidán tento kód ke zdrojovému souboru projektu. Když nyní spustíte kód znovu s **Ctrl**+**F5** (nebo **ladění** > **spustit bez ladění**), můžete přesné výsledky, které jste chtěli zobrazit.

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Spuštění kódu v ladicím programu](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Pomocí interaktivního okna](python-interactive-repl-in-visual-studio.md)
- [Použití Ipythonu REPL](interactive-repl-ipython.md)
