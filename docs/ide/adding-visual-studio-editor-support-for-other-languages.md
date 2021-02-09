---
title: Přidat podporu editoru pro jiné jazyky
description: Seznamte se s tím, jak editor sady Visual Studio podporuje čtení a navigaci v různých jazycích počítače a jak můžete přidat podporu pro jiné jazyky.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5e78f632cdfe3e207e7ce71530d06c2a3b3fc6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914976"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Přidat podporu editoru sady Visual Studio pro jiné jazyky

Přečtěte si, jak editor sady Visual Studio podporuje čtení a navigaci v různých jazycích počítačů a jak můžete přidat podporu editoru sady Visual Studio pro jiné jazyky.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Barevné zvýrazňování syntaxe, dokončování příkazů a přechod na podporu

Funkce v editoru sady Visual Studio, jako je například barevné zvýrazňování syntaxe, dokončování příkazů (označované také jako IntelliSense), a _Navigovat na, které_ vám pomohou snadněji zapisovat, číst a upravovat kód. Následující snímek obrazovky ukazuje příklad úprav skriptu Perl v aplikaci Visual Studio. Syntaxe je automaticky zabarvovaná. Například poznámky v kódu jsou barevné zeleně, kód je černý, cesty jsou červené a příkazy jsou modré. Editor sady Visual Studio automaticky aplikuje barevné zvýrazňování syntaxe pro libovolný jazyk, který podporuje. Kromě toho, když začnete zadávat klíčové slovo nebo objekt známého jazyka, zobrazí se dokončování příkazů seznam možných příkazů a objektů. Doplňování příkazů vám může usnadnit psaní kódu rychleji a snadno.

![Zabarvení syntaxe ve skriptu Perl](../ide/media/vside_perledit.png)

Visual Studio aktuálně poskytuje barevné zvýrazňování syntaxe a podporu dokončování příkazů pro následující jazyky pomocí [TextMate gramatik](https://manual.macromates.com/en/language_grammars). Pokud váš oblíbený jazyk není v tabulce, ale nedělejte si starosti, &mdash; můžete ho přidat.


- Bat
- F#
- Java
- Markdown
- Rust
- Visual Basic
- Clojure
- Go
- JavaDoc
- Objective-C
- ShaderLab
- C#
- CMake
- Groovy
- JSON
- Perl
- ShellScript
- Visual C++
- CoffeeScript
- HTML
- TOLIK
- Python
- SQL
- VBNet
- Šablony stylů CSS
- INI
- LUA
- R
- Swift
- XML
- Docker
- Jade
- Značka
- Ruby
- TypeScript
- YAML

Kromě barevného zabarvení syntaxe a základního dokončování příkazů má Visual Studio také funkci s názvem [Přejít na](/archive/blogs/benwilli/visual-studio-tip-3-use-navigate-to). Tato funkce umožňuje rychle vyhledávat soubory kódu, cesty k souborům a symboly kódu. Visual Studio poskytuje podporu pro následující jazyky.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Přejít

- Java

- PHP

Všechny tyto typy souborů mají funkce popsané výše i v případě, že ještě není nainstalovaná podpora pro daný jazyk. Instalace specializované podpory pro některé jazyky může poskytovat další jazykovou podporu, jako je například IntelliSense nebo jiné rozšířené jazykové funkce jako žárovky.

## <a name="add-support-for-non-supported-languages"></a>Přidání podpory pro nepodporované jazyky

Visual Studio poskytuje jazykovou podporu v editoru pomocí [gramatik TextMate](https://manual.macromates.com/en/language_grammars). Pokud v editoru sady Visual Studio v současné době není aktuálně podporován váš oblíbený programovací jazyk, nejprve vyhledáte &mdash; sadu TextMate, aby tento jazyk již mohl existovat. Pokud ho ale nemůžete najít, můžete ho pro IT oddělení přidat tak, že vytvoříte model TextMate sady pro jazykové gramatiky a fragmenty kódu.

Přidejte všechny nové gramatiky TextMate pro Visual Studio do následující složky:

*% USERPROFILE% \\ . vs\Extensions*

V rámci této základní cesty přidejte následující složky, pokud se vztahují na vaši situaci:

|Název složky|Description|
|-----------------|-----------------|
|\\*\<language name>*|Složka jazyka Nahraďte *\<language name>* názvem jazyka. Například *\Matlab*.|
|*\Syntaxes*|Složka gramatiky. Obsahuje soubory gramatiky *. JSON* pro jazyk, například *Matlab.js*.|
|*\Snippets*|Složka fragmenty. Obsahuje fragmenty kódu pro daný jazyk.|

V systému Windows se *% USERPROFILE%* překládá na cestu *: \\ \<user name> c:\Users*. Pokud složka *rozšíření* v systému neexistuje, budete ji muset vytvořit. Pokud složka již existuje, bude skrytá.

> [!TIP]
> Pokud máte v editoru otevřené nějaké soubory, budete je muset po přidání gramatiky TextMate zavřít a znovu otevřít a podívat se na zvýrazňování syntaxe.

Podrobnosti o tom, jak vytvořit TextMate gramatiky, najdete v tématu [TextMate – Úvod do jazykových gramatik](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) a [poznámky k vytvoření jazykové gramatiky a vlastní motiv pro sadu TextMate](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Viz také

- [Přidání rozšíření protokolu LSP (Language Server Protocol)](../extensibility/adding-an-lsp-extension.md)
- [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)
- [Návod: dokončování příkazů zobrazení](../extensibility/walkthrough-displaying-statement-completion.md)
- [Příklad kódu: gramatika TextMate](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/TextmateGrammar)
- [Příklad kódu: Podpora vlastních jazyků](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/Ook_Language_Integration)