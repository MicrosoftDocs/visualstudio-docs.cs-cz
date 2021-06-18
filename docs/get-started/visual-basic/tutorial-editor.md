---
title: Úvod do úprav pro vývojáře Visual Basic
description: Tento 10 minutový Úvod do editoru kódu v aplikaci Visual Studio ukazuje některé způsoby, jak Visual Studio usnadňuje psaní, navigaci a porozumění Visual Basic kódu.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 56f6570b633941c8f7102e245b7668cd31936f83
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308360"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>Naučte se používat editor kódu s Visual Basic

V tomto 10 minutách úvodu do editoru kódu v aplikaci Visual Studio přidáme kód do souboru, abyste se mohli podívat na některé ze způsobů, které Visual Studio dělá při psaní, navigaci a porozumění kódu Visual Basic snazší.

::: moniker range="vs-2017"

> [!TIP]
> Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Pokud jste ještě nenainstalovali Visual Studio Preview, můžete si ho nainstalovat zdarma na stránku se [soubory ke stažení pro Visual studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) .

::: moniker-end

V tomto článku se předpokládá, že už jste obeznámeni s Visual Basic. Pokud nejste, doporučujeme se podívat na kurz, například [Začínáme s Visual Basic v aplikaci Visual Studio](../../get-started/visual-basic/tutorial-console.md) jako první.

