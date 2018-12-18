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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f0ac463161d42e0d9ddf6b845b752916675ba4fe
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062092"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Přidání podpory editoru sady Visual Studio pro ostatní jazyky

Další informace o způsob, jakým editor sady Visual Studio podporuje čtení a navigaci jazyky jiný počítač a jak můžete přidat editoru Visual Studio – podpora pro další jazyky.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Barevné zvýrazňování syntaxe, dokončování příkazů a přejít na podporu

Funkce v editoru sady Visual Studio, jako je například barevné zvýrazňování syntaxe, dokončování příkazů (označované také jako technologie IntelliSense), a _přejít na_ můžete mnohem snadněji napsat, čtení a úpravy kódu. Následující snímek obrazovky ukazuje příklad úpravy skriptu jazyka Perl v sadě Visual Studio. Syntaxe je automaticky obarveny. Například poznámky v kódu se zobrazí zelená, kód je černá, cesty jsou červená a příkazy jsou modrá. Editor sady Visual Studio automaticky aplikuje na libovolného jazyka, který podporuje barevné zvýrazňování syntaxe. Kromě toho když začnete zadávat známý jazyk – klíčové slovo a objekt, dokončování příkazů zobrazí seznam možných příkazy a objekty. Doplňování výrazů vám umožňují snadno a rychle psát kód.

![Barevné zvýrazňování syntaxe ve skriptu jazyka Perl](../ide/media/vside_perledit.png)

Visual Studio v současné době poskytuje barevné zvýrazňování syntaxe a doplňování výrazů základní podporu pro následující jazyky pomocí [Gramatik TextMate](https://manual.macromates.com/en/language_grammars). Pokud svůj oblíbený jazyk není v tabulce, ale Nedělejte si starosti – můžete ho přidat.

|||||||
|-|-|-|-|-|-|
|Z baterie|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|Go|JavaDoc|Objective-C|ShaderLab|C#|
|CMake|Groovy|FORMÁT JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|MÉNĚ|Python|SQL|VBNet|
|CSS|INI|LUA|R|Kód SWIFT|XML|
|Docker|Jade|Ujistěte se|Ruby|TypeScript|YAML|

Kromě barevného zvýrazňování syntaxe a doplňování výrazů basic, Visual Studio také má funkci zvanou [přejít na](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Tato funkce umožňuje rychle vyhledat soubory kódu, cesty k souborům a kód symboly. Visual Studio poskytuje přejít na podporu pro následující jazyky.

-   Go

-   Java

-   JavaScript

-   PHP

-   TypeScript

-   Visual Basic

-   Visual C++

-   C#

Všechny tyto typy souborů mají funkce popsané dříve i v případě podpory pro daný jazyk ještě se nenainstalovala. Instalace specializované podpory pro některé jazyky mohou poskytnout podpory dalších jazyků, jako je například technologie IntelliSense nebo jiné pokročilé jazyka funkce, jako jsou návrhy.

## <a name="add-support-for-non-supported-languages"></a>Přidání podpory pro jiné podporované jazyky

Visual Studio 2015 Update 1 a novější verze poskytují podporu jazyka v editoru pomocí [Gramatik TextMate](https://manual.macromates.com/en/language_grammars). Pokud vašem oblíbeném programovacím jazyce se aktuálně nepodporuje v editoru sady Visual Studio, nejprve vyhledávání na webu – sady TextMate pro jazyk již existuje. Pokud nemůžete najít jednu, ale můžete přidat podporu sami v Visual Studio 2015 Update 1 nebo později po vytvoření modelu sady TextMate pro jazyk gramatiky a fragmenty kódu.

Přidejte všechny nové Gramatik TextMate pro Visual Studio v následující složce:

*%userprofile%\\.vs\Extensions*

Pod touto cestou základní přidáte následující složky, pokud se vztahují na konkrétní situaci:

|Název složky|Popis|
|-----------------|-----------------|
|\\*\<název jazyka >*|Jazykovou složku. Nahraďte  *\<název jazyka >* s název jazyka. Například *\Matlab*.|
|*\Syntaxes*|Složka gramatiky. Obsahuje gramatiku *.json* souborů pro daný jazyk, jako například *Matlab.json*.|
|*\Snippets*|Složka fragmentů kódu. Obsahuje fragmenty kódu pro jazyk.|

Ve Windows *% userprofile %* překládá na cestu: *c:\Users\\\<uživatelské jméno >*. Pokud složka rozšíření neexistuje ve vašem systému, musíte ji vytvořit. Pokud složka již existuje, bude skrytá.

Podrobnosti o tom, jak vytvořit Gramatik TextMate najdete v tématu [TextMate – Úvod do jazyka gramatiky: Přidání zvýrazňování syntaxe kódu zdroje vložený ve formátu HTML](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) a [poznámky o tom, jak vytvořit jazyk gramatiky a vlastní Motiv pro sady Textmate](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Viz také:

- [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)
- [Návod: Zobrazení dokončování příkazů](../extensibility/walkthrough-displaying-statement-completion.md)
