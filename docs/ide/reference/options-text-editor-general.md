---
title: Možnosti, textový editor, obecné
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 75051013e38d4acf5339193cf9f80e6da6758284
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388791"
---
# <a name="options-text-editor-general"></a>Možnosti, textový editor, obecné

Toto dialogové okno umožňuje měnit globální nastavení pro kód a text editoru sady Visual Studio. Chcete-li zobrazit toto dialogové okno, vyberte **možnosti** na **nástroje** nabídky, rozbalte **textový Editor** složku a pak vyberte **Obecné**.

## <a name="settings"></a>Nastavení

### <a name="drag-and-drop-text-editing"></a>Přetáhnout myší úpravy textu

Při výběru, umožňuje přesunout text jeho výběrem a přetažením myší do jiného umístění v rámci aktuálního dokumentu nebo libovolného otevřeného dokumentu.

### <a name="automatic-delimiter-highlighting"></a>Automatické zvýrazňování oddělovače

Pokud je vybráno, jsou zvýrazněny znaky oddělovače, které oddělují parametry nebo párů hodnot položky, jakož i odpovídající složené závorky.

### <a name="track-changes"></a>Sledování změn

Pokud je vybrána editoru kódu, se zobrazí v okraj výběru označit kód, který se změnil, protože soubor byl uložen jako poslední svislé Žlutá čára. Při ukládání změn budou zelené svislé čáry.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Automatické rozpoznání kódování UTF-8 bez podpisu

Ve výchozím nastavení zjistí editoru kódování tak, že značky pořadí bajtů nebo znaková sada značky. Pokud ani nenajde v aktuálním dokumentu, editoru kódu se pokusí automaticky rozpoznat kódování UTF-8 naskenováním pořadí bajtů. Chcete-li zakázat automatické zjišťování kódování, zrušte zaškrtnutí tohoto políčka.

## <a name="display"></a>Displej

### <a name="selection-margin"></a>Okraj výběru

Pokud je vybráno, zobrazí svislý okraj podél levého okraje editoru textová oblast. Můžete kliknout na tento okraj označit celý řádek textu, nebo klikněte a tažením vyberte po sobě jdoucích řádků textu.

|Okraj výběru|Okraj výběru vypnuto|
| - | - |
|![Snímek obrazovky HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif)|![Snímek obrazovky HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Okraj indikátoru

Pokud je vybráno, zobrazí svislý okraj mimo levého okraje editoru textová oblast. Po kliknutí na toto rozpětí, zobrazí ikonu a popis, který se vztahují na text. Zarážky nebo úloha klávesové zkratky seznamu se zobrazí v okraj indikátoru. Informace o okraj indikátoru nevytiskne.

### <a name="highlight-current-line"></a>Zvýraznit aktuální řádek

Pokud je vybráno, zobrazí šedé okolo řádek kódu, ve kterém se nachází kurzor.

## <a name="see-also"></a>Viz také:

- [Možnosti, Textový editor, Všechny jazyky](../../ide/reference/options-text-editor-all-languages.md)
- [Možnosti, Textový editor, Všechny jazyky, Tabulátory](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Možnosti, Textový editor, Přípona souboru](../../ide/reference/options-text-editor-file-extension.md)
- [Identifikování a přizpůsobení klávesových zkratek](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Vlastní nastavení editoru](../../ide/customizing-the-editor.md)
- [Používání atributu IntelliSense](../../ide/using-intellisense.md)