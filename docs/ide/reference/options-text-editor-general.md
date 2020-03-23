---
title: Možnosti, textový editor, obecné
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
ms.openlocfilehash: ebe526bbac859777edb4c2c78c65a1cdbd27fc85
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568409"
---
# <a name="options-dialog-box-text-editor--general"></a>Dialogové okno Možnosti: Obecné editoru \> textu

Toto dialogové okno umožňuje změnit globální nastavení kódu a textového editoru sady Visual Studio. Chcete-li toto dialogové okno zobrazit, vyberte **možnosti** v nabídce **Nástroje,** rozbalte složku **Editor textu** a pak vyberte **Obecné**.

## <a name="settings"></a>Nastavení

### <a name="drag-and-drop-text-editing"></a>Přetažení textu

Když je tato volba vybraná, můžete text přesunout tak, že ho vyberete a přetáhnete myší na jiné místo v aktuálním dokumentu nebo jiném otevřeném dokumentu.

### <a name="automatic-delimiter-highlighting"></a>Automatické zvýraznění oddělovače

Je-li tato možnost vybrána, zvýrazní se znaky oddělovače, které oddělují parametry nebo dvojice položek a hodnot, stejně jako odpovídající závorky.

### <a name="track-changes"></a>Sledování změn

Když je vybrán editor kódu, ve výběrovém okraji se zobrazí svislá žlutá čára, která označuje kód, který se změnil od posledního uložení souboru. Když uložíte změny, svislé čáry se stanou zelenými.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Automatické rozpoznání kódování UTF-8 bez podpisu

Ve výchozím nastavení editor detekuje kódování vyhledáním značek pořadí bajtů nebo značek znakové sady. Pokud ani v aktuálním dokumentu není nalezen, editor kódu se pokusí automaticky detekovat kódování UTF-8 skenováním sekvencí bajtů. Chcete-li zakázat automatickou detekci kódování, zrušte zaškrtnutí této možnosti.

### <a name="follow-project-coding-conventions"></a>Sledování konvencí kódování projektů

Pokud je tato možnost vybrána, zadané konvence kódování projektu přepíší všechny konvence kódování, které používáte v osobních projektech.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Povolit klepnutí myší k provedení přejít na definici

Když je tato volba vybraná, můžete při klepnutí na tlačítko myši stisknout **klávesu Ctrl** a najet myší na prvek. Tím přejdete k definici vybraného prvku. Můžete také zvolit **alt** nebo **ctrl** + **alt** z rozbalovací ho klíče **modifikátoru.**

Zaškrtnutím políčka **Otevřít definici v náhledovém zobrazení** zobrazíte definici prvku v okně, aniž byste museli v editoru kódu odcházet z aktuálního umístění.

## <a name="display"></a>Displej

### <a name="selection-margin"></a>Výběrová marže

Když je tato volba vybraná, zobrazí se svislý okraj podél levého okraje textové oblasti editoru. Klepnutím na tento okraj můžete vybrat celý řádek textu nebo klepnutím a tažením vybrat po sobě jdoucí řádky textu.

|Výběr oválná hranice|Výběr margin off|
| - | - |
|![HTMLpageSelectionMarginOn snímek obrazovky](../../ide/reference/media/vxselmaron.gif)|![HTMLpageSelectionMarginOff snímek obrazovky](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Ukazatel marže

Když je tato volba vybraná, zobrazí se svislý okraj mimo levý okraj textové oblasti editoru. Po klepnutí na tento okraj se zobrazí ikona a popis, které souvisejí s textem. Například zástupci zarážky nebo seznamu úkolů se zobrazí v okraji ukazatele. Informace o marži indikátoru se nevytisknou.

### <a name="highlight-current-line"></a>Zvýraznění aktuálního řádku

Je-li tato možnost vybrána, zobrazí šedé pole kolem řádku kódu, ve kterém je kurzor umístěn.

### <a name="show-structure-guide-lines"></a>Zobrazit vodicí čáry struktury

Když je tato volba vybraná, v editoru se zobrazí svislé čáry, které jsou zaokřovány do strukturovaných bloků kódu, což umožňuje snadno identifikovat jednotlivé bloky kódu.

## <a name="see-also"></a>Viz také

- [Možnosti, textový editor, všechny jazyky](../../ide/reference/options-text-editor-all-languages.md)
- [Možnosti, Textový editor, Všechny jazyky, Tabulátory](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Možnosti, Textový editor, Přípona souboru](../../ide/reference/options-text-editor-file-extension.md)
- [Identifikování a přizpůsobení klávesových zkratek](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Vlastní nastavení editoru](../how-to-change-text-case-in-the-editor.md)
- [Používání atributu IntelliSense](../../ide/using-intellisense.md)
