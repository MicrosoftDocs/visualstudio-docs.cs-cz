---
title: Možnosti, textový editor, všechny jazyky
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
ms.openlocfilehash: 9815bdec94ce32a3bfcc170dd95d834bc43ea58f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566875"
---
# <a name="options-dialog-box-text-editor--all-languages"></a>Dialogové okno Možnosti: Textový editor \> Všechny jazyky

Toto dialogové okno umožňuje změnit výchozí chování Editoru kódu. Tato nastavení platí také pro ostatní editory založené na Editoru kódu, jako je například zobrazení zdroje návrháře HTML. Chcete-li otevřít toto dialogové okno, vyberte **Možnosti** z nabídky **Nástroje.** Ve složce **Editor textu** rozbalte podsložku **Všechny jazyky** a pak zvolte **Obecné**.

> [!CAUTION]
> Tato stránka nastaví výchozí možnosti pro všechny vývojové jazyky. Nezapomeňte, že obnovení volby v tomto dialogovém okně obnoví obecné možnosti ve všech jazycích na libovolné volby, které jsou zde vybrány. Chcete-li změnit možnosti editoru textu pouze pro jeden jazyk, rozbalte podsložku pro daný jazyk a vyberte jeho stránky možností.

Šedě zaškrtnuté políčko se zobrazí, pokud byla na stránkách Obecné možnosti vybrána možnost pro některé programovací jazyky, ale ne pro jiné.

## <a name="statement-completion"></a>Doplňování výrazů

**Automatické seznamčlenů**

Pokud je tato možnost vybrána, technologie IntelliSense při psaní do editoru zobrazí vyskakovací seznamy dostupných členů, vlastností, hodnot nebo metod. Vyberte libovolnou položku z rozbalovacího seznamu a vložte ji do kódu. Výběrem této možnosti povolíte možnost **Skrýt rozšířené členy.**

**Skrýt pokročilé členy**

Pokud je tato možnost vybrána, zkracuje seznamy dokončení rozbalovacího výpisu zobrazením pouze těch nejčastěji používaných položek. Ostatní položky jsou filtrovány ze seznamu.

**Informace o parametrech**

Je-li tato možnost vybrána, zobrazí se pod kurzorem v editoru úplná syntaxe aktuální deklarace nebo procedury se všemi dostupnými parametry. Další parametr, který můžete přiřadit, se zobrazí tučně.

## <a name="settings"></a>Nastavení

**Povolení virtuálního prostoru**

Pokud je tato volba vybraná a **je zaškrtnutí zalamování aplikace Word,** můžete klepnout na libovolné místo za koncem řádku v Editoru kódu a zadat text. Tuto funkci lze použít k umístění komentáře v konzistentním bodě vedle kódu.

**Zalamování**

Je-li tato možnost vybrána, na dalším řádku se automaticky zobrazí jakákoli část čáry, která se rozprostírá vodorovně za zobrazitelnou oblast editoru. Výběrem této volby povolíte volbu **Zobrazit vizuální glyfy pro zalamování řádků.**

> [!NOTE]
> Funkce **Virtuální prostor** je vypnutá, když je **zapnuté zalamování řádků.**

**Zobrazit vizuální glyfy pro zalamování řádků**

Je-li tato možnost vybrána, zobrazí se indikátor návratové šipky, na kterém se dlouhá čára zalomí na druhý řádek.

![LineBreakSymbol – snímek obrazovky](../../ide/reference/media/linebreak.gif)

Pokud nechcete tyto indikátory zobrazovat, zrušte zaškrtnutí této možnosti.

> [!NOTE]
> Tyto šipky připomenutí nejsou přidány do kódu a netisknou se. Jsou pouze orientační.

**Čísla řádků**

Je-li tato možnost vybrána, zobrazí se vedle každého řádku kódu číslo řádku.

> [!NOTE]
> Tato čísla řádků nejsou přidána do kódu a netisknou se. Jsou pouze orientační.

**Povolení navigace pomocí adresy URL jediným kliknutím**

Když je tato volba vybraná, kurzor myši se při průchodu přes adresu URL v editoru změní na ukazovací ruku. Kliknutím na adresu URL zobrazíte uvedenou stránku ve webovém prohlížeči.

**Navigační panel**

Když je tato volba vybraná, zobrazí **navigační panel** v horní části editoru kódu. Jeho rozevírací **seznamy Objektů** a **Členů** umožňují vybrat konkrétní objekt ve vašem kódu, vybrat z jeho členů a přejde na deklaraci vybraného člena v Editoru kódu.

**Použít příkazy Vyjmout nebo Kopírovat na prázdné řádky, když není žádný výběr**

Tato volba nastaví chování editoru, když umístíte textový kurzor na prázdný řádek, nic nevyberete a potom zkopírujete nebo vyjmete.

- Když je tato volba vybraná, prázdný řádek se zkopíruje nebo vyjme. Pokud potom vložíte, vloží se nový prázdný řádek.

- Když tato volba není jasná, příkaz Vyjmout odstraní prázdné řádky. Data ve schránce jsou však zachována. Pokud tedy použijete příkaz Vložit, vloží se obsah naposledy zkopírovaný do schránky. Pokud nic nebylo zkopírováno dříve, nic je vložen.

Toto nastavení nemá žádný vliv na kopírovat nebo vyjmout, pokud řádek není prázdný. Pokud není nic vybráno, celý řádek se zkopíruje nebo vyjme. Pokud potom vložíte, vloží se text celého řádku a jeho znak koncového řádku.

> [!TIP]
> Chcete-li zobrazit indikátory pro mezery, tabulátory a konce řádků a tedy rozlišovat odsazené čáry od zcela prázdných čar, vyberte v nabídce **Úpravy** možnost **Upřesnit** a zvolte **Zobrazit prázdné místo**.

## <a name="see-also"></a>Viz také

- [Možnosti, Textový editor, Všechny jazyky, Tabulátory](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Používání atributu IntelliSense](../../ide/using-intellisense.md)
