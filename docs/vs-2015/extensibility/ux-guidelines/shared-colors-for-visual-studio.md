---
title: Sdílené barvy
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 87520a7e17d194d7f5cc28665a6f23466bface65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154542"
---
# <a name="shared-colors-for-visual-studio"></a>Sdílené barvy pro Visual Studio

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pokud navrhujete uživatelské rozhraní, které používá společné prvky prostředí sady Visual Studio, nebo chcete, aby element rozhraní byl konzistentní s podobnými funkcemi, použijte existující názvy tokenů v definičních souborech balíčku k výběru a přiřazení barev. Tím se zajistí, že vaše uživatelské rozhraní zůstane v souladu s celkovým prostředím sady Visual Studio a že se automaticky aktualizuje při přidání nebo aktualizaci motivů.

Tento článek popisuje běžné prvky uživatelského rozhraní a názvy tokenů, které používají, na které můžete odkazovat při sestavování podobného uživatelského rozhraní. Konkrétní informace o tom, jak získat přístup k těmto barevným tokenům, najdete v tématu [Služba VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Ujistěte se, že používáte názvy tokenů správně:

- **Použijte názvy tokenů založené na funkci, nikoli na samotné barvě.** Společné sdílené barvy jsou spojeny s konkrétními prvky rozhraní a jsou určeny pouze pro použití pro stejné nebo podobné funkce. Nepoužívejte například barvu stisknutého pole se seznamem pro animaci průběhu, protože jste chtěli barvu. Funkce pole se seznamem a animace se liší a pokud se barva přidružená k poli se seznamem změní, nemusí již být vhodnou barvou pro váš element animace. Konzistentní použití barev pomáhá orientovat uživatele a zabránit nejasnostem.

- **Používejte barvy pozadí a textu ve správné kombinaci.** Barvy pozadí, které se mají použít s textem, budou mít přidruženou barvu textu. Nepoužívejte barvy textu kromě těch, které jsou určeny pro dané pozadí. Pokud není k dispozici žádná barva textu, nepoužívejte tuto barvu pozadí pro všechny plochy, na kterých očekáváte zobrazení textu. Jiné kombinace barvy textu a pozadí můžou mít za následek nečitelný rozhraní.

- **Používejte barvy ovládacích prvků, které jsou vhodné pro jejich umístění.** V některých stavech některé ovládací prvky sady Visual Studio nemají samostatné barvy ohraničení a pozadí. Místo toho tyto barvy vyberou z povrchů za ně. Ujistěte se, že používáte vždy názvy tokenů, které jsou vhodné pro umístění, kam umístíte ovládací prvek.

> [!IMPORTANT]
> Nepoužívejte tokeny nacházející se v kategoriích "Úvodní stránka" nebo "jablečná".

## <a name="command-structures"></a>Struktury příkazů

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Nabídek

Nabídky se můžou vyskytovat na několika místech v sadě Visual Studio: hlavní panel nabídek, vložený v oknech dokument nebo nástroj, nebo klikněte pravým tlačítkem na různá místa v rámci IDE. Implementace nabídek přidružených k ostatním prvkům uživatelského rozhraní jsou popsány v části příslušného prvku. Vždy byste měli použít standardní implementaci nabídky poskytovanou prostředím Visual Studio. Nicméně v některých vzácných instancích byste neměli mít přístup ke standardním nabídkám sady Visual Studio. V těchto situacích použijte následující názvy tokenů, abyste zajistili, že vaše uživatelské rozhraní je konzistentní s jinými nabídkami v aplikaci Visual Studio.

![Nabídky Redline](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 – 000_MenuRedline")

Použít...
- kdykoli potřebujete vytvořit vlastní nabídku.

- Pokud máte novou součást uživatelského rozhraní, která se má shodovat s nabídkami sady Visual Studio.

Nepoužívat...
samostatná barva pozadí. Vždy používat kombinaci pozadí/popředí podle zadání.

#### <a name="menu-title"></a>Název nabídky

Názvy nabídek se skládají z pozadí, ohraničení a textu nadpisu a také z volitelné glyfy, většinou když se nabídka najde na panelu příkazů.

![Název nabídky Redline](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 – 001_MenuTitleRedline")

Použít...
vždy, když vytváříte vlastní název nabídky.

Nepoužívat...
- pro cokoli, co nechcete vždy shodovat s názvem nabídky.

- v jakékoliv kombinaci pozadí/popředí kromě zadaného.

  **Výchozí**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Výchozí název nabídky](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 – 002_MenuTitleDefault")

  **Název nabídky**

  Pozadí

  Žádné

  Popředí (text)

  `Environment.CommandBarTextActive`

  ![Název nabídky s výchozím glyfem](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 – 003_MenuTitleWithGlyphDefault")

  **Název nabídky s glyfem**

  Popředí (glyf)

  `Environment.CommandBarMenuGlyph`

  Ohraničení

  Žádné

  **Hover**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Název nabídky při najetí myší](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 – 004_MenuTitleHover")

  **Název nabídky**

  Pozadí

  `Environment.CommandBarMouseOverBackgroundBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `Environment.CommandBarTextHover`

  ![Název nabídky s glyfem při najetí myší](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 – 005_MenuTitleWithGlyphHover")

  **Název nabídky s glyfem**

  Popředí (glyf)

  `Environment.CommandBarMenuMouseOverGlyph`

  Ohraničení

  `Environment.CommandBarBorder`

  **Pressed**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Stisknutí názvu nabídky](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 – 006_MenuTitlePressed")

  **Název nabídky**

  Pozadí

  `Environment.CommandBarMenuBackgroundGradientBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `Environment.CommandBarTextActive`

  ![Název nabídky se stisknutým glyfem](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 – 007_MenuTitleWithGlyphPressed")

  **Název nabídky s glyfem**

  Popředí (glyf)

  `Environment.CommandBarMenuMouseDownGlyph`

  Ohraničení

  `Environment.CommandBarMenuBorder`

  Pouze levou, horní a pravou stranu.

  **Zakázáno**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Název nabídky se zakázaným glyfem](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 – 008_MenuTitleWithGlyphDisabled")

  **Název nabídky s glyfem**

  Pozadí

  Žádné

  Popředí (text)

  `Environment.CommandBarTextInactive`

  Popředí (glyf)

  `Environment.CommandBarTextInactive`

  Ohraničení

  Žádné

#### <a name="menu"></a>Nabídka

Jednotlivá položka nabídky se skládá z textu nabídky a volitelné ikony, zaškrtávacího políčka nebo piktogramu podnabídky. Změní barvu pozadí a textu při najetí myší. Tento token barvy je dvojice pozadí/popředí.

![Položky nabídky Redline](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 – 009_MenuItemRedline")

Použít...
pro libovolný rozevírací seznam, který se spouští z panelu nabídek nebo panelu příkazů.

Nepoužívat...
- pro libovolný rozevírací seznam, který se vyskytuje v jiném kontextu.

- v jakékoliv kombinaci pozadí/popředí kromě zadaného.

  **Výchozí**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Výchozí nabídka](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 – 010_MenuDefault")

  **Nabídka**

  Pozadí

  `Environment.CommandBarMenuBackgroundGradientBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `Environment.CommandBarTextActive`

  Popředí (piktogram podnabídky)

  `Environment.CommandBarMenuSubmenuGlyph`

  Ohraničení

  `Environment.CommandBarMenuBorder`

  Pozadí kanálu ikon

  `Environment.CommandBarMenuIconBackground`

  Oddělovač

  `Environment.CommandBarMenuSeparator`

  Vytváření

  `Environment.DropShadowBackground`

  ![Zaškrtnutá nabídka](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 – 011_MenuChecked")

  **Kontrolovaný**

  Značka zaškrtnutí

  `Environment.CommandBarCheckBox`

  Pozadí zaškrtnutí

  `Environment.CommandBarSelectedIcon`

  ![Vybraná nabídka](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 – 012_MenuSelected")

  **Vybráno**

  Pozadí ikony

  `Environment.CommandBarSelected`

  Ohraničení ikony

  `Environment.CommandBarSelectedBorder`

  **Hover**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Najeďte do nabídky](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 – 013_MenuHover")

  **Položka nabídky**

  Pozadí

  `Environment.CommandBarMenuItemMouseOver`

  Popředí (text)

  `Environment.CommandBarMenuItemMouseOver`

  Popředí (piktogram podnabídky)

  `Environment.CommandBarMenuMouseOverSubmenuGlyph`

  ![Kontrola najetí myší v nabídce](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 – 014_MenuHoverChecked")

  **Kontrolovaný**

  Značka zaškrtnutí

  `Environment.CommandBarCheckBoxMouseOver`

  Pozadí zaškrtnutí

  `Environment.CommandBarHoverOverSelectedIcon`

  ![Výběr myši v nabídce](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 – 015_MenuHoverSelected")

  **Vybráno**

  Pozadí ikony

  `Environment.CommandBarHoverOverSelected`

  Ohraničení ikony

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Zakázáno**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Nabídka zakázaná](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 – 016_MenuDisabled")

  Položka nabídky

  Popředí (text)

  `Environment.CommandBarTextInactive`

  Popředí (piktogram podnabídky)

  `Environment.CommandBarMenuSubmenuGlyph`

  ![Zaškrtnutá nabídka zakázaná](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 – 017_MenuDisabledChecked")

  Zaškrtnuto

  Značka zaškrtnutí

  `Environment.CommandBarCheckBoxDisabled`

  Pozadí zaškrtnutí

  `Environment.CommandBarSelectedIconDisabled`

### <a name="command-bar"></a>Panel příkazů

Panel příkazů se může zobrazit na více místech v integrovaném vývojovém prostředí sady Visual Studio, zejména v poli pro pole a v oknech nástrojů nebo dokumentu.

Obecně platí, že vždy použijte standardní implementaci panelu příkazů poskytované prostředím Visual Studio. Použití standardního mechanismu zajistí, že se všechny podrobnosti vizuálů zobrazí správně a že interaktivní prvky se budou chovat konzistentně s dalšími ovládacími prvky panelu příkazů sady Visual Studio. Pokud je ale potřeba vytvořit vlastní panel příkazů, ujistěte se, že je správně nakonfigurujete pomocí následujících názvů tokenů.

![Redline panelu příkazů](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 – 018_CommandBarRedline")

![Redline tlačítka přetečení](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 – 019_OverflowButtonRedline")

Použít...
v místech, kde potřebujete vložený panel příkazů, ale nemůžete použít standardní implementaci panelu příkazů sady Visual Studio.

Nepoužívat...
- pro prvky uživatelského rozhraní, které nejsou podobné panelu příkazů.

- pro součásti panelu příkazů kromě těch, pro které jsou zadány názvy tokenů.

#### <a name="command-bar-group"></a>Skupina panelů příkazů

Skupina panelů příkazů se skládá ze související sady ovládacích prvků panelu příkazů a může obsahovat libovolný počet tlačítek, rozdělená tlačítka, rozevírací nabídky, pole se seznamem nebo nabídky. Barvy pro tyto ovládací prvky jsou regulovány pomocí oddělených názvů tokenů a jsou popsány individuálně jinde v této příručce. Oddělovací čára se používá k rozdělení skupiny pruhů příkazů do souvisejících podskupin.

![Redline skupiny panelů příkazů](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 – 020_CommandBarGroupRedline")

Použít...
v místech, kde potřebujete vložený panel příkazů, ale nemůžete použít standardní implementaci panelu příkazů sady Visual Studio.

Nepoužívat...
- pro prvky uživatelského rozhraní, které nejsou podobné panelu příkazů.

- pro součásti panelu příkazů kromě těch, pro které jsou zadány názvy tokenů.

  **Výchozí** (žádné jiné stavy)

  Prvek

  Název tokenu: category. Color

  Pozadí

  `Environment.CommandBarGradientBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Ohraničení

  `Environment.CommandBarToolBarBorder`

  Přetáhněte popisovač

  `Environment.CommandBarDragHandle`

  Oddělovač

  `Environment.CommandBarToolBarSeparator`

  `Environment.CommandBarToolBarSeparatorHighlight`

#### <a name="command-icons"></a>Ikony příkazů

![Ikona příkazu Redline](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 – 021_CommandIconRedline1")

![Ikona příkazu Redline](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 – 022_CommandIconRedline2")

Použít...
pro všechna tlačítka, která budou umístěna na panelu příkazů.

Nepoužívat...
- pro ovládací prvky, které mají své vlastní názvy tokenů.

- v jakékoliv kombinaci pozadí/popředí kromě zadaného.

  **Výchozí**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Výchozí ikona příkazu](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 – 023_CommandIconDefault")

  **Výchozí**

  Pozadí

  Není k dispozici (dědí z pozadí panelu příkazů)

  Popředí (text)

  `Environment.CommandBarTextActive`

  Ohraničení

  –

  ![Vybraná ikona příkazu – výchozí](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 – 024_CommandIconDefaultSelected")

  **Vybráno**

  Pozadí

  `Environment.CommandBarSelected`

  Popředí (text)

  `Environment.CommandBarTextSelected`

  Ohraničení

  `Environment.CommandBarSelectedBorder`

  **Fokus myši a klávesnice**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Ikona příkazu najeďte myší](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 – 025_CommandIconHover")

  **Při najetí myší na standard**

  Pozadí

  `Environment.CommandBarMouseOverBackgroundBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `Environment.CommandBarTextHover`

  Ohraničení

  `Environment.CommandBarBorder`

  ![Ikona příkazu po výběru](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 – 026_CommandIconHoverSelected")

  **Vybráno při najetí myší**

  Pozadí

  `Environment.CommandBarHoverOverSelected`

  Popředí (text)

  `Environment.CommandBarTextHoverOverSelected`

  Ohraničení

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Pressed**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Byla stisknuta ikona příkazu.](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 – 027_CommandIconPressed")

  **Ikona stisknutého příkazu**

  Pozadí

  `Environment.CommandBarMouseDownBackgroundBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `Environment.CommandBarTextMouseDown`

  Ohraničení

  `Environment.CommandBarBorder`

  **Zakázáno**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Ikona příkazu je zakázaná.](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 – 028_CommandIconDisabled")

  **Ikona zakázaného příkazu**

  Pozadí

  Není k dispozici (dědí z pozadí panelu příkazů)

  Popředí (text)

  `Environment.CommandBarTextInactive`

  Ohraničení

  –

#### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a> Pole se seznamem

> [!IMPORTANT]
> Pole se seznamem jsou podobná rozevíracím seznamům, ale obsahují upravitelnou textovou oblast. Pokud rozevírací seznam neobsahuje upravitelnou textovou oblast, použijte v [rozevíracím](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)seznamu tokeny barev.

![Redline pole se seznamem](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 – 029_ComboBoxRedline")

Použít...
- Při sestavování vlastních polí se seznamem.

- Při vytváření ovládacího prvku panelu příkazů, který je podobný poli se seznamem.

  Nepoužívat...
  - cokoli, co nechcete, aby se vždy shodovalo s uživatelským rozhraním panelu příkazů.

- Když máte přístup k poli se seznamem se stylem.

  **Výchozí**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Vstupní pole pole se seznamem](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 – 030_ComboBoxInputField")

  **Vstupní pole**

  Pozadí

  `Environment.ComboBoxBackground`

  Popředí (text)

  `Environment.ComboBoxText`

  Ohraničení

  `Environment.ComboBoxBorder`

  Oddělovač

  Bez oddělovače

  ![Rozevírací tlačítko&#45;rozevíracího seznamu pole se seznamem](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 – 031_ComboBoxDropdownButton")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  Není k dispozici (dědí)

  Popředí (glyf)

  `Environment.ComboBoxGlyph`

  ![Pole se seznamem&#47;rozevírací seznam&#45;](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 – 032_ComboBoxDropdownList")

  **Rozevírací seznam**

  Pozadí

  `Environment.ComboBoxPopupBackgroundBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `Environment.ComboBoxItemText`

  Ohraničení

  `Environment.ComboBoxPopupBorder`

  **Hover**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Vstupní pole pole se seznamem při najetí myší](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 – 033_ComboBoxInputFieldHover")

  **Vstupní pole**

  Pozadí

  `Environment.ComboBoxMouseOverBackgroundBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `Environment.ComboBoxMouseOverText`

  Ohraničení

  `Environment.ComboBoxMouseOverBorder`

  Oddělovač

  `Environment.ComboBoxMouseOverSeparator`

  ![Pole se seznamem&#47;&#45;rozevírací tlačítko myši při umístění ukazatele dolů](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 – 034_ComboBoxDropdownButtonHover")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `Environment.ComboBoxButtonMouseOverBackground`

  Popředí (glyf)

  `Environment.ComboBoxMouseOverGlyph`

  ![Pole se seznamem&#47;při umístění ukazatele myši na seznam&#45;rozevíracího seznamu](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 – 035_ComboBoxDropdownListHover")

  **Rozevírací seznam**

  Background (položka nabídky)

  `Environment.ComboBoxItemMouseOverBackground`

  Popředí (text)

  `Environment.ComboBoxItemMouseOverText`

  Border (položka nabídky)

  `Environment.ComboBoxItemMouseOverBorder`

  **Focused**

  Součást

  Prvek

  Název tokenu: Color. Category

  ![Zaměření na vstupní pole pole se seznamem](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 – 036_ComboBoxInputFieldFocused")

  **Vstupní pole**

  Pozadí

  `Environment.ComboBoxFocusedBackground`

  Popředí (text)

  `Environment.ComboBoxFocusedText`

  Ohraničení

  `Environment.ComboBoxFocusedBorder`

  Oddělovač

  `Environment.ComboBoxFocusedButtonSeparator`

  ![Pole se seznamem&#47;rozevírací tlačítko rozevírací&#45;dolů](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 – 037_ComboBoxDropdownButtonFocused")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `Environment.ComboBoxFocusedButtonBackground`

  Popředí (glyf)

  `Environment.ComboBoxFocusedGlyph`

  **Pressed**

  Součást

  Prvek

  Název tokenu: Color. Category

  ![Stisknuté vstupní pole pole se seznamem](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 – 038_ComboBoxInputFieldPressed")

  **Vstupní pole**

  Pozadí

  `Environment.ComboBoxMouseDownBackground`

  Popředí (text)

  `Environment.ComboBoxMouseDownText`

  Ohraničení

  `Environment.ComboBoxMouseDownBorder`

  Oddělovač

  `Environment.ComboBoxMouseDownSeparator`

  ![Stisknuté tlačítko rozevíracího seznamu&#47;pole se seznamem&#45;](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 – 039_ComboBoxDropdownButtonPressed")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `Environment.ComboBoxButtonMouseDownBackground`

  Popředí (glyf)

  `Environment.ComboBoxMouseDownGlyph`

  **Zakázáno**

  ![Vstupní pole pole se seznamem je zakázané.](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 – 041_ComboBoxInputFieldDisabled")

  **Vstupní pole**

  Pozadí

  `Environment.ComboBoxDisabledBackground`

  Popředí (text)

  `Environment.ComboBoxDisabledText`

  Ohraničení

  `Environment.ComboBoxDisabledBorder`

  Oddělovač

  Bez oddělovače

  ![Pole se seznamem&#47;vypnuté&#45;rozevírací tlačítko dolů](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 – 040_ComboBoxDropdownButtonDisabled")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  Žádné

  Popředí (glyf)

  `Environment.ComboBoxDisabledGlyph`

#### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a> Rozevírací seznam

> [!IMPORTANT]
> Rozevírací seznamy jsou podobné polím se seznamem, ale nemají upravovatelné textové oblasti. Pokud rozevírací seznam obsahuje upravitelnou textovou oblast, použijte tokeny barev nalezené v [poli se seznamem](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Odpustit&#45;Redline dolů](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 – 042_DropdownRedline")

Použít...
Při vytváření vlastních ovládacích prvků rozevíracího seznamu.

Nepoužívat...
- pro cokoli, co není podobné jako v rozevíracím seznamu.

- pro pole se seznamem nebo rozdělená tlačítka.

  **Výchozí**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Odpustit&#45;pole výběru](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 – 043_DropdownSelectionField")

  **Pole výběru**

  Pozadí

  `Environment.DropDownBackground`

  Popředí (text)

  `DropDownText`

  Ohraničení

  `DropDownBorder`

  Oddělovač

  Bez oddělovače

  ![Tlačítko&#45;rozevíracího seznamu](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 – 044_DropdownButton")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  Žádné

  Popředí (glyf)

  `Environment.DropDownGlyph`

  ![Rozevírací seznam&#45;](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 – 045_DropdownList")

  **Rozevírací seznam**

  Pozadí

  `Environment.DropDownPopupBackgroundBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `Environment.ComboBoxItemText`

  Ohraničení

  `Environment.DropDownPopupBorder`

  Vytváření

  `Environment.DropShadowBackground`

  **Hover**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Při najetí myší umístit pole výběru&#45;dolů](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 – 046_DropdownSelectionFieldHover")

  **Pole výběru**

  Pozadí

  `Environment.DropDownMouseOverBackgroundBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `Environment.DropDownMouseOverText`

  Ohraničení

  `Environment.DropDownMouseOverBorder`

  Oddělovač

  `Environment.DropDownButtonMouseOverSeparator`

  ![Při najetí myší umístit tlačítko&#45;dolů](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 – 047_DropdownButtonHover")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `Environment.DropDownButtonMouseOverBackground`

  Popředí (glyf)

  `Environment.DropDownMouseOverGlyph`

  ![Při najetí myší&#45;rozevírací seznam](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 – 048_DropdownListHover")

  **Rozevírací seznam**

  Background (položka nabídky)

  `Environment.ComboBoxItemMouseOverBackground`

  Popředí (text)

  `Environment.ComboBoxItemMouseOverText`

  Border (položka nabídky)

  `Environment.ComboBoxItemMouseOverBorder`

  **Pressed**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Stisknutí pole výběru&#45;dolů](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 – 049_DropdownSelectionFieldPressed")

  **Pole výběru**

  Pozadí

  `Environment.DropDownMouseDownBackground`

  Popředí (text)

  `Environment.DropDownMouseDownText`

  Ohraničení

  `Environment.DropDownMouseDownBorder`

  Oddělovač

  `Environment.DropDownButtonMouseDownSeparator`

  ![Stisknutí tlačítka pro odtažení&#45;dolů](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 – 050_DropdownButtonPressed")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `Environment.DropDownButtonMouseDownBackground`

  Popředí (glyf)

  `Environment.DropDownMouseDownGlyph`

  **Zakázáno**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Zakázané pole výběru&#45;dolů](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 – 051_DropdownSelectionFieldDisabled")

  Pozadí

  `Environment.DropDownDisabledBackground`

  Popředí (text)

  `Environment.DropDownDisabledText`

  Ohraničení

  `Environment.DropDownDisabledBorder`

  Oddělovač

  Bez oddělovače

  ![Tlačítko odtažení&#45;vypnuto](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 – 052_DropdownButtonDisabled")

  Pozadí

  –

  Popředí (glyf)

  `Environment.DropDownDisabledGlyph`

#### <a name="split-button"></a>Tlačítko rozdělení

Rozdělená tlačítka sdílejí mnoho názvů tokenů s jinými ovládacími prvky panelu příkazů, jako jsou tlačítka, nabídky a text panelu příkazů. Pro pohodlí se tady opakují všechny nezbytné názvy tokenů tlačítek a akcí. Rozevírací seznamy rozdělení na tlačítko jsou implementace [nabídek](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)panelu příkazů.

![Redline tlačítko rozdělení](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 – 053_SplitButtonRedline")

Použít...
Když vytváříte vlastní tlačítko rozdělení.

Nepoužívat...
- pro jiné druhy tlačítek.

- v jakékoliv kombinaci pozadí/popředí kromě zadaného.

  **Výchozí**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Tlačítko rozdělení](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 – 054_SplitButton")

  **Tlačítko rozdělení (výchozí)**

  Pozadí

  Žádné

  Popředí (text)

  `Environment.CommandBarTextActive`

  Popředí (glyf)

  `Environment.CommandBarSplitButtonGlyph`

  Ohraničení

  –

  Oddělovač

  –

  **Hover**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Tlačítko rozdělení při najetí myší](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 – 055_SplitButtonHover")

  **Tlačítko rozdělení (při najetí myší)**

  Pozadí

  `Environment.CommandBarMouseOverBackgroundBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `Environment.CommandBarTextHover`

  Popředí (glyf)

  `Environment.CommandBarSplitButtonMouseOverGlyph`

  Ohraničení

  `Environment.CommandBarBorder`

  Oddělovač

  `Environment.CommandBarSplitButtonSeparator`

  **Pressed**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Stisknuté tlačítko rozdělení](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 – 056_SplitButtonPressed")

  **Tlačítko Rozdělit (stisknuté)**

  Pozadí

  `Environment.CommandBarMouseDownBackgroundBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `Environment.CommandBarTextMouseDown`

  Popředí (glyf)

  `Environment.CommandBarSplitButtonMouseDownGlyph`

  Ohraničení

  `Environment.CommandBarBorder`

  Oddělovač

  –

  **Zakázáno**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Tlačítko rozdělení je zakázané.](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 – 057_SplitButtonDisabled")

  **Tlačítko rozdělení (zakázáno)**

  Pozadí

  –

  Popředí (text)

  `Environment.ComboBoxItemTextInactive`

  Popředí (glyf)

  `Environment.CommandBarTextInactive`

  Ohraničení

  –

  Oddělovač

  –

#### <a name="more-options-and-overflow-buttons"></a>Tlačítka Další možnosti a přetečení
 Tlačítko Další možnosti se používá, když je skupina panelů příkazů přizpůsobitelná buď přidáním nebo odebráním souvisejících tlačítek panelu příkazů. Tlačítko přetečení se zobrazí, když je panel příkazů oříznutý z důvodu nedostatku horizontálního prostoru a kliknutím na položku zobrazí nabídku obsahující tlačítka panelu příkazů, která nelze zobrazit. Barvy těchto dvou tlačítek jsou ovládány stejnou sadou názvů tokenů.

 ![Další možnosti Redline](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 – 058_MoreOptionsRedline")

 Použít...
pro vlastní tlačítka Další možnosti nebo přetečení.

 Nepoužívat...
pro tlačítka, která nemají podobné funkce jako tlačítko Další možnosti nebo přetečení.

 **Výchozí**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Další možnosti](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 – 059_MoreOptions")

 **Další možnosti**

 ![Tlačítko přetečení](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 – 060_Overflow")

 **Plně**

 Pozadí

 `Environment.CommandBarOptionsBackground`

 Popředí (glyf)

 `Environment.CommandBarOptionsGlyph`

 **Hover**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Další možnosti při najetí myší](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 – 061_MoreOptionsHover")

 **Další možnosti**

 ![Přetečení při najetí myší](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 – 062_OverflowOptions")

 **Plně**

 Pozadí

 `Environment.CommandBarOptionsMouseOverBackgroundBegin`

 I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

 Popředí (glyf)

 `Environment.CommandBarOptionsMouseDownGlyph`

 **Pressed**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Bylo stisknuto více možností](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 – 063_MoreOptionsPressed")

 **Další možnosti**

 ![Stisknuté přetečení](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 – 064_OverflowPressed")

 **Plně**

 Pozadí

 `Environment.CommandBarOptionsMouseDownBackgroundBegin`

 I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

 Popředí (glyf)

 `Environment.CommandBarOptionsMouseDownGlyph`

## <a name="document-windows"></a>Okna dokumentů
 Není nutné replikovat okna dokumentů, protože jsou k dispozici v prostředí sady Visual Studio. Můžete se ale rozhodnout, že chcete využít barvy používané v oknech dokumentů, aby se vaše uživatelské rozhraní vždy zobrazilo v souladu s touto částí prostředí sady Visual Studio.

 Při použití barevných tokenů okna dokumentu musíte být opatrní, aby je bylo možné používat pouze pro podobné prvky a vždy ve dvojicích. Pokud to neuděláte, budete mít v uživatelském rozhraní neočekávané výsledky.

### <a name="document-window-frame"></a>Rámec okna dokumentu
 Okna dokumentu mohou být buď ukotvena v integrovaném vývojovém prostředí (IDE), nebo plovoucí jako samostatné okno. Když je okno dokumentu plovoucí mimo rozhraní IDE, stále je umístěno v dokumentaci dokumentu a má barvy pozadí, ohraničení, textu a tabulátoru, které jsou stejné jako v případě, že je součástí rozhraní IDE. Dokument však je umístěn uvnitř rámečku, který má vlastní pozadí, ohraničení a barvy textu. Když jsou okna nástrojů ukotvena v dokumentaci dokumentu, dědí chování a barvu jejich karet z názvů tokenů oken dokumentů.

 ![Okno ukotveného dokumentu Redline](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 – 065_DockedDocumentWindowRedline")

 **Okno ukotveného dokumentu**

 ![Plovoucí okno dokumentu Redline](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 – 066_FloatingDocumentWindowRedline")

 **Plovoucí okno dokumentu**

 Použít...
kdekoli vytváříte uživatelské rozhraní, které chcete porovnat s oknem dokumentu.

 Nepoužívat...
pro jakékoli uživatelské rozhraní, které nechcete automaticky změnit, pokud má prostředí aktualizaci motivu.

 **Výchozí**

 Součást

 Prvek

 Název tokenu: category. Color

 Dokument: ukotvený nebo plovoucí

 Pozadí

 Závisí na typu dokumentu

 Popředí (text)

 Závisí na typu dokumentu

 Ohraničení

 `Environment.ToolWindowBorder`

 ![Zaměření na rámec](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 – 067_FrameFocused")

 **Rámec: plovoucí, prioritní**

 Pozadí

 `Environment.ToolWindowFloatingFrame`

 Popředí (text)

 `Environment.ToolWindowFloatingFrame`

 Popředí (glyf)

 `Environment.RaftedWindowButtonActiveGlyph`

 Ohraničení

 `Environment.MainWindowActiveDefaultBorder`

 Border (glyf)

 `Environment.RaftedWindowButtonActiveBorder`

 Nastavit na transparentní

 ![Nevybraný rámec](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 – 068_FrameUnfocused")

 **Frame: plovoucí, nevybrané**

 Pozadí

 `Environment.ToolWindowFloatingFrameInactive`

 Popředí (text)

 `Environment.ToolWindowFloatingFrameInactive`

 Popředí (glyf)

 `Environment.RaftedWindowButtonInactiveGlyph`

 Ohraničení

 `Environment.MainWindowInactiveBorder`

 Border (glyf)

 `Environment.RaftedWindowButtonInactiveBorder`

 Nastavit na transparentní

 **Hover**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Zaměřit se na umístění rámečku při najetí myší](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 – 069_FrameFocusedHover")

 **Rámec: plovoucí, prioritní**

 Pozadí (glyf)

 `Environment.RaftedWindowButtonHoverActive`

 Popředí (glyf)

 `Environment.RaftedWindowButtonHoverActiveGlyph`

 Border (glyf)

 `Environment.RaftedWindowButtonHoverActiveBorder`

 ![Nevybraný rámeček při najetí myší](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 – 070_FrameUnfocusedHover")

 **Frame: plovoucí, nevybrané**

 Pozadí (glyf)

 `EnvironmentRaftedWindowButtonHoverInactive`

 Popředí (glyf)

 `Environment.RaftedWindowButtonHoverInactiveGlyph`

 Border (glyf)

 `Environment.RaftedWindowButtonHoverInactiveBorder`

 **Pressed**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Stisknutí rámečku soustředěné](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 – 071_FrameFocusedPressed")

 **Rámec: plovoucí, prioritní**

 Pozadí (glyf)

 `Environment.RaftedWindowButtonDown`

 Popředí (glyf)

 `Environment.RaftedWindowButtonDownGlyph`

 Border (glyf)

 `Environment.RaftedWindowButtonDownBorder`

### <a name="document-tabs"></a>Záložky dokumentů
 Karty dokumentu sedí na kanálu karet, které označují aktuálně otevřené dokumenty, spolu s tím, která z nich je aktuální vybraný nebo aktivní dokument. Okna nástrojů lze také ukotvit na kanálu na kartě dokumentu, pokud je uživatel umístí do umístění. V takové situaci používají stejné barvy tabulátoru jako okna dokumentu. Pokud vytváříte uživatelské rozhraní, které chcete vždy srovnat s barvami okna dokumentu (včetně aktualizací motivu nebo v případě, že jsou nainstalovány nové motivy), pak na tyto barevné tokeny odkazují.

 ![Redline na kartě dokumentu](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 – 072_DocumentTabRedline")

 Použít...
kdekoli vytváříte uživatelské rozhraní, které chcete porovnat s kartami dokumentů, a automaticky vyberou aktualizace motivů nebo nové barvy motivů.

 Nepoužívat...
pro jakékoli uživatelské rozhraní, které nechcete měnit automaticky, když má prostředí aktualizaci motivu.

#### <a name="open-document-tabs"></a>Otevřít karty dokumentu
 Každý otevřený dokument obsahuje kartu na kanálu na kartě dokumentu, která zobrazuje jeho název. Dokumenty mohou být buď vybrány, nebo otevřeny na pozadí a jejich karty odrážejí tyto stavy:

- Vybraná karta představuje dokument, který je aktuálně zobrazen v dokumentaci dokumentu. Vybraná karta má ohraničení dokumentu, které se rozšíří na horní okraj dokumentu.

- Karty na pozadí jsou jakékoli karty dokumentu, které nejsou aktuálně vybranou kartou. Po kliknutí se stanou vybranými kartami a získá všechny barvy pozadí, ohraničení a textu z názvů těchto tokenů.

  ![Otevřít kartu dokumentu Redline](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 – 073_OpenDocumentTabRedline")

  Použít...
  Při vytváření vlastních karet dokumentů.

  Nepoužívat...
  - pro předběžné karty (Preview).

- pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu.

#### <a name="selected-tab"></a>Vybraná karta
 **Focused**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Vybraná karta – prioritní](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 – 074_SelectedTabFocused")

 **Vybraná karta dokumentu – prioritní**

 Pozadí

 `Environment.FileTabSelectedGradientTop`

 I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

 Popředí (text)

 `Environment.FileTabSelectedText`

 Ohraničení

 `Environment.FileTabSelectedBorder`

 Nastavte na pozadí stejnou barvu.

 Ohraničení dokumentu

 `Environment.FileTabDocumentBorderBackground`

 **Bez fokusu**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Vybraná karta nebyla zaostřená.](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 – 075_SelectedTabUnfocused")

 **Vybraná karta dokumentu bez fokusu**

 Pozadí

 `Environment.FileTabInactiveGradientTop`

 I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

 Popředí (text)

 `Environment.FileTabInactiveText`

 Ohraničení

 `Environment.FileTabInactiveBorder`

 Nastavte na pozadí stejnou barvu.

 Ohraničení dokumentu

 `Environment.FileTabInactiveDocumentBorderBackground`

#### <a name="background-tab"></a>Karta pozadí
 **Výchozí**

 ![Karta pozadí](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 – 076_BackgroundTab")

 **Výchozí hodnota karty na pozadí**

 Pozadí

 `Environment.FileTabBackground`

 Popředí (text)

 `Environment.FileTabText`

 Ohraničení

 `Environment.FileTabBorder`

 Nastavte na pozadí stejnou barvu.

 **Hover**

 ![Karta pozadí při najetí myší](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 – 077_BackgroundTabHover")

 **Karta pozadí při najetí myší**

 Pozadí

 `Environment.FileTabHotGradientTop`

 I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

 Popředí (text)

 `Environment.FileTabHotText`

 Ohraničení

 `Environment.FileTabHotBorder`

 Nastavte na pozadí stejnou barvu.

#### <a name="preview-tab"></a>Karta náhled

Karta Náhled se zobrazí na pravé straně kanálu na kartě dokumentu, když uživatel klikne na položku v okně nástroje Průzkumník řešení. Funguje jako náhled dokumentu a také umožňuje uživateli zachovat otevření dokumentu na levé straně kanálu na kartě dokumentu. V jednom okamžiku může být otevřená jenom jedna otevřená karta náhled. Karty Preview mají jak pozadí, tak vybrané stavy, například otevřené karty a můžou být v jejich aktivním stavu zaměřené nebo nefokusované.

![Redline karty Preview](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 – 078_PreviewTabRedline")

Použít...
kdekoliv vytváříte dočasnou verzi Preview a chcete, aby některý prvek odpovídal aktuální barvě karty náhledu.

Nepoužívat...
- pro libovolný druh dokumentu nebo tabulátoru, který není předběžný (Preview).

- pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu.

  **Vybraná karta náhled: prioritní**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Zaměření karty Preview](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 – 079_PreviewTabFocused")

  **Karta s fokusem ve verzi Preview**

  Pozadí

  `Environment.FileTabProvisionalSelectedActive`

  Popředí (text)

  `Environment.FileTabProvisionalSelectedActiveForeground`

  Ohraničení

  `Environment.FileTabProvisionalSelectedActiveBorder`

  Nastavte na pozadí stejnou barvu.

  Ohraničení dokumentu

  `Environment.FileTabProvisionalSelectedActiveBorder`

  **Vybraná karta náhledu: Nevybráno**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Karta Preview není zaostřená](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 – 080_PreviewTabUnfocused")

  **Karta Náhled se nezaměřuje**

  Pozadí

  `Environment.FileTabProvisionalSelectedInactive`

  Popředí (text)

  `Environment.FileTabProvisionalSelectedInactiveForeground`

  Ohraničení

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  Ohraničení dokumentu

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  **Karta Náhled pozadí: výchozí**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Karta pozadí náhledu](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 – 081_PreviewBackgroundTab")

  **Karta pozadí karty Preview**

  Pozadí

  `Environment.FileTabProvisionalInactive`

  Popředí (text)

  `Environment.FileTabProvisionalInactiveForeground`

  Ohraničení

  `Environment.FileTabProvisionalInactiveBorder`

  Nastavte na pozadí stejnou barvu.

  **Karta náhledu pozadí: najeďte myší**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Náhled karty pozadí při najetí myší](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 – 082_PreviewBackgroundTabHover")

  **Karta pozadí náhledu při najetí myší**

  Pozadí

  `Environment.FileTabProvisionalHover`

  Popředí (text)

  `Environment.FileTabProvisionalHoverForeground`

  Ohraničení

  `Environment.FileTabProvisionalHoverBorder`

  Nastavte na pozadí stejnou barvu.

#### <a name="document-overflow-button"></a>Tlačítko přetečení dokumentu

Tlačítko přetečení dokumentu je k dispozici, pokud je otevřen jeden nebo více dokumentů, bez ohledu na to, zda je v aktuální konfiguraci k dispozici Svislá mezera, aby se všechny karty dokumentu vešly. Rozevírací nabídka přetečení dokumentu, která je ovládána **CommandBarMenu** barvami (viz [nabídky](../../misc/shared-colors.md#BKMK_CommandMenus)), zobrazuje seznam všech otevřených dokumentů, viditelné i skryté a glyf přetečení se mění v závislosti na tom, zda jsou všechny otevřené dokumenty zobrazeny v kanálu karet.

![Redline přetečení](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 – 083_OverflowRedline")

Použít...
Při vytváření vlastního tlačítka přetečení dokumentu.

Nepoužívat...
- pro uživatelské rozhraní, které se nepodobá tlačítku přetečení.

- pro tlačítka přetečení panelu příkazů.

  **Výchozí**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Plně](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 – 084_Overflow")

  **Tlačítko přetečení dokumentu**

  Pozadí

  `Environment.DocWellOverflowButtonBackground`

  Popředí (glyf)

  `Environment.DocWellOverflowButtonGlyph`

  Ohraničení

  –

  **Hover**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Přetečení při najetí myší](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 – 085_OverflowHover")

  **Tlačítko přetečení dokumentu při najetí myší**

  Pozadí

  `Environment.DocWellOverflowButtonMouseOverBackground`

  Popředí (glyf)

  `Environment.DocWellOverflowButtonMouseOverGlyph`

  Ohraničení

  `Environment.DocWellOverflowButtonMouseOverBorder`

  **Pressed**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Stisknuté přetečení](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 – 086_OverflowPressed")

  **Stisknuté tlačítko přetečení dokumentu**

  Pozadí

  `Environment.DocWellOverflowButtonMouseDownBackground`

  Popředí (glyf)

  `Environment.DocWellOverflowButtonMouseDownGlyph`

  Ohraničení

  `Environment.DocWellOverflowButtonMouseDownBorder`

## <a name="tool-windows"></a>Okna nástrojů
 Není nutné replikovat okna nástrojů, protože jsou k dispozici v prostředí sady Visual Studio. Můžete se ale rozhodnout, že chcete využít barvy používané v oknech nástrojů tak, aby se vaše uživatelské rozhraní vždy zobrazilo v souladu s touto částí prostředí sady Visual Studio.

 ![Okno nástroje Redline](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 – 087_ToolWindowRedline")

 Použít...
kdekoli vytváříte uživatelské rozhraní, které chcete porovnat s okny nástrojů.

 Nepoužívat...
pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu.

### <a name="tool-window-frame"></a>Rám okna nástroje
 Okna nástrojů v aplikaci Visual Studio se používají pro celou řadu různých úloh a mohou existovat v jednom z několika různých stavů. Je-li okno nástroje otevřeno, lze jej přiřadit k libovolné ze čtyř stran v oblasti dokumentu. Okna nástrojů můžou být také plovoucí mimo rozhraní IDE, což umožňuje jejich přemístění kdekoli v rámci obrazovky uživatele. Plovoucí okna se vždycky na IDE zasedat. Okna nástrojů lze nakonec ukotvit jako okna dokumentů a zobrazit jako kartu v dokumentaci dokumentu. Okna nástrojů, která jsou ukotvena jako okna dokumentů, jsou v části s použitím názvů tokenů oken dokumentu barevná.

 ![Redline rámečku okna nástroje](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 – 088_ToolWindowFrameRedline")

 Použít...
kdekoli vytváříte uživatelské rozhraní, které chcete porovnat s okny nástrojů.

 Nepoužívat...
pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu.

 **Ukotven**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Ukotvené okno nástroje](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 – 089_ToolWindowDocked")

 Pozadí

 `Environment.ToolWindowBackground`

 Ohraničení

 `Environment.ToolWindowBorder`

 **Plovoucí: prioritní**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Fokus okna nástrojů](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 – 090_ToolWindowFocused")

 Pozadí

 `Environment.ToolWindowBackground`

 Ohraničení

 `Environment.MainWindowActiveDefaultBorder`

 **Plovoucí: nevybrané**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Okno nástroje není vybrané.](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 – 091_ToolWindowUnfocused")

 Pozadí

 `Environment.ToolWindowBackground`

 Ohraničení

 `Environment.MainWindowInactiveBorder`

### <a name="tool-window-title-bar"></a>Panel nástrojů – záhlaví okna
 Ohraničení záhlaví není true Border, ale Tlustá čára v horní části záhlaví. Nemá název tokenu pro svůj nevybraný stav.

 ![Panel nástrojů záhlaví okna Redline](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 – 092_ToolWindowTitleBarRedline")

 Použít...
kdekoli vytváříte uživatelské rozhraní, které chcete porovnat s okny nástrojů.

 Nepoužívat...
pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu.

 **Focused**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Zaměření záhlaví](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 – 093_TitleBarFocused")

 **Prioritní záhlaví**

 Pozadí

 `Environment.TitleBarActiveGradientBegin`

 I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

 Popředí (text)

 `Environment.TitleBarActiveText`

 Ohraničení

 `Environment.TitleBarActiveBorder`

 Nastavte na pozadí stejnou barvu.

 Přetáhněte popisovač

 `Environment.TitleBarDragHandleActive`

 **Bez fokusu**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Záhlaví bez fokusu](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 – 094_TitleBarUnfocused")

 **Nevybraný nadpisový řádek**

 Pozadí

 `Environment.TitleBarInactiveGradientBegin`

 I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

 Popředí (text)

 `Environment.TitleBarInactiveText`

 Ohraničení

 –

 Přetáhněte popisovač

 `Environment.TitleBarDragHandle`

#### <a name="title-bar-buttons"></a>Tlačítka záhlaví

![Redline tlačítka záhlaví](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 – 095_TitleBarButtonRedline")

Použít...
pro tlačítka, která se zobrazí v uživatelském rozhraní, které používá tokeny barev z záhlaví okna nástrojů.

Nepoužívat...
- pro tlačítka, která se zobrazují v jiných umístěních.

- v jakékoliv kombinaci pozadí/popředí kromě zadaného.

  **Výchozí**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Fokus – tlačítko záhlaví](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 – 096_TitleBarButtonFocused")

  **Focused**

  Pozadí

  –

  Popředí (glyf)

  `Environment.ToolWindowButtonActiveGlyph`

  Ohraničení

  –

  ![Tlačítko s záhlavím bez fokusu](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 – 097_TitleBarButtonUnfocused")

  **Bez fokusu**

  Pozadí

  –

  Popředí (glyf)

  `Environment.ToolWindowButtonInactiveGlyph`

  Ohraničení

  –

  **Hover**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Tlačítko záhlaví s fokusem při najetí myší](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 – 098_TitleBarButtonFocusedHover")

  **Focused**

  Pozadí

  `Environment.ToolWindowButtonHoverActive`

  Popředí (glyf)

  `Environment.ToolWindowButtonHoverActiveGlyph`

  Ohraničení

  `Environment.ToolWindowButtonHoverActiveBorder`

  ![Tlačítko s záhlavím bez fokusu při najetí myší](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 – 099_TitleBarButtonUnfocusedHover")

  **Bez fokusu**

  Pozadí

  `Environment.ToolWindowButtonHoverInactive`

  Popředí (glyf)

  `Environment.ToolWindowButtonHoverInactiveGlyph`

  Ohraničení

  `Environment.ToolWindowButtonHoverInactiveBorder`

  **Pressed**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Fokus a stisknutí tlačítka záhlaví](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 – 100_TitleBarButtonFocusedPressed")

  **Focused**

  Pozadí

  `Environment.ToolWindowButtonDown`

  Popředí (glyf)

  `Environment.ToolWindowButtonDownActiveGlyph`

  Ohraničení

  `Environment.ToolWindowButtonDownBorder`

  ![Tlačítko s záhlavím bez fokusu a stisknuté](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 – 101_TitleBarButtonUnfocusedPressed")

  **Bez fokusu**

  Pozadí

  `Environment.ToolWindowButtonDown`

  Popředí (glyf)

  `Environment.ToolWindowButtonDownInactiveGlyph`

  Ohraničení

  `Environment.ToolWindowButtonDownBorder`

### <a name="tool-window-tabs"></a>Karty oken nástrojů
 ![Karta panelu nástrojů Redline](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 – 102_ToolWindowTabRedline")

 Použít...
kdekoli vytváříte uživatelské rozhraní, které chcete porovnat s okny nástrojů.

 Nepoužívat...
pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu.

 **Vybraná karta**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Zaměření na kartu okna nástrojů](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 – 103_ToolWindowTabFocused")

 **Vybraná, karta okna nástrojů s fokusem**

 Pozadí

 `Environment.ToolWindowTabSelectedTab`

 Popředí (text)

 `Environment.ToolWindowTabSelectedActiveText`

 Ohraničení

 `Environment.ToolWindowTabSelectedBorder`

 Nastavte na pozadí stejnou barvu.

 Součást

 Prvek

 Název tokenu: category. Color

 ![Karta okna nástroje není zaostřená](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 – 104_ToolWindowTabUnfocused")

 **Vybraná, karta okna nástrojů na nevybrané**

 Pozadí

 `Environment.ToolWindowTabSelectedTab`

 Popředí (text)

 `Environment.ToolWindowTabSelectedText`

 Ohraničení

 `Environment.ToolWindowTabSelectedBorder`

 Nastavte na pozadí stejnou barvu.

 **Karta pozadí**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Karta pozadí okna nástrojů](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 – 105_ToolWindowBackgroundTab")

 **Karta okno nástrojů na pozadí**

 Pozadí

 `Environment.ToolWindowTabGradientBegin`

 U přechodu se zastaví nastavení na stejnou hodnotu barvy v Visual Studio 2013.

 `Environment.ToolWindowTabGradientEnd`

 U přechodu se zastaví nastavení na stejnou hodnotu barvy v Visual Studio 2013.

 Popředí (text)

 `Environment.ToolWindowTabText`

 Ohraničení

 `Environment.ToolWindowTabBorder`

 Součást

 Prvek

 Název tokenu: category. Color

 ![Karta pozadí okna nástrojů při najetí myší](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 – 106_ToolWindowBackgroundTabHover")

 **Karta okna nástrojů na pozadí při najetí myší**

 Pozadí

 `Environment.ToolWindowTabMouseOverBackgroundBegin`

 U přechodu se zastaví nastavení na stejnou hodnotu barvy v Visual Studio 2013.

 `Environment.ToolWindowTabMouseOverBackgroundEnd`

 U přechodu se zastaví nastavení na stejnou hodnotu barvy v Visual Studio 2013.

 Popředí (text)

 `Environment.ToolWindowTabMouseOverText`

 Ohraničení

 `Environment.ToolWindowTabMouseOverBorder`

 Nastavte na pozadí stejnou barvu.

### <a name="auto-hide-tabs"></a>Automaticky skrývat karty
 ![Automaticky&#45;skrýt Redline](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 – 107_AutoHideRedline")

 Použít...
kdekoli vytváříte uživatelské rozhraní, které chcete najít na kartách okna nástrojů pro automatické skrytí.

 Nepoužívat...
pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu.

 **Výchozí**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Automaticky&#45;Skrýt kartu](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 – 108_AutoHideTab")

 **Automaticky skrývat kartu výchozí**

 Pozadí

 `Environment.AutoHideTabBackgroundBegin`

 I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

 Popředí (text)

 `Environment.AutoHideTabText`

 Ohraničení

 `Environment.AutoHideTabBorder`

 **Hover**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Automaticky&#45;Skrýt kartu při najetí myší](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 – 109_AutoHideTabHover")

 **Automaticky skrývat kartu při najetí myší**

 Pozadí

 `Environment.AutoHideTabMouseOverBackgroundBegin`

 I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

 Popředí (text)

 `Environment.AutoHideTabMouseOverText`

 Ohraničení

 `Environment.AutoHideTabMouseOverBorder`

## <a name="common-shared-controls"></a>Společné sdílené ovládací prvky
 Použijete-li ve své funkci standardní panel příkazů sady Visual Studio, budete mít přístup k ovládacím prvkům ve stylu a neměli byste tyto běžné ovládací prvky znovu nastavovat. Pokud ale potřebujete vytvořit vlastní panel příkazů, možná budete muset vytvořit také vlastní ovládací prvky. V takovém případě nezapomeňte použít správné názvy tokenů pro každý z následujících ovládacích prvků tak, aby vaše uživatelské rozhraní bylo konzistentní se zbytkem sady Visual Studio.

### <a name="search-box"></a>Vyhledávací pole
 Kdykoli je to možné, použijte běžný ovládací prvek vyhledávání poskytovaný prostředím Visual Studio. Barvy vyhledávacího pole se nacházejí v kategorii "SearchControl" v souboru **ShellColors. pkgdef** , který obsahuje názvy tokenů pro vstupní pole, tlačítko akce, tlačítko rozevíracího seznamu a rozevírací nabídku.

 Vyhledávací pole může být jedním z několika stavů, z nichž některé se vzájemně vylučují:

- "Prioritní" nebo "bez fokusu" odkazuje na to, zda je kurzor v textovém poli.

- Možnost "aktivní" nebo "neaktivní" odkazuje na to, zda uživatel zadá vyhledávací dotaz do textového pole.

- "Najetí myší" znamená, že uživatel přejede myší na vyhledávací pole (Tento stav přepisuje všechny ostatní stavy).

- "Disabled" znamená, že funkce vyhledávání je pro aktuální kontext vypnutá.

  ![Vyhledávací pole Redline](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 – 110_SearchBoxRedline")

  Použít...
  Při navrhování vlastního vyhledávacího pole.

  Nepoužívat...
  - pro cokoli, co není vyhledávací pole.

- cokoli, co nechcete, aby se vždy shodovalo s uživatelským rozhraním vyhledávacího pole.

  **Focused**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Hledat zaměření na vstupní pole](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 – 111_SearchInputFieldFocused")

  **Vstupní pole**

  Pozadí

  `SearchControl.FocusedBackground`

  Popředí (text)

  `SearchControl.FocusedBackground`

  Ohraničení

  `SearchControl.FocusedBorder`

  Oddělovač

  `SearchControl.FocusedDropDownSeparator`

  ![Fokus – tlačítko akce hledání](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 – 112_SearchActionButtonFocused")

  **Tlačítko akce**

  Pozadí

  Žádné

  Popředí (piktogram pro hledání)

  `SearchControl.SearchGlyph`

  Popředí (zastavit glyf)

  `SearchControl.StopGlyph`

  Popředí (Vymazat glyf)

  `SearchControl.ClearGlyph`

  Ohraničení

  –

  ![Hledat tlačítko pro&#45;rozevíracího seznamu](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 – 113_SearchDropdownButtonFocused")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `SearchControl.FocusedDropDownButton`

  Popředí (glyf)

  `SearchControl.FocusedDropDownButtonGlyph`

  Ohraničení

  `SearchControl.FocusedDropDownButtonBorder`

  **Bez fokusu**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Hledat vstupní pole nevybrané](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 – 114_SearchInputFieldUnfocused")

  **Aktivní vstupní pole**

  Pozadí

  `SearchControl.SearchActiveBackground`

  Popředí (text)

  `SearchControl.SearchActiveBackground`

  Ohraničení

  `SearchControl.UnfocusedBorder`

  Oddělovač

  `SearchControl.DropDownSeparator`

  ![Hledat vstupní pole nevybrané a neaktivní](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")

  **Neaktivní vstupní pole**

  Pozadí

  `SearchControl.Unfocused`

  Popředí (text)

  `SearchControl.Unfocused`

  Ohraničení

  `SearchControl.UnfocusedBorder`

  Oddělovač

  `SearchControl.DropDownSeparator`

  ![Tlačítko akce hledání nevybrané](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 – 115_SearchActionButtonUnfocused")

  **Tlačítko akce**

  Pozadí

  –

  Popředí (piktogram pro hledání)

  `SearchControl.SearchGlyph`

  Popředí (zastavit glyf)

  `SearchControl.StopGlyph`

  Popředí (Vymazat glyf)

  `SearchControl.ClearGlyph`

  Ohraničení

  –

  ![Tlačítko Hledat&#45;nevybrané tlačítkem dolů](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 – 116_SearchDropdownButtonUnfocused")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `SearchControl.UnfocusedDropDownButton`

  Popředí (glyf)

  `SearchControl.UnfocusedDropDownButtonGlyph`

  Ohraničení

  `SearchControl.UnfocusedDropDownButtonBorder`

  **Pressed**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Stisknutí tlačítka akce hledání](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")

  **Tlačítko akce**

  Pozadí

  `SearchControl.ActionButtonMouseDown`

  Popředí (glyf)

  `SearchControl.ActionButtonMouseDownGlyph`

  Ohraničení

  `SearchControl.ActionButtonMouseDownBorder`

  ![Stisknutí tlačítka Hledat&#45;dolů](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  `SearchControl.MouseDownDropDownButton`

  Popředí (glyf)

  `SearchControl.MouseDownDropDownButtonGlyph`

  Ohraničení

  `SearchControl.MouseDownDropDownButtonBorder`

  **Zvýrazněný (jenom text)**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Zvýraznit vstupní pole pro hledání](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 – 120_SearchInputFieldHighlight")

  **Vstupní pole s zvýrazněným textem**

  Pozadí

  `SearchControl.Selection`

  Popředí (text)

  `SearchControl.FocusedBackground`

  Ohraničení

  Žádné

  Oddělovač

  `SearchControl.FocusedDropDownSeparator`

  **Zakázáno**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Hledání vstupního pole je zakázané.](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 – 121_SearchInputFieldDisabled")

  **Vstupní pole**

  Pozadí

  `SearchControl.Disabled`

  Popředí (text)

  `SearchControl.Disabled`

  Ohraničení

  `SearchControl.DisabledBorder`

  Oddělovač

  `SearchControl.DropDownSeparator`

  ![Tlačítko akce hledání je zakázané.](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 – 122_SearchActionButtonDisabled")

  **Tlačítko akce**

  Pozadí

  Žádné

  Popředí (glyf)

  `SearchControl.ActionButtonDisabledGlyph`

  Ohraničení

  Žádné

  ![Tlačítko Hledat&#45;vypnuto](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 – 123_SearchDropdownButtonDisabled")

  **Tlačítko rozevíracího seznamu**

  Pozadí

  Žádné

  Popředí (glyf)

  `SearchControl.DisabledDownButtonGlyph`

  Ohraničení

  Žádné

#### <a name="search-drop-down-lists"></a>Hledání rozevíracích seznamů

Rozevírací nabídka vyhledávacího pole má potenciál v aplikaci Visual Studio mírně složitější než jiné rozevírací nabídky. Oddíly "navrhované hledání" a "možnosti hledání" se můžou v nabídce objevit samostatně nebo společně a každá z nich se bude barevně zobrazovat. Řádek také oddělí tyto dvě části, když se zobrazí společně a ohraničení celé rozevírací nabídky.

![Hledat&#45;Redline dolů](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 – 124_SearchDropdownRedline")

Použít...
- Když vytváříte rozevírací seznam vlastních hledání.

- správné názvy tokenů pro správné komponenty seznamu.

  Nepoužívat...
  - pro rozevírací seznamy, které se zobrazují v jiných kontextech.

- v jakékoliv kombinaci pozadí/popředí kromě zadaného.

  **Výchozí (žádné jiné stavy)**

  Prvek

  Název tokenu: category. Color

  Ohraničení

  `SearchControl.PopupBorder`

  Oddělovač

  `SearchControl.PopupSectionHeaderSeparator`

  Vytváření

  `Environment.DropShadowBackground`

  **Výchozí**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Doporučené hledání](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 – 125_SearchSuggested")

  **Navrhovaná hledání**

  Pozadí

  `SearchControl.PopupItemsListBackgroundGradientBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `SearchControl.PopupItemText`

  ![Zaškrtávací políčko hledání](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 – 126_SearchCheckbox")

  **Možnosti hledání (zaškrtávací políčko)**

  ![Možnosti hledání](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 – 127_SearchOptions")

  **Možnosti hledání (odkaz)**

  Pozadí

  `SearchControl.PopupSectionBackgroundGradientBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text zaškrtávacího políčka)

  `SearchControl.PopupCheckboxText`

  Popředí (text odkazu)

  `SearchControl.PopupButtonText`

  Pozadí záhlaví

  `SearchControl.PopupSectionHeaderGradientBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text záhlaví)

  `SearchControl.PopupSectionHeaderText`

  **Hover**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Hledání navrhované při najetí myší](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 – 128_SearchSuggestedHover")

  **Navrhovaná hledání**

  Pozadí

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text)

  `SearchControl.PopupMouseOverItemText`

  Ohraničení

  `SearchControl.PopupControlMouseOverBorder`

  ![Zaškrtávací políčko pro hledání při najetí myší](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 – 129_SearchCheckboxHover")

  **Navrhovaná hledání (zaškrtávací políčko)**

  ![Možnosti hledání při najetí myší](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 – 130_SearchOptionsHover")

  **Možnosti hledání**

  Pozadí

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text zaškrtávacího políčka)

  `SearchControl.PopupCheckboxMouseDownText`

  Popředí (text odkazu)

  `SearchControl.PopupButtonMouseDownText`

  Ohraničení

  `SearchControl.PopupControlMouseOverBorder`

  **Pressed**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Hledání navrhovaného stisknutí](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 – 131_SearchSuggestedPressed")

  **Navrhovaná hledání (zaškrtávací políčko)**

  ![Stisknuté možnosti hledání](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 – 132_SearchOptionsPressed")

  **Možnosti hledání**

  Pozadí zaškrtávacího políčka

  `SearchControl.PopupControlMouseDownBackgroundGradientBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  `SearchControl.PopupControlMouseDownBackgroundGradientEnd`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text zaškrtávacího políčka)

  `SearchControl.PopupCheckboxMouseDownText`

  Pozadí odkazu

  `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`

  I když se nepoužívá v uživatelském rozhraní moderních motivů, existují pro toto pozadí zarážky a hodnoty přechodu.

  Popředí (text odkazu)

  `SearchControl.PopupButtonMouseDownText`

### <a name="hyperlink"></a>Hypertextový odkaz
 Hypertextový odkaz je jeden ovládací prvek, který nemá dvojici popředí a na pozadí. Ve všech případech použijte barvu hypertextového odkazu na popředí, která se zobrazí správně na tmavém, šedém a bílé pozadí. Pokud nepoužijete token barvy pro ovládací prvek hypertextový odkaz, zobrazí se výchozí systémová barva "stisknout", která bude blikat červeně. To je signál, že ovládací prvek nepoužívá správný token barvy prostředí.

 ![Hypertextový odkaz Redline](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 – 133_HyperlinkRedline")

 Použít...
Když potřebujete vytvořit vlastní hypertextový odkaz.

 Nepoužívat...
cokoli, co není hypertextový odkaz.

 **Výchozí**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Výchozí hypertextový odkaz](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 – 134_Hyperlink")

 Popředí (text)

 `Environment.PanelHyperlink`

 **Hover**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Hypertextový odkaz při najetí myší](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 – 135_HyperlinkHover")

 Popředí (text)

 `Environment.PanelHyperlinkHover`

 **Pressed**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Hypertextový odkaz byl stisknut](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 – 136_HyperlinkPressed")

 Popředí (text)

 `Environment.PanelHyperlinkPressed`

 **Zakázáno**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Hypertextový odkaz zakázán](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 – 137_HyperlinkDisabled")

 Popředí (text)

 `Environment.PanelHyperlinkDisabled`

### <a name="infobar"></a>Řádku
 Infobars slouží k poskytnutí dalších informací o daném kontextu a vždy se zobrazí v horní části okna dokumentu nebo nástroje.

 ![Redline informačního panelu](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 – 138_InfobarRedline")

 Použít...
Při vytváření vlastních infobars.

 Nepoužívat...
pro prvky uživatelského rozhraní, které nejsou podobné informačnímu panelu.

 Součást

 Prvek

 Název tokenu: category. Color

 ![Řádku](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 – 139_Infobar")

 **Řádku**

 Pozadí

 `Environment.InfoBackground`

 Popředí (text)

 `Environment.InfoText`

 Ohraničení

 `Environment.ToolWindowBorder`

### <a name="scroll-bar"></a>Posuvník
 Posuvníky jsou ve stylu pro prostředí sady Visual Studio a nebudou se muset motivovat. Můžete se ale rozhodnout, že chcete využít barvy používané v posuvníkech, aby se vaše uživatelské rozhraní vždy zobrazilo v souladu s touto částí prostředí sady Visual Studio.

 ![Redline posuvníku](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 – 140_ScrollbarRedline")

 Použít...
Při vytváření uživatelského rozhraní, které chcete porovnat s posuvníky sady Visual Studio.

 Nepoužívat... pro cokoli, co nechcete, aby se rozhraní ScrollBar vždy shodovalo.

 **Výchozí**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Posuvník](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 – 141_Scrollbar")

 **Posuvník**

 Posuvník

 `Environment.ScrollBarBackground`

 Popředí (palec)

 `Environment.ScrollBarThumbBackground`

 ![Šipka posuvníku](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 – 142_ScrollbarArrow")

 **Šipka posuvníku**

 Pozadí

 `Environment.ScrollBarArrowBackground`

 Nastavit na stejnou barvu jako posuvník.

 Popředí (glyf)

 `Environment.ScrollBarArrowGlyph`

 **Hover**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Při najetí myší přejít na posuvník](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 – 143_ScrollbarHover")

 **Posuvník**

 Posuvník

 `Environment.ScrollBarBackground`

 Popředí (palec)

 `Environment.ScrollBarThumbMouseOverBackground`

 ![Šipka posuvníku při najetí myší](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 – 144_ScrollbarArrowHover")

 **Šipka posuvníku**

 Pozadí

 `Environment.ScrollBarArrowMouseOverBackground`

 Nastavit na stejnou barvu jako posuvník.

 Popředí (glyf)

 `Environment.ScrollBarArrowGlyphMouseOver`

 **Pressed**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Stisknutí posuvníku](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 – 145_ScrollbarPressed")

 **Posuvník**

 Posuvník

 `Environment.ScrollBarBackground`

 Popředí (palec)

 `Environment.ScrollBarThumbPressedBackground`

 ![Stisknutí šipky posuvníku](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 – 146_ScrollbarArrowPressed")

 **Šipka posuvníku**

 Pozadí

 `Environment.ScrollBarArrowPressedBackground`

 Nastavte na stejnou barvu jako ScrollBar.

 Popředí (glyf)

 `Environment.ScrollBarArrowGlyphPressed`

### <a name="tree-view"></a><a name="BKMK_TreeView"></a> Stromové zobrazení

Několik oken nástrojů, včetně Průzkumník řešení, Průzkumník serveru a Zobrazení tříd implementují hierarchické organizační schéma, jejichž barvy jsou ovládány pomocí názvů barev v kategorii TreeView. Všechny položky ve stromovém zobrazení mají barvy pozadí a textu. Položky, které mají vnořené podřízené prvky, mají také glyfy, které označují, zda je položka rozbalená nebo sbalená.

![Redline zobrazení stromu](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 – 147_TreeViewRedline")

Použít...
kdekoli potřebujete implementovat hierarchické zobrazení organizace.

Nepoužívat...
- pro cokoli, co není podobné jako stromové zobrazení.

- v jakékoliv kombinaci pozadí/popředí kromě zadaného.

  **Výchozí**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Stromové zobrazení](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 – 148_TreeView")

  Pozadí

  `TreeView.Background`

  Popředí (text)

  `TreeView.Background`

  Popředí (glyf)

  `TreeView.Glyph`

  Ohraničení

  Žádné

  **Hover**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Stromové zobrazení při najetí myší](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 – 149_TreeViewHover")

  Pozadí

  `TreeView.Background`

  Popředí (text)

  `TreeView.Background`

  Popředí (glyf)

  `TreeView.GlyphMouseOver`

  Ohraničení

  Žádné

  **Přetáhnout**

  Součást

  Prvek

  Název tokenu: category. Color

  ![DragOver zobrazení stromu](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 – 150_TreeViewDragOver")

  Pozadí

  `TreeView.DragOverItem`

  Popředí (text)

  `TreeView.DragOverItem`

  Popředí (glyf)

  `TreeView.DragOverItemGlyph`

  Ohraničení

  Žádné

  **Vybráno**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Zaměření stromového zobrazení](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 – 151_TreeViewFocused")

  **Focused**

  Pozadí

  `TreeView.SelectedItemActive`

  Popředí (text)

  `TreeView.SelectedItemActive`

  Popředí (glyf)

  `TreeView.SelectedItemActiveGlyph`

  Ohraničení

  `TreeView.FocusVisualBorder`

  ![Stromové zobrazení není vybrané.](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 – 152_TreeViewUnfocused")

  **Bez fokusu**

  Pozadí

  `TreeView.SelectedItemInactive`

  Popředí (text)

  `TreeView.SelectedItemInactive`

  Popředí (glyf)

  `TreeView.SelectedItemInactiveGlyph`

  Ohraničení

  Žádné

  **Najeďte myší na vybrané**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Stromové zobrazení zaměřené na najetí myší](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 – 153_TreeViewFocusedHover")

  **Focused**

  Pozadí

  `TreeView.SelectedItemActive`

  Popředí (text)

  `TreeView.SelectedItemActive`

  Popředí (glyf)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Ohraničení

  Žádné`TreeView.FocusVisualBorder`

  ![Po najetí myší se stromové zobrazení nezaměřuje](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 – 154_TreeViewUnfocusedHover")

  **Bez fokusu**

  Pozadí

  `TreeView.SelectedItemInactive`

  Popředí (text)

  `TreeView.SelectedItemInactive`

  Popředí (glyf)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Ohraničení

  Žádné

### <a name="button-controls"></a>ovládací prvky tlačítek
 ![Redline ovládacího prvku tlačítko](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 – 155_ButtonControlRedline")

 Použít...
pro tlačítka v dokumentaci dokumentu, které chcete integrovat s motivy sady Visual Studio (světlá, tmavě, modrá nebo motiv systému Vysoký kontrast).

 Nepoužívat...
pro tlačítka, která se zobrazí proti vlastnímu pozadí, které není součástí motivu sady Visual Studio.

 **Výchozí**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Tlačítko](../../extensibility/ux-guidelines/media/0303-156-button.png "0303 – 156_Button")

 Tlačítko

 `CommonControls.Button`

 Ohraničení tlačítka

 `CommonControls.ButtonBorder`

 **Zakázáno**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Tlačítko je zakázané.](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 – 157_ButtonDisabled")

 Tlačítko

 `CommonControls.ButtonDisabled`

 Ohraničení tlačítka

 `CommonControls.ButtonBorderDisabled`

 **Hover**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Tlačítko při najetí myší](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 – 158_ButtonHover")

 Tlačítko

 `CommonControls.ButtonHover`

 Ohraničení tlačítka

 `CommonControls.ButtonBorderHover`

 **Pressed**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Stisknutí tlačítka](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 – 159_ButtonPressed")

 Tlačítko

 `CommonControls.ButtonPressed`

 Ohraničení tlačítka

 `CommonControls.ButtonBorderPressed`

 **Focused**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Fokus – tlačítko](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 – 160_ButtonFocused")

 Tlačítko

 `CommonControls.ButtonFocused`

 Ohraničení tlačítka

 `CommonControls.ButtonBorderFocused`

### <a name="check-box-controls"></a>Ovládací prvky zaškrtávacích políček
 ![Zaškrtávací políčko Redline](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 – 161_CheckboxRedline")

 Použít...
pro ovládací prvky zaškrtávací políčko obsažené v dokumentaci dokumentu.

 Nepoužívat...
pro jakékoli uživatelské rozhraní, které není ovládacím prvkem zaškrtávací políčko.

 **Výchozí**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Zaškrtávací políčko](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 – 162_Checkbox")

 Pozadí

 `CommonControls.CheckBoxBackground`

 Ohraničení

 `CommonControls.CheckBoxBorder`

 Text

 `CommonControls.CheckBoxText`

 Zobrazovat

 `CommonControls.CheckBoxGlyph`

 **Zakázáno**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Zaškrtávací políčko zakázáno](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 – 163_CheckboxDisabled")

 Pozadí

 `CommonControls.CheckBoxBackgroundDisabled`

 Ohraničení

 `CommonControls.CheckBoxBorderDisabled`

 Text

 `CommonControls.CheckBoxTextDisabled`

 Zobrazovat

 `CommonControls.CheckBoxGlyphDisabled`

 **Hover**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Zaškrtávací políčko při najetí myší](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 – 164_CheckboxHover")

 Pozadí

 `CommonControls.CheckBoxBackgroundHover`

 Ohraničení

 `CommonControls.CheckBoxBorderHover`

 Text

 `CommonControls.CheckBoxTextHover`

 Zobrazovat

 `CommonControls.CheckBoxGlyphHover`

 **Pressed**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Stisknuté políčko](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 – 165_CheckboxPressed")

 Pozadí

 `CommonControls.CheckBoxBackgroundPressed`

 Ohraničení

 `CommonControls.CheckBoxBorderPressed`

 Text

 `CommonControls.CheckBoxTextPressed`

 Zobrazovat

 `CommonControls.CheckBoxGlyphPressed`

 **Focused**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Zaměření na zaškrtávací políčko](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 – 166_CheckboxFocused")

 Pozadí

 `CommonControls.CheckBoxBackgroundFocused`

 Ohraničení

 `CommonControls.CheckBoxBorderFocused`

 Text

 `CommonControls.CheckBoxTextFocused`

 Zobrazovat

 `CommonControls.CheckBoxGlyphFocused`

### <a name="drop-boxcombo-box-controls"></a>Rozevírací ovládací prvky pole nebo pole se seznamem

![Odpustit&#45;&#47;pole se seznamem Redline](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 – 167_DropDownComboBoxRedline")

Použít...
pro rozevírací seznamy a pole se seznamem, které jsou součástí dokumentace dokumentu.

Nepoužívat...
- pro jakékoli uživatelské rozhraní, které není rozevírací nebo pole se seznamem.

- pro [rozevírací](../../misc/shared-colors.md#BKMK_CommandDropDown) [seznam nebo pole se seznamem](../../misc/shared-colors.md#BKMK_CommandComboBox) na panelu příkazů.

  **Výchozí**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Rozevírací seznam&#45;dolů&#47;pole se seznamem](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 – 168_DropDownComboBox")

  Pozadí

  `CommonControls.ComboBoxBackground`

  Ohraničení

  `CommonControls.ComboBoxBorder`

  Text

  `CommonControls.ComboBoxText`

  Oddělovač

  `CommonControls.ComboBoxSeparator`

  Zobrazovat

  `CommonControls.ComboBoxGlyph`

  Pozadí glyfu

  `CommonControls.ComboBoxGlyphBackground`

  **Zakázáno**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Odpustit&#45;&#47;pole se seznamem je zakázané.](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 – 169_DropDownComboBoxDisabled")

  Pozadí

  `CommonControls.ComboBoxBackgroundDisabled`

  Ohraničení

  `CommonControls.ComboBoxBorderDisabled`

  Text

  `CommonControls.ComboBoxTextDisabled`

  Oddělovač

  `CommonControls.ComboBoxSeparatorDisabled`

  Zobrazovat

  `CommonControls.ComboBoxGlyphDisabled`

  Pozadí glyfu

  `CommonControls.ComboBoxGlyphBackgroundDisabled`

  **Hover**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Při najetí myší&#45;pole se seznamem rozevíracího seznamu&#47;](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 – 170_DropDownComboBoxHover")

  Pozadí

  `CommonControls.ComboBoxBackgroundHover`

  Ohraničení

  `CommonControls.ComboBoxBorderHover`

  Text

  `CommonControls.ComboBoxTextHover`

  Oddělovač

  `CommonControls.ComboBoxSeparatorHover`

  Zobrazovat

  `CommonControls.ComboBoxGlyphHover`

  Pozadí glyfu

  `CommonControls.ComboBoxGlyphBackgroundHover`

  **Pressed**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Stisknutí&#45;rozevíracího seznamu&#47;pole se seznamem](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 – 171_DropDownComboBoxPressed")

  Pozadí

  `CommonControls.ComboBoxBackgroundPressed`

  Ohraničení

  `CommonControls.ComboBoxBorderPressed`

  Text

  `CommonControls.ComboBoxTextPressed`

  Oddělovač

  `CommonControls.ComboBoxSeparatorPressed`

  Zobrazovat

  `CommonControls.ComboBoxGlyphPressed`

  Pozadí glyfu

  `CommonControls.ComboBoxGlyphBackgroundPressed`

  **Focused**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Roztáhnout&#45;&#47;pole se seznamem – zaměření](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 – 172_DropDownComboBoxFocused")

  Pozadí

  `CommonControls.ComboBoxBackgroundFocused`

  Ohraničení

  `CommonControls.ComboBoxBorderFocused`

  Text

  `CommonControls.ComboBoxTextFocused`

  Oddělovač

  `CommonControls.ComboBoxSeparatorFocused`

  Zobrazovat

  `CommonControls.ComboBoxGlyphFocused`

  Pozadí glyfu

  `CommonControls.ComboBoxGlyphBackgroundFocused`

  **Výběr textového vstupu**

  Součást

  Prvek

  Název tokenu: category. Color

  ![Odpustit&#45;&#47;pole se seznamem](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 – 173_DropDownComboBoxTextInput")

  Zvýraznit

  `CommonControls.ComboBoxTextInputSelection`

  **Stisknuté – zobrazení položek seznamu**

  ![Rozevírací seznam&#45;&#47;pole se seznamem.](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")

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

### <a name="tabular-data-grid-controls"></a>Ovládací prvky tabulkových dat (Grid)
 Ovládací prvky tabulkových dat, označované také jako ovládací prvky mřížky, jsou běžné ovládací prvky pro sadu Visual Studio, které lze použít k zobrazení velkých objemů dat ve více sloupcích. Standardní tabulkové datové ovládací prvky lze nalézt na více místech v sadě Visual Studio: okno Seznam chyb nástrojů, sestavy IntelliTrace a zobrazení haldy paměti, mimo jiné. Vždy používejte standardní dodané tabelární datové ovládací prvky. V některých vzácných instancích je možné, že nebudete mít přístup ke standardním tabulkovým datovým ovládacím prvkům. V těchto situacích použijte následující názvy tokenů, abyste zajistili, že vaše uživatelské rozhraní je konzistentní s jinými ovládacími prvky tabulkových dat v aplikaci Visual Studio.

 ![Ovládací prvek mřížky&#41; Redline &#40;tabulkových dat](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 – 197_TabularDataGridControlRedline")

 Použít...
pro tabulkové nebo mřížkové ovládací prvky.

 Nepoužívat...
pro jakékoli uživatelské rozhraní, které není tabulkové nebo mřížkový ovládací prvek.

#### <a name="column-headers"></a>Záhlaví sloupců
 Záhlaví sloupců se skládají z pozadí, ohraničení, textu nadpisu a volitelné glyfy, která se obvykle používá při řazení mřížky podle daného sloupce.

 Stav

 Prvek

 Název tokenu: category. Color

 Výchozí

 Pozadí

 `Header.Default`

 Popředí (text)

 `Environment.CommandBarTextActive`

 Popředí (glyf)

 `Header.Glyph`

 Ohraničení

 `Header.SeparatorLine`

 Hover

 Pozadí

 `Header.MouseOver`

 Popředí (text)

 `Environment.CommandBarTextHover`

 Popředí (glyf)

 `Header.MouseOverGlyph`

 Ohraničení

 `Header.SeparatorLine`

 Pressed

 Pozadí

 `CommonControls.CheckBoxBackgroundPressed`

 Popředí (text)

 `CommonControls.CheckBoxBorderPressed`

 Popředí (glyf)

 `CommonControls.CheckBoxTextPressed`

 Ohraničení

 `CommonControls.CheckBoxGlyphPressed`

#### <a name="list-view-items"></a>Položky zobrazení seznamu
 Položky zobrazení seznamu se skládají z pozadí a obsahu. Obsah může být text, ikona nebo obojí.

 Stav

 Prvek

 Název tokenu: category. Color

 Výchozí

 Pozadí

 Průhlednost

 Popředí (text)

 `Environment.CommandBarTextActive`

 Ohraničení

 Žádné

 Vybráno (aktivní)

 Pozadí

 `TreeView.SelectedItemActive`

 Popředí (text)

 `TreeView.SelectedItemActiveText`

 Ohraničení

 Žádné

 Vybráno (neaktivní)

 Pozadí

 `TreeView.SelectedItemInactive`

 Popředí (text)

 `TreeView.SelectedItemInactiveText`

 Ohraničení

 Žádné

## <a name="manifest-designer"></a>Návrhář manifestu

Manifest Designer byl navržen jako způsob, jak zjednodušit úpravu souboru manifestu v projektech se systémem Windows 8 a Windows Phone 8. I když není k dispozici žádné sdílené rozhraní pro použití, může být vhodné, abyste se shodovali s rozložením návrhu a barvami karet pro orientaci a navigaci a celkovou strukturou. Další informace o podrobnostech rozložení naleznete v tématu [layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Redline návrháře manifestu](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 – 175_ManifestDesignerRedline")

Použít...
- pro návrháře, kteří jsou podobný návrháři manifestu.

- místo použití běžných ovládacích prvků na kartě v horní části editoru v dokumentaci dokumentu.

Nepoužívat...
- Pokud máte více než šest karet.

- pro jakékoli uživatelské rozhraní, které není strukturované jako Návrhář manifestu.

  Stav

  Součást

  Prvek

  Název tokenu: category. Color

  Výchozí (vybráno)

  Karta

  Pozadí

  `ManifestDesigner.TabActive`

  Ohraničení

  Žádné

  Podokno popisu

  Pozadí

  `ManifestDesigner.DescriptionPane`

  Stránka obsahu

  Pozadí

  `ManifestDesigner.Background`

  Pomocný text dialogového okna

  `ManifestDesigner.WatermarkText`

  Tento název tokenu se neshoduje s jeho funkcí.

  Není vybráno

  Karta

  Pozadí

  `ManifestDesigner.Tab.Inactive`

  Hover

  Karta

  Pozadí

  `ManifestDesigner.Tab.Mouseover`

## <a name="tagging"></a>Označování
 Visual Studio podporuje označování, které umožňuje uživateli deklarovat hledaná klíčová slova pro účely sledování. Například vedoucí projektu a vývojáři mohou použít Team Foundation Server (TFS) k označení pracovních položek. V tabulkách níže jsou uvedeny názvy barev pro samotnou značku a glyf "ikona zavřít", který se zobrazí při najetí myší a vybraných stavů.

 ![Označování Redline](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 – 176_TaggingRedline")

 Použít...
pro uživatelské rozhraní, které podporuje označování.

 Nepoužívat...
pro jakýkoli jiný typ uživatelského rozhraní.

### <a name="tag"></a>Značka
 Součást

 Prvek

 Název tokenu: category. Color

 ![Tag](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303 – 177_Tag")

 **Výchozí**

 Pozadí

 `Tag.Background`

 Popředí (text)

 `Tag.Background`

 ![Označit při najetí myší](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 – 178_TagHover")

 **Hover**

 Pozadí

 `Tag.HoverBackground`

 Popředí (text)

 `Tag.HoverBackgroundText`

 ![Stisknutí značky](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 – 179_TagPressed")

 **Pressed**

 Pozadí

 `Tag.PressedBackground`

 Popředí (text)

 `Tag.PressedBackgroundText`

 ![Vybraná značka](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 – 180_TagSelected")

 **Vybráno**

 Pozadí

 `Tag.SelectedBackground`

 Popředí (text)

 `Tag.SelectedBackgroundText`

### <a name="glyph-close-icon"></a>Glyf (ikona zavřít)
 **Výchozí**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Značka &#40;glyf&#41;](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 – 181_TagGlyph")

 **Výchozí (označit jako výchozí)**

 Pozadí

 –

 Popředí (glyf)

 `Tag.TagHoverGlyph`

 **Hover**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Při najetí myší označit &#40;glyf&#41;](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 – 182_TagGlyphHover")

 **Najeďte myší (výchozí značka)**

 Pozadí

 `Tag.TagHoverGlyphHoverBackground`

 Popředí (glyf)

 `Tag.TagHoverGlyphHover`

 Ohraničení

 `Tag.TagHoverGlyphHoverBorder`

 **Pressed**

 Součást

 Prvek

 Název tokenu: category. Color

 ![&#41; stisknutí značky &#40;glyfu](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 – 183_TagGlyphPressed")

 **Stisknuté (označit jako výchozí)**

 Pozadí

 `Tag.TagHoverGlyphPressedBackground`

 Popředí (glyf)

 `Tag.TagHoverGlyphPressed`

 Ohraničení

 `Tag.TagHoverGlyphPressedBorder`

 **Vybraná značka/výchozí hodnota glyfu**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Vybraná značka](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 – 184_TagSelected")

 **Výchozí (vybraná značka)**

 Pozadí

 –

 Popředí (glyf)

 `Tag.TagSelectedGlyph`

 **Výběr značky/glyfy po ukázání**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Značka vybraná při najetí myší](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 – 185_TagSelectedHover")

 **Najeďte myší (vybraná značka)**

 Pozadí

 `Tag.TagSelectedGlyphHoverBackground`

 Popředí (glyf)

 `Tag.TagSelectedGlyphHover`

 Ohraničení

 `Tag.TagSelectedGlyphHoverBorder`

 **Vybraná značka/stisknutí glyfu**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Stisknutá vybraná značka](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 – 186_TagSelectedPressed")

 **Stisknuté (vybraná značka)**

 Pozadí

 `Tag.TagSelectedGlyphPressedBackground`

 Popředí (glyf)

 `Tag.TagSelectedGlyphPressed`

 Ohraničení

 `Tag.TagSelectedGlyphPressedBorder`

## <a name="shell"></a>Prostředí

### <a name="background"></a>Pozadí

Pozadí prostředí se skládá ze dvou vrstev. Spodní vrstva je plná barva, která pokrývá celé rozhraní IDE. Horní vrstva se přizpůsobí pod police příkazu a mezi oknem nástrojů automaticky skrývá kanály pro levý a pravý okraj IDE. Od Visual Studio 2013 jsou horní a Dolní vrstva pozadí nastavené na stejnou barvu v motivech světlé a tmavé.

![Redline na pozadí prostředí](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 – 187_ShellBackgroundRedline")

Použít...
pro místa, která chcete porovnat s pozadím prostředí sady Visual Studio.

Nepoužívat...
- jako výplň pro místa, která nejsou povrchy na pozadí.

- jako pozadí, na které chcete umístit elementy popředí.

  Součást

  Prvek

  Název tokenu: category. Color

  Spodní vrstva

  Pozadí

  `Environment.EnvironmentBackground`

  Součást

  Prvek

  Název tokenu: category. Color

  Horní vrstva

  Pozadí

  *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*

  `Environment.EnvironmentBackgroundGradientBegin`

  `Environment.EnvironmentBackgroundGradientEnd`

  `Environment.EnvironmentBackgroundGradientMiddle1`

  `Environment.EnvironmentBackgroundGradientMiddle2`

### <a name="command-shelf"></a>Police příkazu

Pro pozadí příkazu se používají dvě sady názvů tokenů: jedna sada, pro kterou je panel nabídek umístěný, a druhý pro místo, kde se panely příkazů nacházejí. Jednotlivé skupiny panelů příkazů mají vlastní hodnoty barvy pozadí, které jsou podrobněji popsány v části "panel příkazů". Řádek nabídek a text panelu příkazů jsou popsány v oddílech nabídky a panelu příkazů v uvedeném pořadí.

![Redline police příkazu](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 – 188_CommandShelfRedline")

Použít...
- pro oblasti, kde umístíte nabídky nebo panely nástrojů.

- se správnou kombinací názvu tokenu popředí na pozadí/?

Nepoužívat...
pro oblasti, které nejsou podobné poli police.

  Součást

  Prvek

  Název tokenu: category. Color

  Řádek nabídek

  Pozadí

  *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*

  `Environment.CommandShelfHighlightGradientBegin`

  `Environment.CommandShelfHighlightGradientMiddle`

  `Environment.CommandShelfHighlightGradientEnd`

  Panel příkazů

  Pozadí

  *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*

  `Environment.CommandShelfBackgroundGradientBegin`

  `Environment.CommandShelfBackgroundGradientMiddle`

  `Environment.CommandShelfBackgroundGradientEnd`

## <a name="toolbox"></a>Sada nástrojů
 Sada nástrojů je jedním z běžných oken nástrojů, které jsou nejčastěji používány v sadě Visual Studio. V podstatě se jedná o ovládací prvek stromu se speciálním motivem a použitým stylem.

 ![Redline nástrojů](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 – 189_ToolboxRedline")

 Použít...
Při navrhování okna nástroje, které chcete vždy konzistentně s panelem nástrojů prostředí.

 Nepoužívat...
pro cokoli, co není podobné uživatelskému rozhraní sady nástrojů, nebo pokud si nejste jistí, jestli bude mít vaše uživatelské rozhraní problémy, pokud se změní barvy sady nástrojů prostředí.

 **Výchozí**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Nadřazený uzel sady nástrojů](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 – 190_ToolboxParentNode")

 **Nadřazený uzel**

 ![Podřízený uzel sady nástrojů](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 – 191_ToolboxChildNode")

 **Podřízený uzel**

 Pozadí

 `Environment.ToolboxContent`

 Nadpisy

 `Environment.ToolWindowBackground`

 Jednotlivé položky nebo celé okno, pokud nejsou k dispozici žádné ovládací prvky

 Ohraničení

 Žádné

 Popředí (glyf)

 `Environment.ToolboxContent`

 Popředí (text)

 `Environment.ToolboxContent`

 **Hover**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Podřízený uzel panelu nástrojů při najetí myší](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 – 192_ToolboxChildNodeHover")

 **Panel nástrojů – najeďte na podřízený uzel**

 Pozadí

 `Environment.ToolboxContentMouseOver`

 Pouze jednotlivé položky

 Ohraničení

 Žádné

 Popředí (text)

 `Environment.ToolboxContentMouseOver`

 Pouze jednotlivé položky

 **Vybráno**

 Součást

 Prvek

 Název tokenu: category. Color

 ![Zaměření nadřazeného uzlu panelu nástrojů](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 – 193_ToolboxParentNodeFocused")

 **Zaměřený nadřazený uzel**

 ![Zaměření podřízeného uzlu sady nástrojů](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 – 194_ToolboxChildNodeFocused")

 **Prioritní podřízený uzel**

 Pozadí

 `TreeView.SelectedItemActive`

 Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Ohraničení

 `TreeView.FocusVisualBorder`

 Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Popředí (glyf)

 `TreeView.SelectedItemActive`

 Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Popředí (text)

 `TreeView.SelectedItemActive`

 Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 ![Nevybraný nadřazený uzel panelu nástrojů](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 – 195_ToolboxParentNodeUnfocused")

 **Nevybraný nadřazený uzel**

 ![Podřízený uzel panelu nástrojů nebyl vybrán.](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 – 196_ToolboxChildNodeUnfocused")

 **Nevybraný podřízený uzel**

 Pozadí

 `TreeView.SelectedItemInactive`

 Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Ohraničení

 Žádné

 Popředí (glyf)

 `TreeView.SelectedItemInactive`

 Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

 Popředí (text)

 `TreeView.SelectedItemInactive`

 Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)
