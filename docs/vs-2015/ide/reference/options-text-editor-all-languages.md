---
title: Možnosti, textový editor, všechny jazyky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- vs.toolsoptionspages.text_editor.all_languages.scrollbars
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ebe2da1dec9917a792f3e4e02516a79cff605c80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662405"
---
# <a name="options-text-editor-all-languages"></a>Možnosti, textový editor, všechny jazyky
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toto dialogové okno umožňuje změnit výchozí chování editoru kódu. Tato nastavení platí také pro ostatní editory na základě editoru kódu, jako je například zobrazení zdroje v Návrháři HTML. Chcete-li otevřít toto dialogové okno, vyberte možnost **Možnosti** v nabídce **nástroje** . V rámci složky **textový editor** rozbalte podsložku **všechny jazyky** a zvolte možnost **Obecné**.

> [!CAUTION]
> Tato stránka nastaví výchozí možnosti pro všechny vývojové jazyky. Mějte na paměti, že při resetování možnosti v tomto dialogu dojde k resetování obecných možností ve všech jazycích na jakékoli vybrané možnosti. Chcete-li změnit možnosti textového editoru pouze pro jeden jazyk, rozbalte podsložku pro daný jazyk a vyberte její stránky možností.

 Po výběru možnosti na stránkách Obecné možnosti pro některé programovací jazyky, ale ne pro jiné, se zobrazí šedá značka zaškrtnutí.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="statement-completion"></a>Doplňování výrazů
 Automaticky vypsat členy Pokud jsou vybrány, budou při psaní v editoru v technologii IntelliSense zobrazeny automaticky otevírané seznamy dostupných členů, vlastností, hodnot nebo metod. Výběrem libovolné položky v rozevíracím seznamu vložte položku do kódu. Výběrem této možnosti povolíte možnost **Skrýt pokročilé členy** .

 Skrýt pokročilé členy Pokud je vybrána, zkrátí seznamy pro doplňování příkazů zobrazením pouze těch nejčastěji používaných položek. Další položky jsou filtrovány ze seznamu.

 Informace o parametrech Pokud je tato možnost vybrána, zobrazí se pod kurzorem v editoru Úplná syntaxe pro aktuální deklaraci nebo proceduru se všemi dostupnými parametry. Další parametr, který můžete přiřadit, se zobrazí tučně.

## <a name="settings"></a>Nastavení
 Povolit virtuální prostor, pokud je vybrána tato možnost a **zalamování** řádků je vymazáno, můžete kliknout kamkoli za konec řádku v editoru kódu a zadat. Tato funkce se dá použít k umístění komentářů v konzistentním bodě vedle vašeho kódu.

 Zalamování řádků, pokud je vybráno, všechny části řádku, které přesahují horizontálně nad zobrazitelnou oblast editoru, se automaticky zobrazí na dalším řádku. Výběrem této možnosti povolíte možnost **Zobrazit vizuální glyfy pro zalamování řádků** .

> [!NOTE]
> Funkce **virtuálního prostoru** je vypnuta, když je zapnuto **zalamování řádků** .

 Zobrazit vizuální glyfy pro zalamování řádků, pokud je vybraná, zobrazí se indikátor návratové šipky, kde se dlouhá čára zalomí na druhý řádek.

 ![Snímek obrazovky LineBreakSymbol](../../ide/reference/media/linebreak.gif "LineBreak")

 Tuto možnost zrušte, pokud nechcete zobrazit tyto indikátory.

> [!NOTE]
> Tyto šipky připomenutí nejsou přidány do kódu a netiskou. Jsou pouze pro referenci.

 Použít příkazy Vyjmout nebo kopírovat na prázdné řádky, když není vybrána tato možnost nastaví chování editoru při umístění kurzoru na prázdný řádek, vyberte Nothing a pak zkopírujte nebo vyjměte.

- Pokud je vybrána tato možnost, je prázdný řádek zkopírován nebo vyjmut. Pokud pak vložíte nový, prázdný řádek se vloží.

- Pokud je tato možnost vymazána, příkaz Vyjmout Odstraní prázdné řádky. Data ve schránce jsou ale zachovaná. Proto pokud použijete příkaz pro vložení, obsah naposledy zkopírovaný do schránky se vloží. Pokud jste nic nezkopírovali, nic se nevloží.

  Toto nastavení nemá žádný vliv na kopírování nebo vyjmutí, pokud řádek není prázdný. Pokud není nic vybráno, je celý řádek zkopírován nebo vyvyjmut. Pokud vložíte, text celého řádku a jeho EndLine objektu SourceLocation znak se vloží.

> [!TIP]
> Chcete-li zobrazit indikátory pro mezery, tabulátory a konce řádků, a odlišit odsazené řádky od řádků, které jsou zcela prázdné, v nabídce **Upravit** vyberte možnost **Upřesnit** a zvolte možnost **Zobrazit prázdné znaky**.

## <a name="display"></a>Zobrazení
 Čísla řádků: Pokud je vybrána, číslo řádku se zobrazí vedle každého řádku kódu.

> [!NOTE]
> Tato čísla řádků nejsou přidána do kódu a netiskou. Jsou pouze pro referenci.

 Když vyberete možnost navigace URL jedním kliknutím, ukazatel myši se změní na ukazující ruku, jak se předává přes adresu URL v editoru. Kliknutím na adresu URL můžete ve webovém prohlížeči zobrazit označenou stránku.

 Navigační panel je-li vybrán, zobrazí **navigační panel** v horní části editoru kódu. Jeho **objekty** DropDown a seznamy **členů** umožňují zvolit konkrétní objekt v kódu, vybrat z jeho členů a přejít k deklaraci vybraného člena v editoru kódu.

## <a name="see-also"></a>Viz také
 [Možnosti, textový editor, všechny jazyky,](../../ide/reference/options-text-editor-all-languages-tabs.md) [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md) [pomocí technologie IntelliSense](../../ide/using-intellisense.md)
