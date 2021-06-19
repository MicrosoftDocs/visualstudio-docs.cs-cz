---
title: 'Kurz: Úpravy pro vývojáře v jazyce C#'
description: Tento 10minutový úvod do editoru kódu v Visual Studio ukazuje některé způsoby, jak Visual Studio usnadňuje psaní, navigaci a pochopení kódu v jazyce C#.
ms.custom: vs-acquisition, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2a6b01e9c26ea816e05a1d2186d904bdb080f098
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390252"
---
# <a name="learn-to-use-the-code-editor-with-c"></a>Naučte se používat editor kódu s jazykem C.\#

V tomto 10minutového úvodu do editoru kódu v Visual Studio přidáme do souboru kód, který se podívá na některé ze způsobů, jak Visual Studio usnadňuje psaní, navigaci a pochopení kódu v jazyce C#.

::: moniker range="vs-2017"

> [!TIP]
> Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2022"

Pokud jste si ještě nenainstalujete Visual Studio 2022 Preview, přejděte na stránku [stahování Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) a nainstalujte si ji zdarma.

::: moniker-end

Tento článek předpokládá, že už máte zkušenosti s jazykem C#. Pokud ne, doporučujeme vám se podívat na kurz, jako je například Začínáme s [jazykem C#](tutorial-aspnet-core.md) a ASP.NET Core v Visual Studio jazyce.

> [!TIP]
> Pokud chcete postupovat podle pokynů v tomto článku, ujistěte se, že máte vybraná nastavení jazyka C# pro Visual Studio. Informace o výběru nastavení pro integrované vývojové prostředí (IDE) najdete v tématu [Výběr nastavení prostředí.](visual-studio-ide.md#select-environment-settings)

## <a name="create-a-new-code-file"></a>Vytvoření nového souboru kódu

Začněte vytvořením nového souboru a přidáním kódu do něj.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio. Stisknutím **klávesy Esc** nebo **kliknutím na** Pokračovat bez kódu v úvodním okně otevřete vývojové prostředí.

::: moniker-end

2. V nabídce **Soubor** na řádku nabídek zvolte **Nový**  >  **soubor** nebo stiskněte **Ctrl** + **N**.

3. V dialogovém **okně Nový** soubor v **kategorii Obecné** zvolte Třída Visual **C#** a pak zvolte **Otevřít.**

   V editoru se otevře nový soubor s kostru třídy jazyka C#. (Všimněte si, že nemusíme vytvářet úplný projekt Visual Studio, abyste získali některé z výhod, které editor kódu nabízí. Potřebujete jen soubor kódu.)

   ![Soubor kódu C# v Visual Studio](../media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Používání fragmentů kódu

Visual Studio poskytuje užitečné *fragmenty* kódu, které můžete použít k rychlému a snadnému generování běžně používaných bloků kódu. [Fragmenty kódu jsou](../../ide/code-snippets.md) k dispozici pro různé programovací jazyky, včetně C#, Visual Basic a C++. Pojďme do souboru přidat `void Main` fragment kódu jazyka C#.

1. Umístěte kurzor přímo nad závěrečnou uzavírací složenou závorku **}** v souboru a zadejte znaky (což znamená , nemusíte se příliš starat, pokud nevíte, co to `svm` `static void Main` &mdash; znamená).

   Zobrazí se automaticky otevírané dialogové okno s informacemi o `svm` fragmentu kódu.

   ![IntelliSense pro fragment kódu v Visual Studio](../media/tutorial-intellisense-snippet.png)

1. Stisknutím **klávesy Tab** dvakrát vložte fragment kódu.

   Uvidíte, že `static void Main()` se do souboru přidal podpis metody. Metoda [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) je vstupním bodem pro aplikace jazyka C#.

Dostupné fragmenty kódu se liší pro různé programovací jazyky. Dostupné fragmenty kódu pro váš jazyk můžete zobrazit tak, že zvolíte Upravit fragment kódu vložení IntelliSense nebo stisknete Ctrl K , Ctrl X a pak zvolíte složku  >    >    +   + vašeho jazyka. V jazyce C# vypadá seznam takhle:

