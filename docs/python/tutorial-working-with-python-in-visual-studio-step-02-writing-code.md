---
title: Python v sadě Visual Studio kurz – krok 2, zápis a spouštění kódu
titleSuffix: ''
description: Krok 2 průvodce základní funkce Pythonu v sadě Visual Studio, včetně úprav kódu a spuštění projektu.
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
ms.openlocfilehash: 9b2f1c4743652f0925ef083d0ca62a34485c219b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054797"
---
# <a name="step-2-write-and-run-code"></a>Krok 2: Zápis a spouštění kódu

**Předchozí krok: [vytvoření nového projektu Pythonu](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

I když **Průzkumníku řešení** je, kde budete spravovat soubory projektu, *editor* okno je obvykle ve kterém můžete pracovat *obsah* souborů, jako je zdrojový kód. Editor je kontextová typu souboru, který upravujete, včetně programovací jazyk (podle přípony souboru), a nabízí funkce vhodné pro daný jazyk, třeba barevné zvýrazňování syntaxe a automatické dokončování pomocí technologie IntelliSense.

1. Po vytvoření nového projektu "Aplikace v Pythonu" výchozí prázdný soubor s názvem *PythonApplication1.py* je otevřen v editoru sady Visual Studio.

1. V editoru, začněte psát `print("Hello, Visual Studio")` a Všimněte si, jak IntelliSense ve Visual Studio se zobrazí možnosti automatického dokončování na cestě. Obrysy možnost v rozevíracím seznamu je výchozí dokončení, který se používá po stisknutí klávesy **kartu** klíč. Dokončování jsou nejužitečnější, když se podílejí delší příkazy nebo identifikátory.

    ![Automaticky otevírané okno automatického dokončování IntelliSense](media/vs-getting-started-python-04-IntelliSense1b.png)

1. Technologie IntelliSense zobrazuje různé informace v závislosti na příkazu, který používáte, funkce, do které voláte a tak dále. S `print` fungovala, zadáním `(` po `print` k označení funkce volání zobrazí informace o úplné využití pro tuto funkci. Okno technologie IntelliSense také ukazuje aktuální argument v tučné písmo (**hodnotu** jak je znázorněno zde):

    ![Automaticky otevírané okno automatického dokončování IntelliSense pro funkci](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Proveďte příkaz tak, aby odpovídala následující:

    ```python
    print("Hello, Visual Studio")
    ```

1. Všimněte si, zabarvení syntaxe, která odlišuje příkaz `print` z argumentu `"Hello Visual Studio"`. Navíc dočasně odstranit poslední `"` na řetězec a Všimněte si, jak sada Visual Studio zobrazí červené podtržení pro kód, který obsahuje chyby syntaxe. Potom nahraďte `"` opravit kód.

    ![Barevné zvýrazňování syntaxe technologie IntelliSense a zvýrazňování chyb](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Protože jeden z vývojového prostředí je velmi osobní řádu, sada Visual Studio poskytuje úplnou kontrolu nad vzhled a chování aplikace Visual Studio. Vyberte **nástroje** > **možnosti** nabídky příkazů a prozkoumejte nastavení v části **prostředí** a **textový Editor** karty. Ve výchozím nastavení se zobrazí pouze omezený počet možností. Pokud chcete zobrazit všechny dostupné možnosti pro každý programovací jazyk, vyberte **zobrazit všechna nastavení** v dolní části dialogového okna. 

1. Spustit kód, který jste zadali do této chvíle stisknutím kombinace kláves **Ctrl**+**F5** nebo jeho výběru **ladění** > **spustit bez ladění**  položky nabídky. Visual Studio vás upozorní, pokud máte stále chyby v kódu.

1. Při spuštění programu, zobrazí se okno konzoly při zobrazení výsledků, tak, jako kdyby byste spustili interpret Pythonu s *PythonApplication1.py* z příkazového řádku. Stisknutím jakékoli klávesy zavřete okno a vraťte se do editoru sady Visual Studio.

    ![Výstup pro první spuštění programu](media/vs-getting-started-python-07-output.png)

1. Kromě dokončování příkazů a funkce, technologie IntelliSense poskytne dokončování Python `import` a `from` příkazy. Tyto dokončování vám snadno zjistit, jaké moduly jsou k dispozici ve vašem prostředí a členy těchto modulů. V editoru, odstraňte `print` řádku a začněte psát `import `. Seznam modulů, které se zobrazí, když zadáte pole:

    ![IntellSense zobrazení dostupných modulů pro příkaz importu](media/vs-getting-started-python-08-import1.png)

1. Dokončení řádku zadáním nebo výběrem `sys`.

1. Na dalším řádku, zadejte `from` znovu zobrazíte seznam modulů:

    ![Zobrazení dostupných modulů pro IntellSense z příkazu](media/vs-getting-started-python-09-import2.png)

1. Vyberte nebo zadejte `math`, pokračujte v zadávání s mezerou a `import`, který zobrazuje modul členy:

    ![IntellSense zobrazující modulu členy](media/vs-getting-started-python-10-import3.png)

1. Dokončete tak, že import `sin`, `cos`, a `radians` členy vašeho povšimnutí dostupné dokončování automaticky pro každý. Jakmile budete hotovi, váš kód by měl vypadat takto:

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > Dokončování pracovat podřetězců hned při psaní, odpovídající části slov, písmena na začátku slova a dokonce přeskočeno znaků. Zobrazit [upravit kód – dokončování](editing-python-code-in-visual-studio.md#completions) podrobnosti.

1. Přidejte trochu další kód pro tisk hodnoty kosinus pro 360 stupňů:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Spusťte program znovu s **Ctrl**+**F5** nebo **ladění** > **spustit bez ladění**. Jakmile budete hotovi, zavřete okno výstup.

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Použití interaktivního okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Úpravy kódu](editing-python-code-in-visual-studio.md)
- [Formátovat kód](formatting-python-code.md)
- [Refaktorování kódu](refactoring-python-code.md)
- [Použití Pylintu](linting-python-code.md)
