---
title: Úvod k úpravám
ms.date: 11/30/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 9e2f451ecfb73e0c1ac69da4e48f3d2c8033aa51
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027503"
---
# <a name="learn-to-use-the-code-editor"></a>Zjistěte, jak pomocí editoru kódu

V tomto úvodu během 10 minut do editoru kódu v sadě Visual Studio přidáme kód pro soubor, který chcete podívat na některé ze způsobů, že sada Visual Studio provádí zápis, procházení a porozumění kódu jednodušší.

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stránku a nainstalovat zdarma.

Tento článek předpokládá, že jste již obeznámeni s programovacím jazyce. Pokud si nejste, doporučujeme nejdřív podívat na jeden z programovací šablon rychlý start, jako je například vytvoření webové aplikace s využitím [Python](../ide/quickstart-python.md) nebo [jazyka C#](../ide/tutorial-csharp-aspnet-core.md), nebo vytvořte aplikaci konzoly pomocí [jazyka Visual Basic](../ide/quickstart-visual-basic-console.md) nebo [C++](../ide/getting-started-with-cpp-in-visual-studio.md).

## <a name="create-a-new-code-file"></a>Vytvořte nový soubor kódu

Začněte tím, že vytváří se nový soubor a přidat nějaký kód do něj.

1. Otevřete sadu Visual Studio a od **souboru** nabídku v panelu nabídky zvolte **nový** > **souboru**.

1. V **nový soubor** dialogovém okně **Obecné** kategorie, zvolte **třídy Visual C#** a klikněte na tlačítko **otevřít**.

   Nový soubor se otevře v editoru pomocí kostru třídy C#. (Všimněte si, že nemáme vytvořit úplný projekt aplikace Visual Studio získáte některé výhody, že nabízí editor kódu; vše, co potřebujete je soubor kódu.)

   ![Kódu souboru C# v sadě Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Používání fragmentů kódu

Visual Studio poskytuje užitečné *fragmenty kódu* , že vám pomůže rychle a snadno generovat běžně používá bloky kódu. [Fragmenty kódu](../ide/code-snippets.md) jsou k dispozici pro různé programovací jazyky, včetně C#, Visual Basic a C++. Přidejme jazyka C# `void Main` fragment kódu do souboru.

1. Umístěte ukazatel myši nad konečné pravou složenou závorku **}** v souboru a zadejte znaky `svm` (což je zkratka `static void Main` &mdash;Nedělejte si starosti příliš mnoho Pokud nevíte, která znamená, že).

   Automaticky se zobrazí dialogové okno s informacemi o `svm` fragmentu kódu.

   ![Technologie IntelliSense pro fragment kódu v sadě Visual Studio](media/tutorial-intellisense-snippet.png)

1. Stisknutím klávesy **kartu** dvakrát pro vložení fragmentu kódu.

   Zobrazí `static void Main()` podpis metody nechejte se přidat do souboru. [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) metoda je vstupním bodem pro aplikace C#.

Fragmenty kódu k dispozici lišit pro různé programovací jazyky. Můžete si prohlédnout fragmenty kódu k dispozici pro váš jazyk výběrem **upravit** > **IntelliSense** > **Vložit fragment**a pak Výběr složky váš jazyk. Pro jazyk C# v seznamu vypadá například takto:

![Seznam fragment kódu jazyka C#](media/tutorial-code-snippet-list.png)

Seznam obsahuje fragmenty kódu pro vytváření [třídy](/dotnet/csharp/programming-guide/classes-and-structs/classes), [konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors), [pro](/dotnet/csharp/language-reference/keywords/for) smyčky, [Pokud](/dotnet/csharp/language-reference/keywords/if-else) nebo [přepnout](/dotnet/csharp/language-reference/keywords/switch)prohlášení a další.

## <a name="comment-out-code"></a>Okomentujte kód

Panel nástrojů, který je řádek tlačítek v panelu nabídek v sadě Visual Studio může pomoct zvýší vaši produktivitu při kódování. Například můžete přepnout režim dokončování IntelliSense ([IntelliSense](../ide/using-intellisense.md) je kódování podpory, který zobrazí seznam odpovídajících metod, mimo jiné), zvětšit nebo zmenšit odsazení řádku nebo okomentujte kód, který nechcete kompilace. V této části jsme vám okomentujte nějaký kód.

![Panel nástrojů editoru](media/tutorial-editor-toolbar.png)

1. Vložte následující kód do `Main()` tělo metody.

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    };

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. Nepoužíváme `morewords` proměnnou, ale můžeme smíte takový software používat později, nechceme zcela odstranit. Místo toho můžeme okomentujte tyto řádky. Vyberte definici celý `morewords` na pravou středníkem a klikněte na tlačítko **Odkomentujte vybrané řádky** tlačítko na panelu nástrojů. Pokud chcete použít klávesnici, stiskněte **Ctrl**+**K**, **Ctrl**+**C**.

   ![Okomentujte tlačítko](media/tutorial-comment-out.png)

   Znaky komentáře jazyka C# `//` jsou přidány do začátku okomentujte kód každém řádku.

## <a name="collapse-code-blocks"></a>Sbalit bloky kódu

Nechceme, pokud chcete zobrazit prázdné [konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors) pro `Class1` , která byla vygenerována, proto k zpřehlednit naše zobrazení kódu umožňuje sbalit. Vyberte malé šedé pole se znaménkem minus uvnitř na okraji první řádek konstruktoru. Nebo, pokud jste uživatel klávesnice, umístěte kurzor kdekoli v konstruktoru kód a stiskněte klávesu **Ctrl**+**M**, **Ctrl**+**M** .

![Sbalování tlačítko Sbalit](media/tutorial-collapse.png)

Sbalí blok kódu pouze na první řádek, následované třemi tečkami (`...`). Rozbalte blok kódu znovu, klikněte na stejnou šedé pole, které teď má znaménko plus nebo stisknutím klávesy **Ctrl**+**M**, **Ctrl**+**M**  znovu. Tato funkce se nazývá [Osnova](../ide/outlining.md) a je zvláště užitečné, když jste sbalení dlouhé metody nebo celé třídy.

## <a name="view-symbol-definitions"></a>Definice zobrazení symbolů

Editor sady Visual Studio usnadňuje Zkontrolujte definici typu, metody atd. Jedním ze způsobů, je přejít na soubor, který obsahuje definici, například výběrem **přejít k definici** kdekoli je odkazováno na symbol. Ještě rychlejší tak, aby váš výběr čárka nepohybuje mimo soubor pracujete v je použití [definice operace Peek](../ide/go-to-and-peek-definition.md#peek-definition). Umožňuje zobrazení náhledu definice `string` typu.

1. Klikněte pravým tlačítkem na jakýmkoli výskytem `string` a zvolte **definice operace Peek** z nabídky obsahu. Také můžete stisknout klávesu **Alt**+**F12**.

   Se zobrazí automaticky otevírané okno s definicí `String` třídy. V automaticky otevíraném okně, nebo dokonce náhled definice jiného typu než peeked kódu můžete posouvat.

   ![Okno definice operace Peek](media/tutorial-peek-definition.png)

1. Zavřete okno Definice nahlédnout do malé pole "x" v pravé horní části v automaticky otevíraném okně výběrem.

## <a name="use-intellisense-to-complete-words"></a>K dokončení slova použít technologie IntelliSense

[Technologie IntelliSense](../ide/using-intellisense.md) je neocenitelný při řízení zdrojů, když jste psaní kódu. Může zobrazit informace o Dostupní členové typu nebo parametr podrobnosti pro jiné přetížení metody. K dokončení slova Jakmile zadáte dostatečný počet znaků k rozlišení ho můžete také použít technologie IntelliSense. Přidáme řádek kódu vytiskne řazené řetězce v okně konzoly, což je standardní místo pro výstup z programu přejděte.

1. Níže `query` proměnné, začněte psát následující kód:

   ```csharp
   foreach (string str in qu
   ```

   Zobrazí technologie IntelliSense zobrazí **rychlé informace** o `query` symbol.

   ![Doplňování technologie IntelliSense aplikace word v sadě Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Chcete-li vložit zbytek slova `query` pomocí funkce doplňování technologie IntelliSense pro Wordu, stiskněte klávesu **kartu**.

1. Dokončete mimo blok kódu, aby vypadala jako následující kód. Dokonce můžete procvičit používání fragmentů kódu znovu tak, že zadáte `cw` a stisknutím klávesy **kartu** dvakrát ke generování `Console.WriteLine` kódu.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refaktorovat název

Nikdo poprvé získá přímo a je jednou z věcí, které budete muset změnit název proměnné nebo metody. Si můžete vyzkoušet Visual Studio [Refaktorujte](../ide/refactoring-in-visual-studio.md) funkce přejmenovat `_words` proměnnou `words`.

1. Umístěte ukazatel myši nad definici `_words` proměnnou a zvolte **přejmenovat** z klikněte pravým tlačítkem nebo místní nabídky nebo stisknutím klávesy **Ctrl**+**R**, **Ctrl**+**R**.

   Automaticky otevírané okno **přejmenovat** dialogové okno se zobrazí v horní části přímo z editoru.

1. Zadejte požadovaný název **slova**. Všimněte si, že odkaz na `words` v dotazu je také automaticky přejmenovány. Než stisknete klávesu **Enter**, vyberte **zahrnutí komentářů** zaškrtávací políčko ve **přejmenovat** v místním okně.

   ![přejmenování dialogového okna](media/tutorial-rename.png)

1. Stisknutím klávesy **zadejte**.

   Oba výskyty `words` byla přejmenována, a také odkaz na `words` v komentáři kódu.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Seznamte se s projekty a řešení](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také:

- [Fragmenty kódu](../ide/code-snippets.md)
- [Vyhledání kódu](../ide/navigating-code.md)
- [Sbalení](../ide/outlining.md)
- [Přejít k definici a Náhled definice](../ide/go-to-and-peek-definition.md)
- [Refactoring](../ide/refactoring-in-visual-studio.md)
- [Používání technologie IntelliSense](../ide/using-intellisense.md)
