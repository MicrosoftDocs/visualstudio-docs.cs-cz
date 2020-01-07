---
title: Přidání podpory editoru pro jiné jazyky
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4fafaf9356d8862808e1ac6ad125207d71769b5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590875"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Přidání podpory editoru sady Visual Studio pro ostatní jazyky

Další informace o způsob, jakým editor sady Visual Studio podporuje čtení a navigaci jazyky jiný počítač a jak můžete přidat editoru Visual Studio – podpora pro další jazyky.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Barevné zvýrazňování syntaxe, dokončování příkazů a přejít na podporu

Funkce v editoru sady Visual Studio, jako je například barevné zvýrazňování syntaxe, dokončování příkazů (označované také jako technologie IntelliSense), a _přejít na_ můžete mnohem snadněji napsat, čtení a úpravy kódu. Následující snímek obrazovky ukazuje příklad úpravy skriptu jazyka Perl v sadě Visual Studio. Syntaxe je automaticky obarveny. Například poznámky v kódu se zobrazí zelená, kód je černá, cesty jsou červená a příkazy jsou modrá. Editor sady Visual Studio automaticky aplikuje na libovolného jazyka, který podporuje barevné zvýrazňování syntaxe. Kromě toho když začnete zadávat známý jazyk – klíčové slovo a objekt, dokončování příkazů zobrazí seznam možných příkazy a objekty. Doplňování výrazů vám umožňují snadno a rychle psát kód.

![Barevné zvýrazňování syntaxe ve skriptu jazyka Perl](../ide/media/vside_perledit.png)

Visual Studio v současné době poskytuje barevné zvýrazňování syntaxe a doplňování výrazů základní podporu pro následující jazyky pomocí [Gramatik TextMate](https://manual.macromates.com/en/language_grammars). Pokud váš oblíbený jazyk není v tabulce, ale nedělejte si starosti&mdash;můžete ho přidat.

|||||||
|-|-|-|-|-|-|
|Z baterie|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|Přejít|JavaDoc|Objective-C|ShaderLab|C#|
|CMake|Groovy|FORMÁT JSON|Perl|ShellScript|Visual C++ –|
|CoffeeScript|HTML|MÉNĚ|Python|SQL|VBNet|
|CSS|INI|LUA|v|Kód SWIFT|XML|
|Docker|Jade|Vytvoření|Ruby|TypeScript|YAML|

Kromě barevného zvýrazňování syntaxe a doplňování výrazů basic, Visual Studio také má funkci zvanou [přejít na](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Tato funkce umožňuje rychle vyhledávat soubory kódu, cesty k souborům a symboly kódu. Visual Studio poskytuje přejít na podporu pro následující jazyky.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Přejít

- Java

- PHP

Všechny tyto typy souborů mají funkce popsané dříve i v případě podpory pro daný jazyk ještě se nenainstalovala. Instalace specializované podpory pro některé jazyky mohou poskytnout podpory dalších jazyků, jako je například technologie IntelliSense nebo jiné pokročilé jazyka funkce, jako jsou návrhy.

## <a name="add-support-for-non-supported-languages"></a>Přidání podpory pro jiné podporované jazyky

Visual Studio poskytuje jazykovou podporu v editoru pomocí [gramatik TextMate](https://manual.macromates.com/en/language_grammars). Pokud v editoru sady Visual Studio v současné době není aktuálně podporován oblíbený programovací jazyk, nejprve vyhledejte web&mdash;sada TextMate pro daný jazyk již možná existuje. Pokud ho ale nemůžete najít, můžete ho pro IT oddělení přidat tak, že vytvoříte model TextMate sady pro jazykové gramatiky a fragmenty kódu.

Přidejte všechny nové Gramatik TextMate pro Visual Studio v následující složce:

*%userprofile%\\.vs\Extensions*

V rámci této základní cesty přidejte následující složky, pokud se vztahují na vaši situaci:

|Název složky|Popis|
|-----------------|-----------------|
|\\ *\<název jazyka >*|Jazykovou složku. Nahraďte  *\<název jazyka >* s název jazyka. Například *\Matlab*.|
|*\Syntaxes*|Složka gramatiky. Obsahuje gramatiku *.json* souborů pro daný jazyk, jako například *Matlab.json*.|
|*\Snippets*|Složka fragmentů kódu. Obsahuje fragmenty kódu pro jazyk.|

Ve Windows *% userprofile %* překládá na cestu: *c:\Users\\\<uživatelské jméno >* . Pokud složka *rozšíření* v systému neexistuje, budete ji muset vytvořit. Pokud složka již existuje, bude skrytá.

> [!TIP]
> Pokud máte v editoru otevřené nějaké soubory, budete je muset po přidání gramatiky TextMate zavřít a znovu otevřít a podívat se na zvýrazňování syntaxe.

Podrobnosti o tom, jak vytvořit TextMate gramatiky, najdete v tématu [TextMate – Úvod do jazykových gramatik](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) a [poznámky k vytvoření jazykové gramatiky a vlastní motiv pro sadu TextMate](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Viz také:

- [Přidání rozšíření protokolu jazykového serveru](../extensibility/adding-an-lsp-extension.md)
- [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)
- [Návod: Zobrazení dokončování příkazů](../extensibility/walkthrough-displaying-statement-completion.md)
