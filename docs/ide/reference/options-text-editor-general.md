---
title: Možnosti, textový editor, obecné
description: Naučte se používat stránku Obecné ke změně globálních nastavení pro Visual Studio Code and text editor.
ms.custom: SEO-VS-2020
ms.date: 01/18/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.PL/SQL
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1665db5fff414227c18fd8de4224302cb6d43c2a
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040599"
---
# <a name="options-dialog-box-text-editor--general"></a>Dialogové okno Možnosti: textový editor \> Obecné

Toto dialogové okno umožňuje změnit globální nastavení pro Editor kódu a text v aplikaci Visual Studio. Chcete-li zobrazit toto dialogové okno, vyberte možnost **Možnosti** v nabídce **nástroje** , rozbalte složku **textový editor** a pak vyberte možnost **Obecné**.

## <a name="settings"></a>Nastavení

### <a name="drag-and-drop-text-editing"></a>Přetažení úprav textu

Když je tato možnost vybraná, umožňuje přesunout text tak, že ho vyberete a přetáhnete myší na jiné místo v rámci aktuálního dokumentu nebo jiného otevřeného dokumentu.

### <a name="automatic-delimiter-highlighting"></a>Zvýrazňování automatického oddělovače

Je-li vybrána tato možnost, jsou zvýrazněny znaky oddělovače, které oddělují parametry nebo páry položek a hodnot a odpovídající závorky.

### <a name="track-changes"></a>Sledování změn

Když je vybrán Editor kódu, v okraji výběru se zobrazí svislá žlutá čára, která označuje kód, který se změnil od posledního uložení souboru. Při uložení změn se svislé čáry změní na zelenou.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Automaticky rozpoznat kódování UTF-8 bez podpisu

Ve výchozím nastavení Editor detekuje kódování hledáním značek pořadí bajtů nebo charset značek. Pokud se v aktuálním dokumentu nenalezne, Editor kódu se pokusí automaticky detekovat kódování UTF-8 kontrolou sekvencí bajtů. Chcete-li zakázat automatickou detekci kódování, zrušte zaškrtnutí tohoto políčka.

### <a name="follow-project-coding-conventions"></a>Sledovat konvence psaní kódu projektu

Je-li vybrána tato možnost, zadané konvence kódování pro projekt přepíší všechny konvence kódování používané v osobních projektech.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Povolit možnost přejít k definici kliknutím myši

Když vyberete tuto možnost, můžete stisknout **CTRL** a při kliknutí myší umístit ukazatel myši na prvek. Provedete to tak, že přejdete do definice vybraného elementu. Můžete také zvolit **ALT** nebo **CTRL**  +  **ALT** z rozevíracího seznamu **použít klávesu modifikátoru** .

Zaškrtněte políčko **Otevřít definici v náhledu zobrazení** , chcete-li v okně zobrazit definici elementu, aniž byste museli přejít pryč z aktuálního umístění v editoru kódu.

## <a name="display"></a>Zobrazení

### <a name="selection-margin"></a>Okraj výběru

Je-li vybrána tato možnost, zobrazí se svislé okraje podél levého okraje textové oblasti editoru. Kliknutím na tuto hranici můžete vybrat celý řádek textu nebo kliknutím a přetažením vybrat po sobě jdoucí řádky textu.

|Okraj výběru na|Okraj výběru vypnut|
| - | - |
|![Snímek obrazovky HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif)|![Snímek obrazovky HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Okraj indikátoru

Je-li vybrána tato možnost, zobrazí se svislé okraje mimo levý okraj textové oblasti editoru. Po kliknutí na tento okraj se zobrazí ikona a popis tlačítka, které se vztahují k danému textu. Například na okraji indikátoru se zobrazí zarážka nebo zástupci seznamu úkolů. Informace o okraji indikátoru se netiskou.

### <a name="highlight-current-line"></a>Zvýraznit aktuální řádek

Je-li vybrána tato možnost, aplikace zobrazí šedé pole kolem řádku kódu, ve kterém je umístěn kurzor.

### <a name="show-structure-guide-lines"></a>Zobrazit vodicí čáry struktury

Je-li vybrána tato možnost, zobrazí se v editoru svislé čáry, které se zařadí do strukturovaných bloků kódu, což vám umožní snadno identifikovat jednotlivé bloky kódu.

### <a name="show-file-health-indicator"></a>Zobrazit indikátor stavu souboru

Je-li toto políčko zaškrtnuto, zobrazí se v levém dolním rohu editoru Stav indikátoru stavu souboru (chyby, varování) s možnostmi vyčištění kódu.

## <a name="see-also"></a>Viz také

- [Možnosti, textový editor, všechny jazyky](../../ide/reference/options-text-editor-all-languages.md)
- [Možnosti, Textový editor, Všechny jazyky, Tabulátory](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Možnosti, Textový editor, Přípona souboru](../../ide/reference/options-text-editor-file-extension.md)
- [Identifikování a přizpůsobení klávesových zkratek](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Vlastní nastavení editoru](../how-to-change-text-case-in-the-editor.md)
- [Pomocí technologie IntelliSense](../../ide/using-intellisense.md)