> [!TIP]
> Pokud chcete postupovat podle tohoto článku, ujistěte se, že máte vybraná nastavení Visual Basic pro Visual Studio. Informace o výběru nastavení pro integrované vývojové prostředí (IDE) najdete v tématu [Výběr nastavení prostředí](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Vytvořit nový soubor kódu

Začněte vytvořením nového souboru a přidáním nějakého kódu do něj.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio. Stisknutím klávesy **ESC** nebo kliknutím na **pokračovat bez kódu** v okně Start otevřete vývojové prostředí.

::: moniker-end

2. V nabídce **soubor** na řádku nabídek vyberte možnost **nový soubor**.

3. V dialogovém okně **nový soubor** v kategorii **obecné** zvolte položku **Visual Basic třída** a pak zvolte možnost **otevřít**.

   V editoru se otevře nový soubor s kostrou Visual Basic třídy. (Už si můžete všimnout, že nemusíte vytvářet úplný projekt sady Visual Studio, abyste získali některé výhody, které Editor kódu nabízí, jako je například zvýrazňování syntaxe. Vše, co potřebujete, je soubor kódu!)

   ![Soubor kódu Visual Basic v aplikaci Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Používání fragmentů kódu

Visual Studio poskytuje užitečné *fragmenty kódu* , které můžete použít k rychlému a snadnému vygenerování běžně používaných bloků kódu. [Fragmenty kódu](../../ide/code-snippets.md) jsou k dispozici pro různé programovací jazyky, včetně Visual Basic, C# a C++. Pojďme přidat **dílčí** fragment Visual Basic do našeho souboru.

1. Umístěte kurzor nad řádek, který říká `End Class` , a zadejte **Sub**.

   Zobrazí se automaticky otevírané okno s informacemi o `Sub` klíčovém slově a způsobu vložení **dílčího** fragmentu kódu.

   ![IntelliSense pro fragment kódu v aplikaci Visual Studio](media/tutorial-intellisense-snippet.png)

1. Stiskněte klávesu **TAB** dvakrát pro vložení fragmentu kódu.

   Osnova pro proceduru Sub `MySub()` je přidána do souboru.

Dostupné fragmenty kódu se liší v různých programovacích jazycích. Můžete se podívat na dostupné fragmenty kódu pro Visual Basic tím, že vyberete **Upravit**  >  **IntelliSense**  >  **Vložit fragment** kódu (nebo stisknout **CTRL** + **K**, **CTRL** + **X**). Pro Visual Basic jsou fragmenty kódu k dispozici pro následující kategorie:

![Visual Basic seznam fragmentů kódu](media/tutorial-code-snippet-list.png)

Existují fragmenty pro zjištění, zda soubor existuje v počítači, zápis do textového souboru, čtení hodnoty registru, provádění dotazu SQL a vytvoření příkazu [pro každý... Další příkaz](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)a mnoho dalších.

## <a name="comment-out-code"></a>Kód odhlašovacího komentáře

Panel nástrojů, který je řádkem tlačítek pod řádkem nabídek v sadě Visual Studio, vám může při psaní kódu zvýšit produktivitu. Můžete například přepnout režim dokončování IntelliSense, zvětšit nebo zmenšit odsazení řádku nebo komentovat kód, který nechcete kompilovat. ([IntelliSense](../../ide/using-intellisense.md) je podpora kódování, která zobrazuje seznam metod porovnání, mimo jiné.) V této části budeme komentovat nějaký kód.

![Tlačítka panelu nástrojů editoru](media/tutorial-editor-toolbar.png)

1. Do těla procedury vložte následující kód `MySub()` .

   ```vb
   ' _words is a string array that we'll sort alphabetically
   Dim _words = New String() {
   "the",
   "quick",
   "brown",
   "fox",
   "jumps"
   }

   Dim morewords = New String() {
   "over",
   "the",
   "lazy",
   "dog"
   }

   Dim query = From word In _words
               Order By word.Length
               Select word
   ```

1. Nepoužíváme `morewords` pole, ale můžeme ho použít později, takže ho nechceme úplně odstranit. Místo toho pojďme tyto řádky komentovat. Vyberte celou definici `morewords` pro pravou složenou závorku a pak zvolte tlačítko **Přidat komentář k vybraným řádkům** na panelu nástrojů. Pokud dáváte přednost používání klávesnice, stiskněte klávesy **CTRL** + **K**, **CTRL** + **C**.

   ![Tlačítko odkomentovat](media/tutorial-comment-out.png)

   Znak komentáře Visual Basic `'` se přidá na začátek každého vybraného řádku, aby se přidal komentář ke kódu.

## <a name="collapse-code-blocks"></a>Sbalit bloky kódu

Můžete sbalit části kódu a soustředit se jenom na části, které vás zajímají. Chcete-li postupovat, sbalte `_words` pole na jeden řádek kódu. Vyberte malé šedé pole s znaménkem mínus uvnitř něj v okraji řádku, který říká `Dim _words = New String() {` . Nebo, pokud jste uživatel klávesnice, umístěte kurzor kamkoli do definice pole a stiskněte **kombinaci kláves CTRL** + **m**, **CTRL** + **m**.

![Sbalit sbalení – tlačítko](media/tutorial-collapse.png)

Blok kódu se sbalí jenom na první řádek následovaný třemi tečkami ( `...` ). Chcete-li znovu rozšířit blok kódu, klikněte na stejné šedé pole, ve kterém je nyní přihlášeno znaménkem plus, nebo stiskněte **kombinaci kláves CTRL** + **m**, **CTRL** + **m** znovu. Tato funkce se nazývá [sbalení a je](../../ide/outlining.md) obzvláště užitečná, když sbalíte dlouhé metody nebo celé třídy.

## <a name="view-symbol-definitions"></a>Zobrazit definice symbolů

Editor sady Visual Studio usnadňuje kontrolu definice typu, metody atd. Jedním ze způsobů je přejít na soubor, který obsahuje definici, například výběrem možnosti **Přejít k definici** kdekoli, kde se odkazuje na symbol. Ještě rychlejší způsob, který nepřesouvá fokus ze souboru, ve kterém pracujete, je použití [náhledu definice](../../ide/go-to-and-peek-definition.md#peek-definition). Pojďme si prohlížet definici `String` typu.

1. Klikněte pravým tlačítkem myši na slovo `String` a v nabídce obsah vyberte možnost **Náhled definice** . Nebo stiskněte **ALT** + **F12**.

   Zobrazí se automaticky otevírané okno s definicí `String` třídy. V místním okně se můžete posouvat nebo dokonce prohlížet definici jiného typu z prohlíženého kódu.

   ![Náhled okna definice](media/tutorial-peek-definition.png)

1. Zavřete okno s náhledem definice výběrem malého pole se znakem x v pravém horním rohu automaticky otevíraného okna.

## <a name="use-intellisense-to-complete-words"></a>Doplňování slov pomocí IntelliSense

[IntelliSense](../../ide/using-intellisense.md) je nevýznamný prostředek při kódování. Může zobrazit informace o dostupných členech typu nebo podrobnosti o parametrech pro různá přetížení metody. Pomocí technologie IntelliSense můžete také vyplnit slovo poté, co zadáte dostatečný počet znaků, které chcete určit jako nejednoznačnost. Pojďme přidat řádek kódu pro vytištění seřazených řetězců do okna konzoly, což je standardní místo pro výstup z programu k přechodu.

1. Pod `query` proměnnou začněte psát následující kód:

   ```vb
   For Each str In qu
   ```

   Vidíte, že vám IntelliSense ukáže **rychlé informace** o `query` symbolu.

   ![Dokončování slov IntelliSense v aplikaci Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Chcete-li vložit zbytek slova `query` pomocí funkce dokončování slov v technologii IntelliSense, stiskněte klávesu **TAB**.

1. Dokončete blok kódu, aby vypadal jako následující kód.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Refaktorovat název

Nikdo nezíská kód napravo poprvé a jedna z věcí, kterou je třeba změnit, je název proměnné nebo metody. Pojďme si vyzkoušíme funkci [refaktoru](../../ide/refactoring-in-visual-studio.md) sady Visual Studio, která proměnnou přejmenuje `_words` na `words` .

1. Umístěte kurzor na definici `_words` proměnné a v místní nabídce klikněte pravým tlačítkem myši na možnost **Přejmenovat** .

   Automaticky otevíraná okna pro **přejmenování** se zobrazí v pravém horním rohu editoru.

1. Když je proměnná `_words` stále vybraná, zadejte požadované názvy **slov**. Všimněte si, že odkaz na `words` v dotazu je také automaticky přejmenován. Před stisknutím klávesy **ENTER** nebo kliknutím na možnost **použít** zaškrtněte políčko **zahrnout komentáře** v automaticky otevíraném okně pro **přejmenování** .

   ![přejmenování dialogového okna](media/tutorial-rename.png)

1. Stiskněte klávesu **ENTER** nebo klikněte na **použít**.

   Oba výskyty `words` jsou přejmenovány a také odkaz na `words` Komentář kódu.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Další informace o projektech a řešeních](tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také

- [Fragmenty kódu](../../ide/code-snippets.md)
- [Navigace v kódu](../../ide/navigating-code.md)
- [Sbalování](../../ide/outlining.md)
- [Přejít k definici a Náhled definice](../../ide/go-to-and-peek-definition.md)
- [Refactoring](../../ide/refactoring-in-visual-studio.md)
- [Používání technologie IntelliSense](../../ide/using-intellisense.md)
