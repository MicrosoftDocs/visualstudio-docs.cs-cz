---
title: Úvod do úprav pro C# vývojáře
description: Tento 10 minutový Úvod do editoru kódu v aplikaci Visual Studio ukazuje některé způsoby, jak aplikace Visual Studio usnadňuje psaní, navigaci a porozumění C# kódu.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0cacd56ff6b3b3510505ca2752404b55a2771429
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590433"
---
# <a name="learn-to-use-the-code-editor"></a>Zjistěte, jak pomocí editoru kódu

V tomto úvodu během 10 minut do editoru kódu v sadě Visual Studio přidáme kód pro soubor, který chcete podívat na některé ze způsobů, že sada Visual Studio provádí zápis, procházení a porozumění kódu jednodušší.

::: moniker range="vs-2017"

> [!TIP]
> Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a nainstalovat zdarma.

::: moniker-end

V tomto článku se předpokládá, že už C#jste obeznámeni s nástrojem. Pokud ne, doporučujeme se podívat na kurz, jako je například [Začínáme s C# a ASP.NET Core v aplikaci Visual Studio](tutorial-aspnet-core.md) jako první.

> [!TIP]
> Pokud chcete postupovat podle tohoto článku, ujistěte se, že C# máte nastavení vybraná pro Visual Studio. Informace o výběru nastavení pro integrované vývojové prostředí (IDE) najdete v tématu [Výběr nastavení prostředí](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Vytvořte nový soubor kódu

Začněte tím, že vytváří se nový soubor a přidat nějaký kód do něj.

::: moniker range="vs-2017"

1. Otevřít Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřít Visual Studio. Stisknutím klávesy **ESC** nebo kliknutím na **pokračovat bez kódu** v okně Start otevřete vývojové prostředí.

::: moniker-end

2. V nabídce **soubor** na řádku nabídek zvolte **Nový** > **soubor**nebo stiskněte **klávesovou zkratku CTRL**+**N**.

3. V **nový soubor** dialogovém okně **Obecné** kategorie, zvolte **třídy Visual C#** a klikněte na tlačítko **otevřít**.

   Nový soubor se otevře v editoru pomocí kostru třídy C#. (Všimněte si, že nemáme vytvořit úplný projekt aplikace Visual Studio získáte některé výhody, že nabízí editor kódu; vše, co potřebujete je soubor kódu.)

   ![Kódu souboru C# v sadě Visual Studio](../media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Používání fragmentů kódu

Visual Studio poskytuje užitečné *fragmenty kódu* , že vám pomůže rychle a snadno generovat běžně používá bloky kódu. [Fragmenty kódu](../../ide/code-snippets.md) jsou k dispozici pro různé programovací jazyky, včetně C#, Visual Basic a C++. Přidejme jazyka C# `void Main` fragment kódu do souboru.

1. Umístěte ukazatel myši nad konečné pravou složenou závorku **}** v souboru a zadejte znaky `svm` (což je zkratka `static void Main` &mdash;Nedělejte si starosti příliš mnoho Pokud nevíte, která znamená, že).

   Automaticky se zobrazí dialogové okno s informacemi o `svm` fragmentu kódu.

   ![Technologie IntelliSense pro fragment kódu v sadě Visual Studio](../media/tutorial-intellisense-snippet.png)

1. Stisknutím klávesy **kartu** dvakrát pro vložení fragmentu kódu.

   Zobrazí `static void Main()` podpis metody nechejte se přidat do souboru. [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) metoda je vstupním bodem pro aplikace C#.

Fragmenty kódu k dispozici lišit pro různé programovací jazyky. Můžete se podívat na dostupné fragmenty kódu pro váš jazyk, a to tak, že vyberete **upravit** > **IntelliSense** > **vložit fragment** nebo stisknout **CTRL**+**K**, **CTRL**+**X**a pak vybrat složku vašeho jazyka. Pro jazyk C# v seznamu vypadá například takto:

