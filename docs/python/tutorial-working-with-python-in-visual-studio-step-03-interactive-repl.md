---
title: Python v aplikaci Visual Studio – Krok 3, interaktivní REPL
titleSuffix: ''
description: Krok 3 základního návodu k funkcím Pythonu v aplikaci Visual Studio, pokrývající interaktivní REPL okno Pythonu.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d88d936a4b470f891f3b2bf2c353f4ef4e595c57
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811042"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Krok 3: použití interaktivního okna REPL

**Předchozí krok: [zápis a spuštění kódu](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

**Interaktivní** okno sady Visual Studio pro Python poskytuje bohatá prostředí pro čtení a hodnocení REPL (Read-Evaluate-Print-Loop), které výrazně zkracuje běžný cyklus úprav-Build-ladění. **Interaktivní** okno poskytuje všechny možnosti REPLho prostředí v příkazovém řádku Pythonu. Také je velmi snadné vyměňovat kód se zdrojovými soubory v editoru sady Visual Studio, který je jinak náročný na příkazový řádek.

> [!NOTE]
> V případě problémů s REPL se ujistěte, že `ipython` máte `ipykernel` nainstalované a balíčky a nápovědu k instalaci balíčků najdete na [kartě balíčky prostředí Python](./python-environments-window-tab-reference.md#packages-tab).

1. Otevřete **interaktivní** okno kliknutím pravým tlačítkem myši na prostředí Python projektu v **Průzkumník řešení** (například **Python 3,6 (32-bit)** zobrazené v předchozí grafice) a výběrem možnosti **otevřít interaktivní okno**. V hlavní nabídce aplikace Visual Studio můžete alternativně vybrat **Zobrazit**  >  **Další**  >  **interaktivní okna Windows Pythonu** .

1. **Interaktivní** okno se otevře pod editorem se standardní **>>>** výzvou REPL Pythonu. Rozevírací seznam **prostředí** vám umožňuje vybrat konkrétní Interpret, se kterým chcete pracovat. Často také, že chcete, aby **interaktivní** okno bylo větší, což můžete udělat přetažením oddělovače mezi dvěma okny:

    ![Interaktivní okno Pythonu a přetahování na velikost](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Můžete změnit velikost všech oken v aplikaci Visual Studio přetažením oddělovačů ohraničení. Můžete také přetáhnout systém Windows nezávisle na rámci rámce sady Visual Studio a změnit jejich uspořádání v rámci rámečku. Úplné podrobnosti najdete v tématu [přizpůsobení rozložení oken](../ide/customizing-window-layouts-in-visual-studio.md).

1. Zadejte několik příkazů, jako jsou `print("Hello, Visual Studio")` výrazy a, jako je například `123/456` zobrazení okamžitých výsledků:

    ![Okamžité výsledky interaktivního okna Pythonu](media/vs-getting-started-python-12-interactive2.png)

1. Když začnete psát víceřádkový příkaz, jako je definice funkce, **interaktivní** okno zobrazuje v jazyce Python **...** prompt pro pokračování řádků, které na rozdíl od REPL příkazového řádku poskytuje automatické odsazení:

    ![Interaktivní okno Pythonu s pokračováním příkazu](media/vs-getting-started-python-13-interactive3.png)

1. **Interaktivní** okno poskytuje úplnou historii všeho, co jste zadali, a zlepšuje se na PŘÍKAZOVÉM řádku REPL s položkami víceřádkové historie. Můžete například snadno vyvolat celou definici `f` funkce jako jednu jednotku a snadno změnit název na `make_double` místo opětovného vytvoření funkce řádek po řádku.

1. Visual Studio může odeslat více řádků kódu z okna editoru do **interaktivního** okna. Tato funkce umožňuje zachovat kód ve zdrojovém souboru a snadno odeslat vybrané části do **interaktivního** okna. Pak můžete pracovat s takovými fragmenty kódu v prostředí Rapid REPL, ale nemusíte spouštět celý program. Tuto funkci zobrazíte tak, že nejprve nahradíte `for` smyčku v souboru *PythonApplication1.py* následujícím způsobem:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. `import` `from` `make_dot_string` V souboru *. py* vyberte příkazy funkce, a. Klikněte pravým tlačítkem myši na vybraný text a zvolte **Odeslat do interaktivního** (nebo stiskněte klávesu **CTRL** + **ENTER**). Fragment kódu se hned vloží do **interaktivního** okna a spustí se. Vzhledem k tomu, že kód definoval funkci, můžete tuto funkci rychle otestovat tak, že ji zavoláte několikrát:

    ![Odeslání kódu do interaktivního okna a jeho testování](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Pomocí **klávesy CTRL** + **ENTER** v editoru *bez* výběru se spustí aktuální řádek kódu v **interaktivním** okně a automaticky umístí blikající kurzor na další řádek. Pomocí této funkce opakovaně nabízí **klávesovou zkratku CTRL** + **ENTER** pohodlný způsob, jak procházet kód, který není možné pouze pomocí příkazového řádku Pythonu. Umožňuje také procházet kód bez spuštění ladicího programu a bez nutnosti spustit program od začátku.

1. Do **interaktivního** okna můžete také zkopírovat a vložit více řádků kódu z libovolného zdroje, jako je například fragment kódu, který se obtížně provede s REPL příkazového řádku Pythonu. Po vložení **interaktivní** okno spustí tento kód, jako kdybyste ho zadali v:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Vložení více řádků kódu pomocí interaktivního odesílání](media/vs-getting-started-python-15-interactive5.png)

1. Jak vidíte, tento kód funguje správně, ale jeho výstup není velmi inspirativní. Jiná hodnota kroku ve `for` smyčce by zobrazila více než Wave kosinus. Naštěstí, protože celá `for` smyčka je v historii REPL jako jedna jednotka, snadno se vrátíte zpět a provedete libovolné změny a pak znovu otestujete funkci. Stisknutím šipky nahoru napřed zavoláte `for` smyčku. Potom stisknutím levé nebo pravé šipky spusťte navigaci v kódu (dokud to neuděláte, šipky nahoru a dolů budou dál cyklicky procházet historii). Přejděte na adresu a změňte `range` specifikaci na `range(0, 360, 12)` . Pak stiskněte klávesu **CTRL** + **ENTER** (kdekoli v kódu) pro opětovné spuštění celého příkazu:

    ![Úprava předchozího příkazu v interaktivním okně](media/vs-getting-started-python-16-interactive6.png)

1. Opakujte postup pro experimentování s různými nastaveními kroku, dokud nenajdete hodnotu, kterou byste chtěli nejlépe. Vlnovkou můžete také vytvořit tak, že prodloužíte rozsah, například `range(0, 1800, 12)` .

1. Až budete spokojeni s kódem, který jste napsali v **interaktivním** okně, vyberte ho. Potom klikněte pravým tlačítkem na kód a vyberte **Kopírovat kód** (**CTRL** + **+** + **C**). Nakonec vložte vybraný kód do editoru. Všimněte si, že tato speciální funkce sady Visual Studio automaticky vynechává libovolný výstup a také `>>>` `...` výzvy a. Například následující obrázek ukazuje použití příkazu **Kopírovat kód** na výběr, který obsahuje výzvy a výstup:

    ![Interaktivní okno – příkaz Kopírovat kód na výběr s výzvami a výstupem](media/vs-getting-started-python-17-interactive7.png)

    Při vložení do editoru získáte pouze kód:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Pokud chcete zkopírovat přesný obsah **interaktivního** okna, včetně výzev a výstupu, stačí použít standardní příkaz **Kopírovat** .

1. To, co jste právě provedli, je použít rychlé prostředí REPL **interaktivního** okna pro práci s podrobnostmi malého kódu, a poté jste pohodlným přidáním tohoto kódu do zdrojového souboru projektu. Když teď kód znovu spustíte s **klávesou Ctrl** + **F5** (nebo pokud chcete **ladit**  >  **Spustit bez ladění**), zobrazí se přesně požadované výsledky.

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Spuštění kódu v ladicím programu](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Použití interaktivního okna](python-interactive-repl-in-visual-studio.md)
- [Použití IPython REPL](interactive-repl-ipython.md)