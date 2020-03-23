---
title: Možnosti, textový editor, všechny jazyky, karty
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
- VS.ToolsOptionsPages.Text_Editor.Basic.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSharp.Tabs
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Tabs
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.Tabs
- VS.ToolsOptionsPages.Text_Editor.F%2523.Tabs
- VS.ToolsOptionsPages.Text_Editor.HQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTML.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTMLX.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.JSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.LESS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.Tabs
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.SCSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Tabs
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.Tabs
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.Tabs
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.XAML.Tabs
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fc169960cf757e4e334d5f77b06ff70b0d6da7c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594744"
---
# <a name="options-text-editor-all-languages-tabs"></a>Možnosti, textový editor, všechny jazyky, karty

Toto dialogové okno umožňuje změnit výchozí chování Editoru kódu. Tato nastavení platí také pro ostatní editory založené na Editoru kódu, jako je například zobrazení zdroje návrháře HTML. Chcete-li tyto možnosti zobrazit, vyberte **možnosti** z nabídky **Nástroje.** Ve složce **Editor textu** rozbalte podsložku **Všechny jazyky** a pak zvolte **Tabulátory**.

> [!CAUTION]
> Tato stránka nastaví výchozí možnosti pro všechny vývojové jazyky. Nezapomeňte, že obnovení volby v tomto dialogovém okně obnoví možnosti tabulátorů ve všech jazycích na libovolné volby, které jsou zde vybrány. Chcete-li změnit možnosti editoru textu pouze pro jeden jazyk, rozbalte podsložku pro daný jazyk a vyberte jeho stránky možností.

Pokud jsou na stránkách možností Záložek pro konkrétní programovací jazyky vybrána různá nastavení, zobrazí se pro různé možnosti **odsazení** zpráva "Nastavení odsazení pro jednotlivé textové formáty". a zobrazí se zpráva "Nastavení tabulátoru pro jednotlivé formáty textu je vzájemně kolize", pro různé možnosti **tabulátoru.** Toto připomenutí se například zobrazí, pokud je pro jazyk Visual Basic vybrána možnost **Inteligentní odsazení,** ale pro visual c++ je vybraná volba **Odsazení bloku.**

## <a name="indenting"></a>Odsazení

Žádný

Je-li tato možnost vybrána, nové řádky nejsou odsazeny. Textový kurzor je umístěn v prvním sloupci nového řádku.

Blok

Když je tato volba vybraná, nové řádky se automaticky odsazují. Textový kurzor je umístěn ve stejném počátečním bodě jako předchozí řádek.

Inteligentní

Když je tato volba vybraná, jsou nové řádky umístěny tak, aby odpovídaly kontextu kódu, podle jiných nastavení formátování kódu a konvencí Technologie IntelliSense pro váš vývojový jazyk. Tato možnost není k dispozici pro všechny vývojové jazyky.

Například řádky uzavřené mezi otevírací závorkou ( { ) a uzavírací složenou závorkou ( } ) mohou být automaticky odsazeny o další zarážku tabulátoru od pozice zarovnaných závorek.

## <a name="tabs"></a>Karty

Velikost tabulátoru

Nastaví vzdálenost v mezerách mezi zarážkami tabulátoru. Výchozí hodnota je čtyři mezery.

Velikost odsazení

Nastaví velikost v prostorech automatického odsazení. Výchozí hodnota je čtyři mezery. Znaky tabulátoru, mezery nebo obojí budou vloženy, aby vyplnily zadanou velikost.

Vložení mezer

Když je tato volba vybraná, operace odsazení vloží pouze mezery, nikoli znaky TABulÁTORU. Pokud je například **velikost Odsazení** nastavena na 5, vloží se pět znaků mezery vždy, když stisknete klávesu TAB nebo tlačítko **Zvětšit odsazení** na panelu nástrojů **Formátování.**

Zachovat přehled

Když je tato volba vybraná, operace odsazení vloží co nejvíce znaků TABulÁTORU. Každý znak TABulátoru vyplní počet mezer určených ve **velikosti tabulátoru**. Pokud **velikost Odsazení** není sudým násobkem **velikosti tabulátoru**, budou přidány mezery, aby se rozdíl vyplnil.

## <a name="see-also"></a>Viz také

- [Možnosti, textový editor, všechny jazyky](../../ide/reference/options-text-editor-all-languages.md)
- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
