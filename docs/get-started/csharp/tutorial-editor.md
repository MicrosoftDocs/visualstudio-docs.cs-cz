---
title: Úvod do úprav pro vývojáře v jazyce C#
description: Tento 10 minutový Úvod do editoru kódu v aplikaci Visual Studio ukazuje některé způsoby, jak aplikace Visual Studio usnadňuje psaní, navigaci a porozumění kódu jazyka C#.
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
ms.openlocfilehash: 72a74c967849703feeb427d89891a023326ca6b7
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234962"
---
# <a name="learn-to-use-the-code-editor-with-c"></a>Naučte se používat editor kódu s C. #

V tomto 10 minutách úvodu do editoru kódu v aplikaci Visual Studio přidáme kód do souboru, abyste se mohli podívat na některé způsoby, jak Visual Studio dělá psaní, navigaci a porozumění kódu v jazyce C#.

::: moniker range="vs-2017"

> [!TIP]
> Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

V tomto článku se předpokládá, že už jste obeznámeni s jazykem C#. Pokud ne, doporučujeme se podívat na kurz, například [Začínáme s C# a ASP.NET Core v aplikaci Visual Studio](tutorial-aspnet-core.md) jako první.

> [!TIP]
> Pokud chcete postupovat podle tohoto článku, ujistěte se, že máte nastavené nastavení C# pro Visual Studio. Informace o výběru nastavení pro integrované vývojové prostředí (IDE) najdete v tématu [Výběr nastavení prostředí](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Vytvořit nový soubor kódu

Začněte vytvořením nového souboru a přidáním nějakého kódu do něj.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio. Stisknutím klávesy **ESC** nebo kliknutím na **pokračovat bez kódu** v okně Start otevřete vývojové prostředí.

::: moniker-end

2. V nabídce **soubor** v řádku nabídek zvolte možnost **Nový**  >  **soubor**nebo stiskněte klávesu **CTRL** + **N**.

