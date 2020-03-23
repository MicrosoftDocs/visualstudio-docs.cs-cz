---
title: Úvod k úpravám pro vývojáře jazyka C#
description: Tento 10minutový úvod do editoru kódu v sadě Visual Studio ukazuje některé způsoby, jak Visual Studio usnadňuje psaní, navigaci a pochopení kódu Jazyka C#.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75590433"
---
# <a name="learn-to-use-the-code-editor"></a>Naučte se používat editor kódu

V tomto 10minutovém úvodu do editoru kódu v sadě Visual Studio přidáme do souboru kód, který se bude zabývat některými způsoby, jakými Visual Studio usnadňuje psaní, navigaci a pochopení kódu.

::: moniker range="vs-2017"

> [!TIP]
> Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

Tento článek předpokládá, že jste již obeznámeni s C#. Pokud nejste, doporučujeme nejprve se podívat na kurz, jako [je Začínáme s C# a ASP.NET Core v sadě Visual Studio.](tutorial-aspnet-core.md)

> [!TIP]
> Chcete-li postupovat spolu s tímto článkem, ujistěte se, že máte c# nastavení vybrané pro Visual Studio. Informace o výběru nastavení integrovaného vývojového prostředí (IDE) naleznete v [tématu Výběr nastavení prostředí](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Vytvoření nového souboru kódu

Začněte vytvořením nového souboru a přidáním kódu.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio. Stisknutím **klávesy Esc** nebo klepnutím na tlačítko **Pokračovat bez kódu** v počátečním okně otevřete vývojové prostředí.

::: moniker-end

2. Z nabídky **Soubor** na řádku nabídek zvolte **Nový** > **soubor**nebo stiskněte **Ctrl**+**N**.

3. V dialogovém okně **Nový soubor** v kategorii **Obecné** zvolte **Visual C# Class**a pak zvolte **Otevřít**.

   V editoru se otevře nový soubor s kostrou třídy C#. (Všimněte si, že nemusíme vytvářet úplný projekt sady Visual Studio, abychom získali některé výhody, které editor kódu nabízí; vše, co potřebujete, je soubor kódu!)

   ![Soubor kódu Jazyka C# v sadě Visual Studio](../media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Používání fragmentů kódu

Visual Studio poskytuje užitečné *fragmenty kódu,* které můžete použít k rychlému a snadnému generování běžně používaných bloků kódu. [Fragmenty kódu](../../ide/code-snippets.md) jsou k dispozici pro různé programovací jazyky včetně C#, Visual Basic a C++. Přidáme fragment jazyka `void Main` C# do našeho souboru.

1. Umístěte kurzor těsně nad **}** konečnou uzavírací závorku `svm` } do `static void Main`souboru a zadejte znaky (což &mdash;znamená, že se nemusíte příliš obávat, pokud nevíte, co to znamená).

   Zobrazí se rozbalovací dialogové okno `svm` s informacemi o fragmentu kódu.

   ![Technologie IntelliSense pro fragment kódu v sadě Visual Studio](../media/tutorial-intellisense-snippet.png)

1. Dvakrát stiskněte **klávesu Tab,** chcete-li vložit fragment kódu.

   Zobrazí se `static void Main()` podpis metody získat přidány do souboru. [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) Metoda je vstupní bod pro aplikace Jazyka C#.

Dostupné fragmenty kódu se u různých programovacích jazyků liší. Na dostupné fragmenty kódu pro váš jazyk se můžete podívat tak, že zvolíte **Upravit** > **výstřižk** vložení technologie**IntelliSense** > nebo stisknutím **kláves Ctrl**+**K**, **Ctrl**+**X**a pak vyberete složku jazyka. Pro C#, seznam vypadá takto:

