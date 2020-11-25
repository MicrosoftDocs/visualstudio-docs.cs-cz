---
title: Možnosti, textový editor, všechny jazyky
description: Naučte se používat stránku Obecné v části všechny jazyky ke změně výchozího chování editoru kódu v sadě Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.General
- VS.ToolsOptionsPages.Text_Editor.CSS.General
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.General
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.Fsharp.General
- VS.ToolsOptionsPages.Text_Editor.HQL.General
- VS.ToolsOptionsPages.Text_Editor.HTML.General
- VS.ToolsOptionsPages.Text_Editor.HTML_(Web_Forms).General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.General
- VS.ToolsOptionsPages.Text_Editor.JSON.General
- VS.ToolsOptionsPages.Text_Editor.LESS.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SCSS.General
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.U-SQL.General
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor.XML.General
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 682097ca08bd570ac025e7b6a1861e45a8f761e4
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96041002"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>Dialogové okno Možnosti: textový editor \> všechny jazyky

Toto dialogové okno umožňuje změnit výchozí chování editoru kódu. Tato nastavení platí také pro ostatní editory na základě editoru kódu, jako je například zobrazení zdroje v Návrháři HTML. Chcete-li otevřít toto dialogové okno, vyberte možnost **Možnosti** v nabídce **nástroje** . V rámci složky **textový editor** rozbalte podsložku **všechny jazyky** a zvolte možnost **Obecné**.

> [!CAUTION]
> Tato stránka nastaví výchozí možnosti pro všechny vývojové jazyky. Mějte na paměti, že při resetování možnosti v tomto dialogu dojde k resetování obecných možností ve všech jazycích na jakékoli vybrané možnosti. Chcete-li změnit možnosti textového editoru pouze pro jeden jazyk, rozbalte podsložku pro daný jazyk a vyberte její stránky možností.

Po výběru možnosti na stránkách Obecné možnosti pro některé programovací jazyky, ale ne pro jiné, se zobrazí šedá značka zaškrtnutí.

## <a name="statement-completion"></a>Doplňování výrazů

**Automatický seznam členů**

V případě, že je tato možnost vybrána, budou při psaní v editoru v technologii IntelliSense zobrazeny automaticky otevírané seznamy dostupných členů, vlastností, hodnot nebo metod. Výběrem libovolné položky v rozevíracím seznamu vložte položku do kódu. Výběrem této možnosti povolíte možnost **Skrýt pokročilé členy** .

**Skrýt pokročilé členy**

Když se tato možnost vybere, zkrátí se seznamy pro doplňování příkazů tím, že se zobrazí jenom ty položky, které se nejčastěji používají. Další položky jsou filtrovány ze seznamu.

**Informace o parametru**

Je-li vybrána tato možnost, je zobrazena Úplná syntaxe pro aktuální deklaraci nebo proceduru v editoru s použitím všech dostupných parametrů. Další parametr, který můžete přiřadit, se zobrazí tučně.

## <a name="settings"></a>Nastavení

**Povolit virtuální prostor**

Pokud je vybrána tato možnost a **zalamování** řádků je vymazáno, můžete kliknout kamkoli za konec řádku v editoru kódu a zadat. Tato funkce se dá použít k umístění komentářů v konzistentním bodě vedle vašeho kódu.

**Zalamování řádků**

Je-li tato možnost vybrána, budou na dalším řádku automaticky zobrazeny všechny části řádku, které se nacházejí vodorovně nad rámec zobrazitelných oblastí editoru. Výběrem této možnosti povolíte možnost **Zobrazit vizuální glyfy pro zalamování řádků** .

> [!NOTE]
> Funkce **virtuálního prostoru** je vypnuta, když je zapnuto **zalamování řádků** .

**Zobrazit vizuální glyfy pro zalamování řádků**

Je-li toto políčko zaškrtnuto, zobrazí se indikátor návratové šipky, kde se na druhý řádek zalomí dlouhá čára.

![Snímek obrazovky LineBreakSymbol](../../ide/reference/media/linebreak.gif)

Tuto možnost zrušte, pokud nechcete zobrazit tyto indikátory.

> [!NOTE]
> Tyto šipky připomenutí nejsou přidány do kódu a netiskou. Jsou pouze pro referenci.

**Čísla řádků**

Je-li toto políčko zaškrtnuto, zobrazí se vedle každého řádku kódu číslo řádku.

> [!NOTE]
> Tato čísla řádků nejsou přidána do kódu a netiskou. Jsou pouze pro referenci.

**Povolit navigaci na adresu URL jedním kliknutím**

Je-li vybrána tato možnost, ukazatel myši se změní na ukazující ruku v případě, že se předává přes adresu URL v editoru. Kliknutím na adresu URL můžete ve webovém prohlížeči zobrazit označenou stránku.

**Navigační panel**

Je-li vybrána tato možnost, zobrazí se **navigační panel** v horní části editoru kódu. Jeho **objekty** DropDown a seznamy **členů** umožňují zvolit konkrétní objekt v kódu, vybrat z jeho členů a přejít k deklaraci vybraného člena v editoru kódu.

**Použít příkazy Vyjmout nebo kopírovat na prázdné řádky, když není vybrán žádný výběr**

Tato možnost nastaví chování editoru při umístění kurzoru na prázdný řádek, výběr možnosti Nothing a zkopírování nebo vyjmutí.

- Pokud je vybrána tato možnost, je prázdný řádek zkopírován nebo vyjmut. Pokud pak vložíte nový, prázdný řádek se vloží.

- Pokud je tato možnost vymazána, příkaz Vyjmout Odstraní prázdné řádky. Data ve schránce jsou ale zachovaná. Proto pokud použijete příkaz pro vložení, obsah naposledy zkopírovaný do schránky se vloží. Pokud jste nic nezkopírovali, nic se nevloží.

Toto nastavení nemá žádný vliv na kopírování nebo vyjmutí, pokud řádek není prázdný. Pokud není nic vybráno, je celý řádek zkopírován nebo vyvyjmut. Pokud vložíte, text celého řádku a jeho EndLine objektu SourceLocation znak se vloží.

> [!TIP]
> Chcete-li zobrazit indikátory pro mezery, tabulátory a konce řádků, a odlišit odsazené řádky od řádků, které jsou zcela prázdné, v nabídce **Upravit** vyberte možnost **Upřesnit** a zvolte možnost **Zobrazit prázdné znaky**.

## <a name="see-also"></a>Viz také

- [Možnosti, Textový editor, Všechny jazyky, Tabulátory](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Pomocí technologie IntelliSense](../../ide/using-intellisense.md)