3. V dialogovém okně **nový soubor** v kategorii **Obecné** zvolte položku **Třída Visual C#** a pak zvolte možnost **otevřít**.

   V editoru se otevře nový soubor s kostrou třídy jazyka C#. (Všimněte si, že nemusíme vytvořit úplný projekt sady Visual Studio, abyste získali některé výhody, které Editor kódu nabízí. všechno, co potřebujete, je soubor kódu!)

   ![Soubor kódu C# v aplikaci Visual Studio](../media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Používání fragmentů kódu

Visual Studio poskytuje užitečné *fragmenty kódu* , které můžete použít k rychlému a snadnému vygenerování běžně používaných bloků kódu. [Fragmenty kódu](../../ide/code-snippets.md) jsou k dispozici pro různé programovací jazyky, včetně jazyků C#, Visual Basic a C++. Pojďme `void Main` do našeho souboru přidat fragment kódu jazyka C#.

1. Umístěte kurzor hned nad poslední pravou závorku **do souboru** a zadejte znaky (které si zapamatují `svm` `static void Main` &mdash; příliš velkou moc, Pokud nevíte, co to znamená).

   Zobrazí se automaticky otevírané okno s informacemi o `svm` fragmentu kódu.

   ![IntelliSense pro fragment kódu v aplikaci Visual Studio](../media/tutorial-intellisense-snippet.png)

1. Stiskněte klávesu **TAB** dvakrát pro vložení fragmentu kódu.

   Uvidíte, že `static void Main()` signatura metody se přidá do souboru. Metoda [Main ()](/dotnet/csharp/programming-guide/main-and-command-args/) je vstupním bodem pro aplikace v jazyce C#.

Dostupné fragmenty kódu se liší v různých programovacích jazycích. Můžete se podívat na dostupné fragmenty kódu pro váš jazyk, a to tak, že vyberete **Upravit**  >  **IntelliSense**  >  **Vložit fragment** nebo stisknout **CTRL** + **K**, **CTRL** + **X**a pak zvolíte složku vašeho jazyka. V jazyce C# seznam vypadá takto:

![Seznam fragmentů kódu v jazyce C#](../media/tutorial-code-snippet-list.png)

Seznam obsahuje fragmenty kódu pro vytvoření [třídy](/dotnet/csharp/programming-guide/classes-and-structs/classes), [konstruktoru](/dotnet/csharp/programming-guide/classes-and-structs/constructors), smyčky [for](/dotnet/csharp/language-reference/keywords/for) , příkazu [if](/dotnet/csharp/language-reference/keywords/if-else) nebo [Switch](/dotnet/csharp/language-reference/keywords/switch) a dalších.

## <a name="comment-out-code"></a>Kód odhlašovacího komentáře

Panel nástrojů, který je řádkem tlačítek pod řádkem nabídek v sadě Visual Studio, vám může při psaní kódu zvýšit produktivitu. Můžete například přepnout režim dokončování IntelliSense ([IntelliSense](../../ide/using-intellisense.md) je pomůcka pro kódování, která zobrazuje seznam odpovídající metody, mimo jiné), zvětšit nebo zmenšit odsazení řádku nebo kód komentáře, který nechcete kompilovat. V této části budeme komentovat nějaký kód.

![Panel nástrojů editoru](../media/tutorial-editor-toolbar.png)

1. Vložte následující kód do `Main()` těla metody.

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

1. Tuto proměnnou nepoužíváme `morewords` , ale můžeme ji použít později, takže ji nechceme úplně odstranit. Místo toho pojďme tyto řádky komentovat. Vyberte celou definici pro celý `morewords` středník a pak zvolte tlačítko **Přidat komentář k vybraným řádkům** na panelu nástrojů. Pokud dáváte přednost používání klávesnice, stiskněte klávesy **CTRL** + **K**, **CTRL** + **C**.

   ![Tlačítko odkomentovat](../media/tutorial-comment-out.png)

   Znaky komentáře jazyka C# `//` jsou přidány na začátek každého vybraného řádku, aby se přidal komentář k kódu.

## <a name="collapse-code-blocks"></a>Sbalit bloky kódu

Nechceme vidět prázdný [konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors) pro `Class1` , který se vygeneroval, takže pokud si chcete prohlédnout kód, Pojďme ho sbalit. Vyberte malé šedé pole se znaménkem mínus uvnitř něj v okraji prvního řádku konstruktoru. Nebo, pokud jste uživatel klávesnice, umístěte kurzor kamkoli do kódu konstruktoru a stiskněte **kombinaci kláves CTRL** + **m**, **CTRL** + **m**.

![Sbalit sbalení – tlačítko](../media/tutorial-collapse.png)

Blok kódu se sbalí jenom na první řádek následovaný třemi tečkami ( `...` ). Chcete-li znovu rozšířit blok kódu, klikněte na stejné šedé pole, ve kterém je nyní přihlášeno znaménkem plus, nebo stiskněte **kombinaci kláves CTRL** + **m**, **CTRL** + **m** znovu. Tato funkce se nazývá [sbalení a je](../../ide/outlining.md) obzvláště užitečná, když sbalíte dlouhé metody nebo celé třídy.

## <a name="view-symbol-definitions"></a>Zobrazit definice symbolů

Editor sady Visual Studio usnadňuje kontrolu definice typu, metody atd. Jedním ze způsobů je přejít na soubor, který obsahuje definici, například výběrem možnosti **Přejít k definici** nebo stisknutím klávesy **F12** kdekoliv, kde se odkazuje na symbol. Ještě rychlejší způsob, který nepřesouvá fokus ze souboru, ve kterém pracujete, je použití [náhledu definice](../../ide/go-to-and-peek-definition.md#peek-definition). Pojďme si prohlížet definici `string` typu.

1. Klikněte pravým tlačítkem na libovolný výskyt `string` a v nabídce obsah vyberte **Náhled definice** . Nebo stiskněte **ALT** + **F12**.

   Zobrazí se automaticky otevírané okno s definicí `String` třídy. V místním okně se můžete posouvat nebo dokonce prohlížet definici jiného typu z prohlíženého kódu.

   ![Náhled okna definice](../media/tutorial-peek-definition.png)

1. Zavřete okno s náhledem definice výběrem malého pole se znakem x v pravém horním rohu automaticky otevíraného okna.

## <a name="use-intellisense-to-complete-words"></a>Doplňování slov pomocí IntelliSense

[IntelliSense](../../ide/using-intellisense.md) je nevýznamný prostředek při kódování. Může zobrazit informace o dostupných členech typu nebo podrobnosti o parametrech pro různá přetížení metody. Pomocí technologie IntelliSense můžete také vyplnit slovo poté, co zadáte dostatečný počet znaků, které chcete určit jako nejednoznačnost. Pojďme přidat řádek kódu pro vytištění seřazených řetězců do okna konzoly, což je standardní místo pro výstup z programu k přechodu.

1. Pod `query` proměnnou začněte psát následující kód:

   ```csharp
   foreach (string str in qu
   ```

   Vidíte, že vám IntelliSense ukáže **rychlé informace** o `query` symbolu.

   ![Dokončování slov IntelliSense v aplikaci Visual Studio](../media/tutorial-intellisense-completion-list.png)

1. Chcete-li vložit zbytek slova `query` pomocí funkce dokončování slov v technologii IntelliSense, stiskněte klávesu **TAB**.

1. Dokončete blok kódu, aby vypadal jako následující kód. Můžete dokonce s použitím fragmentů kódu znovu vyzkoušet zadáním `cw` a následným stisknutím klávesy **TAB** pro generování `Console.WriteLine` kódu.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refaktorovat název

Nikdo nezíská kód napravo poprvé a jedna z věcí, kterou je třeba změnit, je název proměnné nebo metody. Pojďme si vyzkoušíme funkci [refaktoru](../../ide/refactoring-in-visual-studio.md) sady Visual Studio, která proměnnou přejmenuje `_words` na `words` .

1. Umístěte ukazatel myši nad definici `_words` proměnné a zvolte možnost **Přejmenovat** v místní nabídce nebo v místní nabídce nebo stiskněte klávesovou **zkratku CTRL** + **r**, **CTRL** + **r**.

   Automaticky otevíraná okna pro **přejmenování** se zobrazí v pravém horním rohu editoru.

1. Zadejte požadovaná **slova**názvu. Všimněte si, že odkaz na `words` v dotazu je také automaticky přejmenován. Než stisknete klávesu **ENTER**, zaškrtněte políčko **zahrnout komentáře** v automaticky otevíraném okně pro **přejmenování** .

   ![přejmenování dialogového okna](../media/tutorial-rename.png)

1.  Stiskněte **Enter**.

   Oba výskyty `words` byly přejmenovány a také odkaz na `words` Komentář kódu.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Další informace o projektech a řešeních](../tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také:

- [Fragmenty kódu](../../ide/code-snippets.md)
- [Navigace v kódu](../../ide/navigating-code.md)
- [Sbalování](../../ide/outlining.md)
- [Přejít k definici a Náhled definice](../../ide/go-to-and-peek-definition.md)
- [Refactoring](../../ide/refactoring-in-visual-studio.md)
- [Používání technologie IntelliSense](../../ide/using-intellisense.md)
