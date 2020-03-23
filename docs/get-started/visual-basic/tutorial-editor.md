---
title: Úvod k úpravám pro vývojáře jazyka Visual Basic
description: Tento 10minutový úvod do editoru kódu v sadě Visual Studio ukazuje některé způsoby, jak Visual Studio usnadňuje psaní, navigaci a pochopení kódu jazyka Visual Basic.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 695b1600aedb30a9e75a7829af4bac400f069922
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75584605"
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

Tento článek předpokládá, že jste již obeznámeni s visual basic. Pokud nejste, doporučujeme nejprve se podívat na kurz, jako [je Začínáme s Visual Basicem v sadě Visual Studio.](../../get-started/visual-basic/tutorial-console.md)

> [!TIP]
> Chcete-li postupovat spolu s tímto článkem, ujistěte se, že máte nastavení jazyka visual basic vybrané pro Visual Studio. Informace o výběru nastavení integrovaného vývojového prostředí (IDE) naleznete v [tématu Výběr nastavení prostředí](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Vytvoření nového souboru kódu

Začněte vytvořením nového souboru a přidáním kódu.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio. Stisknutím **klávesy Esc** nebo klepnutím na tlačítko **Pokračovat bez kódu** v počátečním okně otevřete vývojové prostředí.

::: moniker-end

2. Z nabídky **Soubor** na řádku nabídek zvolte **Nový soubor**.

3. V dialogovém okně **Nový soubor** v kategorii **Obecné** zvolte Třída jazyka **Visual Basic**a pak zvolte **Otevřít**.

   V editoru se otevře nový soubor s kostrou třídy jazyka Visual Basic. (Už si můžete všimnout, že není třeba vytvořit úplný projekt sady Visual Studio získat některé z výhod, které editor kódu nabízí, jako je například zvýraznění syntaxe. Vše, co potřebujete, je soubor kódu!)

   ![Soubor kódu jazyka Visual Basic v sadě Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Používání fragmentů kódu

Visual Studio poskytuje užitečné *fragmenty kódu,* které můžete použít k rychlému a snadnému generování běžně používaných bloků kódu. [Fragmenty kódu](../../ide/code-snippets.md) jsou k dispozici pro různé programovací jazyky včetně jazyka Visual Basic, C# a C++. Přidáme fragment dílčí **položky** jazyka do našeho souboru.

1. Umístěte kurzor nad čáru, která říká `End Class`, a zadejte **sub**.

   Zobrazí se rozbalovací dialogové okno `Sub` s informacemi o klíčovém slově a o tom, jak vložit fragment **dílčího** kódu.

   ![Technologie IntelliSense pro fragment kódu v sadě Visual Studio](media/tutorial-intellisense-snippet.png)

1. Dvakrát stiskněte **klávesu Tab,** chcete-li vložit fragment kódu.

   Osnova pro proceduru `MySub()` Sub je přidána do souboru.

Dostupné fragmenty kódu se u různých programovacích jazyků liší. Na dostupné fragmenty kódu jazyka Visual Basic se můžete podívat **tak,** > že zvolíte Upravit**výstřižk** vložení technologie**IntelliSense** > (nebo stiskněte **kombinaci kláves Ctrl**+**K**, **Ctrl**+**X**). Pro jazyk Visual Basic jsou fragmenty kódu k dispozici pro následující kategorie:

![Seznam fragmentů kódu jazyka Visual Basic](media/tutorial-code-snippet-list.png)

Existují úryvky pro určení, zda soubor existuje v počítači, zápis do textového souboru, čtení hodnoty registru, spuštění dotazu SQL, vytvoření [pro každý... Další prohlášení](/dotnet/visual-basic/language-reference/statements/for-each-next-statement), a mnoho dalších.

## <a name="comment-out-code"></a>Zakomentovat kód

Panel nástrojů, což je řádek tlačítek pod panelem nabídek v sadě Visual Studio, vám může pomoci zvýšit produktivitu při kódu. Můžete například přepnout režim dokončení technologie IntelliSense, zvětšit nebo snížit odsazení řádku nebo zakomentovat kód, který nechcete zkompilovat. [(IntelliSense](../../ide/using-intellisense.md) je kódovací pomůcka, která zobrazuje seznam odpovídajících metod, mimo jiné.) V této části budeme komentovat nějaký kód.

![Tlačítka panelu nástrojů Editor](media/tutorial-editor-toolbar.png)

1. Vložte následující kód `MySub()` do těla procedury.

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

1. Pole nepoužíváme, `morewords` ale můžeme ho použít později, takže ho nechceme úplně odstranit. Místo toho pojďme komentovat tyto řádky. Vyberte celou `morewords` definici závěrečné složené závorky a pak zvolte **tlačítko Vykomentovat vybrané řádky** na panelu nástrojů. Pokud dáváte přednost použití klávesnice, stiskněte **kombinaci kláves Ctrl**+**K**, **Ctrl**+**C**.

   ![Tlačítko Zakomentovat](media/tutorial-comment-out.png)

   Znak `'` komentáře jazyka je přidán na začátek každého vybraného řádku, aby se kód zakomentoval.

## <a name="collapse-code-blocks"></a>Sbalit bloky kódu

Části kódu můžete sbalit a zaměřit se pouze na části, které vás zajímají. Chcete-li cvičit, sbalte `_words` pole na jeden řádek kódu. Vyberte malé šedé pole se znaménkem mínus uvnitř na okraji čáry, která říká `Dim _words = New String() {`. Pokud jste uživatelem klávesnice, umístěte kurzor na libovolné místo v definici pole a stiskněte **klávesu Ctrl**+**M**, **Ctrl**+**M**.

![Tlačítko Prosbalení osnovy](media/tutorial-collapse.png)

Blok kódu se sbalí pouze na první řádek`...`následovaný třemi tečkami ( ). Chcete-li znovu rozbalit blok kódu, klepněte na stejné šedé pole, ve které je nyní znaménko plus, nebo stiskněte **znovu kombinaci kláves Ctrl**+**M**, **Ctrl**+**M.** Tato funkce se nazývá [Osnova](../../ide/outlining.md) a je zvláště užitečná, když sbalíte dlouhé metody nebo celé třídy.

## <a name="view-symbol-definitions"></a>Zobrazení definic symbolů

Editor sady Visual Studio usnadňuje kontrolu definice typu, metody atd. Jedním ze způsobů je přejít na soubor, který obsahuje definici, například výběrem **přejít na definici** kdekoli symbol je odkazován. Ještě rychlejší způsob, který nepřesune vaše zaměření od souboru, ve kterém pracujete, je použití [definice náhledu](../../ide/go-to-and-peek-definition.md#peek-definition). Podívejme se na definici `String` typu.

1. Klikněte pravým tlačítkem myši na slovo `String` a z nabídky obsahu zvolte Peek **Definition.** Nebo stiskněte **klávesu Alt**+**F12**.

   Zobrazí se automaticky otevírané `String` okno s definicí třídy. Můžete se posouvat v rozbalovacím okně nebo dokonce nahlédnout do definice jiného typu z kódu náhledu.

   ![Okno definice náhledu](media/tutorial-peek-definition.png)

1. Zavřete okno definice náhledu výběrem malého rámečku s "x" v pravém horním rohu vyskakovacího okna.

## <a name="use-intellisense-to-complete-words"></a>K dokončení slov použijte službu IntelliSense.

[Technologie IntelliSense](../../ide/using-intellisense.md) je při kódování neocenitelným zdrojem. Může zobrazit informace o dostupných členech typu nebo podrobnosti o parametru pro různá přetížení metody. Můžete také použít IntelliSense k dokončení slova poté, co zadáte dostatek znaků, abyste ho rozpletli. Přidáme řádek kódu pro tisk uspořádaných řetězců do okna konzoly, což je standardní místo pro výstup z programu.

1. Pod `query` proměnnou začněte psát následující kód:

   ```vb
   For Each str In qu
   ```

   Zobrazí se informace o **Quick Info** symbolu, `query` která zobrazuje technologie IntelliSense.

   ![Dokončování slov IntelliSense v sadě Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Chcete-li vložit zbytek slova `query` pomocí funkce dokončování slov technologie IntelliSense, stiskněte **klávesu Tab**.

1. Dokončete blok kódu tak, aby vypadal jako následující kód.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Refaktorovat název

Nikdo dostane kód právo napoprvé a jedna z věcí, které budete muset změnit, je název proměnné nebo metody. Vyzkoušejte funkci [refaktorování](../../ide/refactoring-in-visual-studio.md) sady Visual Studio a `_words` přejmenujte proměnnou na `words`.

1. Umístěte kurzor nad definici `_words` proměnné a zvolte **Přejmenovat** z nabídky pravým tlačítkem myši nebo kontextové nabídky.

   V pravém horním rohu editoru se zobrazí dialogové okno **Přejmenování.**

1. S proměnnou `_words` stále vybranou, zadejte požadovaný název **slov**. Všimněte si, `words` že odkaz na v dotazu je také automaticky přejmenován. Než stisknete **Enter** nebo kliknete na **Použít**, zaškrtněte v rozbalovacím poli **Přejmenovat** políčko **Zahrnout komentáře.**

   ![přejmenování dialogového okna](media/tutorial-rename.png)

1. Stiskněte **Enter** nebo na **Použít**.

   Oba výskyty `words` jsou přejmenovány, stejně `words` jako odkaz na v komentáři kódu.

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