![Seznam fragmentů kódu jazyka C#](../media/tutorial-code-snippet-list.png)

Seznam obsahuje fragmenty kódu pro vytvoření [třídy](/dotnet/csharp/programming-guide/classes-and-structs/classes), [konstruktoru](/dotnet/csharp/programming-guide/classes-and-structs/constructors), smyčky [for,](/dotnet/csharp/language-reference/keywords/for) [příkazu if](/dotnet/csharp/language-reference/keywords/if-else) nebo [switch](/dotnet/csharp/language-reference/keywords/switch) a dalších.

## <a name="comment-out-code"></a>Okomentování kódu

Panel nástrojů, což je řádek tlačítek pod řádkem nabídek v Visual Studio, vám může pomoct zvýšit produktivitu při práci s kódem. Můžete například přepnout režim doplňování IntelliSense ([IntelliSense](../../ide/using-intellisense.md) je pomůcka pro kódování, která mimo jiné zobrazuje seznam odpovídajících metod), zvětšovat nebo zmenšovat odsazení řádku nebo okomentovat kód, který nechcete kompilovat. V této části zakomentujeme nějaký kód.

![Panel nástrojů editoru](../media/tutorial-editor-toolbar.png)

1. Do těla metody vložte `Main()` následující kód.

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

1. Proměnnou nebudeme používat, ale můžeme ji použít později, takže ji nebudeme chtít `morewords` úplně odstranit. Místo toho tyto řádky zakomentujeme. Vyberte celou definici na uzavírací středník a pak zvolte tlačítko Okomentovat vybrané řádky `morewords` na panelu nástrojů.  Pokud dáváte přednost použití klávesnice, stiskněte **Ctrl** + **K** a **Ctrl** + **C.**

   ![Tlačítko Pro okomentování](../media/tutorial-comment-out.png)

   Znaky komentáře jazyka C# `//` se přidávají na začátek každého vybraného řádku, aby se kód zakomentoval.

## <a name="collapse-code-blocks"></a>Sbalení bloků kódu

Nechceme vidět prázdný konstruktor pro [](/dotnet/csharp/programming-guide/classes-and-structs/constructors) , který byl vygenerován, takže pro přehledné zobrazení kódu `Class1` ho sbalme. Vyberte šedé pole se znaménkem minus uvnitř na okraji prvního řádku konstruktoru. Nebo, pokud jste uživatel klávesnice, umístěte kurzor kamkoli do kódu konstruktoru a stiskněte **Ctrl** + **M**, **Ctrl** + **M**.

![Sbalení tlačítka](../media/tutorial-collapse.png)

Blok kódu se sbalí jenom na první řádek a za ním tři tečky ( `...` ). Pokud chcete blok kódu znovu rozbalit, klikněte na stejné šedé pole, ve které je teď znaménko plus, nebo znovu stiskněte **Ctrl** + **M**, **Ctrl** + **M.** Tato funkce se nazývá [osnova](../../ide/outlining.md) a je zvláště užitečná, když sbalíte dlouhé metody nebo celé třídy.

## <a name="view-symbol-definitions"></a>Zobrazení definic symbolů

Editor Visual Studio usnadňuje kontrolu definice typu, metody atd. Jedním ze možností je přejít na soubor, který obsahuje  definici, například výběrem možnosti Přejít k definici nebo stisknutím klávesy **F12** kdekoli, kde se symbol odkazuje. Ještě rychlejší způsob, jak přesunout fokus od souboru, ve které pracujete, je použít náhled [definice](../../ide/go-to-and-peek-definition.md#peek-definition). Pojďme se podívat na definici `string` typu.

1. Klikněte pravým tlačítkem na libovolný výskyt a v nabídce obsahu zvolte Náhled `string` definice.  Nebo stiskněte **Klávesu Alt** + **F12**.

   Zobrazí se automaticky otevírané okno s definicí `String` třídy . V automaticky otevíraných oknech se můžete posouvat nebo se v náhledu kódu dokonce podívat na definici jiného typu.

   ![Okno Náhled definice](../media/tutorial-peek-definition.png)

1. Zavřete okno náhledu definice výběrem malého pole s x v pravém horním rohu automaticky otevíraných oken.

## <a name="use-intellisense-to-complete-words"></a>Použití IntelliSense k dokončení slov

[IntelliSense](../../ide/using-intellisense.md) je neocenitelný prostředek při psaní kódu. Může zobrazit informace o dostupných členech typu nebo podrobnosti o parametru pro různá přetížení metody. IntelliSense můžete použít také k dokončení slova po zadání dostatečného počet znaků, aby bylo možné ho jednoznačně rozpoznat. Přidejme řádek kódu pro tisk seřazených řetězců do okna konzoly, což je standardní místo pro výstup z programu.

1. Pod `query` proměnnou začněte psát následující kód:

   ```csharp
   foreach (string str in qu
   ```

   Zobrazí se funkce IntelliSense s **rychlými informacemi** o `query` symbolu.

   ![Dokončování slov IntelliSense v Visual Studio](../media/tutorial-intellisense-completion-list.png)

1. Pokud chcete vložit zbytek slova pomocí funkce dokončování slov `query` technologie IntelliSense, stiskněte **klávesu Tab**.

1. Dokončete blok kódu, aby vypadal jako následující kód. Dokonce si můžete znovu procvičit používání fragmentů kódu tak, že zadáte a `cw` pak dvakrát stisknete klávesu **Tab** a vygeneruje `Console.WriteLine` se kód.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refaktoring názvu

Nikdo na první pohled nedostane kód a jednou z věcí, které možná budete muset změnit, je název proměnné nebo metody. Pojďme si vyzkoušet Visual Studio funkce [refaktoringu](../../ide/refactoring-in-visual-studio.md) a proměnnou přejmenujte `_words` na `words` .

1. Umístěte kurzor na definici proměnné a v místní nabídce nebo kliknutím pravým tlačítkem zvolte Přejmenovat nebo stiskněte `_words` **Ctrl**  + **R**, **Ctrl** + **R**.

   V pravém horním **rohu** editoru se zobrazí automaticky otevírané dialogové okno Přejmenovat.

1. Zadejte slova požadovaného **názvu**. Všimněte si, že `words` odkaz na v dotazu je také automaticky přejmenován. Než **stisknete Enter,** zaškrtněte **políčko Include comments (Zahrnout komentáře)** v automaticky otevírané nabídce **Přejmenovat.**

   ![přejmenování dialogového okna](../media/tutorial-rename.png)

1.  Stiskněte **Enter**.

   Oba výskyty byly přejmenovány a také odkaz na v `words` `words` komentáři ke kódu.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Další informace o projektech a řešeních](../tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také

- [Fragmenty kódu](../../ide/code-snippets.md)
- [Navigace v kódu](../../ide/navigating-code.md)
- [Sbalování](../../ide/outlining.md)
- [Přejít k definici a Náhled definice](../../ide/go-to-and-peek-definition.md)
- [Refactoring](../../ide/refactoring-in-visual-studio.md)
- [Používání technologie IntelliSense](../../ide/using-intellisense.md)
