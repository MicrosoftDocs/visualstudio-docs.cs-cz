---
title: Úvod do úprav pro Visual Basic vývojáře
description: Tento 10minutový úvod do editoru kódu v Visual Studio ukazuje některé způsoby, jak Visual Studio usnadňuje psaní, navigaci a pochopení Visual Basic kódu.
ms.custom:
- vs-acquisition
- seodec18
- get-started
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
ms.openlocfilehash: fe411074c95db15fde4819ffb07eca39a05e844d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390161"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>Naučte se používat editor kódu s Visual Basic

V tomto 10minutového úvodu do editoru kódu v Visual Studio přidáme do souboru kód, který se podívá na některé ze způsobů, jak Visual Studio usnadňuje psaní, navigaci a pochopení Visual Basic kódu.

::: moniker range="vs-2017"

> [!TIP]
> Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Pokud jste si ještě nenainstalujete Visual Studio Preview, nainstalujte si ho zdarma na [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) downloads.

::: moniker-end

Tento článek předpokládá, že už máte zkušenosti s Visual Basic. Pokud ne, doporučujeme, abyste se nejprve podívali na kurz, například Začínáme s [Visual Basic v Visual Studio.](../../get-started/visual-basic/tutorial-console.md)

> [!TIP]
> Pokud chcete postupovat podle pokynů v tomto článku, ujistěte se, že Visual Basic nastavení pro Visual Studio. Informace o výběru nastavení pro integrované vývojové prostředí (IDE) najdete v tématu [Výběr nastavení prostředí.](visual-studio-ide.md#select-environment-settings)

## <a name="create-a-new-code-file"></a>Vytvoření nového souboru kódu

Začněte vytvořením nového souboru a přidáním kódu do něj.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio. Stisknutím **klávesy Esc** nebo **kliknutím na** Pokračovat bez kódu v úvodním okně otevřete vývojové prostředí.

::: moniker-end

2. V **nabídce File** (Soubor) na řádku nabídek zvolte **New File (Nový soubor).**

3. V dialogovém **okně Nový** soubor v **kategorii** Obecné zvolte **Visual Basic a** pak zvolte **Otevřít.**

   V editoru se otevře nový soubor s kostru Visual Basic třídy. (Už si můžete všimnout, že nemusíte vytvářet úplný projekt Visual Studio, abyste získali některé z výhod, které editor kódu nabízí, například zvýraznění syntaxe. Potřebujete jen soubor kódu.)

   ![Visual Basic souboru kódu v Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Používání fragmentů kódu

Visual Studio poskytuje užitečné *fragmenty* kódu, které můžete použít k rychlému a snadnému generování běžně používaných bloků kódu. [Fragmenty kódu jsou](../../ide/code-snippets.md) k dispozici pro různé programovací jazyky, včetně Visual Basic, C# a C++. Pojďme do souboru přidat Visual Basic **Sub.**

1. Umístěte kurzor nad řádek s textem `End Class` a zadejte **sub**.

   Zobrazí se automaticky otevírané dialogové okno s informacemi o klíčovém slově a o `Sub` tom, jak vložit fragment **kódu Sub.**

   ![IntelliSense pro fragment kódu v Visual Studio](media/tutorial-intellisense-snippet.png)

1. Stisknutím **klávesy Tab** dvakrát vložte fragment kódu.

   Osnova procedury Sub `MySub()` se přidá do souboru .

Dostupné fragmenty kódu se liší pro různé programovací jazyky. Dostupné fragmenty kódu pro váš Visual Basic můžete zobrazit tak, že zvolíte Upravit fragment kódu vložení  >  **IntelliSense**  >   (nebo  +   + stisknete Ctrl K , Ctrl X ). Například Visual Basic fragmenty kódu dostupné pro následující kategorie:

![Visual Basic seznamu fragmentů kódu](media/tutorial-code-snippet-list.png)

Existují fragmenty kódu, které určují, jestli v počítači existuje soubor, zapisování do textového souboru, čtení hodnoty registru, spuštění dotazu SQL, vytvoření příkazu [For Each... Další příkaz](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)a mnoho dalších.

## <a name="comment-out-code"></a>Okomentování kódu

Panel nástrojů, což je řádek tlačítek pod řádkem nabídek v Visual Studio, vám může pomoct zvýšit produktivitu při práci s kódem. Můžete například přepnout režim dokončování IntelliSense, zvětšit nebo zmenšit odsazení řádku nebo okomentovat kód, který nechcete kompilovat. ([IntelliSense](../../ide/using-intellisense.md) je kódovací pomůcka, která mimo jiné zobrazuje seznam odpovídajících metod.) V této části zakomentujeme nějaký kód.

![Tlačítka panelu nástrojů editoru](media/tutorial-editor-toolbar.png)

1. Do těla procedury vložte `MySub()` následující kód.

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

1. Toto pole nebudeme používat, ale můžeme ho použít později, takže ho nechcete úplně `morewords` odstranit. Místo toho tyto řádky zakomentujeme. Vyberte celou definici u uzavírací složené závorky a pak zvolte tlačítko Okomentovat vybrané řádky `morewords` na panelu nástrojů.  Pokud dáváte přednost použití klávesnice, stiskněte **Ctrl** + **K** a **Ctrl** + **C.**

   ![Tlačítko Pro okomentování](media/tutorial-comment-out.png)

   Znak Visual Basic se přidá na začátek každého vybraného řádku, aby se kód `'` okomentoval.

## <a name="collapse-code-blocks"></a>Sbalení bloků kódu

Můžete sbalit oddíly kódu a zaměřit se pouze na části, které vás zajímají. Procvičme si sbalení `_words` pole na jeden řádek kódu. Vyberte malé šedé pole se znaménkem minus uvnitř na okraji řádku s textem `Dim _words = New String() {` . Nebo, pokud jste uživatel klávesnice, umístěte kurzor kamkoli do definice pole a stiskněte **Ctrl** + **M**, **Ctrl** + **M**.

![Sbalení tlačítka](media/tutorial-collapse.png)

Blok kódu se sbalí jenom na první řádek a za ním tři tečky ( `...` ). Pokud chcete blok kódu znovu rozbalit, klikněte na stejné šedé pole, ve které je teď znaménko plus, nebo znovu stiskněte **Ctrl** + **M**, **Ctrl** + **M.** Tato funkce se nazývá [osnova](../../ide/outlining.md) a je zvláště užitečná, když sbalíte dlouhé metody nebo celé třídy.

## <a name="view-symbol-definitions"></a>Zobrazení definic symbolů

Editor Visual Studio usnadňuje kontrolu definice typu, metody atd. Jedním ze způsobů je přejít na soubor, který obsahuje definici, například výběrem možnosti **Přejít** k definici všude, kde se symbol odkazuje. Ještě rychlejší způsob, jak přesunout fokus od souboru, ve které pracujete, je použít náhled [definice](../../ide/go-to-and-peek-definition.md#peek-definition). Pojďme se podívat na definici `String` typu.

1. Klikněte pravým tlačítkem na slovo a v nabídce obsahu zvolte Náhled `String` definice.  Nebo stiskněte **Klávesu Alt** + **F12**.

   Zobrazí se automaticky otevírané okno s definicí `String` třídy . V automaticky otevíraných oknech se můžete posouvat nebo se v náhledu kódu dokonce podívat na definici jiného typu.

   ![Okno Náhled definice](media/tutorial-peek-definition.png)

1. Zavřete okno náhledu definice výběrem malého pole s x v pravém horním rohu automaticky otevíraných oken.

## <a name="use-intellisense-to-complete-words"></a>Použití IntelliSense k dokončení slov

[IntelliSense](../../ide/using-intellisense.md) je neocenitelný prostředek při psaní kódu. Může zobrazit informace o dostupných členech typu nebo podrobnosti o parametru pro různá přetížení metody. IntelliSense můžete použít také k dokončení slova po zadání dostatečného počet znaků, aby bylo možné ho jednoznačně rozpoznat. Přidejme řádek kódu pro tisk seřazených řetězců do okna konzoly, což je standardní místo pro výstup z programu.

1. Pod `query` proměnnou začněte psát následující kód:

   ```vb
   For Each str In qu
   ```

   Zobrazí se funkce IntelliSense s **rychlými informacemi** o `query` symbolu.

   ![Dokončování slov IntelliSense v Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Pokud chcete vložit zbytek slova pomocí funkce dokončování slov `query` technologie IntelliSense, stiskněte **klávesu Tab**.

1. Dokončete blok kódu, aby vypadal jako následující kód.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Refaktoring názvu

Nikdo na první pohled nedostane kód a jednou z věcí, které možná budete muset změnit, je název proměnné nebo metody. Pojďme si vyzkoušet Visual Studio funkce [refaktoringu](../../ide/refactoring-in-visual-studio.md) a proměnnou přejmenujte `_words` na `words` .

1. Umístěte kurzor na definici proměnné a v místní nabídce nebo kliknutí pravým tlačítkem zvolte `_words` Přejmenovat. 

   V pravém horním **rohu** editoru se zobrazí automaticky otevírané dialogové okno Přejmenovat.

1. Když je `_words` proměnná stále vybraná, zadejte požadovaný název **slov**. Všimněte si, že `words` odkaz na v dotazu je také automaticky přejmenován. Než **stisknete Enter** nebo **kliknete na Použít,** zaškrtněte políčko Include comments (Zahrnout **komentáře)** v automaticky otevírané nabídce **Přejmenovat.**

   ![přejmenování dialogového okna](media/tutorial-rename.png)

1. Stiskněte **Enter** nebo klikněte na **Použít.**

   Oba výskyty se přejmenují, stejně jako `words` odkaz na v `words` komentáři ke kódu.

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