![Seznam fragmentů kódu jazyka C#](../media/tutorial-code-snippet-list.png)

Seznam obsahuje úryvky pro vytvoření [třídy](/dotnet/csharp/programming-guide/classes-and-structs/classes), [konstruktoru](/dotnet/csharp/programming-guide/classes-and-structs/constructors), smyčky [for,](/dotnet/csharp/language-reference/keywords/for) příkazu [if](/dotnet/csharp/language-reference/keywords/if-else) nebo [switch](/dotnet/csharp/language-reference/keywords/switch) a dalších.

## <a name="comment-out-code"></a>Zakomentovat kód

Panel nástrojů, což je řádek tlačítek pod panelem nabídek v sadě Visual Studio, vám může pomoci zvýšit produktivitu při kódu. Můžete například přepnout režim dokončení technologie IntelliSense ([Technologie IntelliSense](../../ide/using-intellisense.md) je kódovací pomůcka, která mimo jiné zobrazuje seznam odpovídajících metod, zvýšit nebo snížit odsazení řádku nebo zakomentovat kód, který nechcete zkompilovat. V této části budeme komentovat nějaký kód.

![Panel nástrojů Editor](../media/tutorial-editor-toolbar.png)

1. Vložte následující kód `Main()` do těla metody.

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

1. Proměnnou `morewords` nepoužíváme, ale můžeme ji použít později, takže ji nechceme úplně odstranit. Místo toho pojďme komentovat tyto řádky. Vyberte celou `morewords` definici uzavíracího středníku a pak zvolte **tlačítko Vykomentovat vybrané řádky** na panelu nástrojů. Pokud dáváte přednost použití klávesnice, stiskněte **kombinaci kláves Ctrl**+**K**, **Ctrl**+**C**.

   ![Tlačítko Zakomentovat](../media/tutorial-comment-out.png)

   Znaky `//` komentáře Jazyka C# jsou přidány na začátek každého vybraného řádku, aby se kód zakomentoval.

## <a name="collapse-code-blocks"></a>Sbalit bloky kódu

Nechceme vidět prázdný [konstruktor,](/dotnet/csharp/programming-guide/classes-and-structs/constructors) `Class1` který byl vygenerován, takže abychom zpřehledňovali náš pohled na kód, sbalte ho. Zvolte malé šedé pole se znaménkem mínus uvnitř na okraji prvního řádku konstruktoru. Pokud jste uživatelem klávesnice, umístěte kurzor na libovolné místo v kódu konstruktoru a stiskněte **ctrl**+**m**, **Ctrl**+**M**.

![Tlačítko Prosbalení osnovy](../media/tutorial-collapse.png)

Blok kódu se sbalí pouze na první řádek`...`následovaný třemi tečkami ( ). Chcete-li znovu rozbalit blok kódu, klepněte na stejné šedé pole, ve které je nyní znaménko plus, nebo stiskněte **znovu kombinaci kláves Ctrl**+**M**, **Ctrl**+**M.** Tato funkce se nazývá [Osnova](../../ide/outlining.md) a je zvláště užitečná, když sbalíte dlouhé metody nebo celé třídy.

## <a name="view-symbol-definitions"></a>Zobrazení definic symbolů

Editor sady Visual Studio usnadňuje kontrolu definice typu, metody atd. Jedním ze způsobů je přejít na soubor, který obsahuje definici, například výběrem **přejít na definici** nebo stisknutím **klávesy F12** kdekoli, kde je symbol odkazován. Ještě rychlejší způsob, který nepřesune vaše zaměření od souboru, ve kterém pracujete, je použití [definice náhledu](../../ide/go-to-and-peek-definition.md#peek-definition). Podívejme se na definici `string` typu.

1. Klikněte pravým tlačítkem `string` myši na jakýkoli výskyt a z nabídky obsahu zvolte **Peek Definition.** Nebo stiskněte **klávesu Alt**+**F12**.

   Zobrazí se automaticky otevírané `String` okno s definicí třídy. Můžete se posouvat v rozbalovacím okně nebo dokonce nahlédnout do definice jiného typu z kódu náhledu.

   ![Okno definice náhledu](../media/tutorial-peek-definition.png)

1. Zavřete okno definice náhledu výběrem malého rámečku s "x" v pravém horním rohu vyskakovacího okna.

## <a name="use-intellisense-to-complete-words"></a>K dokončení slov použijte službu IntelliSense.

[Technologie IntelliSense](../../ide/using-intellisense.md) je při kódování neocenitelným zdrojem. Může zobrazit informace o dostupných členech typu nebo podrobnosti o parametru pro různá přetížení metody. Můžete také použít IntelliSense k dokončení slova poté, co zadáte dostatek znaků, abyste ho rozpletli. Přidáme řádek kódu pro tisk uspořádaných řetězců do okna konzoly, což je standardní místo pro výstup z programu.

1. Pod `query` proměnnou začněte psát následující kód:

   ```csharp
   foreach (string str in qu
   ```

   Zobrazí se informace o **Quick Info** symbolu, `query` která zobrazuje technologie IntelliSense.

   ![Dokončování slov IntelliSense v sadě Visual Studio](../media/tutorial-intellisense-completion-list.png)

1. Chcete-li vložit zbytek slova `query` pomocí funkce dokončování slov technologie IntelliSense, stiskněte **klávesu Tab**.

1. Dokončete blok kódu tak, aby vypadal jako následující kód. Můžete dokonce procvičit pomocí fragmenty kódu `cw` znovu zadáním a `Console.WriteLine` stisknutím **klávesy Tab** dvakrát generovat kód.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refaktorovat název

Nikdo dostane kód právo napoprvé a jedna z věcí, které budete muset změnit, je název proměnné nebo metody. Vyzkoušejte funkci [refaktorování](../../ide/refactoring-in-visual-studio.md) sady Visual Studio a `_words` přejmenujte proměnnou na `words`.

1. Umístěte kurzor nad definici `_words` proměnné a zvolte **Přejmenovat** z nabídky pravým tlačítkem myši nebo v místní nabídce nebo stiskněte **Ctrl**+**R**, **Ctrl**+**R**.

   V pravém horním rohu editoru se zobrazí dialogové okno **Přejmenování.**

1. Zadejte požadovaná **názvová slova**. Všimněte si, `words` že odkaz na v dotazu je také automaticky přejmenován. Před stisknutím **klávesy Enter**zaškrtněte políčko **Zahrnout komentáře** do pole **Přejmenovat.**

   ![přejmenování dialogového okna](../media/tutorial-rename.png)

1. Stiskněte **Enter**.

   Oba výskyty `words` byly přejmenovány, stejně `words` jako odkaz na v komentáři kódu.

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
