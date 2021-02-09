---
title: Možnosti, textový editor, všechny jazyky, karty
description: Naučte se, jak pomocí stránky karty v části všechny jazyky změnit výchozí chování karet editoru kódu v rámci sady Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c429b8e6dbf6931ebf68717b6d43fcf746cf13ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905564"
---
# <a name="options-text-editor-all-languages-tabs"></a>Možnosti, textový editor, všechny jazyky, karty

Toto dialogové okno umožňuje změnit výchozí chování editoru kódu. Tato nastavení platí také pro ostatní editory na základě editoru kódu, jako je například zobrazení zdroje v Návrháři HTML. Chcete-li zobrazit tyto možnosti, vyberte **Možnosti** v nabídce **nástroje** . V rámci složky **textový editor** rozbalte podsložku **všechny jazyky** a pak zvolte **karty**.

> [!CAUTION]
> Tato stránka nastaví výchozí možnosti pro všechny vývojové jazyky. Mějte na paměti, že při resetování možnosti v tomto dialogu dojde k výběru možností karet ve všech jazycích, ať už jsou vybrané volby. Chcete-li změnit možnosti textového editoru pouze pro jeden jazyk, rozbalte podsložku pro daný jazyk a vyberte její stránky možností.

Pokud jsou na stránkách možností karet pro konkrétní programovací jazyky vybraná jiná nastavení, zobrazí se u různých možností **odsazení** zpráva nastavení odsazení pro jednotlivé textové formáty. a zpráva "nastavení tabulátoru pro jednotlivé textové formáty jsou v konfliktu." se zobrazí pro různé možnosti **tabulátoru** . Toto připomenutí se zobrazí například v případě, že je vybrána možnost **inteligentního odsazení** pro Visual Basic, ale u Visual C++ je vybráno **blokování odrážek** .

## <a name="indenting"></a>Odsazení

Žádné

Pokud je tato možnost vybrána, nové řádky nebudou odsazeny. Místo vložení se umístí do prvního sloupce nového řádku.

Blok

Je-li tato možnost vybrána, budou nové řádky automaticky odsazeny. Bod vložení se umístí na stejný výchozí bod jako předchozí řádek.

Oblé

Je-li vybrána tato možnost, jsou nové řádky umístěny tak, aby odpovídaly kontextu kódu, pro další nastavení formátování kódu a konvence technologie IntelliSense pro váš vývojový jazyk. Tato možnost není k dispozici pro všechny vývojové jazyky.

Například řádky uzavřené mezi levou složenou závorkou ({) a pravou složenou závorkou (}) mohou být automaticky odsazeny o další zarážku tabulátoru z pozice zarovnaných složených závorek.

## <a name="tabs"></a>Karty

Velikost tabulátoru

Nastaví vzdálenost mezi zarážkami tabulátoru v mezerách. Výchozí hodnota je čtyři mezery.

Zvětšit velikost

Nastaví velikost v mezerách automatického odsazení. Výchozí hodnota je čtyři mezery. Pro vyplnění zadané velikosti budou vloženy znaky tabulátoru, znaky mezery nebo obojí.

Vložit mezery

Pokud je tato možnost vybrána, operace odsazení zabírají pouze znaky, nikoli znaky TABULÁTORu. Pokud je **Velikost odsazení** nastavená na 5, například, pak se při každém stisknutí klávesy TAB nebo **zvětšení odsazení** na panelu nástrojů **formátování** vloží pět znaků mezer.

Zachovat záložky

Pokud je tato možnost vybrána, operace odsazení zaplňují tolik znaků TABULÁTORu. Každý znak TABULÁTORu vyplní počet mezer zadaný v poli **velikost tabulátoru**. Pokud **Velikost odsazení** není sudým násobkem **velikosti tabulátoru**, přidají se k vyplnění rozdílu znaky mezer.

## <a name="see-also"></a>Viz také

- [Možnosti, textový editor, všechny jazyky](../../ide/reference/options-text-editor-all-languages.md)
- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