![Seznam fragment kódu jazyka C#](../media/tutorial-code-snippet-list.png)

Seznam obsahuje fragmenty kódu pro vytváření [třídy](/dotnet/csharp/programming-guide/classes-and-structs/classes), [konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors), [pro](/dotnet/csharp/language-reference/keywords/for) smyčky, [Pokud](/dotnet/csharp/language-reference/keywords/if-else) nebo [přepnout](/dotnet/csharp/language-reference/keywords/switch)prohlášení a další.

## <a name="comment-out-code"></a>Okomentujte kód

Panel nástrojů, který je řádek tlačítek v panelu nabídek v sadě Visual Studio může pomoct zvýší vaši produktivitu při kódování. Například můžete přepnout režim dokončování IntelliSense ([IntelliSense](../../ide/using-intellisense.md) je kódování podpory, který zobrazí seznam odpovídajících metod, mimo jiné), zvětšit nebo zmenšit odsazení řádku nebo okomentujte kód, který nechcete kompilace. V této části jsme vám okomentujte nějaký kód.

![Panel nástrojů editoru](../media/tutorial-editor-toolbar.png)

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

   ![Okomentujte tlačítko](../media/tutorial-comment-out.png)

   Znaky komentáře jazyka C# `//` jsou přidány do začátku okomentujte kód každém řádku.

## <a name="collapse-code-blocks"></a>Sbalit bloky kódu

Nechceme, pokud chcete zobrazit prázdné [konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors) pro `Class1` , která byla vygenerována, proto k zpřehlednit naše zobrazení kódu umožňuje sbalit. Vyberte malé šedé pole se znaménkem minus uvnitř na okraji první řádek konstruktoru. Nebo, pokud jste uživatel klávesnice, umístěte kurzor kdekoli v konstruktoru kód a stiskněte klávesu **Ctrl**+**M**, **Ctrl**+**M** .

![Sbalování tlačítko Sbalit](../media/tutorial-collapse.png)

Sbalí blok kódu pouze na první řádek, následované třemi tečkami (`...`). Rozbalte blok kódu znovu, klikněte na stejnou šedé pole, které teď má znaménko plus nebo stisknutím klávesy **Ctrl**+**M**, **Ctrl**+**M**  znovu. Tato funkce se nazývá [Osnova](../../ide/outlining.md) a je zvláště užitečné, když jste sbalení dlouhé metody nebo celé třídy.

## <a name="view-symbol-definitions"></a>Definice zobrazení symbolů

Editor sady Visual Studio usnadňuje kontrolu definice typu, metody atd. Jedním ze způsobů je přejít na soubor, který obsahuje definici, například výběrem možnosti **Přejít k definici** nebo stisknutím klávesy **F12** kdekoliv, kde se odkazuje na symbol. Ještě rychlejší tak, aby váš výběr čárka nepohybuje mimo soubor pracujete v je použití [definice operace Peek](../../ide/go-to-and-peek-definition.md#peek-definition). Umožňuje zobrazení náhledu definice `string` typu.

1. Klikněte pravým tlačítkem na jakýmkoli výskytem `string` a zvolte **definice operace Peek** z nabídky obsahu. Také můžete stisknout klávesu **Alt**+**F12**.

   Se zobrazí automaticky otevírané okno s definicí `String` třídy. V automaticky otevíraném okně, nebo dokonce náhled definice jiného typu než peeked kódu můžete posouvat.

   ![Okno definice operace Peek](../media/tutorial-peek-definition.png)

1. Zavřete okno Definice nahlédnout do malé pole "x" v pravé horní části v automaticky otevíraném okně výběrem.

## <a name="use-intellisense-to-complete-words"></a>K dokončení slova použít technologie IntelliSense

[Technologie IntelliSense](../../ide/using-intellisense.md) je neocenitelný při řízení zdrojů, když jste psaní kódu. Může zobrazit informace o Dostupní členové typu nebo parametr podrobnosti pro jiné přetížení metody. K dokončení slova Jakmile zadáte dostatečný počet znaků k rozlišení ho můžete také použít technologie IntelliSense. Přidáme řádek kódu vytiskne řazené řetězce v okně konzoly, což je standardní místo pro výstup z programu přejděte.

1. Níže `query` proměnné, začněte psát následující kód:

   ```csharp
   foreach (string str in qu
   ```

   Zobrazí technologie IntelliSense zobrazí **rychlé informace** o `query` symbol.

   ![Doplňování technologie IntelliSense aplikace word v sadě Visual Studio](../media/tutorial-intellisense-completion-list.png)

1. Chcete-li vložit zbytek slova `query` pomocí funkce doplňování technologie IntelliSense pro Wordu, stiskněte klávesu **kartu**.

1. Dokončete mimo blok kódu, aby vypadala jako následující kód. Dokonce můžete procvičit používání fragmentů kódu znovu tak, že zadáte `cw` a stisknutím klávesy **kartu** dvakrát ke generování `Console.WriteLine` kódu.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refaktorovat název

Nikdo poprvé získá přímo a je jednou z věcí, které budete muset změnit název proměnné nebo metody. Si můžete vyzkoušet Visual Studio [Refaktorujte](../../ide/refactoring-in-visual-studio.md) funkce přejmenovat `_words` proměnnou `words`.

1. Umístěte ukazatel myši nad definici `_words` proměnnou a zvolte **přejmenovat** z klikněte pravým tlačítkem nebo místní nabídky nebo stisknutím klávesy **Ctrl**+**R**, **Ctrl**+**R**.

   Automaticky otevírané okno **přejmenovat** dialogové okno se zobrazí v horní části přímo z editoru.

1. Zadejte požadovaný název **slova**. Všimněte si, že odkaz na `words` v dotazu je také automaticky přejmenovány. Než stisknete klávesu **Enter**, vyberte **zahrnutí komentářů** zaškrtávací políčko ve **přejmenovat** v místním okně.

   ![přejmenování dialogového okna](../media/tutorial-rename.png)

1. Stisknutím klávesy **zadejte**.

   Oba výskyty `words` byla přejmenována, a také odkaz na `words` v komentáři kódu.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Seznamte se s projekty a řešení](../tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také:

- [Fragmenty kódu](../../ide/code-snippets.md)
- [Vyhledání kódu](../../ide/navigating-code.md)
- [Sbalení](../../ide/outlining.md)
- [Přejít k definici a Náhled definice](../../ide/go-to-and-peek-definition.md)
- [Refactoring](../../ide/refactoring-in-visual-studio.md)
- [Používání technologie IntelliSense](../../ide/using-intellisense.md)
