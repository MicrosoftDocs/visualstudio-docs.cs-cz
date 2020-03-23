---
title: Python v kurzu Visual Studia krok 2, psaní a spouštění kódu
titleSuffix: ''
description: Krok 2 základního návodu možností Pythonu v Sadě Visual Studio, včetně úprav kódu a spuštění projektu.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fda68b9e5bffbd1afab3389a0d8d624312a8de3f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "62430029"
---
# <a name="step-2-write-and-run-code"></a>Krok 2: Zápis a spuštění kódu

**Předchozí krok: [Vytvoření nového projektu Pythonu](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

Přestože **Průzkumník řešení** je místo, kde můžete spravovat soubory projektu, okno *editoru* je obvykle místo, kde pracujete s *obsahem* souborů, jako je zdrojový kód. Editor je kontextově vědom typu souboru, který upravujete, včetně programovacího jazyka (na základě přípony souboru) a nabízí funkce odpovídající tomuto jazyku, jako je zbarvení syntaxe a automatické dokončování pomocí technologie IntelliSense.

1. Po vytvoření nového projektu "Aplikace Pythonu" je v editoru Visual Studio otevřen výchozí prázdný soubor s názvem *PythonApplication1.py.*

1. V editoru začněte `print("Hello, Visual Studio")` psát a všimněte si, jak visual studio IntelliSense zobrazuje možnosti automatického dokončování podél cesty. Možnost nastíněná v rozevíracím seznamu je výchozí dokončení, které se používá při stisknutí klávesy **Tabulátor.** Dokončení jsou velmi užitečné, pokud se jedná o delší příkazy nebo identifikátory.

    ![Místní okno automatického dokončování technologie IntelliSense](media/vs-getting-started-python-04-IntelliSense1b.png)

1. Technologie IntelliSense zobrazuje různé informace v závislosti na příkazu, který používáte, na funkci, kterou voláte, a tak dále. S `print` funkcí, `(` zadáním `print` pro označení volání funkce zobrazí úplné informace o využití pro tuto funkci. Vyskakovací okno IntelliSense také zobrazuje aktuální argument tučným písmem **(hodnota,** jak je znázorněno zde):

    ![Automaticky otevírat funkce funkce při automatickém dokončování technologie IntelliSense](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Vyplňte příkaz tak, aby odpovídal následující:

    ```python
    print("Hello, Visual Studio")
    ```

1. Všimněte si zbarvení syntaxe, která odlišuje příkaz `print` od argumentu `"Hello Visual Studio"`. Také dočasně odstranit `"` poslední na řetězci a všimněte si, jak Visual Studio zobrazuje červené podtržení pro kód, který obsahuje chyby syntaxe. Pak nahradit `"` opravit kód.

    ![Zvýraznění syntaxe technologie IntelliSense](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Vzhledem k tomu, že vývojové prostředí je velmi osobní záležitost, Visual Studio poskytuje úplnou kontrolu nad vzhled a chování sady Visual Studio. Vyberte příkaz nabídky**Možnosti** **nástrojů** > a prozkoumejte nastavení na kartách **Prostředí** a **Textový editor.** Ve výchozím nastavení se zobrazí pouze omezený počet možností; chcete-li zobrazit všechny možnosti pro každý programovací jazyk, vyberte **Zobrazit všechna nastavení** v dolní části dialogového okna.

1. Spusťte kód, který jste napsali do tohoto bodu stisknutím **ctrl**+**f5** nebo výběrem **ladění** > **start bez ladění** položky nabídky. Visual Studio vás upozorní, pokud máte stále chyby v kódu.

1. Když spustíte program, zobrazí se okno konzoly zobrazující výsledky, stejně jako byste spouštěli překladač Pythonu s *PythonApplication1.py* z příkazového řádku. Stisknutím klávesy zavřete okno a vraťte se do editoru sady Visual Studio.

    ![Výstup pro první spuštění programu](media/vs-getting-started-python-07-output.png)

1. Kromě dokončení příkazů a funkcí poskytuje technologie IntelliSense `import` dokončení `from` pro Python a příkazy. Tyto dokončení vám pomohou snadno zjistit, jaké moduly jsou k dispozici ve vašem prostředí a členy těchto modulů. V editoru odstraňte `print` řádek a `import`začněte psát . Při psaní mezery se zobrazí seznam modulů:

    ![Technologie IntellSense zobrazující dostupné moduly pro příkaz importu](media/vs-getting-started-python-08-import1.png)

1. Řádek vyplňte zadáním nebo `sys`výběrem .

1. Na dalším řádku `from` zadejte, chcete-li znovu zobrazit seznam modulů:

    ![Technologie IntellSense zobrazující dostupné moduly pro příkaz from](media/vs-getting-started-python-09-import2.png)

1. Vyberte `math`nebo zadejte , pak `import`pokračujte v psaní mezerou a , která zobrazí členy modulu:

    ![Technologie IntellSense zobrazující členy modulu](media/vs-getting-started-python-10-import3.png)

1. Dokončete `sin` `cos`importem `radians` , a členů, všímat si automatické dokončování k dispozici pro každý. Po dokončení by se měl kód zobrazit takto:

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > Dokončení práce s podřetězce při psaní, odpovídající části slov, písmena na začátku slova, a dokonce i přeskočené znaky. Podrobnosti naleznete [v tématu Upravit kód – Dokončení.](editing-python-code-in-visual-studio.md#completions)

1. Přidejte trochu více kódu pro tisk hodnot kosinusu pro 360 stupňů:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Spusťte program znovu s **Ctrl**+**F5** nebo **Ladění** > **Start bez ladění**. Po dokončení zavřete výstupní okno.

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Použití interaktivního okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [Upravit kód](editing-python-code-in-visual-studio.md)
- [Formátování kódu](formatting-python-code.md)
- [Refaktorivační kód](refactoring-python-code.md)
- [Použití analyzátoru PyLint](linting-python-code.md)
