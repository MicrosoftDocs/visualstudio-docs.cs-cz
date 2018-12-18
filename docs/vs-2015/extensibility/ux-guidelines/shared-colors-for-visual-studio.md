---
title: Sdílené barvy
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03cfcf2b4ea2b3a0b4773e9c2632c84091819f45
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063225"
---
# <a name="shared-colors-for-visual-studio"></a>Sdílené barvy pro sadu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Při navrhování uživatelského rozhraní, který používá společné prvky prostředí sady Visual Studio, nebo chcete prvek rozhraní pro zajištění konzistence s podobné funkce, použijte existující token názvy v definičních souborech balíčku vybrat a přiřadit barvy. Tím se zajistí, že vaše uživatelské rozhraní zůstane konzistentní s celkové prostředí sady Visual Studio a že se automaticky aktualizuje při přidávání nebo aktualizaci motivy.

 Tento článek popisuje obecné prvky uživatelského rozhraní a token názvy, které používají, které můžete využít při sestavování podobným uživatelským rozhraním. Konkrétní informace o tom, jak přístupové tokeny tyto barvy, naleznete v tématu [VSColor službu](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

 Nezapomeňte použít token názvy správně:

-   **Používejte token názvy založené na funkce, nikoli na vlastní barvu.** Společné sdílené barvy jsou spojeny s prvky určité rozhraní a jsou určeny pouze pro stejné nebo podobné funkce. Například nepoužívejte soubory Barva při stisknutí tlačítka pole se seznamem pro animace průběhu pokryjte pouze z důvodu jako barva. Funkce pole se seznamem a animace se liší, a pokud barva přidružené změny pole se seznamem, už může být vhodné barvu pro prvek animace. Konzistentní použití barev pomůže zorientovat uživatelům a zabránit nejasnostem.

-   **Barvy textu a pozadí pomocí správné kombinace.** Barvy pozadí, které jsou určeny pro použití s textem bude mít k přidružené textového barvu. Nepoužívejte barvy textu, než který je určen pro pozadí. Pokud není k přidružené barvy, nepoužívejte pro všechny povrch, na kterém budete chtít zobrazit text barvy pozadí. Nejde přečíst rozhraní může vést k jiné kombinace barvy textu a pozadí.

-   **Pomocí řízení barvy, které jsou vhodné pro jejich umístění.** V některých stavech některé ovládací prvky sady Visual Studio nemají samostatné ohraničení a barvy pozadí. Místo toho že sbírání tyto barvy z plochy za nimi stojí. Ujistěte se, že vždy používáte token názvy, které jsou vhodné pro umístění, ve kterém jsou umístění ovládacího prvku.

> [!IMPORTANT]
>  Nepoužívejte tokeny v kategorii "Stránka Start" nebo "Jablečného."

## <a name="command-structures"></a>Příkaz struktury

###  <a name="BKMK_CommandMenus"></a> Nabídky
 Nabídek může dojít v několika místech v rámci sady Visual Studio: hlavní nabídek vložený v dokumentu nebo nástroje systému windows, nebo klikněte pravým tlačítkem na různých místech v celém rozhraní IDE. Implementace nabídky spojené s další prvky uživatelského rozhraní jsou popsány v části pro odpovídající prvek. Vždy byste měli používat standardní nabídky implementace poskytovaných prostředím sady Visual Studio. V některých výjimečných případech ale nebudete mít přístup k standardní nabídky sady Visual Studio. V těchto situacích nepoužívejte následující názvy token k zajištění, že vaše uživatelské rozhraní je v souladu s jiným nabídkám v sadě Visual Studio.

 ![Červená nabídky značka](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 000_MenuRedline")

 Použití...
 -   vždy, když je potřeba vytvořit vlastní nabídku.

- Pokud máte nové komponenty uživatelského rozhraní, který chcete porovnat nabídek sady Visual Studio.

  Nepoužívejte...
  Barva pozadí samostatně. Vždy použijte kombinaci na pozadí a popředí uvedené.

#### <a name="menu-title"></a>Název nabídky
 Názvy nabídek se skládají z na pozadí, ohraničení a text nadpisu, jakož i volitelný glyf, obvykle, když se nachází v nabídce v panelu příkazů.

 ![Název nabídky červená značka](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 001_MenuTitleRedline")

 Použití...
vždy, když vytváříte název vlastní nabídku.

 Nepoužívejte...
 -   pro všechno, co nechcete vždy odpovídat názvu nabídky.

- v libovolné na pozadí a popředí jinými než která byla specifikována.

  **Default**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Výchozí název nabídky](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 002_MenuTitleDefault")

  **Název nabídky**

  Pozadí

  Žádné

  Popředí (Text)

  `Environment.CommandBarTextActive`

  ![Název nabídky s výchozí piktogram](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")

  **Název nabídky glyfem**

  Popředí (piktogram)

  `Environment.CommandBarMenuGlyph`

  Ohraničení

  Žádné

  **Při najetí myší**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Název nabídky při najetí myší](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 004_MenuTitleHover")

  **Název nabídky**

  Pozadí

  `Environment.CommandBarMouseOverBackgroundBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `Environment.CommandBarTextHover`

  ![Název nabídky glyfem při najetí myší](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")

  **Název nabídky glyfem**

  Popředí (piktogram)

  `Environment.CommandBarMenuMouseOverGlyph`

  Ohraničení

  `Environment.CommandBarBorder`

  **Stisknutí**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Název nabídky stisknutí](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 006_MenuTitlePressed")

  **Název nabídky**

  Pozadí

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `Environment.CommandBarTextActive`

  ![Název nabídky glyfem stisknutí](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")

  **Název nabídky glyfem**

  Popředí (piktogram)

  `Environment.CommandBarMenuMouseDownGlyph`

  Ohraničení

  `Environment.CommandBarMenuBorder`

  Pouze vlevo nahoře a pravé straně.

  **Zakázané**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Název nabídky glyfem zakázané](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")

  **Název nabídky glyfem**

  Pozadí

  Žádné

  Popředí (Text)

  `Environment.CommandBarTextInactive`

  Popředí (piktogram)

  `Environment.CommandBarTextInactive`

  Ohraničení

  Žádné

#### <a name="menu"></a>Nabídka
 Individuální nabídky položky se skládá z text nabídky a volitelné ikony, zaškrtněte políčko nebo podnabídka glyfů. Jeho textu a pozadí Změna barvy při najetí myší. Tento token barva je pár na pozadí a popředí.

 ![Červená značka položky nabídky](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 009_MenuItemRedline")

 Použití...
pro všechny rozevíracího seznamu, který se spustí z panelu příkazů a nabídek.

 Nepoužívejte...
 -   pro všechny rozevíracího seznamu, který se nachází v jiném kontextu.

- v libovolné na pozadí a popředí jinými než která byla specifikována.

  **Default**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Výchozí nabídky](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")

  **Nabídka**

  Pozadí

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `Environment.CommandBarTextActive`

  Popředí (podnabídky piktogram)

  `Environment.CommandBarMenuSubmenuGlyph`

  Ohraničení

  `Environment.CommandBarMenuBorder`

  Pozadí ikony kanálu

  `Environment.CommandBarMenuIconBackground`

  Oddělovač

  `Environment.CommandBarMenuSeparator`

  Stín

  `Environment.DropShadowBackground`

  ![Nabídka zaškrtnutí](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 011_MenuChecked")

  **Zaškrtnuto**

  Zaškrtávací políčko

  `Environment.CommandBarCheckBox`

  Zaškrtávací políčko na pozadí

  `Environment.CommandBarSelectedIcon`

  ![Nabídky vybrána](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 012_MenuSelected")

  **Vybrané**

  Pozadí ikony

  `Environment.CommandBarSelected`

  Okraj ikony

  `Environment.CommandBarSelectedBorder`

  **Při najetí myší**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Nabídky při najetí myší](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")

  **Položka nabídky**

  Pozadí

  `Environment.CommandBarMenuItemMouseOver`

  Popředí (Text)

  `Environment.CommandBarMenuItemMouseOver`

  Popředí (podnabídky piktogram)

  `Environment.CommandBarMenuMouseOverSubmenuGlyph`

  ![Nabídky při najetí myší zaškrtnutí](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 014_MenuHoverChecked")

  **Zaškrtnuto**

  Zaškrtávací políčko

  `Environment.CommandBarCheckBoxMouseOver`

  Zaškrtávací políčko na pozadí

  `Environment.CommandBarHoverOverSelectedIcon`

  ![Nabídky při najetí myší vybraný](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 015_MenuHoverSelected")

  **Vybrané**

  Pozadí ikony

  `Environment.CommandBarHoverOverSelected`

  Okraj ikony

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Zakázané**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Nabídka zakázané](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 016_MenuDisabled")

  Položka nabídky

  Popředí (Text)

  `Environment.CommandBarTextInactive`

  Popředí (podnabídky piktogram)

  `Environment.CommandBarMenuSubmenuGlyph`

  ![Nabídky zakázáno zaškrtnutí](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 017_MenuDisabledChecked")

  Zaškrtnuto

  Zaškrtávací políčko

  `Environment.CommandBarCheckBoxDisabled`

  Zaškrtávací políčko na pozadí

  `Environment.CommandBarSelectedIconDisabled`

### <a name="command-bar"></a>Panel příkazů
 Na panelu příkazů lze zobrazit na více místech v rámci rozhraní IDE sady Visual Studio, zejména příkaz polici a embedded v nástroji nebo okna dokumentu.

 Obecně platí vždy používejte implementace standardních příkazů panelu poskytovaných prostředím sady Visual Studio. Pomocí standardní mechanismus zajišťuje, že se správně zobrazí všechny podrobnosti o visual a interaktivní prvky, ke které přistupuje konzistentní s jinými ovládacími prvky sady Visual Studio příkazového řádku. Nicméně pokud je nutné, můžete vytvořit vlastní panel příkazů, ujistěte se, že správně pomocí následující token názvy stylu.

 ![Panel příkazů červená značka](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 018_CommandBarRedline")

 ![Červená tlačítku přetečení značka](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 019_OverflowButtonRedline")

 Použití...
na místech, kde je třeba vložené příkaz panelu ale nebudou moct používat standardní implementace panel příkaz sady Visual Studio.

 Nepoužívejte...
 -   pro prvky uživatelského rozhraní, které nejsou podobný panelu příkazů.

-   pro příkaz součástí než ty, pro kterou token názvy jsou určené.

#### <a name="command-bar-group"></a>Příkaz pruhový graf
 Příkaz pruhový graf se skládá ze sady související ovládací prvky stavového řádku příkaz a může obsahovat libovolný počet tlačítek rozdělení tlačítek, rozevíracích nabídek, pole se seznamem nebo nabídky. Barvy pro tyto ovládací prvky se budou řídit token názvy a jsou jednotlivě jinde popsaných v této příručce. Oddělovací čáry se používá k rozdělení skupiny panelu příkazů na související podskupiny.

 ![Skupiny příkazového řádku červeně označit](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 020_CommandBarGroupRedline")

 Použití...
na místech, kde je třeba vložené příkaz panelu ale nebudou moct používat standardní implementace panel příkaz sady Visual Studio.

 Nepoužívejte...
 -   pro prvky uživatelského rozhraní, které nejsou podobný panelu příkazů.

- pro příkaz součástí než ty, pro kterou token názvy jsou určené.

  **Výchozí** (ostatní stavy)

  Prvek

  Název tokenu: Category.color

  Pozadí

  `Environment.CommandBarGradientBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Ohraničení

  `Environment.CommandBarToolBarBorder`

  Úchyt pro přetažení

  `Environment.CommandBarDragHandle`

  Oddělovač

  `Environment.CommandBarToolBarSeparator`

  `Environment.CommandBarToolBarSeparatorHighlight`

#### <a name="command-icons"></a>Ikony příkazů
 ![Červená ikona příkazu. značka](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 021_CommandIconRedline1")

 ![Červená ikona příkazu. značka](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 022_CommandIconRedline2")

 Použití...
u tlačítek, které budou umístěny na panelu příkazů.

 Nepoužívejte...
 -   pro ovládací prvky, které mají své vlastní token názvy.

- v libovolné na pozadí a popředí jinými než která byla specifikována.

  **Default**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Příkaz výchozí ikona](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")

  **Default**

  Pozadí

  Není k dispozici (dědí nastavení z příkazového řádku na pozadí)

  Popředí (Text)

  `Environment.CommandBarTextActive`

  Ohraničení

  Není k dispozici

  ![Příkaz výchozí ikona vybrané](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")

  **Vybrané**

  Pozadí

  `Environment.CommandBarSelected`

  Popředí (Text)

  `Environment.CommandBarTextSelected`

  Ohraničení

  `Environment.CommandBarSelectedBorder`

  **Podržte ukazatel myši a klávesnice, zaměřuje**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Příkaz ikonu při najetí myší](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")

  **Standardní při najetí myší**

  Pozadí

  `Environment.CommandBarMouseOverBackgroundBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `Environment.CommandBarTextHover`

  Ohraničení

  `Environment.CommandBarBorder`

  ![Příkaz vybrali při najetí myší ikonu](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")

  **Vybráno při najetí myší**

  Pozadí

  `Environment.CommandBarHoverOverSelected`

  Popředí (Text)

  `Environment.CommandBarTextHoverOverSelected`

  Ohraničení

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Stisknutí**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Ikona příkaz stisknutí](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")

  **Ikona při stisknutí příkazu.**

  Pozadí

  `Environment.CommandBarMouseDownBackgroundBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `Environment.CommandBarTextMouseDown`

  Ohraničení

  `Environment.CommandBarBorder`

  **Zakázané**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Ikona příkazu zakázané](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")

  **Ikona zakázané příkazu.**

  Pozadí

  Není k dispozici (dědí nastavení z příkazového řádku na pozadí)

  Popředí (Text)

  `Environment.CommandBarTextInactive`

  Ohraničení

  Není k dispozici

####  <a name="BKMK_CommandComboBox"></a> Pole se seznamem

> [!IMPORTANT]
>  Pole se seznamem se podobají rozevírací seznamy, ale zahrnují určitá oblast upravitelný text. Pokud rozevírací seznam neobsahuje určitá oblast upravitelný text, použití tokenů barva nalezené pod [rozevíracího seznamu](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

 ![Červená pole se seznamem značka](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 029_ComboBoxRedline")

 Použití...
 -   Při vytváření vlastního pole se seznamem.

- Při vytváření ovládací prvek panelu příkazů, který je podobný pole se seznamem.

  Nepoužívejte...
  -   pro všechno, co nechcete, aby vždy tak, aby odpovídaly příkaz uživatelské rozhraní panelu.

- Když máte přístup k upravený pole se seznamem.

  **Default**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vstupní pole se seznamem](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")

  **Vstupní pole**

  Pozadí

  `Environment.ComboBoxBackground`

  Popředí (Text)

  `Environment.ComboBoxText`

  Ohraničení

  `Environment.ComboBoxBorder`

  Oddělovač

  Žádný oddělovač

  ![Rozevírací pole se seznamem&#45;tlačítko](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  Není k dispozici (dědí)

  Popředí (piktogram)

  `Environment.ComboBoxGlyph`

  ![Pole se seznamem&#47;vyřadit&#45;dolů seznam](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")

  **Rozevírací seznam**

  Pozadí

  `Environment.ComboBoxPopupBackgroundBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `Environment.ComboBoxItemText`

  Ohraničení

  `Environment.ComboBoxPopupBorder`

  **Při najetí myší**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vstupní pole se seznamem při najetí myší](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")

  **Vstupní pole**

  Pozadí

  `Environment.ComboBoxMouseOverBackgroundBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `Environment.ComboBoxMouseOverText`

  Ohraničení

  `Environment.ComboBoxMouseOverBorder`

  Oddělovač

  `Environment.ComboBoxMouseOverSeparator`

  ![Pole se seznamem&#47;vyřadit&#45;tlačítka při najetí myší](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `Environment.ComboBoxButtonMouseOverBackground`

  Popředí (piktogram)

  `Environment.ComboBoxMouseOverGlyph`

  ![Pole se seznamem&#47;vyřadit&#45;seznamu při najetí myší dolů](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")

  **Rozevírací seznam**

  Na pozadí (položka nabídky)

  `Environment.ComboBoxItemMouseOverBackground`

  Popředí (Text)

  `Environment.ComboBoxItemMouseOverText`

  Ohraničení (položka nabídky)

  `Environment.ComboBoxItemMouseOverBorder`

  **Fokus**

  Součást

  Prvek

  Název tokenu: Color.category

  ![Pole se seznamem vstupní fokus](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")

  **Vstupní pole**

  Pozadí

  `Environment.ComboBoxFocusedBackground`

  Popředí (Text)

  `Environment.ComboBoxFocusedText`

  Ohraničení

  `Environment.ComboBoxFocusedBorder`

  Oddělovač

  `Environment.ComboBoxFocusedButtonSeparator`

  ![Pole se seznamem&#47;vyřadit&#45;tlačítko, zaměřuje](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `Environment.ComboBoxFocusedButtonBackground`

  Popředí (piktogram)

  `Environment.ComboBoxFocusedGlyph`

  **Stisknutí**

  Součást

  Prvek

  Název tokenu: Color.category

  ![Pole se seznamem vstupního stisknutí](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")

  **Vstupní pole**

  Pozadí

  `Environment.ComboBoxMouseDownBackground`

  Popředí (Text)

  `Environment.ComboBoxMouseDownText`

  Ohraničení

  `Environment.ComboBoxMouseDownBorder`

  Oddělovač

  `Environment.ComboBoxMouseDownSeparator`

  ![Pole se seznamem&#47;vyřadit&#45;dolů stisknutí tlačítka](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `Environment.ComboBoxButtonMouseDownBackground`

  Popředí (piktogram)

  `Environment.ComboBoxMouseDownGlyph`

  **Zakázané**

  ![Pole se seznamem vstupního zakázané](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")

  **Vstupní pole**

  Pozadí

  `Environment.ComboBoxDisabledBackground`

  Popředí (Text)

  `Environment.ComboBoxDisabledText`

  Ohraničení

  `Environment.ComboBoxDisabledBorder`

  Oddělovač

  Žádný oddělovač

  ![Pole se seznamem&#47;vyřadit&#45;tlačítko zakázané](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  Žádné

  Popředí (piktogram)

  `Environment.ComboBoxDisabledGlyph`

####  <a name="BKMK_CommandDropDown"></a> Rozevírací seznam

> [!IMPORTANT]
>  Rozevírací seznamy jsou podobné polích se seznamem, ale nemají upravitelný text oblastech. Pokud rozevírací seznam obsahuje určitá oblast upravitelný text, použití tokenů barva nalezené pod [– pole se seznamem](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

 ![Vyřadit&#45;dolů červená značka](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 042_DropdownRedline")

 Použití...
Pokud při vytváření vlastní rozevírací seznam ovládacích prvků.

 Nepoužívejte...
 -   pro všechno, co to není podobný rozevíracího seznamu.

- pro pole se seznamem nebo tlačítka rozdělení.

  **Default**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vyřadit&#45;dolů pole výběru](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")

  **Výběr pole**

  Pozadí

  `Environment.DropDownBackground`

  Popředí (Text)

  `DropDownText`

  Ohraničení

  `DropDownBorder`

  Oddělovač

  Žádný oddělovač

  ![Vyřadit&#45;tlačítko](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 044_DropdownButton")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  Žádné

  Popředí (piktogram)

  `Environment.DropDownGlyph`

  ![Vyřadit&#45;dolů seznam](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")

  **Rozevírací seznam**

  Pozadí

  `Environment.DropDownPopupBackgroundBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `Environment.ComboBoxItemText`

  Ohraničení

  `Environment.DropDownPopupBorder`

  Stín

  `Environment.DropShadowBackground`

  **Při najetí myší**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vyřadit&#45;dolů výběr pole při najetí myší](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")

  **Výběr pole**

  Pozadí

  `Environment.DropDownMouseOverBackgroundBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `Environment.DropDownMouseOverText`

  Ohraničení

  `Environment.DropDownMouseOverBorder`

  Oddělovač

  `Environment.DropDownButtonMouseOverSeparator`

  ![Vyřadit&#45;tlačítka při najetí myší](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 047_DropdownButtonHover")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `Environment.DropDownButtonMouseOverBackground`

  Popředí (piktogram)

  `Environment.DropDownMouseOverGlyph`

  ![Vyřadit&#45;seznamu při najetí myší dolů](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")

  **Rozevírací seznam**

  Na pozadí (položka nabídky)

  `Environment.ComboBoxItemMouseOverBackground`

  Popředí (Text)

  `Environment.ComboBoxItemMouseOverText`

  Ohraničení (položka nabídky)

  `Environment.ComboBoxItemMouseOverBorder`

  **Stisknutí**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vyřadit&#45;dolů pole výběru stisknutí](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")

  **Výběr pole**

  Pozadí

  `Environment.DropDownMouseDownBackground`

  Popředí (Text)

  `Environment.DropDownMouseDownText`

  Ohraničení

  `Environment.DropDownMouseDownBorder`

  Oddělovač

  `Environment.DropDownButtonMouseDownSeparator`

  ![Vyřadit&#45;dolů stisknutí tlačítka](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `Environment.DropDownButtonMouseDownBackground`

  Popředí (piktogram)

  `Environment.DropDownMouseDownGlyph`

  **Zakázané**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vyřadit&#45;dolů pole výběru zakázané](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")

  Pozadí

  `Environment.DropDownDisabledBackground`

  Popředí (Text)

  `Environment.DropDownDisabledText`

  Ohraničení

  `Environment.DropDownDisabledBorder`

  Oddělovač

  Žádný oddělovač

  ![Vyřadit&#45;tlačítko zakázané](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")

  Pozadí

  Není k dispozici

  Popředí (piktogram)

  `Environment.DropDownDisabledGlyph`

#### <a name="split-button"></a>Tlačítko rozdělení
 Tlačítka rozdělení sdílet s jinými ovládacími prvky příkazového řádku, jako jsou tlačítka, nabídky a panelu text příkazu mnoho názvů token. Všechny potřebné akce a tlačítkem rozevírací nabídky token názvy pro usnadnění práce tady opakují. Rozdělené tlačítko rozevírací seznamy jsou implementace panelu příkazů [nabídky](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

 ![Tlačítko rozdělení červená značka](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 053_SplitButtonRedline")

 Použití...
Když vytváříte tlačítko rozdělení vlastní.

 Nepoužívejte...
 -   pro jiné typy tlačítek.

- v libovolné na pozadí a popředí jinými než která byla specifikována.

  **Default**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Tlačítko rozdělení](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")

  **Tlačítko rozdělení (výchozí)**

  Pozadí

  Žádné

  Popředí (Text)

  `Environment.CommandBarTextActive`

  Popředí (piktogram)

  `Environment.CommandBarSplitButtonGlyph`

  Ohraničení

  Není k dispozici

  Oddělovač

  Není k dispozici

  **Při najetí myší**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Tlačítko rozdělení při najetí myší](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")

  **Tlačítko rozdělení (při najetí myší)**

  Pozadí

  `Environment.CommandBarMouseOverBackgroundBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `Environment.CommandBarTextHover`

  Popředí (piktogram)

  `Environment.CommandBarSplitButtonMouseOverGlyph`

  Ohraničení

  `Environment.CommandBarBorder`

  Oddělovač

  `Environment.CommandBarSplitButtonSeparator`

  **Stisknutí**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Stisknutí tlačítka rozdělení](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")

  **Tlačítko rozdělení (stisknutí)**

  Pozadí

  `Environment.CommandBarMouseDownBackgroundBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `Environment.CommandBarTextMouseDown`

  Popředí (piktogram)

  `Environment.CommandBarSplitButtonMouseDownGlyph`

  Ohraničení

  `Environment.CommandBarBorder`

  Oddělovač

  Není k dispozici

  **Zakázané**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Tlačítko rozdělení zakázané](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")

  **Tlačítko rozdělení (zakázáno)**

  Pozadí

  Není k dispozici

  Popředí (Text)

  `Environment.ComboBoxItemTextInactive`

  Popředí (piktogram)

  `Environment.CommandBarTextInactive`

  Ohraničení

  Není k dispozici

  Oddělovač

  Není k dispozici

#### <a name="more-options-and-overflow-buttons"></a>Další možnosti a 'Overflow' tlačítka
 Tlačítko "Další možnosti" se používá při skupinou příkazů panelu přizpůsobitelné buď přidáním nebo odebráním související panelu příkazů. Tlačítko "Přetečení" se zobrazí, když je zkrácena kvůli nedostatku místa na vodorovné panel příkazů a při kliknutí zobrazí nabídku, která obsahuje panelu příkazů nelze zobrazit. Barvy pro tyto dvě tlačítka se řídí stejnou sadu token názvy.

 ![Další možnosti červená značka](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 058_MoreOptionsRedline")

 Použití...
pro vlastní "Další možnosti' nebo 'Overflow' tlačítka.

 Nepoužívejte...
u tlačítek, které nemají podobné funkce jako více možností nebo 'Overflow' tlačítko.

 **Default**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Další možnosti](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 059_MoreOptions")

 **Další možnosti**

 ![Tlačítko přetečení](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 060_Overflow")

 **přetečení**

 Pozadí

 `Environment.CommandBarOptionsBackground`

 Popředí (piktogram)

 `Environment.CommandBarOptionsGlyph`

 **Při najetí myší**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Další možnosti při najetí myší](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 061_MoreOptionsHover")

 **Další možnosti**

 ![Přetečení při najetí myší](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 062_OverflowOptions")

 **přetečení**

 Pozadí

 `Environment.CommandBarOptionsMouseOverBackgroundBegin`

 Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

 Popředí (piktogram)

 `Environment.CommandBarOptionsMouseDownGlyph`

 **Stisknutí**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Další možnosti stisknutí](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 063_MoreOptionsPressed")

 **Další možnosti**

 ![Přetečení stisknutí](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 064_OverflowPressed")

 **přetečení**

 Pozadí

 `Environment.CommandBarOptionsMouseDownBackgroundBegin`

 Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

 Popředí (piktogram)

 `Environment.CommandBarOptionsMouseDownGlyph`

## <a name="document-windows"></a>Okna dokumentů
 Není nutné replikovat okna dokumentu, protože jsou poskytovány prostředí sady Visual Studio. Ale můžete se rozhodnout, že chcete využít barvy použité v dokumentu systému windows tak, aby vaše uživatelské rozhraní se vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.

 Při použití tokenů barva okno dokumentu, musíte být opatrní při jejich použití pouze pro podobné prvky a vždy ve dvojicích. Pokud to neuděláte, budete mít neočekávané výsledky v uživatelském rozhraní.

### <a name="document-window-frame"></a>Rámeček okna dokumentu
 Okna dokumentu může být ukotven v integrovaném vývojovém prostředí nebo s plovoucí desetinnou čárkou jako samostatném okně. Pokud je číslo s plovoucí čárkou okna dokumentu mimo rozhraní IDE, ji stále nachází v kontejneru dokumentu a má na pozadí, ohraničení, textu a barvy karet MDI, které se shodují, pokud je částí rozhraní IDE. Ale dokumentu se nachází uvnitř rámečku, který má svou vlastní pozadí ohraničení a barvy textu. Když okna nástrojů jsou ukotveny v kontejneru dokumentu, dědí chování a barvy pro jejich karty z tokenu názvy oken dokumentů.

 ![Červená ukotvených dokumentu – okno značka](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")

 **Ukotvené dokumentu – okno**

 ![Plovoucí okna dokumentu červená značka](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")

 **Plovoucí okna dokumentu**

 Použití...
kdekoli vytvoříte uživatelské rozhraní, které chcete najít okno dokumentu.

 Nepoužívejte...
uživatelské rozhraní, který chcete změnit, pokud nechcete automaticky prostředí má aktualizace motivu.

 **Default**

 Součást

 Prvek

 Název tokenu: Category.color

 Dokument: ukotven nebo s plovoucí desetinnou čárkou

 Pozadí

 Závisí na typu dokumentu

 Popředí (Text)

 Závisí na typu dokumentu

 Ohraničení

 `Environment.ToolWindowBorder`

 ![Rámce, zaměřuje](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")

 **Snímek: s plovoucí desetinnou čárkou, zaměřuje**

 Pozadí

 `Environment.ToolWindowFloatingFrame`

 Popředí (Text)

 `Environment.ToolWindowFloatingFrame`

 Popředí (piktogram)

 `Environment.RaftedWindowButtonActiveGlyph`

 Ohraničení

 `Environment.MainWindowActiveDefaultBorder`

 Ohraničení (piktogram)

 `Environment.RaftedWindowButtonActiveBorder`

 Nastavte na transparentní

 ![Rámec bez fokusu](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")

 **Snímek: s plovoucí desetinnou čárkou, bez fokusu**

 Pozadí

 `Environment.ToolWindowFloatingFrameInactive`

 Popředí (Text)

 `Environment.ToolWindowFloatingFrameInactive`

 Popředí (piktogram)

 `Environment.RaftedWindowButtonInactiveGlyph`

 Ohraničení

 `Environment.MainWindowInactiveBorder`

 Ohraničení (piktogram)

 `Environment.RaftedWindowButtonInactiveBorder`

 Nastavte na transparentní

 **Při najetí myší**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Rámce, zaměřuje při najetí myší](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")

 **Snímek: s plovoucí desetinnou čárkou, zaměřuje**

 Na pozadí (piktogram)

 `Environment.RaftedWindowButtonHoverActive`

 Popředí (piktogram)

 `Environment.RaftedWindowButtonHoverActiveGlyph`

 Ohraničení (piktogram)

 `Environment.RaftedWindowButtonHoverActiveBorder`

 ![Rámce při najetí myší bez fokusu](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")

 **Snímek: s plovoucí desetinnou čárkou, bez fokusu**

 Na pozadí (piktogram)

 `EnvironmentRaftedWindowButtonHoverInactive`

 Popředí (piktogram)

 `Environment.RaftedWindowButtonHoverInactiveGlyph`

 Ohraničení (piktogram)

 `Environment.RaftedWindowButtonHoverInactiveBorder`

 **Stisknutí**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Rámce, zaměřuje při stisknutí](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")

 **Snímek: s plovoucí desetinnou čárkou, zaměřuje**

 Na pozadí (piktogram)

 `Environment.RaftedWindowButtonDown`

 Popředí (piktogram)

 `Environment.RaftedWindowButtonDownGlyph`

 Ohraničení (piktogram)

 `Environment.RaftedWindowButtonDownBorder`

### <a name="document-tabs"></a>Záložky dokumentů
 Karty dokumentů se nacházejí v kanálu kartu označující dokumenty, které jsou právě otevřeny, a která z nich je aktuální vybraná nebo aktivní dokument. Okna nástrojů lze také ukotvit v kanálu kartu dokumentu, pokud existuje uživatel je umístí. V takovém případě používají stejné barvy karet jako okna dokumentu. Při vytváření uživatelského rozhraní, který chcete vždy odpovídat barvy okno dokumentu (včetně aktualizací motiv nebo pokud jsou nainstalovány nové motivy) a pak odkazovat na tyto barvy tokeny.

 ![Červená záložky v dokumentu značka](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 072_DocumentTabRedline")

 Použití...
kdekoli vytvoříte uživatelské rozhraní, které chcete odpovídat karty dokumentů a automaticky získávají aktualizace motiv nebo nové barvy motivu.

 Nepoužívejte...
pro všechny uživatelské rozhraní, které nechcete automaticky změnit, pokud prostředí má motiv aktualizovat.

#### <a name="open-document-tabs"></a>Karty otevřených dokumentů
 Každý otevřený dokument obsahuje kartu v kanálu kartu dokumentu, který se zobrazí její název. Dokumenty, můžete buď vybrat nebo otevřete na pozadí a jejich karty, aby odrážela tyto stavy:

- Vybraná karta představuje dokument, který je dobře zobrazeno v dokumentu. Vybraná karta má ohraničení dokumentu, který rozšiřuje dobře mezi horním okrajem dokumentu.

- Karty na pozadí jsou všechny karty dokumentů, které nejsou aktuálně vybraná karta. Po kliknutí na stát vybraná karta a získat všechny barvy ohraničení, textu a pozadí z těchto tokenů názvy.

  ![Červená dokument otevřít kartu značka](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")

  Použití...
  Pokud při vytváření vlastního dokumentu karty.

  Nepoužívejte...
  -   u tabulátorů prozatímní (preview).

- prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.

#### <a name="selected-tab"></a>Vybraná karta
 **Fokus**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Vybraná karta, zaměřuje](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")

 **Vybraný dokument kartu, zaměřuje**

 Pozadí

 `Environment.FileTabSelectedGradientTop`

 Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

 Popředí (Text)

 `Environment.FileTabSelectedText`

 Ohraničení

 `Environment.FileTabSelectedBorder`

 Nastavte stejnou barvu jako pozadí.

 Dokument ohraničení

 `Environment.FileTabDocumentBorderBackground`

 **Bez fokusu**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Vybraná karta bez fokusu](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")

 **Vybraný dokument karty, bez fokusu**

 Pozadí

 `Environment.FileTabInactiveGradientTop`

 Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

 Popředí (Text)

 `Environment.FileTabInactiveText`

 Ohraničení

 `Environment.FileTabInactiveBorder`

 Nastavte stejnou barvu jako pozadí.

 Dokument ohraničení

 `Environment.FileTabInactiveDocumentBorderBackground`

#### <a name="background-tab"></a>Karty na pozadí
 **Default**

 ![Karta pozadí](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")

 **Výchozí kartu na pozadí**

 Pozadí

 `Environment.FileTabBackground`

 Popředí (Text)

 `Environment.FileTabText`

 Ohraničení

 `Environment.FileTabBorder`

 Nastavte stejnou barvu jako pozadí.

 **Při najetí myší**

 ![Karty na pozadí při najetí myší](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")

 **Karty na pozadí při najetí myší**

 Pozadí

 `Environment.FileTabHotGradientTop`

 Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

 Popředí (Text)

 `Environment.FileTabHotText`

 Ohraničení

 `Environment.FileTabHotBorder`

 Nastavte stejnou barvu jako pozadí.

#### <a name="preview-tab"></a>Karta náhledu
 Na kartě preview se zobrazí na pravé straně kanálu kartu dokumentu po kliknutí na položku v panelu nástrojů Průzkumníku řešení. Funguje jako náhled dokumentu a také umožňuje uživateli možnost zachovat dokument otevřít na levé straně kanálu kartu dokumentu. Otevřenou kartou pouze jednu verzi preview může být najednou otevřený. Ve verzi Preview karty mají i na pozadí a vybraných států, jako jsou otevřené karty a může být zaměřené nebo bez fokusu v aktivním stavu.

 ![Červená kartu náhledu značka](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 078_PreviewTabRedline")

 Použití...
kdekoli vytváření prozatímní ve verzi preview a má nějaký element tak, aby odpovídaly aktuální barvu karty ve verzi preview.

 Nepoužívejte...
 -   pro jakýkoli druh dokumentu nebo kartu, která není prozatímní (preview).

- prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.

  **Karta vybrané ve verzi preview: fokus**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Kartu náhledu, zaměřuje](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")

  **Karta cílené ve verzi preview**

  Pozadí

  `Environment.FileTabProvisionalSelectedActive`

  Popředí (Text)

  `Environment.FileTabProvisionalSelectedActiveForeground`

  Ohraničení

  `Environment.FileTabProvisionalSelectedActiveBorder`

  Nastavte stejnou barvu jako pozadí.

  Dokument ohraničení

  `Environment.FileTabProvisionalSelectedActiveBorder`

  **Karta vybrané ve verzi preview: bez fokusu**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Karta náhled bez fokusu](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")

  **Karta náhled bez fokusu**

  Pozadí

  `Environment.FileTabProvisionalSelectedInactive`

  Popředí (Text)

  `Environment.FileTabProvisionalSelectedInactiveForeground`

  Ohraničení

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  Dokument ohraničení

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  **Karta náhled na pozadí: výchozí**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Ve verzi Preview na pozadí kartu](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")

  **Kartu pozadí kartu náhledu**

  Pozadí

  `Environment.FileTabProvisionalInactive`

  Popředí (Text)

  `Environment.FileTabProvisionalInactiveForeground`

  Ohraničení

  `Environment.FileTabProvisionalInactiveBorder`

  Nastavte stejnou barvu jako pozadí.

  **Karta náhled na pozadí: při najetí myší**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Karta náhled na pozadí při najetí myší](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")

  **Karty na pozadí karta náhled při najetí myší**

  Pozadí

  `Environment.FileTabProvisionalHover`

  Popředí (Text)

  `Environment.FileTabProvisionalHoverForeground`

  Ohraničení

  `Environment.FileTabProvisionalHoverBorder`

  Nastavte stejnou barvu jako pozadí.

#### <a name="document-overflow-button"></a>Dokument tlačítku přetečení
 Tlačítko přetečení dokument je k dispozici, pokud existuje jedna nebo více dokumentů otevřít, bez ohledu na to, zda je v aktuální konfiguraci podle všechny karty dokumentu svislé mezery. Rozevírací nabídky přetečení dokumentu, který je kontrolován **CommandBarMenu** barvy (naleznete v tématu [nabídky](../../misc/shared-colors.md#BKMK_CommandMenus)), zobrazí seznam všech otevřených dokumentech, viditelný nebo skrytý a změny piktogram přetečení podle toho, jestli se zobrazí všechny otevřené dokumenty v kanálu kartu.

 ![Červená přetečení značka](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 083_OverflowRedline")

 Použití...
Když vytvoříte tlačítko přetečení vlastní šablony dokumentů.

 Nepoužívejte...
 -   pro uživatelské rozhraní, která není podobné k tlačítku přetečení.

- pro tlačítka přetečení panelu příkazů.

  **Default**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Overflow](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 084_Overflow")

  **Dokument tlačítku přetečení**

  Pozadí

  `Environment.DocWellOverflowButtonBackground`

  Popředí (piktogram)

  `Environment.DocWellOverflowButtonGlyph`

  Ohraničení

  Není k dispozici

  **Při najetí myší**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Přetečení při najetí myší](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")

  **Dokument přetečení tlačítka při najetí myší**

  Pozadí

  `Environment.DocWellOverflowButtonMouseOverBackground`

  Popředí (piktogram)

  `Environment.DocWellOverflowButtonMouseOverGlyph`

  Ohraničení

  `Environment.DocWellOverflowButtonMouseOverBorder`

  **Stisknutí**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Přetečení stisknutí](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")

  **Stiskne tlačítko přetečení dokument**

  Pozadí

  `Environment.DocWellOverflowButtonMouseDownBackground`

  Popředí (piktogram)

  `Environment.DocWellOverflowButtonMouseDownGlyph`

  Ohraničení

  `Environment.DocWellOverflowButtonMouseDownBorder`

## <a name="tool-windows"></a>Nástroje systému windows
 Není nutné replikovat okna nástrojů, protože jsou poskytovány prostředí sady Visual Studio. Ale můžete se rozhodnout, že chcete využít barvy použité v oknech nástrojů tak, aby vaše uživatelské rozhraní se vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.

 ![Panel nástrojů červená značka](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 087_ToolWindowRedline")

 Použití...
kdekoli vytvoříte uživatelské rozhraní, které chcete porovnat okna nástrojů.

 Nepoužívejte...
prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.

### <a name="tool-window-frame"></a>Rámeček okna nástroje
 Okna nástrojů v sadě Visual Studio se používají pro celou řadu různých úloh a může existovat v jednom z několika různých stavů. Pokud je panel nástrojů otevřen, může být přiřazena k některému z čtyřech stranách oblasti dokumentu. Nástroje systému windows můžete také uvolnit mimo rozhraní IDE, odkud můžou přesunout kamkoli v rámci obrazovce uživatele. Plovoucí okna vždy nacházejí na integrovaném vývojovém prostředí. Nakonec panely nástrojů lze ukotvit jako dokument windows a zobrazí jako karty v dobře dokumentu. Okna nástrojů, které byly ukotvit jako dokument windows se zobrazí v části pomocí tokenu názvy oken dokumentů.

 ![Červená rámec okna nástrojů značka](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")

 Použití...
kdekoli vytvoříte uživatelské rozhraní, které chcete porovnat okna nástrojů.

 Nepoužívejte...
prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.

 **Ukotvení**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Ukotvení panelu nástrojů](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 089_ToolWindowDocked")

 Pozadí

 `Environment.ToolWindowBackground`

 Ohraničení

 `Environment.ToolWindowBorder`

 **S plovoucí desetinnou čárkou: fokus**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Panel nástrojů, zaměřuje](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 090_ToolWindowFocused")

 Pozadí

 `Environment.ToolWindowBackground`

 Ohraničení

 `Environment.MainWindowActiveDefaultBorder`

 **S plovoucí desetinnou čárkou: bez fokusu**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Panel nástrojů bez fokusu](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 091_ToolWindowUnfocused")

 Pozadí

 `Environment.ToolWindowBackground`

 Ohraničení

 `Environment.MainWindowInactiveBorder`

### <a name="tool-window-title-bar"></a>Záhlaví okna nástroje
 Ohraničení panelu název není true ohraničení, ale tlustá čára v horní části záhlaví. Nemá název tokenu bez fokusu stavu.

 ![Červená značka záhlaví okna nástroje](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")

 Použití...
kdekoli vytvoříte uživatelské rozhraní, které chcete porovnat okna nástrojů.

 Nepoužívejte...
prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.

 **Fokus**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Záhlaví, zaměřuje](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")

 **Cílené záhlaví**

 Pozadí

 `Environment.TitleBarActiveGradientBegin`

 Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

 Popředí (Text)

 `Environment.TitleBarActiveText`

 Ohraničení

 `Environment.TitleBarActiveBorder`

 Nastavte stejnou barvu jako pozadí.

 Úchyt pro přetažení

 `Environment.TitleBarDragHandleActive`

 **Bez fokusu**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Záhlaví bez fokusu](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")

 **Záhlaví bez fokusu**

 Pozadí

 `Environment.TitleBarInactiveGradientBegin`

 Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

 Popředí (Text)

 `Environment.TitleBarInactiveText`

 Ohraničení

 Není k dispozici

 Úchyt pro přetažení

 `Environment.TitleBarDragHandle`

#### <a name="title-bar-buttons"></a>Název tlačítka na panelu
 ![Červená tlačítko nadpisu značka](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")

 Použití...
u tlačítek, která se zobrazí v uživatelském rozhraní, která používá tokeny barvu ze záhlaví okna nástrojů.

 Nepoužívejte...
 -   u tlačítek, která se zobrazí v jiných umístěních.

- v libovolné na pozadí a popředí jinými než která byla specifikována.

  **Default**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Záhlaví tlačítko, zaměřuje](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")

  **Fokus**

  Pozadí

  Není k dispozici

  Popředí (piktogram)

  `Environment.ToolWindowButtonActiveGlyph`

  Ohraničení

  Není k dispozici

  ![Záhlaví tlačítko bez fokusu](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")

  **Bez fokusu**

  Pozadí

  Není k dispozici

  Popředí (piktogram)

  `Environment.ToolWindowButtonInactiveGlyph`

  Ohraničení

  Není k dispozici

  **Při najetí myší**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Tlačítko nadpisu, zaměřuje při najetí myší](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")

  **Fokus**

  Pozadí

  `Environment.ToolWindowButtonHoverActive`

  Popředí (piktogram)

  `Environment.ToolWindowButtonHoverActiveGlyph`

  Ohraničení

  `Environment.ToolWindowButtonHoverActiveBorder`

  ![Záhlaví tlačítka při najetí myší bez fokusu](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")

  **Bez fokusu**

  Pozadí

  `Environment.ToolWindowButtonHoverInactive`

  Popředí (piktogram)

  `Environment.ToolWindowButtonHoverInactiveGlyph`

  Ohraničení

  `Environment.ToolWindowButtonHoverInactiveBorder`

  **Stisknutí**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Záhlaví tlačítko, zaměřuje a stisknutí](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")

  **Fokus**

  Pozadí

  `Environment.ToolWindowButtonDown`

  Popředí (piktogram)

  `Environment.ToolWindowButtonDownActiveGlyph`

  Ohraničení

  `Environment.ToolWindowButtonDownBorder`

  ![Záhlaví tlačítko bez fokusu a při stisknutí](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")

  **Bez fokusu**

  Pozadí

  `Environment.ToolWindowButtonDown`

  Popředí (piktogram)

  `Environment.ToolWindowButtonDownInactiveGlyph`

  Ohraničení

  `Environment.ToolWindowButtonDownBorder`

### <a name="tool-window-tabs"></a>Karty okna nástrojů
 ![Karta okna nástroje červená značka](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 102_ToolWindowTabRedline")

 Použití...
kdekoli vytvoříte uživatelské rozhraní, které chcete porovnat okna nástrojů.

 Nepoužívejte...
prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.

 **Vybraná karta**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Karta okna nástroje, zaměřuje](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")

 **Karta okna vybrané, úzce zaměřený nástroje**

 Pozadí

 `Environment.ToolWindowTabSelectedTab`

 Popředí (Text)

 `Environment.ToolWindowTabSelectedActiveText`

 Ohraničení

 `Environment.ToolWindowTabSelectedBorder`

 Nastavte stejnou barvu jako pozadí.

 Součást

 Prvek

 Název tokenu: Category.color

 ![Karta okna nástroje bez fokusu](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")

 **Karta okna nástroje vybrané, bez fokusu**

 Pozadí

 `Environment.ToolWindowTabSelectedTab`

 Popředí (Text)

 `Environment.ToolWindowTabSelectedText`

 Ohraničení

 `Environment.ToolWindowTabSelectedBorder`

 Nastavte stejnou barvu jako pozadí.

 **Karty na pozadí**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Karta pozadí okna nástroje](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")

 **Karta okna nástroje na pozadí**

 Pozadí

 `Environment.ToolWindowTabGradientBegin`

 Přechod zastaví nastavenou na hodnotu barvy v sadě Visual Studio 2013.

 `Environment.ToolWindowTabGradientEnd`

 Přechod zastaví nastavenou na hodnotu barvy v sadě Visual Studio 2013.

 Popředí (Text)

 `Environment.ToolWindowTabText`

 Ohraničení

 `Environment.ToolWindowTabBorder`

 Součást

 Prvek

 Název tokenu: Category.color

 ![Karta Nástroje pro pozadí okna při najetí myší](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")

 **Karta okna nástroje na pozadí při najetí myší**

 Pozadí

 `Environment.ToolWindowTabMouseOverBackgroundBegin`

 Přechod zastaví nastavenou na hodnotu barvy v sadě Visual Studio 2013.

 `Environment.ToolWindowTabMouseOverBackgroundEnd`

 Přechod zastaví nastavenou na hodnotu barvy v sadě Visual Studio 2013.

 Popředí (Text)

 `Environment.ToolWindowTabMouseOverText`

 Ohraničení

 `Environment.ToolWindowTabMouseOverBorder`

 Nastavte stejnou barvu jako pozadí.

### <a name="auto-hide-tabs"></a>Automatického skrytí karty
 ![Automatické&#45;červená značka skrýt](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 107_AutoHideRedline")

 Použití...
kdekoli vytvoříte uživatelské rozhraní, které můžete chtít, aby nástroj automaticky skrývaná okna karet.

 Nepoužívejte...
prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.

 **Default**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Automatické&#45;Skrýt kartu](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")

 **Výchozí kartu automatického schovávání**

 Pozadí

 `Environment.AutoHideTabBackgroundBegin`

 Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

 Popředí (Text)

 `Environment.AutoHideTabText`

 Ohraničení

 `Environment.AutoHideTabBorder`

 **Při najetí myší**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Automatické&#45;Skrýt kartu při najetí myší](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")

 **Karta automatického schovávání při najetí myší**

 Pozadí

 `Environment.AutoHideTabMouseOverBackgroundBegin`

 Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

 Popředí (Text)

 `Environment.AutoHideTabMouseOverText`

 Ohraničení

 `Environment.AutoHideTabMouseOverBorder`

## <a name="common-shared-controls"></a>Běžné ovládací prvky sdílené
 Při použití standardní panel příkazů sady Visual Studio v vaši funkci, budete mít přístup k ovládacím prvkům upravený prostředí a byste měli znovu template tyto běžné ovládací prvky. Ale pokud budete muset sestavit vlastní příkazového řádku, potřebujete k vytváření vlastních ovládacích prvků. V takovém případě nezapomeňte použít správný token názvy pro každý z následujících ovládacích prvků tak, aby vaše uživatelské rozhraní je konzistentní se zbytkem pracovního sadě Visual Studio.

### <a name="search-box"></a>Vyhledávací pole
 Kdykoli je to možné, použijte běžný ovládací prvek vyhledávání poskytovaných prostředím sady Visual Studio. Vyhledávací pole barvy se nacházejí v kategorii "SearchControl" **ShellColors.pkgdef** soubor, který obsahuje token názvy pro vstupní pole, tlačítko akce, tlačítko rozevíracího seznamu a rozevírací nabídky.

 Vyhledávací pole může být jedna z několika státy, z nichž některé se vzájemně vylučují:

- "Zaměřuje" nebo "bez fokusu" odkazuje na Určuje, jestli je kurzor v textovém poli.

- "Aktivní" nebo "neaktivní" odkazuje na tom, jestli uživatel zadal vyhledávací dotaz v textovém poli.

- "Při najetí myší" znamená, že uživatel má moused prostřednictvím vyhledávacího pole pomocí myši (Tento stav potlačí všechny ostatní stavy).

- "Zakázáno" znamená, že funkce vyhledávání je vypnuté pro aktuální kontext.

  ![Červená pole hledání značka](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 110_SearchBoxRedline")

  Použití...
  Při navrhování vlastní vyhledávací pole.

  Nepoužívejte...
  -   pro všechno, co není vyhledávací pole.

- pro všechno, co, které nechcete, aby vždy tak, aby odpovídaly hledání pole uživatelského rozhraní.

  **Fokus**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vstupní pole hledání, zaměřuje](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")

  **Vstupní pole**

  Pozadí

  `SearchControl.FocusedBackground`

  Popředí (Text)

  `SearchControl.FocusedBackground`

  Ohraničení

  `SearchControl.FocusedBorder`

  Oddělovač

  `SearchControl.FocusedDropDownSeparator`

  ![Tlačítko vyhledat akce, zaměřuje](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")

  **Akce tlačítka**

  Pozadí

  Žádné

  Popředí (piktogram vyhledávání)

  `SearchControl.SearchGlyph`

  Popředí (Zastavit piktogram)

  `SearchControl.StopGlyph`

  Popředí (Vymazat piktogram)

  `SearchControl.ClearGlyph`

  Ohraničení

  Není k dispozici

  ![Hledání rozevírací&#45;tlačítko, zaměřuje](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `SearchControl.FocusedDropDownButton`

  Popředí (piktogram)

  `SearchControl.FocusedDropDownButtonGlyph`

  Ohraničení

  `SearchControl.FocusedDropDownButtonBorder`

  **Bez fokusu**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vstupní pole hledání bez fokusu](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")

  **Aktivní vstupní pole**

  Pozadí

  `SearchControl.SearchActiveBackground`

  Popředí (Text)

  `SearchControl.SearchActiveBackground`

  Ohraničení

  `SearchControl.UnfocusedBorder`

  Oddělovač

  `SearchControl.DropDownSeparator`

  ![Vstupní pole hledání bez fokusu a neaktivní](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303. 114 1_SearchInputFieldUnfocusedInactive")

  **Neaktivní vstupního pole**

  Pozadí

  `SearchControl.Unfocused`

  Popředí (Text)

  `SearchControl.Unfocused`

  Ohraničení

  `SearchControl.UnfocusedBorder`

  Oddělovač

  `SearchControl.DropDownSeparator`

  ![Tlačítko akce hledání bez fokusu](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")

  **Akce tlačítka**

  Pozadí

  Není k dispozici

  Popředí (piktogram vyhledávání)

  `SearchControl.SearchGlyph`

  Popředí (Zastavit piktogram)

  `SearchControl.StopGlyph`

  Popředí (Vymazat piktogram)

  `SearchControl.ClearGlyph`

  Ohraničení

  Není k dispozici

  ![Hledání rozevírací&#45;tlačítko bez fokusu](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `SearchControl.UnfocusedDropDownButton`

  Popředí (piktogram)

  `SearchControl.UnfocusedDropDownButtonGlyph`

  Ohraničení

  `SearchControl.UnfocusedDropDownButtonBorder`

  **Stisknutí**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Stisknutí tlačítka akce hledání](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303. 116 1_SearchActionButtonPressed")

  **Akce tlačítka**

  Pozadí

  `SearchControl.ActionButtonMouseDown`

  Popředí (piktogram)

  `SearchControl.ActionButtonMouseDownGlyph`

  Ohraničení

  `SearchControl.ActionButtonMouseDownBorder`

  ![Hledání rozevírací&#45;dolů stisknutí tlačítka](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303. 116 2_SearchDropdownButtonPressed")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `SearchControl.MouseDownDropDownButton`

  Popředí (piktogram)

  `SearchControl.MouseDownDropDownButtonGlyph`

  Ohraničení

  `SearchControl.MouseDownDropDownButtonBorder`

  **Zvýrazněný (pouze Text)**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Zvýraznění vstupní pole hledání](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")

  **Vstupní pole s textem zvýrazněnou**

  Pozadí

  `SearchControl.Selection`

  Popředí (Text)

  `SearchControl.FocusedBackground`

  Ohraničení

  Žádné

  Oddělovač

  `SearchControl.FocusedDropDownSeparator`

  **Zakázané**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vstupní pole hledání zakázané](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")

  **Vstupní pole**

  Pozadí

  `SearchControl.Disabled`

  Popředí (Text)

  `SearchControl.Disabled`

  Ohraničení

  `SearchControl.DisabledBorder`

  Oddělovač

  `SearchControl.DropDownSeparator`

  ![Tlačítko hledání akce zakázané](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")

  **Akce tlačítka**

  Pozadí

  Žádné

  Popředí (piktogram)

  `SearchControl.ActionButtonDisabledGlyph`

  Ohraničení

  Žádné

  ![Hledání rozevírací&#45;tlačítko zakázané](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  Žádné

  Popředí (piktogram)

  `SearchControl.DisabledDownButtonGlyph`

  Ohraničení

  Žádné

#### <a name="search-drop-down-lists"></a>Hledání rozevírací seznamy
 Vyhledávací pole rozevírací nabídce má potenciál být o něco složitější než ostatní rozevíracích nabídek v sadě Visual Studio. "Navrhované hledání" a "možnosti hledání" oddílů se může objevit samostatně nebo společně v nabídce a každý z nich jsou zobrazeny samostatně. Řádek také odděluje tyto dva oddíly, když jsou uvedeny společně a ohraničení kolem celého rozevírací nabídky.

 ![Hledání rozevírací&#45;dolů červená značka](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 124_SearchDropdownRedline")

 Použití...
 -   Pokud při vytváření vlastních vyhledávacích rozevíracím seznamu.

- správný token názvy správný seznam součástí.

  Nepoužívejte...
  -   pro rozevíracích seznamů, které se zobrazí v jiném kontextu.

- v libovolné na pozadí a popředí jinými než která byla specifikována.

  **Výchozí (ostatní stavy)**

  Prvek

  Název tokenu: Category.color

  Ohraničení

  `SearchControl.PopupBorder`

  Oddělovač

  `SearchControl.PopupSectionHeaderSeparator`

  Stín

  `Environment.DropShadowBackground`

  **Default**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Hledání navrhované](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 125_SearchSuggested")

  **Navrhované hledání**

  Pozadí

  `SearchControl.PopupItemsListBackgroundGradientBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `SearchControl.PopupItemText`

  ![Zaškrtávací políčko Hledat](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")

  **Možnosti hledání (zaškrtávací políčko)**

  ![Možnosti hledání](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")

  **Možnosti hledání (odkaz)**

  Pozadí

  `SearchControl.PopupSectionBackgroundGradientBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (zaškrtávací políčko text)

  `SearchControl.PopupCheckboxText`

  Popředí (text odkazu)

  `SearchControl.PopupButtonText`

  Pozadí záhlaví

  `SearchControl.PopupSectionHeaderGradientBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (text záhlaví)

  `SearchControl.PopupSectionHeaderText`

  **Při najetí myší**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Hledání navrhované při najetí myší](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")

  **Navrhované hledání**

  Pozadí

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (Text)

  `SearchControl.PopupMouseOverItemText`

  Ohraničení

  `SearchControl.PopupControlMouseOverBorder`

  ![Zaškrtávací políčko Hledat při najetí myší](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")

  **Navrhované vyhledávání (zaškrtávací políčko)**

  ![Možnosti při najetí myší hledání](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")

  **Možnosti hledání**

  Pozadí

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (zaškrtávací políčko text)

  `SearchControl.PopupCheckboxMouseDownText`

  Popředí (text odkazu)

  `SearchControl.PopupButtonMouseDownText`

  Ohraničení

  `SearchControl.PopupControlMouseOverBorder`

  **Stisknutí**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Hledání navrhované stisknutí](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")

  **Navrhované vyhledávání (zaškrtávací políčko)**

  ![Možnosti stisknutí hledání](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")

  **Možnosti hledání**

  Pozadí zaškrtávacího políčka

  `SearchControl.PopupControlMouseDownBackgroundGradientBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  `SearchControl.PopupControlMouseDownBackgroundGradientEnd`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (zaškrtávací políčko text)

  `SearchControl.PopupCheckboxMouseDownText`

  Odkaz na pozadí

  `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`

  Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.

  Popředí (text odkazu)

  `SearchControl.PopupButtonMouseDownText`

### <a name="hyperlink"></a>Hypertextový odkaz
 Hypertextový odkaz je jeden ovládací prvek, který nemá dvojici popředí nebo pozadí. Ve všech případech použijte barvu popředí hypertextový odkaz, který se zobrazí správně na tmavě šedou a bílé pozadí. Pokud nepoužijete token barvu ovládacího prvku hypertextový odkaz, zobrazí se výchozí systémové barvy pro "stisknutí", "který blikat červené. To je signál, že ovládací prvek není pomocí tokenu barva správné prostředí.

 ![Červená hypertextový odkaz značka](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 133_HyperlinkRedline")

 Použití...
Když je potřeba vytvořit vlastní hypertextový odkaz.

 Nepoužívejte...
pro všechno, co není hypertextový odkaz.

 **Default**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Hypertextový odkaz výchozí](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 134_Hyperlink")

 Popředí (Text)

 `Environment.PanelHyperlink`

 **Při najetí myší**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Hypertextového odkazu při umístění kurzoru myši](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 135_HyperlinkHover")

 Popředí (Text)

 `Environment.PanelHyperlinkHover`

 **Stisknutí**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Hypertextový odkaz stisknutí](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 136_HyperlinkPressed")

 Popředí (Text)

 `Environment.PanelHyperlinkPressed`

 **Zakázané**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Hypertextový odkaz zakázané](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 137_HyperlinkDisabled")

 Popředí (Text)

 `Environment.PanelHyperlinkDisabled`

### <a name="infobar"></a>Informační panel
 Infobars se používají k poskytují další informace o daném kontextu a vždy se zobrazí v horní části okna dokumentu nebo panelu nástrojů.

 ![Červená informační panel značka](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 138_InfobarRedline")

 Použití...
Při vytváření vlastní infobars.

 Nepoužívejte...
pro prvky uživatelského rozhraní, které nejsou podobný informačního panelu.

 Součást

 Prvek

 Název tokenu: Category.color

 ![Informační panel](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 139_Infobar")

 **Informační panel**

 Pozadí

 `Environment.InfoBackground`

 Popředí (Text)

 `Environment.InfoText`

 Ohraničení

 `Environment.ToolWindowBorder`

### <a name="scroll-bar"></a>Posuvník
 Posuvníky jsou ve stylu prostředím sady Visual Studio a nebude nutné použít motiv. Ale můžete se rozhodnout, že chcete využít barvy použité v posuvníky tak, aby vaše uživatelské rozhraní se vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.

 ![Červená posuvník značka](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 140_ScrollbarRedline")

 Použití...
Pokud při vytváření uživatelského rozhraní, které chcete odpovídá posuvníky sady Visual Studio.

 Nepoužívejte... pro všechno, co nechcete vždy odpovídat posuvník uživatelského rozhraní.

 **Default**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Posuvník](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 141_Scrollbar")

 **Posuvník**

 Posuvník

 `Environment.ScrollBarBackground`

 Popředí (palce)

 `Environment.ScrollBarThumbBackground`

 ![Šipky posuvníku](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 142_ScrollbarArrow")

 **Posouvací šipky**

 Pozadí

 `Environment.ScrollBarArrowBackground`

 Nastavte stejnou barvu jako posuvníku.

 Popředí (piktogram)

 `Environment.ScrollBarArrowGlyph`

 **Při najetí myší**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Posuvník při najetí myší](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 143_ScrollbarHover")

 **Posuvník**

 Posuvník

 `Environment.ScrollBarBackground`

 Popředí (palce)

 `Environment.ScrollBarThumbMouseOverBackground`

 ![Posuvníku šipky při najetí myší](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 144_ScrollbarArrowHover")

 **Posouvací šipky**

 Pozadí

 `Environment.ScrollBarArrowMouseOverBackground`

 Nastavte stejnou barvu jako posuvníku.

 Popředí (piktogram)

 `Environment.ScrollBarArrowGlyphMouseOver`

 **Stisknutí**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Posuvník stisknutí](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 145_ScrollbarPressed")

 **Posuvník**

 Posuvník

 `Environment.ScrollBarBackground`

 Popředí (palce)

 `Environment.ScrollBarThumbPressedBackground`

 ![Posuvníku šipku stisknutí](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")

 **Posouvací šipky**

 Pozadí

 `Environment.ScrollBarArrowPressedBackground`

 Nastavte stejnou barvu jako posuvník.

 Popředí (piktogram)

 `Environment.ScrollBarArrowGlyphPressed`

###  <a name="BKMK_TreeView"></a> Stromové zobrazení
 Několika okny nástrojů, včetně Průzkumníka řešení, Průzkumníka serveru a zobrazení tříd, implementace hierarchické organizační schéma, jejichž barvy se řídí názvy barev v kategorii prvku TreeView. Barvy textu a pozadí mají všechny položky ve stromovém zobrazení. Položky, které mají vnořené podřízené prvky mají také glyfy označující, zda položka rozbalená nebo sbalená.

 ![Červená stromové zobrazení značka](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 147_TreeViewRedline")

 Použití...
kdekoli potřebujete implementovat hierarchické organizační zobrazení.

 Nepoužívejte...
 -   pro všechno, co to není podobné zobrazení stromu.

- v libovolné na pozadí a popředí jinými než která byla specifikována.

  **Default**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Zobrazení stromové struktury](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")

  Pozadí

  `TreeView.Background`

  Popředí (Text)

  `TreeView.Background`

  Popředí (piktogram)

  `TreeView.Glyph`

  Ohraničení

  Žádné

  **Při najetí myší**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Stromové zobrazení při najetí myší](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")

  Pozadí

  `TreeView.Background`

  Popředí (Text)

  `TreeView.Background`

  Popředí (piktogram)

  `TreeView.GlyphMouseOver`

  Ohraničení

  Žádné

  **Přetáhněte**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Stromové zobrazení dragover](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")

  Pozadí

  `TreeView.DragOverItem`

  Popředí (Text)

  `TreeView.DragOverItem`

  Popředí (piktogram)

  `TreeView.DragOverItemGlyph`

  Ohraničení

  Žádné

  **Vybrané**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Stromové zobrazení, zaměřuje](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")

  **Fokus**

  Pozadí

  `TreeView.SelectedItemActive`

  Popředí (Text)

  `TreeView.SelectedItemActive`

  Popředí (piktogram)

  `TreeView.SelectedItemActiveGlyph`

  Ohraničení

  `TreeView.FocusVisualBorder`

  ![Stromové zobrazení bez fokusu](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")

  **Bez fokusu**

  Pozadí

  `TreeView.SelectedItemInactive`

  Popředí (Text)

  `TreeView.SelectedItemInactive`

  Popředí (piktogram)

  `TreeView.SelectedItemInactiveGlyph`

  Ohraničení

  Žádné

  **Podržte ukazatel myši nad vybraný**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Stromové zobrazení, zaměřuje při najetí myší](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")

  **Fokus**

  Pozadí

  `TreeView.SelectedItemActive`

  Popředí (Text)

  `TreeView.SelectedItemActive`

  Popředí (piktogram)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Ohraničení

  None`TreeView.FocusVisualBorder`

  ![Stromové zobrazení bez fokusu při najetí myší](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")

  **Bez fokusu**

  Pozadí

  `TreeView.SelectedItemInactive`

  Popředí (Text)

  `TreeView.SelectedItemInactive`

  Popředí (piktogram)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Ohraničení

  Žádné

### <a name="button-controls"></a>ovládací prvky tlačítek
 ![Ovládací prvek tlačítko červená značka](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 155_ButtonControlRedline")

 Použití...
u tlačítek v dokumentu kontejneru, kterou chcete integrovat s motivů aplikace Visual Studio (světla, tmavý, modrá nebo motiv s vysokým kontrastem systému).

 Nepoužívejte...
u tlačítek, které se zobrazí na vlastní pozadí, který není součástí sady Visual Studio motivu.

 **Default**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Tlačítko](../../extensibility/ux-guidelines/media/0303-156-button.png "0303 156_Button")

 Tlačítko

 `CommonControls.Button`

 Ohraničení tlačítka

 `CommonControls.ButtonBorder`

 **Zakázané**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Tlačítko zakázáno](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 157_ButtonDisabled")

 Tlačítko

 `CommonControls.ButtonDisabled`

 Ohraničení tlačítka

 `CommonControls.ButtonBorderDisabled`

 **Při najetí myší**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Tlačítka při najetí myší](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 158_ButtonHover")

 Tlačítko

 `CommonControls.ButtonHover`

 Ohraničení tlačítka

 `CommonControls.ButtonBorderHover`

 **Stisknutí**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Stisknutí tlačítka](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 159_ButtonPressed")

 Tlačítko

 `CommonControls.ButtonPressed`

 Ohraničení tlačítka

 `CommonControls.ButtonBorderPressed`

 **Fokus**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Tlačítko, zaměřuje](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 160_ButtonFocused")

 Tlačítko

 `CommonControls.ButtonFocused`

 Ohraničení tlačítka

 `CommonControls.ButtonBorderFocused`

### <a name="check-box-controls"></a>Ovládací prvky zaškrtávacích políček
 ![Červená značka zaškrtnutí políčka](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 161_CheckboxRedline")

 Použití...
pro ovládací prvky zaškrtávacích políček dobře obsažených v dokumentu.

 Nepoužívejte...
pro uživatelské rozhraní, který není ovládací prvek zaškrtávací políčko.

 **Default**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Zaškrtněte políčko](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")

 Pozadí

 `CommonControls.CheckBoxBackground`

 Ohraničení

 `CommonControls.CheckBoxBorder`

 Text

 `CommonControls.CheckBoxText`

 Piktogram

 `CommonControls.CheckBoxGlyph`

 **Zakázané**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Zaškrtávací políčko zakázán](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")

 Pozadí

 `CommonControls.CheckBoxBackgroundDisabled`

 Ohraničení

 `CommonControls.CheckBoxBorderDisabled`

 Text

 `CommonControls.CheckBoxTextDisabled`

 Piktogram

 `CommonControls.CheckBoxGlyphDisabled`

 **Při najetí myší**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Zaškrtněte políčko při najetí myší](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")

 Pozadí

 `CommonControls.CheckBoxBackgroundHover`

 Ohraničení

 `CommonControls.CheckBoxBorderHover`

 Text

 `CommonControls.CheckBoxTextHover`

 Piktogram

 `CommonControls.CheckBoxGlyphHover`

 **Stisknutí**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Zaškrtněte políčko stisknutí](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")

 Pozadí

 `CommonControls.CheckBoxBackgroundPressed`

 Ohraničení

 `CommonControls.CheckBoxBorderPressed`

 Text

 `CommonControls.CheckBoxTextPressed`

 Piktogram

 `CommonControls.CheckBoxGlyphPressed`

 **Fokus**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Zaškrtněte políčko, zaměřuje](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")

 Pozadí

 `CommonControls.CheckBoxBackgroundFocused`

 Ohraničení

 `CommonControls.CheckBoxBorderFocused`

 Text

 `CommonControls.CheckBoxTextFocused`

 Piktogram

 `CommonControls.CheckBoxGlyphFocused`

### <a name="drop-boxcombo-box-controls"></a>Přetáhněte pole nebo pole se seznamem
 ![Vyřadit&#45;dolů&#47;červená pole se seznamem značka](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")

 Použití...
rozevírací seznamy a pole se seznamem polí, které jsou součástí dokumentu kontejneru.

 Nepoužívejte...
 -   pro uživatelské rozhraní, která není pole rozevíracího seznamu nebo pole se seznamem.

- pro [rozevíracího seznamu](../../misc/shared-colors.md#BKMK_CommandDropDown) nebo [– pole se seznamem](../../misc/shared-colors.md#BKMK_CommandComboBox) na panelu příkazů.

  **Default**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vyřadit&#45;dolů&#47;– pole se seznamem](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")

  Pozadí

  `CommonControls.ComboBoxBackground`

  Ohraničení

  `CommonControls.ComboBoxBorder`

  Text

  `CommonControls.ComboBoxText`

  Oddělovač

  `CommonControls.ComboBoxSeparator`

  Piktogram

  `CommonControls.ComboBoxGlyph`

  Piktogram na pozadí

  `CommonControls.ComboBoxGlyphBackground`

  **Zakázané**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vyřadit&#45;dolů&#47;– pole se seznamem zakázané](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")

  Pozadí

  `CommonControls.ComboBoxBackgroundDisabled`

  Ohraničení

  `CommonControls.ComboBoxBorderDisabled`

  Text

  `CommonControls.ComboBoxTextDisabled`

  Oddělovač

  `CommonControls.ComboBoxSeparatorDisabled`

  Piktogram

  `CommonControls.ComboBoxGlyphDisabled`

  Piktogram na pozadí

  `CommonControls.ComboBoxGlyphBackgroundDisabled`

  **Při najetí myší**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vyřadit&#45;dolů&#47;– pole se seznamem při najetí myší](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")

  Pozadí

  `CommonControls.ComboBoxBackgroundHover`

  Ohraničení

  `CommonControls.ComboBoxBorderHover`

  Text

  `CommonControls.ComboBoxTextHover`

  Oddělovač

  `CommonControls.ComboBoxSeparatorHover`

  Piktogram

  `CommonControls.ComboBoxGlyphHover`

  Piktogram na pozadí

  `CommonControls.ComboBoxGlyphBackgroundHover`

  **Stisknutí**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vyřadit&#45;dolů&#47;– pole se seznamem stisknutí](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")

  Pozadí

  `CommonControls.ComboBoxBackgroundPressed`

  Ohraničení

  `CommonControls.ComboBoxBorderPressed`

  Text

  `CommonControls.ComboBoxTextPressed`

  Oddělovač

  `CommonControls.ComboBoxSeparatorPressed`

  Piktogram

  `CommonControls.ComboBoxGlyphPressed`

  Piktogram na pozadí

  `CommonControls.ComboBoxGlyphBackgroundPressed`

  **Fokus**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vyřadit&#45;dolů&#47;pole se seznamem, zaměřuje](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")

  Pozadí

  `CommonControls.ComboBoxBackgroundFocused`

  Ohraničení

  `CommonControls.ComboBoxBorderFocused`

  Text

  `CommonControls.ComboBoxTextFocused`

  Oddělovač

  `CommonControls.ComboBoxSeparatorFocused`

  Piktogram

  `CommonControls.ComboBoxGlyphFocused`

  Piktogram na pozadí

  `CommonControls.ComboBoxGlyphBackgroundFocused`

  **Výběr vstupního textu**

  Součást

  Prvek

  Název tokenu: Category.color

  ![Vyřadit&#45;dolů&#47;vstupní text pole se seznamem](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")

  Zvýraznění

  `CommonControls.ComboBoxTextInputSelection`

  **Stisknutí – zobrazení seznamu položek**

  ![Vyřadit&#45;dolů&#47;zobrazení seznamu pole se seznamem](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")

  Pozadí

  `CommonControls.ComboBoxListBackground`

  `CommonControls.ComboBoxListBackgroundHover`

  `CommonControls.ComboBoxListItemBackgroundPressed`

  `CommonControls.ComboBoxListItemBackgroundFocused`

  Ohraničení

  `CommonControls.ComboBoxListBorder`

  `CommonControls.ComboBoxListBorderHover`

  `CommonControls.ComboBoxListBorderPressed`

  `CommonControls.ComboBoxListBorderFocused`

  Text položky

  `CommonControls.ComboBoxListItemText`

  `CommonControls.ComboBoxListItemTextHover`

  `CommonControls.ComboBoxListItemTextPressed`

  `CommonControls.ComboBoxListItemTextFocused`

  Stín pozadí

  `CommonControls.ComboBoxListBackgroundShadow`

### <a name="tabular-data-grid-controls"></a>Ovládací prvky tabulkových dat (grid)
 Ovládací prvky tabulkových dat, označované také jako ovládací prvky mřížky, jsou běžné ovládací prvky pro Visual Studio, která slouží k zobrazení velkého objemu dat ve více sloupcích. Ovládací prvky standardní tabulkových dat najdete na více místech v rámci sady Visual Studio: panel nástrojů Seznam chyb, sestavy IntelliTrace a zobrazení paměti haldy, mimo jiné. Vždy používejte standardní tabulková data ovládací prvky k dispozici. V některých výjimečných případech nemusí mít přístup k ovládacím prvkům standardní tabulková data. V těchto situacích nepoužívejte následující názvy token k zajištění, že vaše uživatelské rozhraní je konzistentní s jinými ovládacími prvky tabulková data v sadě Visual Studio.

 ![Tabulková data &#40;ovládací prvek mřížky&#41; červená značka](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")

 Použití...
pro tabulkové nebo ovládací prvky mřížky.

 Nepoužívejte...
pro uživatelské rozhraní, který není ovládacího prvku tabulky nebo tabulky.

#### <a name="column-headers"></a>Záhlaví sloupců
 Záhlaví sloupců se skládají z na pozadí, ohraničení, text nadpisu a volitelné piktogram obvykle se používá pro mřížku je seřazený podle tohoto sloupce.

 Stav

 Prvek

 Název tokenu: Category.color

 Výchozí

 Pozadí

 `Header.Default`

 Popředí (Text)

 `Environment.CommandBarTextActive`

 Popředí (piktogram)

 `Header.Glyph`

 Ohraničení

 `Header.SeparatorLine`

 Při najetí myší

 Pozadí

 `Header.MouseOver`

 Popředí (Text)

 `Environment.CommandBarTextHover`

 Popředí (piktogram)

 `Header.MouseOverGlyph`

 Ohraničení

 `Header.SeparatorLine`

 Stisknutí

 Pozadí

 `CommonControls.CheckBoxBackgroundPressed`

 Popředí (Text)

 `CommonControls.CheckBoxBorderPressed`

 Popředí (piktogram)

 `CommonControls.CheckBoxTextPressed`

 Ohraničení

 `CommonControls.CheckBoxGlyphPressed`

#### <a name="list-view-items"></a>Položky seznamu
 Položky seznamu se skládají z na pozadí a obsah. Obsah může být text nebo ikonu.

 Stav

 Prvek

 Název tokenu: Category.color

 Výchozí

 Pozadí

 Transparentní

 Popředí (Text)

 `Environment.CommandBarTextActive`

 Ohraničení

 Žádné

 Vybraná (aktivní)

 Pozadí

 `TreeView.SelectedItemActive`

 Popředí (Text)

 `TreeView.SelectedItemActiveText`

 Ohraničení

 Žádné

 Vybraná (neaktivní)

 Pozadí

 `TreeView.SelectedItemInactive`

 Popředí (Text)

 `TreeView.SelectedItemInactiveText`

 Ohraničení

 Žádné

## <a name="manifest-designer"></a>Návrhář manifestu
 Nástroj Manifest Designer je navržená jako způsob, jak bylo snazší upravit soubor manifestu v projektech pro systém Windows 8 a Windows Phone 8. Neplatí žádné sdílené architektuře k dispozici pro použití, může být vhodné pro tak, aby odpovídala návrhu rozložení a barvy orientace/navigačních karet a celkovou strukturu. Další informace o rozložení podrobnosti najdete v tématu [rozložení pro sadu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

 ![Manifest Designer červená značka](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 175_ManifestDesignerRedline")

 Použití...
 -   pro profesionální návrháře využívající, které jsou podobné pro Nástroj Manifest Designer.

- místo použití běžných ovládacích prvků kartě v horní části editoru v rámci dokumentu kontejneru.

  Nepoužívejte...
  -   Pokud máte víc než šest karet.

- pro všechny uživatelské rozhraní, která není strukturované jako nástroj Manifest Designer.

  Stav

  Součást

  Prvek

  Název tokenu: Category.color

  Výchozí (vybrané)

  Tabulátor

  Pozadí

  `ManifestDesigner.TabActive`

  Ohraničení

  Žádné

  Podokno s popisem

  Pozadí

  `ManifestDesigner.DescriptionPane`

  Stránka obsahu

  Pozadí

  `ManifestDesigner.Background`

  Dialogové okno text pomocné rutiny

  `ManifestDesigner.WatermarkText`

  Tento název tokenu se neshoduje s jeho funkci.

  Non vybraná

  Tabulátor

  Pozadí

  `ManifestDesigner.Tab.Inactive`

  Při najetí myší

  Tabulátor

  Pozadí

  `ManifestDesigner.Tab.Mouseover`

## <a name="tagging"></a>Označování
 Visual Studio podporuje označování, které umožňuje uživateli deklarovat prohledávatelná klíčová slova pro účely sledování. Například projektových manažerů a vývojářů může používat Team Foundation Server (TFS) k označení pracovních položek. Následující tabulky poskytují názvy barev pro vlastní značku i "Zavřít ikonu" šifra, která se zobrazí při najetí myší a vybraných států.

 ![Označování červená značka](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 176_TaggingRedline")

 Použití...
pro uživatelské rozhraní, který podporuje označování.

 Nepoužívejte...
u ostatních typů uživatelského rozhraní.

### <a name="tag"></a>Značka
 Součást

 Prvek

 Název tokenu: Category.color

 ![Značka](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303 177_Tag")

 **Default**

 Pozadí

 `Tag.Background`

 Popředí (Text)

 `Tag.Background`

 ![Označit při najetí myší](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 178_TagHover")

 **Při najetí myší**

 Pozadí

 `Tag.HoverBackground`

 Popředí (Text)

 `Tag.HoverBackgroundText`

 ![Značka stisknutí](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 179_TagPressed")

 **Stisknutí**

 Pozadí

 `Tag.PressedBackground`

 Popředí (Text)

 `Tag.PressedBackgroundText`

 ![Vybrané značky](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 180_TagSelected")

 **Vybrané**

 Pozadí

 `Tag.SelectedBackground`

 Popředí (Text)

 `Tag.SelectedBackgroundText`

### <a name="glyph-close-icon"></a>Piktogram (ikonu pro zavření)
 **Default**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Značka &#40;piktogram&#41;](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 181_TagGlyph")

 **Výchozí (výchozí značky)**

 Pozadí

 Není k dispozici

 Popředí (piktogram)

 `Tag.TagHoverGlyph`

 **Při najetí myší**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Značka &#40;piktogram&#41; při najetí myší](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")

 **Podržte ukazatel myši (výchozí značky)**

 Pozadí

 `Tag.TagHoverGlyphHoverBackground`

 Popředí (piktogram)

 `Tag.TagHoverGlyphHover`

 Ohraničení

 `Tag.TagHoverGlyphHoverBorder`

 **Stisknutí**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Značka &#40;piktogram&#41; stisknutí](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 183_TagGlyphPressed")

 **Stisknutí (výchozí značky)**

 Pozadí

 `Tag.TagHoverGlyphPressedBackground`

 Popředí (piktogram)

 `Tag.TagHoverGlyphPressed`

 Ohraničení

 `Tag.TagHoverGlyphPressedBorder`

 **Výchozí vybraná/piktogramu značky**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Vybrané značky](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 184_TagSelected")

 **Výchozí (značky)**

 Pozadí

 Není k dispozici

 Popředí (piktogram)

 `Tag.TagSelectedGlyph`

 **Při najetí myší vybraný/piktogramu značky**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Značky, které vybrali při najetí myší](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")

 **Podržte ukazatel myši (značky)**

 Pozadí

 `Tag.TagSelectedGlyphHoverBackground`

 Popředí (piktogram)

 `Tag.TagSelectedGlyphHover`

 Ohraničení

 `Tag.TagSelectedGlyphHoverBorder`

 **Vybrané/piktogram stisknutí**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Vybrané značky stisknutí](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")

 **Při stisknutí (značky)**

 Pozadí

 `Tag.TagSelectedGlyphPressedBackground`

 Foreground(Glyph)

 `Tag.TagSelectedGlyphPressed`

 Ohraničení

 `Tag.TagSelectedGlyphPressedBorder`

## <a name="shell"></a>Prostředí

### <a name="background"></a>Pozadí
 Na pozadí prostředí se skládá ze dvou vrstev. Spodní vrstva je plnou barvu, která zahrnuje celou integrovaného vývojového prostředí. Horní vrstvě vejde v rámci příkazu polici a mezi kanálů automatického skrytí okna nástroje na levých a pravých okrajů integrovaného vývojového prostředí. Od verze Visual Studio 2013 pozadí vrstvy horní a dolní nastavené na stejnou barvu v motivy tmavý a světlý motiv.

 ![Červená značka prostředí pozadí](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 187_ShellBackgroundRedline")

 Použití...
pro míst, na které můžete chtít, aby na pozadí prostředí sady Visual Studio.

 Nepoužívejte...
 -   jako výplň místa, které nejsou na pozadí plochy.

- na pozadí, na kterém chcete umístit prvky popředí.

  Součást

  Prvek

  Název tokenu: Category.color

  Dolní vrstvy

  Pozadí

  `Environment.EnvironmentBackground`

  Součást

  Prvek

  Název tokenu: Category.color

  Vrstvu na nejvyšší úrovni

  Pozadí

  *Přechod zastaví nastavenou na hodnotu barvy v aplikaci Visual Studio 2013 světla a tmavé motivy.*

  `Environment.EnvironmentBackgroundGradientBegin`

  `Environment.EnvironmentBackgroundGradientEnd`

  `Environment.EnvironmentBackgroundGradientMiddle1`

  `Environment.EnvironmentBackgroundGradientMiddle2`

### <a name="command-shelf"></a>Příkaz police
 Dvě sady token názvů, které se používají pro pozadí příkaz police: nastavit jeden kde je umístěn řádku nabídek a jeden pro kde panely příkazů nacházejí. Pruhový graf konkrétní příkaz má svůj vlastní pozadí hodnot barev, které jsou popsány podrobněji v oddílu "panel příkazů". Řádek nabídek panelu a příkaz text je popsána v části panel nabídek a příkazů.

 ![Příkaz police červená značka](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 188_CommandShelfRedline")

 Použití...
 -   pro oblasti, kam umístit nabídek a panelů nástrojů.

- na pozadí a správné /? popředí kombinaci název tokenu.

  Nepoužívejte...
  pro oblasti, které nejsou podobný police příkazu.

  Součást

  Prvek

  Název tokenu: Category.color

  Panel nabídek

  Pozadí

  *Přechod zastaví nastavenou na hodnotu barvy v aplikaci Visual Studio 2013 světla a tmavé motivy.*

  `Environment.CommandShelfHighlightGradientBegin`

  `Environment.CommandShelfHighlightGradientMiddle`

  `Environment.CommandShelfHighlightGradientEnd`

  Panel příkazů

  Pozadí

  *Přechod zastaví nastavenou na hodnotu barvy v aplikaci Visual Studio 2013 světla a tmavé motivy.*

  `Environment.CommandShelfBackgroundGradientBegin`

  `Environment.CommandShelfBackgroundGradientMiddle`

  `Environment.CommandShelfBackgroundGradientEnd`

## <a name="toolbox"></a>Sada nástrojů
 Panelu nástrojů je jedním z běžných okna nástrojů, které se nejčastěji používá v sadě Visual Studio. Je v podstatě ovládací prvek stromu se speciální motivu a styly použijí.

 ![Červená nástrojů značka](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 189_ToolboxRedline")

 Použití...
Při navrhování panelu nástrojů, kterou chcete vždy bylo v souladu s prostředí nástrojů.

 Nepoužívejte...
pro cokoli, co není podobný panelu nástrojů uživatelského rozhraní nebo pokud si nejste jistí, jestli vaše uživatelské rozhraní bude mít problémy se změna barvy panelu prostředí.

 **Default**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Panel nástrojů nadřazený uzel](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")

 **Nadřazený uzel**

 ![Panel nástrojů podřízený uzel](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")

 **Podřízený uzel**

 Pozadí

 `Environment.ToolboxContent`

 Záhlaví

 `Environment.ToolWindowBackground`

 Jednotlivé položky nebo celé okno, pokud žádné dostupné ovládací prvky

 Ohraničení

 Žádné

 Popředí (piktogram)

 `Environment.ToolboxContent`

 Popředí (Text)

 `Environment.ToolboxContent`

 **Při najetí myší**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Podřízený uzel panelu nástrojů při najetí myší](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")

 **Panel nástrojů při přechodu myší na podřízený uzel**

 Pozadí

 `Environment.ToolboxContentMouseOver`

 Pouze jednotlivé položky

 Ohraničení

 Žádné

 Popředí (Text)

 `Environment.ToolboxContentMouseOver`

 Pouze jednotlivé položky

 **Vybrané**

 Součást

 Prvek

 Název tokenu: Category.color

 ![Panel nástrojů nadřazeného uzlu, zaměřuje](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")

 **Cílené nadřazený uzel**

 ![Panel nástrojů podřízený uzel, zaměřuje](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")

 **Cílené podřízený uzel**

 Pozadí

 `TreeView.SelectedItemActive`

 Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie

 Ohraničení

 `TreeView.FocusVisualBorder`

 Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie

 Popředí (piktogram)

 `TreeView.SelectedItemActive`

 Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie

 Popředí (Text)

 `TreeView.SelectedItemActive`

 Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie

 ![Panel nástrojů nadřazený uzel bez fokusu](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")

 **Bez fokusu nadřazený uzel**

 ![Panel nástrojů podřízený uzel bez fokusu](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")

 **Bez fokusu podřízený uzel**

 Pozadí

 `TreeView.SelectedItemInactive`

 Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie

 Ohraničení

 Žádné

 Popředí (piktogram)

 `TreeView.SelectedItemInactive`

 Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie

 Popředí (Text)

 `TreeView.SelectedItemInactive`

 Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie
