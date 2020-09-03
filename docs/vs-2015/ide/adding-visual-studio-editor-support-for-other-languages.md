---
title: Přidání podpory editoru pro jiné jazyky | Microsoft Docs
ms.date: 11/15/2016
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
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9dbd245edd81907197e23c0d193a01cc07424b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548106"
---
# <a name="adding-visual-studio-editor-support-for-other-languages"></a>Přidání podpory editoru sady Visual Studio pro jiné jazyky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Přečtěte si, jak editor sady Visual Studio podporuje čtení a navigaci v různých jazycích počítačů a jak můžete přidat podporu editoru sady Visual Studio pro jiné jazyky.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Barevné zvýrazňování syntaxe, dokončování příkazů a přechod na podporu
 Funkce v editoru sady Visual Studio, jako je například barevné zvýrazňování syntaxe, dokončování příkazů a navigace, vám můžou usnadnit snazší čtení, vytváření a úpravy kódu. Následující snímek obrazovky ukazuje příklad úprav skriptu Perl v aplikaci Visual Studio. Syntaxe je automaticky zabarvovaná. Například poznámky v kódu jsou barevné zeleně, kód je černý, cesty jsou červené a příkazy jsou modré. Editor sady Visual Studio automaticky aplikuje barevné zvýrazňování syntaxe pro libovolný jazyk, který podporuje. Kromě toho, když začnete zadávat klíčové slovo nebo objekt známého jazyka, zobrazí se dokončování příkazů seznam možných příkazů a objektů. Doplňování příkazů vám může usnadnit vytváření kódu rychleji a snadno.

 ![Zabarvení syntaxe ve skriptu Perl](../ide/media/vside-perledit.png "VSIDE_PerlEdit")

 Visual Studio aktuálně poskytuje barevné zvýrazňování syntaxe a podporu dokončování příkazů pro následující jazyky pomocí [TextMate gramatik](https://manual.macromates.com/en/language_grammars). Pokud váš oblíbený jazyk není v tabulce, ale nedělejte si starosti – můžete ho přidat.

- Bat
- F#
- Java
- Markdown
- Rust
- Visual Basic
- Clojure
- Přejít
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

 Kromě barevného zabarvení syntaxe a základního dokončování příkazů má Visual Studio také funkci s názvem [Přejít na](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Tato funkce umožňuje rychle vyhledat soubory kódu, cesty k souborům a symboly kódu. Visual Studio poskytuje podporu pro následující jazyky.

- Přejít

- Java

- JavaScript

- PHP

- TypeScript

- Visual Basic

- Visual C++

- Visual C#

  Všechny tyto typy souborů mají funkce popsané výše i v případě, že ještě není nainstalovaná podpora pro daný jazyk. Instalace specializované podpory pro některé jazyky může poskytovat další jazykovou podporu, jako je například IntelliSense nebo jiné rozšířené jazykové funkce, jako jsou například žárovky.

## <a name="adding-support-for-non-supported-languages"></a>Přidání podpory pro nepodporované jazyky
 Visual Studio 2015 Update 1 a novější verze poskytují jazykovou podporu v editoru pomocí [gramatik TextMate](https://manual.macromates.com/en/language_grammars). Pokud váš oblíbený programovací jazyk aktuálně není v editoru sady Visual Studio podporován, nejprve vyhledejte web – sada TextMate pro jazyk již možná existuje. Pokud ho nemůžete najít, můžete ho ale přidat sami do sady Visual Studio 2015 Update 1 nebo novější vytvořením modelu TextMate sady pro jazykové gramatiky a fragmenty kódu.

 Přidejte všechny nové gramatiky TextMate pro Visual Studio do následující složky:

 % USERPROFILE% \\ . vs\Extensions

 V rámci této základní cesty přidejte následující složky, pokud se na vaši situaci vztahují:

|Název složky|Popis|
|-----------------|-----------------|
|\\*\<language name>*|Složka jazyka Nahraďte *\<language name>* názvem jazyka. Například **\Matlab**.|
|\Syntaxes|Složka gramatiky. Obsahuje soubory gramatiky. JSON pro jazyk, například **Matlab.js**.|
|\Snippets|Složka fragmenty. Obsahuje fragmenty kódu pro daný jazyk.|

 V systému Windows se% USERPROFILE% překládá na cestu: c:\Users \\ *\<user name>* . Pokud složka rozšíření v systému neexistuje, budete ji muset vytvořit. Pokud složka již existuje, bude skrytá.

 Podrobnosti o tom, jak vytvořit TextMate gramatiky, najdete v tématu [TextMate – Úvod do jazykových gramatik: jak přidat zvýrazňování syntaxe zdrojového kódu vloženého do HTML](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) a [poznámky k vytvoření jazykové gramatiky a vlastní motiv pro sadu TextMate](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Viz také
 [Visual Studio 2013 přejděte na](https://blogs.msdn.microsoft.com/mvpawardprogram/2013/10/22/visual-studio-2013-navigate-to-improvements/) [postupy vylepšení: vytvoření návodu fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md) [: zobrazení dokončování příkazů](../extensibility/walkthrough-displaying-statement-completion.md)
