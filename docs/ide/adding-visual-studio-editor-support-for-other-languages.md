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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590875"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Přidání podpory editoru Visual Studia pro jiné jazyky

Přečtěte si, jak editor Sady Visual Studio podporuje čtení a navigaci v různých jazycích počítače a jak můžete přidat podporu editoru sady Visual Studio pro jiné jazyky.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Syntaktické vybarvení, dokončení výpisu a podpora přechodu

Funkce v editoru Visual Studio, jako je například vybarvení syntaxe, dokončování příkazů (označované také jako IntelliSense) a _Přechod na,_ vám pomůžou snadněji psát, číst a upravovat kód. Následující snímek obrazovky ukazuje příklad úpravy skriptu Perl v sadě Visual Studio. Syntaxe je automaticky obarvena. Například poznámky v kódu jsou zbarveny zeleně, kód je černý, cesty jsou červené a příkazy jsou modré. Editor Visual Studio automaticky aplikuje vybarvení syntaxe na libovolný jazyk, který podporuje. Kromě toho, když začnete zadávat klíčové slovo nebo objekt známého jazyka, dokončení příkazu zobrazí seznam možných příkazů a objektů. Dokončení výkazu vám může pomoci psát kód rychleji a snadněji.

![Syntaktické zbarvení ve skriptu Perlu](../ide/media/vside_perledit.png)

Visual Studio aktuálně poskytuje syntaxi zbarvení a základní dokončování příkazu podporu pro následující jazyky pomocí [TextMate Gramatiky](https://manual.macromates.com/en/language_grammars). Pokud váš oblíbený jazyk není v tabulce, nebojte&mdash;se, můžete jej přidat.

|||||||
|-|-|-|-|-|-|
|Bat|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|Přejít|Javadoc|Objective-C|ShaderLab|C#|
|CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|Jazyk coffeescript|HTML|Méně|Python|SQL|VBNet|
|CSS|INI|Lua|R|Swift|XML|
|Docker|Jade|Značka|Ruby|TypeScript|YAML|

Kromě zbarvení syntaxe a dokončení základního příkazu má Visual Studio také funkci [nazvanou Přejít na](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Tato funkce umožňuje rychle vyhledávat soubory kódu, cesty k souborům a symboly kódu. Visual Studio poskytuje podporu navigace pro následující jazyky.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Přejít

- Java

- PHP

Všechny tyto typy souborů mají dříve popsané funkce, i když ještě nebyla nainstalována podpora pro daný jazyk. Instalace specializované podpory pro některé jazyky může poskytnout další jazykovou podporu, například intelliSense nebo jiné pokročilé jazykové funkce, jako jsou žárovky.

## <a name="add-support-for-non-supported-languages"></a>Přidání podpory pro nepodporované jazyky

Visual Studio poskytuje jazykovou podporu v editoru pomocí [TextMate Gramatiky](https://manual.macromates.com/en/language_grammars). Pokud váš oblíbený programovací jazyk aktuálně není v editoru sady&mdash;Visual Studio podporován, můžete nejprve vyhledat na webu sadu TextMate pro daný jazyk. Pokud nemůžete najít, i když, můžete přidat podporu pro něj sami vytvořením TextMate balíček model pro jazykové gramatiky a úryvky.

Přidejte všechny nové gramatiky TextMate pro Visual Studio do následující složky:

*%userprofile%\\.vs\Extensions*

Pod touto základní cestou přidejte následující složky, pokud se vztahují na vaši situaci:

|Název složky|Popis|
|-----------------|-----------------|
|\\*\<název jazyka>*|Jazyková složka. Nahraďte * \<název jazyka>* názvem jazyka. Například *\Matlab*.|
|*\Syntaxe*|Složka gramatiky. Obsahuje soubory *gramatiky json* pro jazyk, například *Matlab.json*.|
|*\Výstřižky*|Složka výstřižky. Obsahuje úryvky pro jazyk.|

V systému Windows *%userprofile%* překládá na cestu: *c:\Uživatelské\\\<jméno>*. Pokud složka *Rozšíření* v systému neexistuje, budete ji muset vytvořit. Pokud složka již existuje, bude skryta.

> [!TIP]
> Pokud máte v editoru otevřené nějaké soubory, budete je muset po přidání gramatiky TextMate zavřít a znovu otevřít, abyste viděli zvýraznění syntaxe.

Podrobnosti o tom, jak vytvořit gramatiky TextMate, naleznete v tématu [TextMate - Úvod do jazykových gramatik](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) a [poznámek o tom, jak vytvořit jazykovou gramatiku a vlastní motiv pro sadu Textmate .](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle)

## <a name="see-also"></a>Viz také

- [Přidání rozšíření protokolu LSP (Language Server Protocol)](../extensibility/adding-an-lsp-extension.md)
- [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)
- [Návod: Zobrazení dokončení příkazu](../extensibility/walkthrough-displaying-statement-completion.md)
