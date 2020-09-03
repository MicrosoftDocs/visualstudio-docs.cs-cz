---
title: Možnosti, textový editor, obecné | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
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
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa81b08d6e375da4ad67b2e6eec32f244a779408
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662252"
---
# <a name="options-text-editor-general"></a>Možnosti, textový editor, obecné
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toto dialogové okno umožňuje změnit globální nastavení pro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Editor kódu a text. Chcete-li zobrazit toto dialogové okno, klikněte na tlačítko **Možnosti** v nabídce **nástroje** , rozbalte složku **textový editor** a poté klikněte na možnost **Obecné**.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Nastavení
 Když je vybraná možnost upravování textu, umožňuje přesunout text tím, že ho vyberete a přetáhnete myší na jiné místo v rámci aktuálního dokumentu nebo jiného otevřeného dokumentu.

 Automatické zvýrazňování oddělovače, pokud je vybraná, jsou zvýrazněné znaky oddělovače, které oddělují parametry nebo páry položek a hodnot a odpovídající závorky.

 Sledovat změny po výběru editoru kódu se v okraji výběru zobrazí svislá žlutá čára, která označuje kód, který se změnil od posledního uložení souboru. Při uložení změn se svislé čáry změní na zelenou.

 Automatické rozpoznání kódování UTF-8 bez podpisu ve výchozím nastavení Editor detekuje kódování hledáním značek pořadí bajtů nebo znakem znakové sady. Pokud není v aktuálním dokumentu nalezen, Editor kódu se pokusí automaticky rozpoznat kódování UTF-8 kontrolou sekvencí bajtů. Chcete-li zakázat automatické zjišťování kódování, zrušte zaškrtnutí tohoto políčka.

## <a name="display"></a>Zobrazení
 Výběr okraje výběru: zobrazí svislý okraj podél levého okraje textové oblasti editoru. Kliknutím na tuto hranici můžete vybrat celý řádek textu nebo kliknutím a přetažením vybrat po sobě jdoucí řádky textu.

|Okraj výběru na|Okraj výběru vypnut|
|-------------------------|--------------------------|
|![Snímek obrazovky HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif "vxSelmaron")|![Snímek obrazovky HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|

 Okraj indikátoru Pokud je vybrána, zobrazí se svislé okraje mimo levý okraj textové oblasti editoru. Po kliknutí na tento okraj se zobrazí ikona a popis tlačítka, které se vztahují k danému textu. Například na okraji indikátoru se zobrazí zarážka nebo zástupci seznamu úkolů. Informace o okraji indikátoru netiskou.

 Svislý posuvník: Pokud je vybraná, zobrazí svislý posuvník, který umožňuje posun nahoru a dolů, aby se zobrazily elementy, které spadají mimo oblast zobrazení editoru. Pokud nejsou svislé posuvníky k dispozici, můžete k posouvání použít klávesu Page Up, Page Down a Cursor.

 Vodorovný posuvník: když je vybraný, zobrazí vodorovný posuvník, který vám umožní posouvat se od sebe, aby se zobrazily elementy, které spadají mimo oblast zobrazení editoru. Pokud nejsou k dispozici vodorovné posuvníky, můžete k posouvání použít klávesy kurzoru.

 Zvýraznit aktuální řádek při výběru zobrazí šedé pole kolem řádku kódu, ve kterém se nachází kurzor.

## <a name="see-also"></a>Viz také
 [Možnosti, textový editor, všechny](../../ide/reference/options-text-editor-all-languages.md) [Možnosti jazyků, textový editor, všechny jazyky, možnosti karet](../../ide/reference/options-text-editor-all-languages-tabs.md) [, textový editor,](../../ide/reference/options-text-editor-file-extension.md) [identifikace a přizpůsobení klávesových zkratek](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) [přizpůsobení editoru](../../ide/customizing-the-editor.md) [pomocí technologie IntelliSense](../../ide/using-intellisense.md)
