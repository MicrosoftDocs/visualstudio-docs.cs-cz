---
title: Python v aplikaci Visual Studio – Krok 2, zápis a spuštění kódu
titleSuffix: ''
description: Krok 2 základního návodu k funkcím Pythonu v aplikaci Visual Studio, včetně úprav kódu a spuštění projektu.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62430029"
---
# <a name="step-2-write-and-run-code"></a>Krok 2: zápis a spuštění kódu

**Předchozí krok: [Vytvoření nového projektu v Pythonu](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

I když **Průzkumník řešení** je místo, kde spravujete soubory projektu, okno *editoru* je obvykle místo, kde pracujete s *obsahem* souborů, jako je zdrojový kód. Editor je kontextové informace o typu upravovaného souboru, včetně programovacího jazyka (založeného na příponě souboru), a nabízí funkce, které jsou vhodné pro daný jazyk, jako je například zvýrazňování syntaxe a automatické dokončování pomocí technologie IntelliSense.

1. Po vytvoření nového projektu "aplikace Python" je v editoru sady Visual Studio otevřen výchozí prázdný soubor s názvem *PythonApplication1.py* .

1. V editoru začněte psát `print("Hello, Visual Studio")` a Všimněte si, jak Visual Studio IntelliSense zobrazuje možnosti automatického dokončování podél. Možnost vyčleněná v rozevíracím seznamu je výchozí dokončování, které se používá při stisknutí klávesy **tabulátoru** . Doplňování jsou nejužitečnější, když jsou zapojeny delší příkazy nebo identifikátory.

    ![Automaticky otevírané okno automatického dokončování IntelliSense](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense zobrazuje různé informace v závislosti na příkazu, který používáte, funkci, kterou voláte, a tak dále. `print`Po zadání, `(` po označení, že `print` volání funkce zobrazí úplné informace o použití této funkce. V překryvném okně technologie IntelliSense se také zobrazuje aktuální argument tučně (**hodnota** , jak je znázorněno zde):

    ![Místní nabídka automatického dokončování IntelliSense pro funkci](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Dokončete příkaz tak, aby odpovídal následujícímu:

    ```python
    print("Hello, Visual Studio")
    ```

1. Všimněte si zbarvení syntaxe, které rozlišuje příkaz `print` od argumentu `"Hello Visual Studio"` . Také dočasně odstraňte poslední `"` z řetězce a Všimněte si, jak Visual Studio zobrazuje červené podtržení pro kód, který obsahuje syntaktické chyby. Potom nahraďte `"` kód opravou kódu.

    ![Barevné zvýrazňování syntaxe IntelliSense a zvýrazňování chyb](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Vzhledem k tomu, že je vývojové prostředí s jedním z nich velmi osobní, nabízí Visual Studio plnou kontrolu nad zobrazením a chováním sady Visual Studio. Vyberte **Tools**  >  příkaz nabídky**Možnosti** nástrojů a prozkoumejte nastavení pod kartami **prostředí** a **textový editor** . Ve výchozím nastavení vidíte pouze omezený počet možností; Chcete-li zobrazit všechny možnosti pro všechny programovací jazyky, vyberte možnost **Zobrazit všechna nastavení** v dolní části dialogového okna.

1. Spuštěním kódu, který jste napsali do tohoto bodu, stiskněte **klávesu CTRL** + **F5** nebo vyberte **ladit**  >  **Spustit bez ladění** položky nabídky. Visual Studio vás upozorní, pokud stále máte chyby ve vašem kódu.

1. Když program spustíte, zobrazí se okno konzoly se zobrazenými výsledky, stejně jako v případě, že jste spustili překladač Pythonu s *PythonApplication1.py* z příkazového řádku. Stisknutím klávesy zavřete okno a vraťte se do editoru sady Visual Studio.

    ![Výstup pro první spuštění programu](media/vs-getting-started-python-07-output.png)

1. Kromě dokončování příkazů a funkcí IntelliSense nabízí dokončování pro Python `import` a `from` příkazy. Tato doplňování vám pomůžou snadno zjistit, jaké moduly jsou k dispozici ve vašem prostředí, a členy těchto modulů. V editoru odstraňte `print` řádek a začněte psát `import` . Po zadání prostoru se zobrazí seznam modulů:

    ![IntellSense zobrazující dostupné moduly pro příkaz Import](media/vs-getting-started-python-08-import1.png)

1. Dokončete řádek zadáním nebo výběrem `sys` .

1. Na dalším řádku zadejte `from` znovu zobrazení seznamu modulů:

    ![IntellSense zobrazující dostupné moduly pro příkaz from](media/vs-getting-started-python-09-import2.png)

1. Vyberte nebo zadejte `math` a pak pokračujte v zadávání s mezerou a `import` , která zobrazuje členy modulu:

    ![IntellSense zobrazující členy modulů](media/vs-getting-started-python-10-import3.png)

1. Dokončete importem `sin` členů, `cos` a `radians` , všímáte se automatické dokončování, které jsou pro každý z nich k dispozici. Až budete hotovi, váš kód by měl vypadat takto:

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > Dokončí práci s podřetězci při psaní, odpovídá částem slov, písmenům na začátku slov a dokonce i vynechanými znaky. Podrobnosti najdete v tématu [Úprava dokončování kódu](editing-python-code-in-visual-studio.md#completions) .

1. Přidejte ještě pár kódů pro tisk hodnot kosinusu pro 360 stupňů:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Spusťte program znovu s **kombinací kláves CTRL** + **F5** nebo **ladění**  >  **Spusťte bez ladění**. Až skončíte, zavřete okno výstup.

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Používání interaktivního okna REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Upravit kód](editing-python-code-in-visual-studio.md)
- [Formátování kódu](formatting-python-code.md)
- [Refaktorování kódu](refactoring-python-code.md)
- [Použití analyzátoru PyLint](linting-python-code.md)
