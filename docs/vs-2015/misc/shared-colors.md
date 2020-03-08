---
title: Sdílené barvy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: brgeorge
ms.openlocfilehash: 421ff85831bb611b655de2bc35f01423b61921a2
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410077"
---
# <a name="shared-colors"></a>Sdílené barvy
Sem vložte úvod.  
  
## <a name="shared-colors"></a>Sdílené barvy  
 Při navrhování uživatelského rozhraní, který používá společné prvky prostředí sady Visual Studio, nebo chcete prvek rozhraní pro zajištění konzistence s podobné funkce, použijte existující token názvy v definičních souborech balíčku vybrat a přiřadit barvy. Tím se zajistí, že vaše uživatelské rozhraní zůstane konzistentní s celkové prostředí sady Visual Studio a že se automaticky aktualizuje při přidávání nebo aktualizaci motivy.  
  
 Tento článek popisuje obecné prvky uživatelského rozhraní a token názvy, které používají, které můžete využít při sestavování podobným uživatelským rozhraním. Konkrétní informace o tom, jak získat přístup k těmto barevným tokenům, najdete v tématu [Služba VSColor](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Nezapomeňte použít token názvy správně:  
  
- **Použijte názvy tokenů založené na funkci, nikoli na samotné barvě.** Společné sdílené barvy jsou spojeny s prvky určité rozhraní a jsou určeny pouze pro stejné nebo podobné funkce. Například nepoužívejte soubory Barva při stisknutí tlačítka pole se seznamem pro animace průběhu pokryjte pouze z důvodu jako barva. Funkce pole se seznamem a animace se liší, a pokud barva přidružené změny pole se seznamem, už může být vhodné barvu pro prvek animace. Konzistentní použití barev pomůže zorientovat uživatelům a zabránit nejasnostem.  
  
- **Používejte barvy pozadí a textu ve správné kombinaci.** Barvy pozadí, které jsou určeny pro použití s textem bude mít k přidružené textového barvu. Nepoužívejte barvy textu, než který je určen pro pozadí. Pokud není k přidružené barvy, nepoužívejte pro všechny povrch, na kterém budete chtít zobrazit text barvy pozadí. Nejde přečíst rozhraní může vést k jiné kombinace barvy textu a pozadí.  
  
- **Používejte barvy ovládacích prvků, které jsou vhodné pro jejich umístění.** V některých stavech některé ovládací prvky sady Visual Studio nemají samostatné ohraničení a barvy pozadí. Místo toho že sbírání tyto barvy z plochy za nimi stojí. Ujistěte se, že vždy používáte token názvy, které jsou vhodné pro umístění, ve kterém jsou umístění ovládacího prvku.  
  
> [!IMPORTANT]
> Nepoužívejte tokeny nacházející se v kategoriích "Úvodní stránka" nebo "jablečná".  
  
### <a name="command-structures"></a>Příkaz struktury  
  
#### <a name="BKMK_CommandMenus"></a>Nabídek  
 Nabídky se můžou vyskytovat na několika místech Visual Studio 2013: hlavní panel nabídek, vložený v oknech dokumentů nebo nástrojů, nebo na různých místech v prostředí IDE, klikněte pravým tlačítkem myši. Implementace nabídky spojené s další prvky uživatelského rozhraní jsou popsány v části pro odpovídající prvek. Vždy byste měli používat standardní nabídky implementace poskytovaných prostředím sady Visual Studio. V některých výjimečných případech ale nebudete mít přístup k standardní nabídky sady Visual Studio. V těchto situacích nepoužívejte následující názvy token k zajištění, že vaše uživatelské rozhraní je v souladu s jiným nabídkám v sadě Visual Studio.  
  
 ![Nabídky Redline](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 – 000_MenuRedline")  
  
Použití...  
- vždy, když je potřeba vytvořit vlastní nabídku.  
  
- Pokud máte nové komponenty uživatelského rozhraní, který chcete porovnat nabídek sady Visual Studio.  
  
Nepoužívejte...  
Barva pozadí samostatně. Vždy použijte kombinaci na pozadí a popředí uvedené.  
  
##### <a name="menu-title"></a>Název nabídky  
 Názvy nabídek se skládají z na pozadí, ohraničení a text nadpisu, jakož i volitelný glyf, obvykle, když se nachází v nabídce v panelu příkazů.  
  
 ![Název nabídky Redline](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 – 001_MenuTitleRedline")  
  
Použití...  
vždy, když vytváříte název vlastní nabídku.  
  
Nepoužívejte...  
- pro všechno, co nechcete vždy odpovídat názvu nabídky.  
  
- v libovolné na pozadí a popředí jinými než která byla specifikována.  
  
  **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Výchozí název nabídky](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 – 002_MenuTitleDefault")<br /><br /> **Název nabídky**|Pozadí|Žádná|  
|![Výchozí název nabídky](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 – 002_MenuTitleDefault")<br /><br /> **Název nabídky**|Popředí (Text)|`Environment.CommandBarTextActive`|  
|![Název nabídky s výchozím glyfem](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 – 003_MenuTitleWithGlyphDefault")<br /><br /> **Název nabídky s glyfem**|Popředí (piktogram)|`Environment.CommandBarMenuGlyph`|  
|![Název nabídky s výchozím glyfem](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 – 003_MenuTitleWithGlyphDefault")<br /><br /> **Název nabídky s glyfem**|Ohraničení|Žádná|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Název nabídky při najetí myší](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 – 004_MenuTitleHover")<br /><br /> **Název nabídky**|Pozadí|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Název nabídky při najetí myší](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 – 004_MenuTitleHover")<br /><br /> **Název nabídky**|Popředí (Text)|`Environment.CommandBarTextHover`|  
|![Název nabídky s glyfem při najetí myší](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 – 005_MenuTitleWithGlyphHover")<br /><br /> **Název nabídky s glyfem**|Popředí (piktogram)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Název nabídky s glyfem při najetí myší](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 – 005_MenuTitleWithGlyphHover")<br /><br /> **Název nabídky s glyfem**|Ohraničení|`Environment.CommandBarBorder`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknutí názvu nabídky](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 – 006_MenuTitlePressed")<br /><br /> **Název nabídky**|Pozadí|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Stisknutí názvu nabídky](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 – 006_MenuTitlePressed")<br /><br /> **Název nabídky**|Popředí (Text)|`Environment.CommandBarTextActive`|  
|![Název nabídky se stisknutým glyfem](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 – 007_MenuTitleWithGlyphPressed")<br /><br /> **Název nabídky s glyfem**|Popředí (piktogram)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Název nabídky se stisknutým glyfem](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 – 007_MenuTitleWithGlyphPressed")<br /><br /> **Název nabídky s glyfem**|Ohraničení|`Environment.CommandBarMenuBorder`<br /><br /> Pouze vlevo nahoře a pravé straně.|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Název nabídky se zakázaným glyfem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 – 008_MenuTitleWithGlyphDisabled")<br /><br /> **Název nabídky s glyfem**|Pozadí|Žádná|  
|![Název nabídky se zakázaným glyfem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 – 008_MenuTitleWithGlyphDisabled")<br /><br /> **Název nabídky s glyfem**|Popředí (Text)|`Environment.CommandBarTextInactive`|  
|![Název nabídky se zakázaným glyfem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 – 008_MenuTitleWithGlyphDisabled")<br /><br /> **Název nabídky s glyfem**|Popředí (piktogram)|`Environment.CommandBarTextInactive`|  
|![Název nabídky se zakázaným glyfem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 – 008_MenuTitleWithGlyphDisabled")<br /><br /> **Název nabídky s glyfem**|Ohraničení|Žádná|  
  
##### <a name="menu"></a>Nabídka  
 Individuální nabídky položky se skládá z text nabídky a volitelné ikony, zaškrtněte políčko nebo podnabídka glyfů. Jeho textu a pozadí Změna barvy při najetí myší. Tento token barva je pár na pozadí a popředí.  
  
 ![Položky nabídky Redline](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 – 009_MenuItemRedline")  
  
 Použití...  
 pro všechny rozevíracího seznamu, který se spustí z panelu příkazů a nabídek.  
  
Nepoužívejte...  
- pro všechny rozevíracího seznamu, který se nachází v jiném kontextu.  

- v libovolné na pozadí a popředí jinými než která byla specifikována.  
  
  **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 – 010_MenuDefault")<br /><br /> **Nabídka**|Pozadí|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 – 010_MenuDefault")<br /><br /> **Nabídka**|Popředí (Text)|`Environment.CommandBarTextActive`|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 – 010_MenuDefault")<br /><br /> **Nabídka**|Popředí (podnabídky piktogram)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 – 010_MenuDefault")<br /><br /> **Nabídka**|Ohraničení|`Environment.CommandBarMenuBorder`|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 – 010_MenuDefault")<br /><br /> **Nabídka**|Pozadí ikony kanálu|`Environment.CommandBarMenuIconBackground`|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 – 010_MenuDefault")<br /><br /> **Nabídka**|Oddělovač|`Environment.CommandBarMenuSeparator`|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 – 010_MenuDefault")<br /><br /> **Nabídka**|Stín|`Environment.DropShadowBackground`|  
|![Zaškrtnutá nabídka](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 – 011_MenuChecked")<br /><br /> **Kontrolovaný**|Zaškrtávací políčko|`Environment.CommandBarCheckBox`|  
|![Zaškrtnutá nabídka](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 – 011_MenuChecked")<br /><br /> **Kontrolovaný**|Zaškrtávací políčko na pozadí|`Environment.CommandBarSelectedIcon`|  
|![Vybraná nabídka](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 – 012_MenuSelected")<br /><br /> **Vyberte**|Pozadí ikony|`Environment.CommandBarSelected`|  
|![Vybraná nabídka](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 – 012_MenuSelected")<br /><br /> **Vyberte**|Okraj ikony|`Environment.CommandBarSelectedBorder`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Najeďte do nabídky](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 – 013_MenuHover")<br /><br /> **Položka nabídky**|Pozadí|`Environment.CommandBarMenuItemMouseOver`|  
|![Najeďte do nabídky](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 – 013_MenuHover")<br /><br /> **Položka nabídky**|Popředí (Text)|`Environment.CommandBarMenuItemMouseOver`|  
|![Najeďte do nabídky](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 – 013_MenuHover")<br /><br /> **Položka nabídky**|Popředí (podnabídky piktogram)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![Kontrola najetí myší v nabídce](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 – 014_MenuHoverChecked")<br /><br /> **Kontrolovaný**|Zaškrtávací políčko|`Environment.CommandBarCheckBoxMouseOver`|  
|![Kontrola najetí myší v nabídce](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 – 014_MenuHoverChecked")<br /><br /> **Kontrolovaný**|Zaškrtávací políčko na pozadí|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Výběr myši v nabídce](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 – 015_MenuHoverSelected")<br /><br /> **Vyberte**|Pozadí ikony|`Environment.CommandBarHoverOverSelected`|  
|![Výběr myši v nabídce](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 – 015_MenuHoverSelected")<br /><br /> **Vyberte**|Okraj ikony|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nabídka zakázaná](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 – 016_MenuDisabled")<br /><br /> Položka nabídky|Popředí (Text)|`Environment.CommandBarTextInactive`|  
|![Nabídka zakázaná](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 – 016_MenuDisabled")<br /><br /> Položka nabídky|Popředí (podnabídky piktogram)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Zaškrtnutá nabídka zakázaná](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 – 017_MenuDisabledChecked")<br /><br /> Zaškrtnuté|Zaškrtávací políčko|`Environment.CommandBarCheckBoxDisabled`|  
|![Zaškrtnutá nabídka zakázaná](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 – 017_MenuDisabledChecked")<br /><br /> Zaškrtnuté|Zaškrtávací políčko na pozadí|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Panel příkazů  
 Na panelu příkazů lze zobrazit na více místech v rámci rozhraní IDE sady Visual Studio, zejména příkaz polici a embedded v nástroji nebo okna dokumentu.  
  
 Obecně platí vždy používejte implementace standardních příkazů panelu poskytovaných prostředím sady Visual Studio. Pomocí standardní mechanismus zajišťuje, že se správně zobrazí všechny podrobnosti o visual a interaktivní prvky, ke které přistupuje konzistentní s jinými ovládacími prvky sady Visual Studio příkazového řádku. Nicméně pokud je nutné, můžete vytvořit vlastní panel příkazů, ujistěte se, že správně pomocí následující token názvy stylu.  
  
 ![Redline panelu příkazů](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 – 018_CommandBarRedline")  
  
 ![Redline tlačítka přetečení](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 – 019_OverflowButtonRedline")  
  
 Použití...  
 na místech, kde je třeba vložené příkaz panelu ale nebudou moct používat standardní implementace panel příkaz sady Visual Studio.  
  
Nepoužívejte...  
- pro prvky uživatelského rozhraní, které nejsou podobný panelu příkazů.  

- pro příkaz součástí než ty, pro kterou token názvy jsou určené.  
  
##### <a name="command-bar-group"></a>Příkaz pruhový graf  
 Příkaz pruhový graf se skládá ze sady související ovládací prvky stavového řádku příkaz a může obsahovat libovolný počet tlačítek rozdělení tlačítek, rozevíracích nabídek, pole se seznamem nebo nabídky. Barvy pro tyto ovládací prvky se budou řídit token názvy a jsou jednotlivě jinde popsaných v této příručce. Oddělovací čáry se používá k rozdělení skupiny panelu příkazů na související podskupiny.  
  
 ![Redline skupiny panelů příkazů](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 – 020_CommandBarGroupRedline")  
  
 Použití...  
 na místech, kde je třeba vložené příkaz panelu ale nebudou moct používat standardní implementace panel příkaz sady Visual Studio.  
  
Nepoužívejte...  
- pro prvky uživatelského rozhraní, které nejsou podobný panelu příkazů.  

- pro příkaz součástí než ty, pro kterou token názvy jsou určené.  
  
  **Výchozí** (žádné jiné stavy)  
  
|Prvek|Název tokenu: Category.color|  
|-------------|--------------------------------|  
|Pozadí|`Environment.CommandBarGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|Ohraničení|`Environment.CommandBarToolBarBorder`|  
|Úchyt pro přetažení|`Environment.CommandBarDragHandle`|  
|Oddělovač|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Ikony příkazů  
 ![Ikona příkazu Redline](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 – 021_CommandIconRedline1")  
  
 ![Ikona příkazu Redline](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 – 022_CommandIconRedline2")  
  
 Použití...  
 u tlačítek, které budou umístěny na panelu příkazů.  
  
Nepoužívejte...  
- pro ovládací prvky, které mají své vlastní token názvy.  

- v libovolné na pozadí a popředí jinými než která byla specifikována.  
  
  **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Výchozí ikona příkazu](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 – 023_CommandIconDefault")<br /><br /> **Výchozí**|Pozadí|Není k dispozici (dědí nastavení z příkazového řádku na pozadí)|  
|![Výchozí ikona příkazu](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 – 023_CommandIconDefault")<br /><br /> **Výchozí**|Popředí (Text)|`Environment.CommandBarTextActive`|  
|![Výchozí ikona příkazu](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 – 023_CommandIconDefault")<br /><br /> **Výchozí**|Ohraničení|neuvedeno|  
|![Vybraná ikona příkazu – výchozí](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 – 024_CommandIconDefaultSelected")<br /><br /> **Vyberte**|Pozadí|`Environment.CommandBarSelected`|  
|![Vybraná ikona příkazu – výchozí](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 – 024_CommandIconDefaultSelected")<br /><br /> **Vyberte**|Popředí (Text)|`Environment.CommandBarTextSelected`|  
|![Vybraná ikona příkazu – výchozí](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 – 024_CommandIconDefaultSelected")<br /><br /> **Vyberte**|Ohraničení|`Environment.CommandBarSelectedBorder`|  
  
 **Fokus myši a klávesnice**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ikona příkazu najeďte myší](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 – 025_CommandIconHover")<br /><br /> **Při najetí myší na standard**|Pozadí|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Ikona příkazu najeďte myší](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 – 025_CommandIconHover")<br /><br /> **Při najetí myší na standard**|Popředí (Text)|`Environment.CommandBarTextHover`|  
|![Ikona příkazu najeďte myší](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 – 025_CommandIconHover")<br /><br /> **Při najetí myší na standard**|Ohraničení|`Environment.CommandBarBorder`|  
|![Ikona příkazu po výběru](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 – 026_CommandIconHoverSelected")<br /><br /> **Vybráno při najetí myší**|Pozadí|`Environment.CommandBarHoverOverSelected`|  
|![Ikona příkazu po výběru](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 – 026_CommandIconHoverSelected")<br /><br /> **Vybráno při najetí myší**|Popředí (Text)|`Environment.CommandBarTextHoverOverSelected`|  
|![Ikona příkazu po výběru](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 – 026_CommandIconHoverSelected")<br /><br /> **Vybráno při najetí myší**|Ohraničení|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Byla stisknuta ikona příkazu.](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 – 027_CommandIconPressed")<br /><br /> **Ikona stisknutého příkazu**|Pozadí|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Byla stisknuta ikona příkazu.](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 – 027_CommandIconPressed")<br /><br /> **Ikona stisknutého příkazu**|Popředí (Text)|`Environment.CommandBarTextMouseDown`|  
|![Byla stisknuta ikona příkazu.](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 – 027_CommandIconPressed")<br /><br /> **Ikona stisknutého příkazu**|Ohraničení|`Environment.CommandBarBorder`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ikona příkazu je zakázaná.](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 – 028_CommandIconDisabled")<br /><br /> **Ikona zakázaného příkazu**|Pozadí|Není k dispozici (dědí nastavení z příkazového řádku na pozadí)|  
|![Ikona příkazu je zakázaná.](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 – 028_CommandIconDisabled")<br /><br /> **Ikona zakázaného příkazu**|Popředí (Text)|`Environment.CommandBarTextInactive`|  
|![Ikona příkazu je zakázaná.](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 – 028_CommandIconDisabled")<br /><br /> **Ikona zakázaného příkazu**|Ohraničení|neuvedeno|  
  
##### <a name="BKMK_CommandComboBox"></a>Pole se seznamem  
  
> [!IMPORTANT]
> Pole se seznamem se podobají rozevírací seznamy, ale zahrnují určitá oblast upravitelný text. Pokud rozevírací seznam neobsahuje upravitelnou textovou oblast, použijte v [rozevíracím](../misc/shared-colors.md#BKMK_CommandDropDown)seznamu tokeny barev.  
  
 ![Redline pole se seznamem](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 – 029_ComboBoxRedline")  
  
Použití...  
- Při vytváření vlastního pole se seznamem.  

- Při vytváření ovládací prvek panelu příkazů, který je podobný pole se seznamem.  

Nepoužívejte...  
- pro všechno, co nechcete, aby vždy tak, aby odpovídaly příkaz uživatelské rozhraní panelu.  

- Když máte přístup k upravený pole se seznamem.  
  
  **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vstupní pole pole se seznamem](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 – 030_ComboBoxInputField")<br /><br /> **Vstupní pole**|Pozadí|`Environment.ComboBoxBackground`|  
|![Vstupní pole pole se seznamem](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 – 030_ComboBoxInputField")<br /><br /> **Vstupní pole**|Popředí (Text)|`Environment.ComboBoxText`|  
|![Vstupní pole pole se seznamem](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 – 030_ComboBoxInputField")<br /><br /> **Vstupní pole**|Ohraničení|`Environment.ComboBoxBorder`|  
|![Vstupní pole pole se seznamem](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 – 030_ComboBoxInputField")<br /><br /> **Vstupní pole**|Oddělovač|Žádný oddělovač|  
|![Rozevírací&#45;tlačítko pole se seznamem](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 – 031_ComboBoxDropdownButton")<br /><br /> **Tlačítko rozevíracího seznamu**|Pozadí|Není k dispozici (dědí)|  
|![Rozevírací&#45;tlačítko pole se seznamem](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 – 031_ComboBoxDropdownButton")<br /><br /> **Tlačítko rozevíracího seznamu**|Popředí (piktogram)|`Environment.ComboBoxGlyph`|  
|![Rozevírací&#45;seznam&#47;pole se seznamem](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 – 032_ComboBoxDropdownList")<br /><br /> **Rozevírací seznam**|Pozadí|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Rozevírací&#45;seznam&#47;pole se seznamem](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 – 032_ComboBoxDropdownList")<br /><br /> **Rozevírací seznam**|Popředí (Text)|`Environment.ComboBoxItemText`|  
|![Rozevírací&#45;seznam&#47;pole se seznamem](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 – 032_ComboBoxDropdownList")<br /><br /> **Rozevírací seznam**|Ohraničení|`Environment.ComboBoxPopupBorder`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vstupní pole pole se seznamem při najetí myší](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 – 033_ComboBoxInputFieldHover")<br /><br /> **Vstupní pole**|Pozadí|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Vstupní pole pole se seznamem při najetí myší](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 – 033_ComboBoxInputFieldHover")<br /><br /> **Vstupní pole**|Popředí (Text)|`Environment.ComboBoxMouseOverText`|  
|![Vstupní pole pole se seznamem při najetí myší](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 – 033_ComboBoxInputFieldHover")<br /><br /> **Vstupní pole**|Ohraničení|`Environment.ComboBoxMouseOverBorder`|  
|![Vstupní pole pole se seznamem při najetí myší](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 – 033_ComboBoxInputFieldHover")<br /><br /> **Vstupní pole**|Oddělovač|`Environment.ComboBoxMouseOverSeparator`|  
|![Rozevírací&#45;tlačítko&#47;pole se seznamem při najetí myší](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 – 034_ComboBoxDropdownButtonHover")<br /><br /> **Tlačítko rozevíracího seznamu**|Pozadí|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Rozevírací&#45;tlačítko&#47;pole se seznamem při najetí myší](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 – 034_ComboBoxDropdownButtonHover")<br /><br /> **Tlačítko rozevíracího seznamu**|Popředí (piktogram)|`Environment.ComboBoxMouseOverGlyph`|  
|![Rozevírací&#45;seznam&#47;při najetí myší pole se seznamem](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 – 035_ComboBoxDropdownListHover")<br /><br /> **Rozevírací seznam**|Na pozadí (položka nabídky)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Rozevírací&#45;seznam&#47;při najetí myší pole se seznamem](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 – 035_ComboBoxDropdownListHover")<br /><br /> **Rozevírací seznam**|Popředí (Text)|`Environment.ComboBoxItemMouseOverText`|  
|![Rozevírací&#45;seznam&#47;při najetí myší pole se seznamem](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 – 035_ComboBoxDropdownListHover")<br /><br /> **Rozevírací seznam**|Ohraničení (položka nabídky)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Zaměřil**  
  
|Komponenta|Prvek|Název tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Zaměření na vstupní pole pole se seznamem](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 – 036_ComboBoxInputFieldFocused")<br /><br /> **Vstupní pole**|Pozadí|`Environment.ComboBoxFocusedBackground`|  
|![Zaměření na vstupní pole pole se seznamem](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 – 036_ComboBoxInputFieldFocused")<br /><br /> **Vstupní pole**|Popředí (Text)|`Environment.ComboBoxFocusedText`|  
|![Zaměření na vstupní pole pole se seznamem](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 – 036_ComboBoxInputFieldFocused")<br /><br /> **Vstupní pole**|Ohraničení|`Environment.ComboBoxFocusedBorder`|  
|![Zaměření na vstupní pole pole se seznamem](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 – 036_ComboBoxInputFieldFocused")<br /><br /> **Vstupní pole**|Oddělovač|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Rozevírací tlačítko&#47;rozevíracího&#45;seznamu pole se seznamem](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 – 037_ComboBoxDropdownButtonFocused")<br /><br /> **Tlačítko rozevíracího seznamu**|Pozadí|`Environment.ComboBoxFocusedButtonBackground`|  
|![Rozevírací tlačítko&#47;rozevíracího&#45;seznamu pole se seznamem](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 – 037_ComboBoxDropdownButtonFocused")<br /><br /> **Tlačítko rozevíracího seznamu**|Popředí (piktogram)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Stisknuté vstupní pole pole se seznamem](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 – 038_ComboBoxInputFieldPressed")<br /><br /> **Vstupní pole**|Pozadí|`Environment.ComboBoxMouseDownBackground`|  
|![Stisknuté vstupní pole pole se seznamem](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 – 038_ComboBoxInputFieldPressed")<br /><br /> **Vstupní pole**|Popředí (Text)|`Environment.ComboBoxMouseDownText`|  
|![Stisknuté vstupní pole pole se seznamem](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 – 038_ComboBoxInputFieldPressed")<br /><br /> **Vstupní pole**|Ohraničení|`Environment.ComboBoxMouseDownBorder`|  
|![Stisknuté vstupní pole pole se seznamem](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 – 038_ComboBoxInputFieldPressed")<br /><br /> **Vstupní pole**|Oddělovač|`Environment.ComboBoxMouseDownSeparator`|  
|![Stisknuté&#47;tlačítko&#45;rozevíracího seznamu pole se seznamem](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 – 039_ComboBoxDropdownButtonPressed")<br /><br /> **Tlačítko rozevíracího seznamu**|Pozadí|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Stisknuté&#47;tlačítko&#45;rozevíracího seznamu pole se seznamem](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 – 039_ComboBoxDropdownButtonPressed")<br /><br /> **Tlačítko rozevíracího seznamu**|Popředí (piktogram)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Prvek|Název tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Vstupní pole pole se seznamem je zakázané.](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 – 041_ComboBoxInputFieldDisabled")<br /><br /> **Vstupní pole**|Pozadí|`Environment.ComboBoxDisabledBackground`|  
|![Vstupní pole pole se seznamem je zakázané.](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 – 041_ComboBoxInputFieldDisabled")<br /><br /> **Vstupní pole**|Popředí (Text)|`Environment.ComboBoxDisabledText`|  
|![Vstupní pole pole se seznamem je zakázané.](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 – 041_ComboBoxInputFieldDisabled")<br /><br /> **Vstupní pole**|Ohraničení|`Environment.ComboBoxDisabledBorder`|  
|![Vstupní pole pole se seznamem je zakázané.](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 – 041_ComboBoxInputFieldDisabled")<br /><br /> **Vstupní pole**|Oddělovač|Žádný oddělovač|  
|![Tlačítko&#47;rozevíracího&#45;seznamu pole se seznamem je zakázané.](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 – 040_ComboBoxDropdownButtonDisabled")<br /><br /> **Tlačítko rozevíracího seznamu**|Pozadí|Žádná|  
|![Tlačítko&#47;rozevíracího&#45;seznamu pole se seznamem je zakázané.](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 – 040_ComboBoxDropdownButtonDisabled")<br /><br /> **Tlačítko rozevíracího seznamu**|Popředí (piktogram)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="BKMK_CommandDropDown"></a>Rozevírací seznam  
  
> [!IMPORTANT]
> Rozevírací seznamy jsou podobné polích se seznamem, ale nemají upravitelný text oblastech. Pokud rozevírací seznam obsahuje upravitelnou textovou oblast, použijte tokeny barev nalezené v [poli se seznamem](../misc/shared-colors.md#BKMK_CommandComboBox).  
  
 ![Rozevírací&#45;Redline](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 – 042_DropdownRedline")  
  
 Použití...  
 Pokud při vytváření vlastní rozevírací seznam ovládacích prvků.  
  
Nepoužívejte...  
- pro všechno, co to není podobný rozevíracího seznamu.  

- pro pole se seznamem nebo tlačítka rozdělení.  
  
  **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozevírací&#45;pole pro výběr](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 – 043_DropdownSelectionField")<br /><br /> **Pole výběru**|Pozadí|`Environment.DropDownBackground`|  
|![Rozevírací&#45;pole pro výběr](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 – 043_DropdownSelectionField")<br /><br /> **Pole výběru**|Popředí (Text)|`DropDownText`|  
|![Rozevírací&#45;pole pro výběr](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 – 043_DropdownSelectionField")<br /><br /> **Pole výběru**|Ohraničení|`DropDownBorder`|  
|![Rozevírací&#45;pole pro výběr](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 – 043_DropdownSelectionField")<br /><br /> **Pole výběru**|Oddělovač|Žádný oddělovač|  
|![Tlačítko&#45;rozevíracího seznamu](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 – 044_DropdownButton")<br /><br /> **Tlačítko rozevíracího seznamu**|Pozadí|Žádná|  
|![Tlačítko&#45;rozevíracího seznamu](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 – 044_DropdownButton")<br /><br /> **Tlačítko rozevíracího seznamu**|Popředí (piktogram)|`Environment.DropDownGlyph`|  
|![Rozevírací&#45;seznam](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 – 045_DropdownList")<br /><br /> **Rozevírací seznam**|Pozadí|`Environment.DropDownPopupBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Rozevírací&#45;seznam](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 – 045_DropdownList")<br /><br /> **Rozevírací seznam**|Popředí (Text)|`Environment.ComboBoxItemText`|  
|![Rozevírací&#45;seznam](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 – 045_DropdownList")<br /><br /> **Rozevírací seznam**|Ohraničení|`Environment.DropDownPopupBorder`|  
|![Rozevírací&#45;seznam](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 – 045_DropdownList")<br /><br /> **Rozevírací seznam**|Stín|`Environment.DropShadowBackground`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozevírací&#45;pole pro výběr při najetí myší](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 – 046_DropdownSelectionFieldHover")<br /><br /> **Pole výběru**|Pozadí|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Rozevírací&#45;pole pro výběr při najetí myší](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 – 046_DropdownSelectionFieldHover")<br /><br /> **Pole výběru**|Popředí (Text)|`Environment.DropDownMouseOverText`|  
|![Rozevírací&#45;pole pro výběr při najetí myší](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 – 046_DropdownSelectionFieldHover")<br /><br /> **Pole výběru**|Ohraničení|`Environment.DropDownMouseOverBorder`|  
|![Rozevírací&#45;pole pro výběr při najetí myší](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 – 046_DropdownSelectionFieldHover")<br /><br /> **Pole výběru**|Oddělovač|`Environment.DropDownButtonMouseOverSeparator`|  
|![Tlačítko&#45;rozevíracího seznamu při najetí myší](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 – 047_DropdownButtonHover")<br /><br /> **Tlačítko rozevíracího seznamu**|Pozadí|`Environment.DropDownButtonMouseOverBackground`|  
|![Tlačítko&#45;rozevíracího seznamu při najetí myší](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 – 047_DropdownButtonHover")<br /><br /> **Tlačítko rozevíracího seznamu**|Popředí (piktogram)|`Environment.DropDownMouseOverGlyph`|  
|![Rozevírací&#45;seznam při najetí myší](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 – 048_DropdownListHover")<br /><br /> **Rozevírací seznam**|Na pozadí (položka nabídky)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Rozevírací&#45;seznam při najetí myší](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 – 048_DropdownListHover")<br /><br /> **Rozevírací seznam**|Popředí (Text)|`Environment.ComboBoxItemMouseOverText`|  
|![Rozevírací&#45;seznam při najetí myší](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 – 048_DropdownListHover")<br /><br /> **Rozevírací seznam**|Ohraničení (položka nabídky)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknutí pole výběru rozevíracího seznamu&#45;](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 – 049_DropdownSelectionFieldPressed")<br /><br /> **Pole výběru**|Pozadí|`Environment.DropDownMouseDownBackground`|  
|![Stisknutí pole výběru rozevíracího seznamu&#45;](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 – 049_DropdownSelectionFieldPressed")<br /><br /> **Pole výběru**|Popředí (Text)|`Environment.DropDownMouseDownText`|  
|![Stisknutí pole výběru rozevíracího seznamu&#45;](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 – 049_DropdownSelectionFieldPressed")<br /><br /> **Pole výběru**|Ohraničení|`Environment.DropDownMouseDownBorder`|  
|![Stisknutí pole výběru rozevíracího seznamu&#45;](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 – 049_DropdownSelectionFieldPressed")<br /><br /> **Pole výběru**|Oddělovač|`Environment.DropDownButtonMouseDownSeparator`|  
|![Stisknuté tlačítko rozevíracího seznamu&#45;](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 – 050_DropdownButtonPressed")<br /><br /> **Tlačítko rozevíracího seznamu**|Pozadí|`Environment.DropDownButtonMouseDownBackground`|  
|![Stisknuté tlačítko rozevíracího seznamu&#45;](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 – 050_DropdownButtonPressed")<br /><br /> **Tlačítko rozevíracího seznamu**|Popředí (piktogram)|`Environment.DropDownMouseDownGlyph`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pole&#45;výběru rozevíracího seznamu je zakázané.](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 – 051_DropdownSelectionFieldDisabled")|Pozadí|`Environment.DropDownDisabledBackground`|  
|![Pole&#45;výběru rozevíracího seznamu je zakázané.](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 – 051_DropdownSelectionFieldDisabled")|Popředí (Text)|`Environment.DropDownDisabledText`|  
|![Pole&#45;výběru rozevíracího seznamu je zakázané.](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 – 051_DropdownSelectionFieldDisabled")|Ohraničení|`Environment.DropDownDisabledBorder`|  
|![Pole&#45;výběru rozevíracího seznamu je zakázané.](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 – 051_DropdownSelectionFieldDisabled")|Oddělovač|Žádný oddělovač|  
|![Tlačítko&#45;rozevíracího seznamu je zakázané.](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 – 052_DropdownButtonDisabled")|Pozadí|neuvedeno|  
|![Tlačítko&#45;rozevíracího seznamu je zakázané.](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 – 052_DropdownButtonDisabled")|Popředí (piktogram)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Tlačítko rozdělení  
 Tlačítka rozdělení sdílet s jinými ovládacími prvky příkazového řádku, jako jsou tlačítka, nabídky a panelu text příkazu mnoho názvů token. Všechny potřebné akce a tlačítkem rozevírací nabídky token názvy pro usnadnění práce tady opakují. Rozevírací seznamy rozdělení na tlačítko jsou implementace [nabídek](../misc/shared-colors.md#BKMK_CommandMenus)panelu příkazů.  
  
 ![Redline tlačítko rozdělení](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 – 053_SplitButtonRedline")  
  
 Použití...  
 Když vytváříte tlačítko rozdělení vlastní.  
  
Nepoužívejte...  
- pro jiné typy tlačítek.  

- v libovolné na pozadí a popředí jinými než která byla specifikována.  
  
  **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko rozdělení](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 – 054_SplitButton")<br /><br /> **Tlačítko rozdělení (výchozí)**|Pozadí|Žádná|  
|![Tlačítko rozdělení](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 – 054_SplitButton")<br /><br /> **Tlačítko rozdělení (výchozí)**|Popředí (Text)|`Environment.CommandBarTextActive`|  
|![Tlačítko rozdělení](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 – 054_SplitButton")<br /><br /> **Tlačítko rozdělení (výchozí)**|Popředí (piktogram)|`Environment.CommandBarSplitButtonGlyph`|  
|![Tlačítko rozdělení](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 – 054_SplitButton")<br /><br /> **Tlačítko rozdělení (výchozí)**|Ohraničení|neuvedeno|  
|![Tlačítko rozdělení](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 – 054_SplitButton")<br /><br /> **Tlačítko rozdělení (výchozí)**|Oddělovač|neuvedeno|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko rozdělení při najetí myší](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 – 055_SplitButtonHover")<br /><br /> **Tlačítko rozdělení (při najetí myší)**|Pozadí|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Tlačítko rozdělení při najetí myší](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 – 055_SplitButtonHover")<br /><br /> **Tlačítko rozdělení (při najetí myší)**|Popředí (Text)|`Environment.CommandBarTextHover`|  
|![Tlačítko rozdělení při najetí myší](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 – 055_SplitButtonHover")<br /><br /> **Tlačítko rozdělení (při najetí myší)**|Popředí (piktogram)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Tlačítko rozdělení při najetí myší](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 – 055_SplitButtonHover")<br /><br /> **Tlačítko rozdělení (při najetí myší)**|Ohraničení|`Environment.CommandBarBorder`|  
|![Tlačítko rozdělení při najetí myší](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 – 055_SplitButtonHover")<br /><br /> **Tlačítko rozdělení (při najetí myší)**|Oddělovač|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknuté tlačítko rozdělení](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 – 056_SplitButtonPressed")<br /><br /> **Tlačítko Rozdělit (stisknuté)**|Pozadí|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Stisknuté tlačítko rozdělení](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 – 056_SplitButtonPressed")<br /><br /> **Tlačítko Rozdělit (stisknuté)**|Popředí (Text)|`Environment.CommandBarTextMouseDown`|  
|![Stisknuté tlačítko rozdělení](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 – 056_SplitButtonPressed")<br /><br /> **Tlačítko Rozdělit (stisknuté)**|Popředí (piktogram)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Stisknuté tlačítko rozdělení](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 – 056_SplitButtonPressed")<br /><br /> **Tlačítko Rozdělit (stisknuté)**|Ohraničení|`Environment.CommandBarBorder`|  
|![Stisknuté tlačítko rozdělení](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 – 056_SplitButtonPressed")<br /><br /> **Tlačítko Rozdělit (stisknuté)**|Oddělovač|neuvedeno|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko rozdělení je zakázané.](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 – 057_SplitButtonDisabled")<br /><br /> **Tlačítko rozdělení (zakázáno)**|Pozadí|neuvedeno|  
|![Tlačítko rozdělení je zakázané.](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 – 057_SplitButtonDisabled")<br /><br /> **Tlačítko rozdělení (zakázáno)**|Popředí (Text)|`Environment.ComboBoxItemTextInactive`|  
|![Tlačítko rozdělení je zakázané.](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 – 057_SplitButtonDisabled")<br /><br /> **Tlačítko rozdělení (zakázáno)**|Popředí (piktogram)|`Environment.CommandBarTextInactive`|  
|![Tlačítko rozdělení je zakázané.](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 – 057_SplitButtonDisabled")<br /><br /> **Tlačítko rozdělení (zakázáno)**|Ohraničení|neuvedeno|  
|![Tlačítko rozdělení je zakázané.](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 – 057_SplitButtonDisabled")<br /><br /> **Tlačítko rozdělení (zakázáno)**|Oddělovač|neuvedeno|  
  
##### <a name="more-options-and-overflow-buttons"></a>Další možnosti a 'Overflow' tlačítka  
 Tlačítko "Další možnosti" se používá při skupinou příkazů panelu přizpůsobitelné buď přidáním nebo odebráním související panelu příkazů. Tlačítko "Přetečení" se zobrazí, když je zkrácena kvůli nedostatku místa na vodorovné panel příkazů a při kliknutí zobrazí nabídku, která obsahuje panelu příkazů nelze zobrazit. Barvy pro tyto dvě tlačítka se řídí stejnou sadu token názvy.  
  
 ![Další možnosti Redline](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 – 058_MoreOptionsRedline")  
  
 Použití...  
 pro vlastní "Další možnosti' nebo 'Overflow' tlačítka.  
  
 Nepoužívejte...  
 u tlačítek, které nemají podobné funkce jako více možností nebo 'Overflow' tlačítko.  
  
 **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Další možnosti](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 – 059_MoreOptions")<br /><br /> **Další možnosti**|Pozadí|`Environment.CommandBarOptionsBackground`|  
|![Další možnosti](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 – 059_MoreOptions")<br /><br /> **Další možnosti**|Popředí (piktogram)|`Environment.CommandBarOptionsGlyph`|  
|![Tlačítko přetečení](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 – 060_Overflow")<br /><br /> **Plně**|Pozadí|`Environment.CommandBarOptionsBackground`|  
|![Tlačítko přetečení](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 – 060_Overflow")<br /><br /> **Plně**|Popředí (piktogram)|`Environment.CommandBarOptionsGlyph`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Další možnosti při najetí myší](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 – 061_MoreOptionsHover")<br /><br /> **Další možnosti**|Pozadí|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Další možnosti při najetí myší](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 – 061_MoreOptionsHover")<br /><br /> **Další možnosti**|Popředí (piktogram)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Přetečení při najetí myší](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 – 062_OverflowOptions")<br /><br /> **Plně**|Pozadí|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Přetečení při najetí myší](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 – 062_OverflowOptions")<br /><br /> **Plně**|Popředí (piktogram)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bylo stisknuto více možností](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 – 063_MoreOptionsPressed")<br /><br /> **Další možnosti**|Pozadí|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Bylo stisknuto více možností](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 – 063_MoreOptionsPressed")<br /><br /> **Další možnosti**|Popředí (piktogram)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Stisknuté přetečení](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 – 064_OverflowPressed")<br /><br /> **Plně**|Pozadí|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Stisknuté přetečení](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 – 064_OverflowPressed")<br /><br /> **Plně**|Popředí (piktogram)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Okna dokumentů  
 Není nutné replikovat okna dokumentu, protože jsou poskytovány prostředí sady Visual Studio. Ale můžete se rozhodnout, že chcete využít barvy použité v dokumentu systému windows tak, aby vaše uživatelské rozhraní se vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.  
  
 Při použití tokenů barva okno dokumentu, musíte být opatrní při jejich použití pouze pro podobné prvky a vždy ve dvojicích. Pokud to neuděláte, budete mít neočekávané výsledky v uživatelském rozhraní.  
  
#### <a name="document-window-frame"></a>Rámeček okna dokumentu  
 Okna dokumentu může být ukotven v integrovaném vývojovém prostředí nebo s plovoucí desetinnou čárkou jako samostatném okně. Pokud je číslo s plovoucí čárkou okna dokumentu mimo rozhraní IDE, ji stále nachází v kontejneru dokumentu a má na pozadí, ohraničení, textu a barvy karet MDI, které se shodují, pokud je částí rozhraní IDE. Ale dokumentu se nachází uvnitř rámečku, který má svou vlastní pozadí ohraničení a barvy textu. Když okna nástrojů jsou ukotveny v kontejneru dokumentu, dědí chování a barvy pro jejich karty z tokenu názvy oken dokumentů.  
  
 ![Okno ukotveného dokumentu Redline](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 – 065_DockedDocumentWindowRedline")  
  
 **Okno ukotveného dokumentu**  
  
 ![Plovoucí okno dokumentu Redline](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 – 066_FloatingDocumentWindowRedline")  
  
 **Plovoucí okno dokumentu**  
  
 Použití...  
 kdekoli vytvoříte uživatelské rozhraní, které chcete najít okno dokumentu.  
  
 Nepoužívejte...  
 uživatelské rozhraní, který chcete změnit, pokud nechcete automaticky prostředí má aktualizace motivu.  
  
 **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|Dokument: ukotven nebo s plovoucí desetinnou čárkou|Pozadí|Závisí na typu dokumentu|  
|Dokument: ukotven nebo s plovoucí desetinnou čárkou|Popředí (Text)|Závisí na typu dokumentu|  
|Dokument: ukotven nebo s plovoucí desetinnou čárkou|Ohraničení|`Environment.ToolWindowBorder`|  
|![Zaměření na rámec](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 – 067_FrameFocused")<br /><br /> **Rámec: plovoucí, prioritní**|Pozadí|`Environment.ToolWindowFloatingFrame`|  
|![Zaměření na rámec](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 – 067_FrameFocused")<br /><br /> **Rámec: plovoucí, prioritní**|Popředí (Text)|`Environment.ToolWindowFloatingFrame`|  
|![Zaměření na rámec](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 – 067_FrameFocused")<br /><br /> **Rámec: plovoucí, prioritní**|Popředí (piktogram)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Zaměření na rámec](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 – 067_FrameFocused")<br /><br /> **Rámec: plovoucí, prioritní**|Ohraničení|`Environment.MainWindowActiveDefaultBorder`|  
|![Zaměření na rámec](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 – 067_FrameFocused")<br /><br /> **Rámec: plovoucí, prioritní**|Ohraničení (piktogram)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Nastavte na transparentní|  
|![Nevybraný rámec](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 – 068_FrameUnfocused")<br /><br /> **Frame: plovoucí, nevybrané**|Pozadí|`Environment.ToolWindowFloatingFrameInactive`|  
|![Nevybraný rámec](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 – 068_FrameUnfocused")<br /><br /> **Frame: plovoucí, nevybrané**|Popředí (Text)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Nevybraný rámec](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 – 068_FrameUnfocused")<br /><br /> **Frame: plovoucí, nevybrané**|Popředí (piktogram)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Nevybraný rámec](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 – 068_FrameUnfocused")<br /><br /> **Frame: plovoucí, nevybrané**|Ohraničení|`Environment.MainWindowInactiveBorder`|  
|![Nevybraný rámec](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 – 068_FrameUnfocused")<br /><br /> **Frame: plovoucí, nevybrané**|Ohraničení (piktogram)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Nastavte na transparentní|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaměřit se na umístění rámečku při najetí myší](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 – 069_FrameFocusedHover")<br /><br /> **Rámec: plovoucí, prioritní**|Na pozadí (piktogram)|`Environment.RaftedWindowButtonHoverActive`|  
|![Zaměřit se na umístění rámečku při najetí myší](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 – 069_FrameFocusedHover")<br /><br /> **Rámec: plovoucí, prioritní**|Popředí (piktogram)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Zaměřit se na umístění rámečku při najetí myší](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 – 069_FrameFocusedHover")<br /><br /> **Rámec: plovoucí, prioritní**|Ohraničení (piktogram)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Nevybraný rámeček při najetí myší](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 – 070_FrameUnfocusedHover")<br /><br /> **Frame: plovoucí, nevybrané**|Na pozadí (piktogram)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Nevybraný rámeček při najetí myší](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 – 070_FrameUnfocusedHover")<br /><br /> **Frame: plovoucí, nevybrané**|Popředí (piktogram)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Nevybraný rámeček při najetí myší](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 – 070_FrameUnfocusedHover")<br /><br /> **Frame: plovoucí, nevybrané**|Ohraničení (piktogram)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknutí rámečku soustředěné](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 – 071_FrameFocusedPressed")<br /><br /> **Rámec: plovoucí, prioritní**|Na pozadí (piktogram)|`Environment.RaftedWindowButtonDown`|  
|![Stisknutí rámečku soustředěné](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 – 071_FrameFocusedPressed")<br /><br /> **Rámec: plovoucí, prioritní**|Popředí (piktogram)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Stisknutí rámečku soustředěné](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 – 071_FrameFocusedPressed")<br /><br /> **Rámec: plovoucí, prioritní**|Ohraničení (piktogram)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Záložky dokumentů  
 Karty dokumentů se nacházejí v kanálu kartu označující dokumenty, které jsou právě otevřeny, a která z nich je aktuální vybraná nebo aktivní dokument. Okna nástrojů lze také ukotvit v kanálu kartu dokumentu, pokud existuje uživatel je umístí. V takovém případě používají stejné barvy karet jako okna dokumentu. Při vytváření uživatelského rozhraní, který chcete vždy odpovídat barvy okno dokumentu (včetně aktualizací motiv nebo pokud jsou nainstalovány nové motivy) a pak odkazovat na tyto barvy tokeny.  
  
 ![Redline na kartě dokumentu](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 – 072_DocumentTabRedline")  
  
 Použití...  
 kdekoli vytvoříte uživatelské rozhraní, které chcete odpovídat karty dokumentů a automaticky získávají aktualizace motiv nebo nové barvy motivu.  
  
 Nepoužívejte...  
 pro všechny uživatelské rozhraní, které nechcete automaticky změnit, pokud prostředí má motiv aktualizovat.  
  
##### <a name="open-document-tabs"></a>Karty otevřených dokumentů  
 Každý otevřený dokument obsahuje kartu v kanálu kartu dokumentu, který se zobrazí její název. Dokumenty, můžete buď vybrat nebo otevřete na pozadí a jejich karty, aby odrážela tyto stavy:  
  
- Vybraná karta představuje dokument, který je dobře zobrazeno v dokumentu. Vybraná karta má ohraničení dokumentu, který rozšiřuje dobře mezi horním okrajem dokumentu.  
  
- Karty na pozadí jsou jakékoli karty dokumentu, které nejsou aktuálně vybranou kartou. Po kliknutí se stanou vybranými kartami a získá všechny barvy pozadí, ohraničení a textu z názvů těchto tokenů.  
  
  ![Otevřít kartu dokumentu Redline](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 – 073_OpenDocumentTabRedline")  
  
  Použití...  
  Pokud při vytváření vlastního dokumentu karty.  
  
  Nepoužívejte...  
  - u tabulátorů prozatímní (preview).  
  
- prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.  
  
##### <a name="selected-tab"></a>Vybraná karta  
 **Zaměřil**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vybraná karta – prioritní](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 – 074_SelectedTabFocused")<br /><br /> **Vybraná karta dokumentu – prioritní**|Pozadí|`Environment.FileTabSelectedGradientTop`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Vybraná karta – prioritní](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 – 074_SelectedTabFocused")<br /><br /> **Vybraná karta dokumentu – prioritní**|Popředí (Text)|`Environment.FileTabSelectedText`|  
|![Vybraná karta – prioritní](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 – 074_SelectedTabFocused")<br /><br /> **Vybraná karta dokumentu – prioritní**|Ohraničení|`Environment.FileTabSelectedBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
|![Vybraná karta – prioritní](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 – 074_SelectedTabFocused")<br /><br /> **Vybraná karta dokumentu – prioritní**|Dokument ohraničení|`Environment.FileTabDocumentBorderBackground`|  
  
 **Bez fokusu**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vybraná karta nebyla zaostřená.](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 – 075_SelectedTabUnfocused")<br /><br /> **Vybraná karta dokumentu bez fokusu**|Pozadí|`Environment.FileTabInactiveGradientTop`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Vybraná karta nebyla zaostřená.](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 – 075_SelectedTabUnfocused")<br /><br /> **Vybraná karta dokumentu bez fokusu**|Popředí (Text)|`Environment.FileTabInactiveText`|  
|![Vybraná karta nebyla zaostřená.](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 – 075_SelectedTabUnfocused")<br /><br /> **Vybraná karta dokumentu bez fokusu**|Ohraničení|`Environment.FileTabInactiveBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
|![Vybraná karta nebyla zaostřená.](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 – 075_SelectedTabUnfocused")<br /><br /> **Vybraná karta dokumentu bez fokusu**|Dokument ohraničení|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Karty na pozadí  
 **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Karta pozadí](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 – 076_BackgroundTab")<br /><br /> **Výchozí hodnota karty na pozadí**|Pozadí|`Environment.FileTabBackground`|  
|![Karta pozadí](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 – 076_BackgroundTab")<br /><br /> **Výchozí hodnota karty na pozadí**|Popředí (Text)|`Environment.FileTabText`|  
|![Karta pozadí](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 – 076_BackgroundTab")<br /><br /> **Výchozí hodnota karty na pozadí**|Ohraničení|`Environment.FileTabBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Karta pozadí při najetí myší](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 – 077_BackgroundTabHover")<br /><br /> **Karta pozadí při najetí myší**|Pozadí|`Environment.FileTabHotGradientTop`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Karta pozadí při najetí myší](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 – 077_BackgroundTabHover")<br /><br /> **Karta pozadí při najetí myší**|Popředí (Text)|`Environment.FileTabHotText`|  
|![Karta pozadí při najetí myší](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 – 077_BackgroundTabHover")<br /><br /> **Karta pozadí při najetí myší**|Ohraničení|`Environment.FileTabHotBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
##### <a name="preview-tab"></a>Karta náhledu  
 Na kartě preview se zobrazí na pravé straně kanálu kartu dokumentu po kliknutí na položku v panelu nástrojů Průzkumníku řešení. Funguje jako náhled dokumentu a také umožňuje uživateli možnost zachovat dokument otevřít na levé straně kanálu kartu dokumentu. Otevřenou kartou pouze jednu verzi preview může být najednou otevřený. Ve verzi Preview karty mají i na pozadí a vybraných států, jako jsou otevřené karty a může být zaměřené nebo bez fokusu v aktivním stavu.  
  
 ![Redline karty Preview](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 – 078_PreviewTabRedline")  
  
 Použití...  
 kdekoli vytváření prozatímní ve verzi preview a má nějaký element tak, aby odpovídaly aktuální barvu karty ve verzi preview.  
  
Nepoužívejte...  
- pro jakýkoli druh dokumentu nebo kartu, která není prozatímní (preview).  

- prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.  
  
  **Vybraná karta náhled: prioritní**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaměření karty Preview](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 – 079_PreviewTabFocused")<br /><br /> **Karta s fokusem ve verzi Preview**|Pozadí|`Environment.FileTabProvisionalSelectedActive`|  
|![Zaměření karty Preview](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 – 079_PreviewTabFocused")<br /><br /> **Karta s fokusem ve verzi Preview**|Popředí (Text)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Zaměření karty Preview](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 – 079_PreviewTabFocused")<br /><br /> **Karta s fokusem ve verzi Preview**|Ohraničení|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
|![Zaměření karty Preview](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 – 079_PreviewTabFocused")<br /><br /> **Karta s fokusem ve verzi Preview**|Dokument ohraničení|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Vybraná karta náhledu: Nevybráno**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta Preview není zaostřená](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 – 080_PreviewTabUnfocused")<br /><br /> **Karta Náhled se nezaměřuje**|Pozadí|`Environment.FileTabProvisionalSelectedInactive`|  
|![Karta Preview není zaostřená](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 – 080_PreviewTabUnfocused")<br /><br /> **Karta Náhled se nezaměřuje**|Popředí (Text)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Karta Preview není zaostřená](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 – 080_PreviewTabUnfocused")<br /><br /> **Karta Náhled se nezaměřuje**|Ohraničení|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Karta Preview není zaostřená](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 – 080_PreviewTabUnfocused")<br /><br /> **Karta Náhled se nezaměřuje**|Dokument ohraničení|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Karta Náhled pozadí: výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta pozadí náhledu](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 – 081_PreviewBackgroundTab")<br /><br /> **Karta pozadí karty Preview**|Pozadí|`Environment.FileTabProvisionalInactive`|  
|![Karta pozadí náhledu](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 – 081_PreviewBackgroundTab")<br /><br /> **Karta pozadí karty Preview**|Popředí (Text)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Karta pozadí náhledu](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 – 081_PreviewBackgroundTab")<br /><br /> **Karta pozadí karty Preview**|Ohraničení|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
 **Karta náhledu pozadí: najeďte myší**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Náhled karty pozadí při najetí myší](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 – 082_PreviewBackgroundTabHover")<br /><br /> **Karta pozadí náhledu při najetí myší**|Pozadí|`Environment.FileTabProvisionalHover`|  
|![Náhled karty pozadí při najetí myší](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 – 082_PreviewBackgroundTabHover")<br /><br /> **Karta pozadí náhledu při najetí myší**|Popředí (Text)|`Environment.FileTabProvisionalHoverForeground`|  
|![Náhled karty pozadí při najetí myší](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 – 082_PreviewBackgroundTabHover")<br /><br /> **Karta pozadí náhledu při najetí myší**|Ohraničení|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
##### <a name="document-overflow-button"></a>Dokument tlačítku přetečení  
 Tlačítko přetečení dokument je k dispozici, pokud existuje jedna nebo více dokumentů otevřít, bez ohledu na to, zda je v aktuální konfiguraci podle všechny karty dokumentu svislé mezery. Rozevírací nabídka přetečení dokumentu, která je ovládána **CommandBarMenu** barvami (viz [nabídky](../misc/shared-colors.md#BKMK_CommandMenus)), zobrazuje seznam všech otevřených dokumentů, viditelné i skryté a glyf přetečení se mění v závislosti na tom, zda jsou všechny otevřené dokumenty zobrazeny v kanálu karet.  
  
 ![Redline přetečení](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 – 083_OverflowRedline")  
  
Použití...  
Když vytvoříte tlačítko přetečení vlastní šablony dokumentů.  

Nepoužívejte...  
- pro uživatelské rozhraní, která není podobné k tlačítku přetečení.  

- pro tlačítka přetečení panelu příkazů.  
  
  **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Plně](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 – 084_Overflow")<br /><br /> **Tlačítko přetečení dokumentu**|Pozadí|`Environment.DocWellOverflowButtonBackground`|  
|![Plně](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 – 084_Overflow")<br /><br /> **Tlačítko přetečení dokumentu**|Popředí (piktogram)|`Environment.DocWellOverflowButtonGlyph`|  
|![Plně](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 – 084_Overflow")<br /><br /> **Tlačítko přetečení dokumentu**|Ohraničení|neuvedeno|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Přetečení při najetí myší](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 – 085_OverflowHover")<br /><br /> **Tlačítko přetečení dokumentu při najetí myší**|Pozadí|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Přetečení při najetí myší](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 – 085_OverflowHover")<br /><br /> **Tlačítko přetečení dokumentu při najetí myší**|Popředí (piktogram)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Přetečení při najetí myší](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 – 085_OverflowHover")<br /><br /> **Tlačítko přetečení dokumentu při najetí myší**|Ohraničení|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknuté přetečení](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 – 086_OverflowPressed")<br /><br /> **Stisknuté tlačítko přetečení dokumentu**|Pozadí|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Stisknuté přetečení](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 – 086_OverflowPressed")<br /><br /> **Stisknuté tlačítko přetečení dokumentu**|Popředí (piktogram)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Stisknuté přetečení](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 – 086_OverflowPressed")<br /><br /> **Stisknuté tlačítko přetečení dokumentu**|Ohraničení|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Nástroje systému windows  
 Není nutné replikovat okna nástrojů, protože jsou poskytovány prostředí sady Visual Studio. Ale můžete se rozhodnout, že chcete využít barvy použité v oknech nástrojů tak, aby vaše uživatelské rozhraní se vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.  
  
 ![Okno nástroje Redline](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 – 087_ToolWindowRedline")  
  
 Použití...  
 kdekoli vytvoříte uživatelské rozhraní, které chcete porovnat okna nástrojů.  
  
 Nepoužívejte...  
 prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.  
  
#### <a name="tool-window-frame"></a>Rámeček okna nástroje  
 Okna nástrojů v sadě Visual Studio se používají pro celou řadu různých úloh a může existovat v jednom z několika různých stavů. Pokud je panel nástrojů otevřen, může být přiřazena k některému z čtyřech stranách oblasti dokumentu. Nástroje systému windows můžete také uvolnit mimo rozhraní IDE, odkud můžou přesunout kamkoli v rámci obrazovce uživatele. Plovoucí okna vždy nacházejí na integrovaném vývojovém prostředí. Nakonec panely nástrojů lze ukotvit jako dokument windows a zobrazí jako karty v dobře dokumentu. Okna nástrojů, které byly ukotvit jako dokument windows se zobrazí v části pomocí tokenu názvy oken dokumentů.  
  
 ![Redline rámečku okna nástroje](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 – 088_ToolWindowFrameRedline")  
  
 Použití...  
 kdekoli vytvoříte uživatelské rozhraní, které chcete porovnat okna nástrojů.  
  
 Nepoužívejte...  
 prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.  
  
 **Ukotven**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ukotvené okno nástroje](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 – 089_ToolWindowDocked")|Pozadí|`Environment.ToolWindowBackground`|  
|![Ukotvené okno nástroje](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 – 089_ToolWindowDocked")|Ohraničení|`Environment.ToolWindowBorder`|  
  
 **Plovoucí: prioritní**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Fokus okna nástrojů](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 – 090_ToolWindowFocused")|Pozadí|`Environment.ToolWindowBackground`|  
|![Fokus okna nástrojů](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 – 090_ToolWindowFocused")|Ohraničení|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Plovoucí: nevybrané**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Okno nástroje není vybrané.](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 – 091_ToolWindowUnfocused")|Pozadí|`Environment.ToolWindowBackground`|  
|![Okno nástroje není vybrané.](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 – 091_ToolWindowUnfocused")|Ohraničení|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Záhlaví okna nástroje  
 Ohraničení panelu název není true ohraničení, ale tlustá čára v horní části záhlaví. Nemá název tokenu bez fokusu stavu.  
  
 ![Panel nástrojů záhlaví okna Redline](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 – 092_ToolWindowTitleBarRedline")  
  
 Použití...  
 kdekoli vytvoříte uživatelské rozhraní, které chcete porovnat okna nástrojů.  
  
 Nepoužívejte...  
 prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.  
  
 **Zaměřil**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaměření záhlaví](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 – 093_TitleBarFocused")<br /><br /> **Prioritní záhlaví**|Pozadí|`Environment.TitleBarActiveGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Zaměření záhlaví](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 – 093_TitleBarFocused")<br /><br /> **Prioritní záhlaví**|Popředí (Text)|`Environment.TitleBarActiveText`|  
|![Zaměření záhlaví](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 – 093_TitleBarFocused")<br /><br /> **Prioritní záhlaví**|Ohraničení|`Environment.TitleBarActiveBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
|![Zaměření záhlaví](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 – 093_TitleBarFocused")<br /><br /> **Prioritní záhlaví**|Úchyt pro přetažení|`Environment.TitleBarDragHandleActive`|  
  
 **Bez fokusu**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Záhlaví bez fokusu](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 – 094_TitleBarUnfocused")<br /><br /> **Nevybraný nadpisový řádek**|Pozadí|`Environment.TitleBarInactiveGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Záhlaví bez fokusu](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 – 094_TitleBarUnfocused")<br /><br /> **Nevybraný nadpisový řádek**|Popředí (Text)|`Environment.TitleBarInactiveText`|  
|![Záhlaví bez fokusu](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 – 094_TitleBarUnfocused")<br /><br /> **Nevybraný nadpisový řádek**|Ohraničení|neuvedeno|  
|![Záhlaví bez fokusu](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 – 094_TitleBarUnfocused")<br /><br /> **Nevybraný nadpisový řádek**|Úchyt pro přetažení|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Název tlačítka na panelu  
 ![Redline tlačítka záhlaví](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 – 095_TitleBarButtonRedline")  
  
 Použití...  
 u tlačítek, která se zobrazí v uživatelském rozhraní, která používá tokeny barvu ze záhlaví okna nástrojů.  
  
Nepoužívejte...  
- u tlačítek, která se zobrazí v jiných umístěních.  

- v libovolné na pozadí a popředí jinými než která byla specifikována.  
  
  **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Fokus – tlačítko záhlaví](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 – 096_TitleBarButtonFocused")<br /><br /> **Zaměřil**|Pozadí|neuvedeno|  
|![Fokus – tlačítko záhlaví](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 – 096_TitleBarButtonFocused")<br /><br /> **Zaměřil**|Popředí (piktogram)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Fokus – tlačítko záhlaví](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 – 096_TitleBarButtonFocused")<br /><br /> **Zaměřil**|Ohraničení|neuvedeno|  
|![Tlačítko s záhlavím bez fokusu](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 – 097_TitleBarButtonUnfocused")<br /><br /> **Bez fokusu**|Pozadí|neuvedeno|  
|![Tlačítko s záhlavím bez fokusu](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 – 097_TitleBarButtonUnfocused")<br /><br /> **Bez fokusu**|Popředí (piktogram)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Tlačítko s záhlavím bez fokusu](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 – 097_TitleBarButtonUnfocused")<br /><br /> **Bez fokusu**|Ohraničení|neuvedeno|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko záhlaví s fokusem při najetí myší](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 – 098_TitleBarButtonFocusedHover")<br /><br /> **Zaměřil**|Pozadí|`Environment.ToolWindowButtonHoverActive`|  
|![Tlačítko záhlaví s fokusem při najetí myší](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 – 098_TitleBarButtonFocusedHover")<br /><br /> **Zaměřil**|Popředí (piktogram)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Tlačítko záhlaví s fokusem při najetí myší](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 – 098_TitleBarButtonFocusedHover")<br /><br /> **Zaměřil**|Ohraničení|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Tlačítko s záhlavím bez fokusu při najetí myší](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 – 099_TitleBarButtonUnfocusedHover")<br /><br /> **Bez fokusu**|Pozadí|`Environment.ToolWindowButtonHoverInactive`|  
|![Tlačítko s záhlavím bez fokusu při najetí myší](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 – 099_TitleBarButtonUnfocusedHover")<br /><br /> **Bez fokusu**|Popředí (piktogram)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Tlačítko s záhlavím bez fokusu při najetí myší](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 – 099_TitleBarButtonUnfocusedHover")<br /><br /> **Bez fokusu**|Ohraničení|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Fokus a stisknutí tlačítka záhlaví](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 – 100_TitleBarButtonFocusedPressed")<br /><br /> **Zaměřil**|Pozadí|`Environment.ToolWindowButtonDown`|  
|![Fokus a stisknutí tlačítka záhlaví](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 – 100_TitleBarButtonFocusedPressed")<br /><br /> **Zaměřil**|Popředí (piktogram)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Fokus a stisknutí tlačítka záhlaví](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 – 100_TitleBarButtonFocusedPressed")<br /><br /> **Zaměřil**|Ohraničení|`Environment.ToolWindowButtonDownBorder`|  
|![Tlačítko s záhlavím bez fokusu a stisknuté](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 – 101_TitleBarButtonUnfocusedPressed")<br /><br /> **Bez fokusu**|Pozadí|`Environment.ToolWindowButtonDown`|  
|![Tlačítko s záhlavím bez fokusu a stisknuté](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 – 101_TitleBarButtonUnfocusedPressed")<br /><br /> **Bez fokusu**|Popředí (piktogram)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Tlačítko s záhlavím bez fokusu a stisknuté](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 – 101_TitleBarButtonUnfocusedPressed")<br /><br /> **Bez fokusu**|Ohraničení|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Karty okna nástrojů  
 ![Karta panelu nástrojů Redline](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 – 102_ToolWindowTabRedline")  
  
 Použití...  
 kdekoli vytvoříte uživatelské rozhraní, které chcete porovnat okna nástrojů.  
  
 Nepoužívejte...  
 prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.  
  
 **Vybraná karta**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaměření na kartu okna nástrojů](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 – 103_ToolWindowTabFocused")<br /><br /> **Vybraná, karta okna nástrojů s fokusem**|Pozadí|`Environment.ToolWindowTabSelectedTab`|  
|![Zaměření na kartu okna nástrojů](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 – 103_ToolWindowTabFocused")<br /><br /> **Vybraná, karta okna nástrojů s fokusem**|Popředí (Text)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Zaměření na kartu okna nástrojů](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 – 103_ToolWindowTabFocused")<br /><br /> **Vybraná, karta okna nástrojů s fokusem**|Ohraničení|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta okna nástroje není zaostřená](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 – 104_ToolWindowTabUnfocused")<br /><br /> **Vybraná, karta okna nástrojů na nevybrané**|Pozadí|`Environment.ToolWindowTabSelectedTab`|  
|![Karta okna nástroje není zaostřená](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 – 104_ToolWindowTabUnfocused")<br /><br /> **Vybraná, karta okna nástrojů na nevybrané**|Popředí (Text)|`Environment.ToolWindowTabSelectedText`|  
|![Karta okna nástroje není zaostřená](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 – 104_ToolWindowTabUnfocused")<br /><br /> **Vybraná, karta okna nástrojů na nevybrané**|Ohraničení|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
 **Karta pozadí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta pozadí okna nástrojů](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 – 105_ToolWindowBackgroundTab")<br /><br /> **Karta okno nástrojů na pozadí**|Pozadí|`Environment.ToolWindowTabGradientBegin`<br /><br /> Přechod zastaví nastavenou na hodnotu barvy v sadě Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> Přechod zastaví nastavenou na hodnotu barvy v sadě Visual Studio 2013.|  
|![Karta pozadí okna nástrojů](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 – 105_ToolWindowBackgroundTab")<br /><br /> **Karta okno nástrojů na pozadí**|Popředí (Text)|`Environment.ToolWindowTabText`|  
|![Karta pozadí okna nástrojů](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 – 105_ToolWindowBackgroundTab")<br /><br /> **Karta okno nástrojů na pozadí**|Ohraničení|`Environment.ToolWindowTabBorder`|  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta pozadí okna nástrojů při najetí myší](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 – 106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okna nástrojů na pozadí při najetí myší**|Pozadí|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> Přechod zastaví nastavenou na hodnotu barvy v sadě Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> Přechod zastaví nastavenou na hodnotu barvy v sadě Visual Studio 2013.|  
|![Karta pozadí okna nástrojů při najetí myší](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 – 106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okna nástrojů na pozadí při najetí myší**|Popředí (Text)|`Environment.ToolWindowTabMouseOverText`|  
|![Karta pozadí okna nástrojů při najetí myší](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 – 106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okna nástrojů na pozadí při najetí myší**|Ohraničení|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
#### <a name="auto-hide-tabs"></a>Automatického skrytí karty  
 ![Automaticky&#45;skrývat Redline](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 – 107_AutoHideRedline")  
  
 Použití...  
 kdekoli vytvoříte uživatelské rozhraní, které můžete chtít, aby nástroj automaticky skrývaná okna karet.  
  
 Nepoužívejte...  
 prostředí pro uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizace motivu.  
  
 **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Automaticky&#45;Skrýt kartu](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 – 108_AutoHideTab")<br /><br /> **Automaticky skrývat kartu výchozí**|Pozadí|`Environment.AutoHideTabBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Automaticky&#45;Skrýt kartu](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 – 108_AutoHideTab")<br /><br /> **Automaticky skrývat kartu výchozí**|Popředí (Text)|`Environment.AutoHideTabText`|  
|![Automaticky&#45;Skrýt kartu](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 – 108_AutoHideTab")<br /><br /> **Automaticky skrývat kartu výchozí**|Ohraničení|`Environment.AutoHideTabBorder`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Automaticky&#45;skrývat kartu při najetí myší](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 – 109_AutoHideTabHover")<br /><br /> **Automaticky skrývat kartu při najetí myší**|Pozadí|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Automaticky&#45;skrývat kartu při najetí myší](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 – 109_AutoHideTabHover")<br /><br /> **Automaticky skrývat kartu při najetí myší**|Popředí (Text)|`Environment.AutoHideTabMouseOverText`|  
|![Automaticky&#45;skrývat kartu při najetí myší](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 – 109_AutoHideTabHover")<br /><br /> **Automaticky skrývat kartu při najetí myší**|Ohraničení|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Běžné ovládací prvky sdílené  
 Při použití standardní panel příkazů sady Visual Studio v vaši funkci, budete mít přístup k ovládacím prvkům upravený prostředí a byste měli znovu template tyto běžné ovládací prvky. Ale pokud budete muset sestavit vlastní příkazového řádku, potřebujete k vytváření vlastních ovládacích prvků. V takovém případě nezapomeňte použít správný token názvy pro každý z následujících ovládacích prvků tak, aby vaše uživatelské rozhraní je konzistentní se zbytkem pracovního sadě Visual Studio.  
  
#### <a name="search-box"></a>Vyhledávací pole  
 Kdykoli je to možné, použijte běžný ovládací prvek vyhledávání poskytovaných prostředím sady Visual Studio. Barvy vyhledávacího pole se nacházejí v kategorii "SearchControl" v souboru **ShellColors. pkgdef** , který obsahuje názvy tokenů pro vstupní pole, tlačítko akce, tlačítko rozevíracího seznamu a rozevírací nabídku.  
  
 Vyhledávací pole může být jedna z několika státy, z nichž některé se vzájemně vylučují:  
  
- "Zaměřuje" nebo "bez fokusu" odkazuje na Určuje, jestli je kurzor v textovém poli.  
  
- "Aktivní" nebo "neaktivní" odkazuje na tom, jestli uživatel zadal vyhledávací dotaz v textovém poli.  
  
- "Při najetí myší" znamená, že uživatel má moused prostřednictvím vyhledávacího pole pomocí myši (Tento stav potlačí všechny ostatní stavy).  
  
- "Zakázáno" znamená, že funkce vyhledávání je vypnuté pro aktuální kontext.  
  
  ![Vyhledávací pole Redline](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 – 110_SearchBoxRedline")  
  
  Použití...  
  Při navrhování vlastní vyhledávací pole.  
  
  Nepoužívejte...  
  - pro všechno, co není vyhledávací pole.  
  
- pro všechno, co, které nechcete, aby vždy tak, aby odpovídaly hledání pole uživatelského rozhraní.  
  
  **Zaměřil**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hledat zaměření na vstupní pole](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 – 111_SearchInputFieldFocused")<br /><br /> **Vstupní pole**|Pozadí|`SearchControl.FocusedBackground`|  
|![Hledat zaměření na vstupní pole](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 – 111_SearchInputFieldFocused")<br /><br /> **Vstupní pole**|Popředí (Text)|`SearchControl.FocusedBackground`|  
|![Hledat zaměření na vstupní pole](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 – 111_SearchInputFieldFocused")<br /><br /> **Vstupní pole**|Ohraničení|`SearchControl.FocusedBorder`|  
|![Hledat zaměření na vstupní pole](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 – 111_SearchInputFieldFocused")<br /><br /> **Vstupní pole**|Oddělovač|`SearchControl.FocusedDropDownSeparator`|  
|![Fokus – tlačítko akce hledání](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 – 112_SearchActionButtonFocused")<br /><br /> **Tlačítko akce**|Pozadí|Žádná|  
|![Fokus – tlačítko akce hledání](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 – 112_SearchActionButtonFocused")<br /><br /> **Tlačítko akce**|Popředí (piktogram vyhledávání)|`SearchControl.SearchGlyph`|  
|![Fokus – tlačítko akce hledání](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 – 112_SearchActionButtonFocused")<br /><br /> **Tlačítko akce**|Popředí (Zastavit piktogram)|`SearchControl.StopGlyph`|  
|![Fokus – tlačítko akce hledání](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 – 112_SearchActionButtonFocused")<br /><br /> **Tlačítko akce**|Popředí (Vymazat piktogram)|`SearchControl.ClearGlyph`|  
|![Fokus – tlačítko akce hledání](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 – 112_SearchActionButtonFocused")<br /><br /> **Tlačítko akce**|Ohraničení|neuvedeno|  
|![Hledání –&#45;tlačítko rozevíracího seznamu](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 – 113_SearchDropdownButtonFocused")<br /><br /> **Tlačítko rozevíracího seznamu**|Pozadí|`SearchControl.FocusedDropDownButton`|  
|![Hledání –&#45;tlačítko rozevíracího seznamu](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 – 113_SearchDropdownButtonFocused")<br /><br /> **Tlačítko rozevíracího seznamu**|Popředí (piktogram)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Hledání –&#45;tlačítko rozevíracího seznamu](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 – 113_SearchDropdownButtonFocused")<br /><br /> **Tlačítko rozevíracího seznamu**|Ohraničení|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Bez fokusu**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hledat vstupní pole nevybrané](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 – 114_SearchInputFieldUnfocused")<br /><br /> **Aktivní vstupní pole**|Pozadí|`SearchControl.SearchActiveBackground`|  
|![Hledat vstupní pole nevybrané](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 – 114_SearchInputFieldUnfocused")<br /><br /> **Aktivní vstupní pole**|Popředí (Text)|`SearchControl.SearchActiveBackground`|  
|![Hledat vstupní pole nevybrané](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 – 114_SearchInputFieldUnfocused")<br /><br /> **Aktivní vstupní pole**|Ohraničení|`SearchControl.UnfocusedBorder`|  
|![Hledat vstupní pole nevybrané](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 – 114_SearchInputFieldUnfocused")<br /><br /> **Aktivní vstupní pole**|Oddělovač|`SearchControl.DropDownSeparator`|  
|![Hledat vstupní pole nevybrané a neaktivní](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Neaktivní vstupní pole**|Pozadí|`SearchControl.Unfocused`|  
|![Hledat vstupní pole nevybrané a neaktivní](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Neaktivní vstupní pole**|Popředí (Text)|`SearchControl.Unfocused`|  
|![Hledat vstupní pole nevybrané a neaktivní](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Neaktivní vstupní pole**|Ohraničení|`SearchControl.UnfocusedBorder`|  
|![Hledat vstupní pole nevybrané a neaktivní](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Neaktivní vstupní pole**|Oddělovač|`SearchControl.DropDownSeparator`|  
|![Tlačítko akce hledání nevybrané](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 – 115_SearchActionButtonUnfocused")<br /><br /> **Tlačítko akce**|Pozadí|neuvedeno|  
|![Tlačítko akce hledání nevybrané](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 – 115_SearchActionButtonUnfocused")<br /><br /> **Tlačítko akce**|Popředí (piktogram vyhledávání)|`SearchControl.SearchGlyph`|  
|![Tlačítko akce hledání nevybrané](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 – 115_SearchActionButtonUnfocused")<br /><br /> **Tlačítko akce**|Popředí (Zastavit piktogram)|`SearchControl.StopGlyph`|  
|![Tlačítko akce hledání nevybrané](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 – 115_SearchActionButtonUnfocused")<br /><br /> **Tlačítko akce**|Popředí (Vymazat piktogram)|`SearchControl.ClearGlyph`|  
|![Tlačítko akce hledání nevybrané](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 – 115_SearchActionButtonUnfocused")<br /><br /> **Tlačítko akce**|Ohraničení|neuvedeno|  
|![Tlačítko pro&#45;hledání v nevybraném umístění](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 – 116_SearchDropdownButtonUnfocused")<br /><br /> **Tlačítko rozevíracího seznamu**|Pozadí|`SearchControl.UnfocusedDropDownButton`|  
|![Tlačítko pro&#45;hledání v nevybraném umístění](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 – 116_SearchDropdownButtonUnfocused")<br /><br /> **Tlačítko rozevíracího seznamu**|Popředí (piktogram)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Tlačítko pro&#45;hledání v nevybraném umístění](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 – 116_SearchDropdownButtonUnfocused")<br /><br /> **Tlačítko rozevíracího seznamu**|Ohraničení|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknutí tlačítka akce hledání](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Tlačítko akce**|Pozadí|`SearchControl.ActionButtonMouseDown`|  
|![Stisknutí tlačítka akce hledání](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Tlačítko akce**|Popředí (piktogram)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Stisknutí tlačítka akce hledání](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Tlačítko akce**|Ohraničení|`SearchControl.ActionButtonMouseDownBorder`|  
|![Stisknutí&#45;tlačítka pro hledání v rozevíracím seznamu](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Tlačítko rozevíracího seznamu**|Pozadí|`SearchControl.MouseDownDropDownButton`|  
|![Stisknutí&#45;tlačítka pro hledání v rozevíracím seznamu](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Tlačítko rozevíracího seznamu**|Popředí (piktogram)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Stisknutí&#45;tlačítka pro hledání v rozevíracím seznamu](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Tlačítko rozevíracího seznamu**|Ohraničení|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Zvýrazněný (jenom text)**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zvýraznit vstupní pole pro hledání](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 – 120_SearchInputFieldHighlight")<br /><br /> **Vstupní pole s zvýrazněným textem**|Pozadí|`SearchControl.Selection`|  
|![Zvýraznit vstupní pole pro hledání](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 – 120_SearchInputFieldHighlight")<br /><br /> **Vstupní pole s zvýrazněným textem**|Popředí (Text)|`SearchControl.FocusedBackground`|  
|![Zvýraznit vstupní pole pro hledání](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 – 120_SearchInputFieldHighlight")<br /><br /> **Vstupní pole s zvýrazněným textem**|Ohraničení|Žádná|  
|![Zvýraznit vstupní pole pro hledání](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 – 120_SearchInputFieldHighlight")<br /><br /> **Vstupní pole s zvýrazněným textem**|Oddělovač|`SearchControl.FocusedDropDownSeparator`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hledání vstupního pole je zakázané.](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 – 121_SearchInputFieldDisabled")<br /><br /> **Vstupní pole**|Pozadí|`SearchControl.Disabled`|  
|![Hledání vstupního pole je zakázané.](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 – 121_SearchInputFieldDisabled")<br /><br /> **Vstupní pole**|Popředí (Text)|`SearchControl.Disabled`|  
|![Hledání vstupního pole je zakázané.](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 – 121_SearchInputFieldDisabled")<br /><br /> **Vstupní pole**|Ohraničení|`SearchControl.DisabledBorder`|  
|![Hledání vstupního pole je zakázané.](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 – 121_SearchInputFieldDisabled")<br /><br /> **Vstupní pole**|Oddělovač|`SearchControl.DropDownSeparator`|  
|![Tlačítko akce hledání je zakázané.](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 – 122_SearchActionButtonDisabled")<br /><br /> **Tlačítko akce**|Pozadí|Žádná|  
|![Tlačítko akce hledání je zakázané.](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 – 122_SearchActionButtonDisabled")<br /><br /> **Tlačítko akce**|Popředí (piktogram)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Tlačítko akce hledání je zakázané.](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 – 122_SearchActionButtonDisabled")<br /><br /> **Tlačítko akce**|Ohraničení|Žádná|  
|![Tlačítko Hledat&#45;v rozevíracím seznamu zakázáno](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 – 123_SearchDropdownButtonDisabled")<br /><br /> **Tlačítko rozevíracího seznamu**|Pozadí|Žádná|  
|![Tlačítko Hledat&#45;v rozevíracím seznamu zakázáno](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 – 123_SearchDropdownButtonDisabled")<br /><br /> **Tlačítko rozevíracího seznamu**|Popředí (piktogram)|`SearchControl.DisabledDownButtonGlyph`|  
|![Tlačítko Hledat&#45;v rozevíracím seznamu zakázáno](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 – 123_SearchDropdownButtonDisabled")<br /><br /> **Tlačítko rozevíracího seznamu**|Ohraničení|Žádná|  
  
##### <a name="search-drop-down-lists"></a>Hledání rozevírací seznamy  
 Vyhledávací pole rozevírací nabídce má potenciál být o něco složitější než ostatní rozevíracích nabídek v sadě Visual Studio. "Navrhované hledání" a "možnosti hledání" oddílů se může objevit samostatně nebo společně v nabídce a každý z nich jsou zobrazeny samostatně. Řádek také odděluje tyto dva oddíly, když jsou uvedeny společně a ohraničení kolem celého rozevírací nabídky.  
  
 ![Hledat rozevírací&#45;seznam Redline](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 – 124_SearchDropdownRedline")  
  
Použití...  
- Pokud při vytváření vlastních vyhledávacích rozevíracím seznamu.  

- správný token názvy správný seznam součástí.  

Nepoužívejte...  
- pro rozevíracích seznamů, které se zobrazí v jiném kontextu.  

- v libovolné na pozadí a popředí jinými než která byla specifikována.  
  
  **Výchozí (žádné jiné stavy)**  
  
|Prvek|Název tokenu: Category.color|  
|-------------|--------------------------------|  
|Ohraničení|`SearchControl.PopupBorder`|  
|Oddělovač|`SearchControl.PopupSectionHeaderSeparator`|  
|Stín|`Environment.DropShadowBackground`|  
  
 **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Doporučené hledání](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 – 125_SearchSuggested")<br /><br /> **Navrhovaná hledání**|Pozadí|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Doporučené hledání](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 – 125_SearchSuggested")<br /><br /> **Navrhovaná hledání**|Popředí (Text)|`SearchControl.PopupItemText`|  
|![Zaškrtávací políčko hledání](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 – 126_SearchCheckbox")<br /><br /> **Možnosti hledání (zaškrtávací políčko)**|Pozadí|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Možnosti hledání](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 – 127_SearchOptions")<br /><br /> **Možnosti hledání (odkaz)**|Pozadí|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Zaškrtávací políčko hledání](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 – 126_SearchCheckbox")<br /><br /> **Možnosti hledání (zaškrtávací políčko)**|Popředí (zaškrtávací políčko text)|`SearchControl.PopupCheckboxText`|  
|![Možnosti hledání](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 – 127_SearchOptions")<br /><br /> **Možnosti hledání (odkaz)**|Popředí (zaškrtávací políčko text)|`SearchControl.PopupCheckboxText`|  
|![Zaškrtávací políčko hledání](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 – 126_SearchCheckbox")<br /><br /> **Možnosti hledání (zaškrtávací políčko)**|Popředí (text odkazu)|`SearchControl.PopupButtonText`|  
|![Možnosti hledání](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 – 127_SearchOptions")<br /><br /> **Možnosti hledání (odkaz)**|Popředí (text odkazu)|`SearchControl.PopupButtonText`|  
|![Zaškrtávací políčko hledání](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 – 126_SearchCheckbox")<br /><br /> **Možnosti hledání (zaškrtávací políčko)**|Pozadí záhlaví|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Možnosti hledání](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 – 127_SearchOptions")<br /><br /> **Možnosti hledání (odkaz)**|Pozadí záhlaví|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Zaškrtávací políčko hledání](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 – 126_SearchCheckbox")<br /><br /> **Možnosti hledání (zaškrtávací políčko)**|Popředí (text záhlaví)|`SearchControl.PopupSectionHeaderText`|  
|![Možnosti hledání](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 – 127_SearchOptions")<br /><br /> **Možnosti hledání (odkaz)**|Popředí (text záhlaví)|`SearchControl.PopupSectionHeaderText`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hledání navrhované při najetí myší](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 – 128_SearchSuggestedHover")<br /><br /> **Navrhovaná hledání**|Pozadí|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Hledání navrhované při najetí myší](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 – 128_SearchSuggestedHover")<br /><br /> **Navrhovaná hledání**|Popředí (Text)|`SearchControl.PopupMouseOverItemText`|  
|![Hledání navrhované při najetí myší](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 – 128_SearchSuggestedHover")<br /><br /> **Navrhovaná hledání**|Ohraničení|`SearchControl.PopupControlMouseOverBorder`|  
|![Zaškrtávací políčko pro hledání při najetí myší](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 – 129_SearchCheckboxHover")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Pozadí|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Možnosti hledání při najetí myší](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 – 130_SearchOptionsHover")<br /><br /> **Možnosti hledání**|Pozadí|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Zaškrtávací políčko pro hledání při najetí myší](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 – 129_SearchCheckboxHover")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Popředí (zaškrtávací políčko text)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Možnosti hledání při najetí myší](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 – 130_SearchOptionsHover")<br /><br /> **Možnosti hledání**|Popředí (zaškrtávací políčko text)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Zaškrtávací políčko pro hledání při najetí myší](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 – 129_SearchCheckboxHover")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Popředí (text odkazu)|`SearchControl.PopupButtonMouseDownText`|  
|![Možnosti hledání při najetí myší](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 – 130_SearchOptionsHover")<br /><br /> **Možnosti hledání**|Popředí (text odkazu)|`SearchControl.PopupButtonMouseDownText`|  
|![Zaškrtávací políčko pro hledání při najetí myší](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 – 129_SearchCheckboxHover")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Ohraničení|`SearchControl.PopupControlMouseOverBorder`|  
|![Možnosti hledání při najetí myší](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 – 130_SearchOptionsHover")<br /><br /> **Možnosti hledání**|Ohraničení|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hledání navrhovaného stisknutí](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 – 131_SearchSuggestedPressed")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Pozadí zaškrtávacího políčka|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Stisknuté možnosti hledání](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 – 132_SearchOptionsPressed")<br /><br /> **Možnosti hledání**|Pozadí zaškrtávacího políčka|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Hledání navrhovaného stisknutí](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 – 131_SearchSuggestedPressed")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Pozadí zaškrtávacího políčka|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Stisknuté možnosti hledání](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 – 132_SearchOptionsPressed")<br /><br /> **Možnosti hledání**|Pozadí zaškrtávacího políčka|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Hledání navrhovaného stisknutí](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 – 131_SearchSuggestedPressed")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Popředí (zaškrtávací políčko text)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Stisknuté možnosti hledání](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 – 132_SearchOptionsPressed")<br /><br /> **Možnosti hledání**|Popředí (zaškrtávací políčko text)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Hledání navrhovaného stisknutí](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 – 131_SearchSuggestedPressed")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Odkaz na pozadí|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Stisknuté možnosti hledání](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 – 132_SearchOptionsPressed")<br /><br /> **Možnosti hledání**|Odkaz na pozadí|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Přestože nepoužívá moderní uživatelské rozhraní s motivem, existují Přechodové zarážky a hodnoty pro tato na pozadí.|  
|![Hledání navrhovaného stisknutí](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 – 131_SearchSuggestedPressed")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Popředí (text odkazu)|`SearchControl.PopupButtonMouseDownText`|  
|![Stisknuté možnosti hledání](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 – 132_SearchOptionsPressed")<br /><br /> **Možnosti hledání**|Popředí (text odkazu)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Hypertextový odkaz  
 Hypertextový odkaz je jeden ovládací prvek, který nemá dvojici popředí nebo pozadí. Ve všech případech použijte barvu popředí hypertextový odkaz, který se zobrazí správně na tmavě šedou a bílé pozadí. Pokud nepoužijete token barvu ovládacího prvku hypertextový odkaz, zobrazí se výchozí systémové barvy pro "stisknutí", "který blikat červené. To je signál, že ovládací prvek není pomocí tokenu barva správné prostředí.  
  
 ![Hypertextový odkaz Redline](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 – 133_HyperlinkRedline")  
  
 Použití...  
 Když je potřeba vytvořit vlastní hypertextový odkaz.  
  
 Nepoužívejte...  
 pro všechno, co není hypertextový odkaz.  
  
 **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Výchozí hypertextový odkaz](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 – 134_Hyperlink")|Popředí (Text)|`Environment.PanelHyperlink`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hypertextový odkaz při najetí myší](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 – 135_HyperlinkHover")|Popředí (Text)|`Environment.PanelHyperlinkHover`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hypertextový odkaz byl stisknut](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 – 136_HyperlinkPressed")|Popředí (Text)|`Environment.PanelHyperlinkPressed`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hypertextový odkaz zakázán](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 – 137_HyperlinkDisabled")|Popředí (Text)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Informační panel  
 Infobars se používají k poskytují další informace o daném kontextu a vždy se zobrazí v horní části okna dokumentu nebo panelu nástrojů.  
  
 ![Redline informačního panelu](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 – 138_InfobarRedline")  
  
 Použití...  
 Při vytváření vlastní infobars.  
  
 Nepoužívejte...  
 pro prvky uživatelského rozhraní, které nejsou podobný informačního panelu.  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Řádku](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 – 139_Infobar")<br /><br /> **Řádku**|Pozadí|`Environment.InfoBackground`|  
|![Řádku](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 – 139_Infobar")<br /><br /> **Řádku**|Popředí (Text)|`Environment.InfoText`|  
|![Řádku](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 – 139_Infobar")<br /><br /> **Řádku**|Ohraničení|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Posuvník  
 Posuvníky jsou ve stylu prostředím sady Visual Studio a nebude nutné použít motiv. Ale můžete se rozhodnout, že chcete využít barvy použité v posuvníky tak, aby vaše uživatelské rozhraní se vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.  
  
 ![Redline posuvníku](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 – 140_ScrollbarRedline")  
  
 Použití...  
 Pokud při vytváření uživatelského rozhraní, které chcete odpovídá posuvníky sady Visual Studio.  
  
 Nepoužívat...  
 pro cokoli, co nechcete, aby se rozhraní ScrollBar vždy shodovalo.  
  
 **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Posuvník](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 – 141_Scrollbar")<br /><br /> **Posuvník**|Posuvník|`Environment.ScrollBarBackground`|  
|![Posuvník](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 – 141_Scrollbar")<br /><br /> **Posuvník**|Popředí (palce)|`Environment.ScrollBarThumbBackground`|  
|![Šipka posuvníku](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 – 142_ScrollbarArrow")<br /><br /> **Šipka posuvníku**|Pozadí|`Environment.ScrollBarArrowBackground`<br /><br /> Nastavte stejnou barvu jako posuvníku.|  
|![Šipka posuvníku](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 – 142_ScrollbarArrow")<br /><br /> **Šipka posuvníku**|Popředí (piktogram)|`Environment.ScrollBarArrowGlyph`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Při najetí myší přejít na posuvník](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 – 143_ScrollbarHover")<br /><br /> **Posuvník**|Posuvník|`Environment.ScrollBarBackground`|  
|![Při najetí myší přejít na posuvník](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 – 143_ScrollbarHover")<br /><br /> **Posuvník**|Popředí (palce)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![Šipka posuvníku při najetí myší](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 – 144_ScrollbarArrowHover")<br /><br /> **Šipka posuvníku**|Pozadí|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Nastavte stejnou barvu jako posuvníku.|  
|![Šipka posuvníku při najetí myší](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 – 144_ScrollbarArrowHover")<br /><br /> **Šipka posuvníku**|Popředí (piktogram)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknutí posuvníku](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 – 145_ScrollbarPressed")<br /><br /> **Posuvník**|Posuvník|`Environment.ScrollBarBackground`|  
|![Stisknutí posuvníku](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 – 145_ScrollbarPressed")<br /><br /> **Posuvník**|Popředí (palce)|`Environment.ScrollBarThumbPressedBackground`|  
|![Stisknutí šipky posuvníku](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 – 146_ScrollbarArrowPressed")<br /><br /> **Šipka posuvníku**|Pozadí|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Nastavte stejnou barvu jako posuvník.|  
|![Stisknutí šipky posuvníku](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 – 146_ScrollbarArrowPressed")<br /><br /> **Šipka posuvníku**|Popředí (piktogram)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="BKMK_TreeView"></a>Stromové zobrazení  
 Několika okny nástrojů, včetně Průzkumníka řešení, Průzkumníka serveru a zobrazení tříd, implementace hierarchické organizační schéma, jejichž barvy se řídí názvy barev v kategorii prvku TreeView. Barvy textu a pozadí mají všechny položky ve stromovém zobrazení. Položky, které mají vnořené podřízené prvky mají také glyfy označující, zda položka rozbalená nebo sbalená.  
  
 ![Redline zobrazení stromu](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 – 147_TreeViewRedline")  
  
 Použití...  
 kdekoli potřebujete implementovat hierarchické organizační zobrazení.  
  
Nepoužívejte...  
- pro všechno, co to není podobné zobrazení stromu.  

- v libovolné na pozadí a popředí jinými než která byla specifikována.  
  
  **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stromové zobrazení](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 – 148_TreeView")|Pozadí|`TreeView.Background`|  
|![Stromové zobrazení](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 – 148_TreeView")|Popředí (Text)|`TreeView.Background`|  
|![Stromové zobrazení](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 – 148_TreeView")|Popředí (piktogram)|`TreeView.Glyph`|  
|![Stromové zobrazení](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 – 148_TreeView")|Ohraničení|Žádná|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stromové zobrazení při najetí myší](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 – 149_TreeViewHover")|Pozadí|`TreeView.Background`|  
|![Stromové zobrazení při najetí myší](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 – 149_TreeViewHover")|Popředí (Text)|`TreeView.Background`|  
|![Stromové zobrazení při najetí myší](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 – 149_TreeViewHover")|Popředí (piktogram)|`TreeView.GlyphMouseOver`|  
|![Stromové zobrazení při najetí myší](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 – 149_TreeViewHover")|Ohraničení|Žádná|  
  
 **Přetáhnout**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![DragOver zobrazení stromu](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 – 150_TreeViewDragOver")|Pozadí|`TreeView.DragOverItem`|  
|![DragOver zobrazení stromu](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 – 150_TreeViewDragOver")|Popředí (Text)|`TreeView.DragOverItem`|  
|![DragOver zobrazení stromu](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 – 150_TreeViewDragOver")|Popředí (piktogram)|`TreeView.DragOverItemGlyph`|  
|![DragOver zobrazení stromu](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 – 150_TreeViewDragOver")|Ohraničení|Žádná|  
  
 **Vyberte**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaměření stromového zobrazení](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 – 151_TreeViewFocused")<br /><br /> **Zaměřil**|Pozadí|`TreeView.SelectedItemActive`|  
|![Zaměření stromového zobrazení](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 – 151_TreeViewFocused")<br /><br /> **Zaměřil**|Popředí (Text)|`TreeView.SelectedItemActive`|  
|![Zaměření stromového zobrazení](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 – 151_TreeViewFocused")<br /><br /> **Zaměřil**|Popředí (piktogram)|`TreeView.SelectedItemActiveGlyph`|  
|![Zaměření stromového zobrazení](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 – 151_TreeViewFocused")<br /><br /> **Zaměřil**|Ohraničení|`TreeView.FocusVisualBorder`|  
|![Stromové zobrazení není vybrané.](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 – 152_TreeViewUnfocused")<br /><br /> **Bez fokusu**|Pozadí|`TreeView.SelectedItemInactive`|  
|![Stromové zobrazení není vybrané.](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 – 152_TreeViewUnfocused")<br /><br /> **Bez fokusu**|Popředí (Text)|`TreeView.SelectedItemInactive`|  
|![Stromové zobrazení není vybrané.](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 – 152_TreeViewUnfocused")<br /><br /> **Bez fokusu**|Popředí (piktogram)|`TreeView.SelectedItemInactiveGlyph`|  
|![Stromové zobrazení není vybrané.](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 – 152_TreeViewUnfocused")<br /><br /> **Bez fokusu**|Ohraničení|Žádná|  
  
 **Najeďte myší na vybrané**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stromové zobrazení zaměřené na najetí myší](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 – 153_TreeViewFocusedHover")<br /><br /> **Zaměřil**|Pozadí|`TreeView.SelectedItemActive`|  
|![Stromové zobrazení zaměřené na najetí myší](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 – 153_TreeViewFocusedHover")<br /><br /> **Zaměřil**|Popředí (Text)|`TreeView.SelectedItemActive`|  
|![Stromové zobrazení zaměřené na najetí myší](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 – 153_TreeViewFocusedHover")<br /><br /> **Zaměřil**|Popředí (piktogram)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Stromové zobrazení zaměřené na najetí myší](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 – 153_TreeViewFocusedHover")<br /><br /> **Zaměřil**|Ohraničení|Žádná`TreeView.FocusVisualBorder`|  
|![Po najetí myší se stromové zobrazení nezaměřuje](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 – 154_TreeViewUnfocusedHover")<br /><br /> **Bez fokusu**|Pozadí|`TreeView.SelectedItemInactive`|  
|![Po najetí myší se stromové zobrazení nezaměřuje](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 – 154_TreeViewUnfocusedHover")<br /><br /> **Bez fokusu**|Popředí (Text)|`TreeView.SelectedItemInactive`|  
|![Po najetí myší se stromové zobrazení nezaměřuje](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 – 154_TreeViewUnfocusedHover")<br /><br /> **Bez fokusu**|Popředí (piktogram)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Po najetí myší se stromové zobrazení nezaměřuje](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 – 154_TreeViewUnfocusedHover")<br /><br /> **Bez fokusu**|Ohraničení|Žádná|  
  
#### <a name="button-controls"></a>ovládací prvky tlačítek  
 ![Redline ovládacího prvku tlačítko](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 – 155_ButtonControlRedline")  
  
 Použití...  
 u tlačítek v dokumentu kontejneru, kterou chcete integrovat s motivů aplikace Visual Studio (světla, tmavý, modrá nebo motiv s vysokým kontrastem systému).  
  
 Nepoužívejte...  
 u tlačítek, které se zobrazí na vlastní pozadí, který není součástí sady Visual Studio motivu.  
  
 **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko](../extensibility/ux-guidelines/media/0303-156-button.png "0303 – 156_Button")|Tlačítko|`CommonControls.Button`|  
|![Tlačítko](../extensibility/ux-guidelines/media/0303-156-button.png "0303 – 156_Button")|Ohraničení tlačítka|`CommonControls.ButtonBorder`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko je zakázané.](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 – 157_ButtonDisabled")|Tlačítko|`CommonControls.ButtonDisabled`|  
|![Tlačítko je zakázané.](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 – 157_ButtonDisabled")|Ohraničení tlačítka|`CommonControls.ButtonBorderDisabled`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko při najetí myší](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 – 158_ButtonHover")|Tlačítko|`CommonControls.ButtonHover`|  
|![Tlačítko při najetí myší](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 – 158_ButtonHover")|Ohraničení tlačítka|`CommonControls.ButtonBorderHover`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknutí tlačítka](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 – 159_ButtonPressed")|Tlačítko|`CommonControls.ButtonPressed`|  
|![Stisknutí tlačítka](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 – 159_ButtonPressed")|Ohraničení tlačítka|`CommonControls.ButtonBorderPressed`|  
  
 **Zaměřil**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Fokus – tlačítko](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 – 160_ButtonFocused")|Tlačítko|`CommonControls.ButtonFocused`|  
|![Fokus – tlačítko](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 – 160_ButtonFocused")|Ohraničení tlačítka|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Ovládací prvky zaškrtávacích políček  
 ![Zaškrtávací políčko Redline](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 – 161_CheckboxRedline")  
  
 Použití...  
 pro ovládací prvky zaškrtávacích políček dobře obsažených v dokumentu.  
  
 Nepoužívejte...  
 pro uživatelské rozhraní, který není ovládací prvek zaškrtávací políčko.  
  
 **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaškrtávací políčko](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 – 162_Checkbox")|Pozadí|`CommonControls.CheckBoxBackground`|  
|![Zaškrtávací políčko](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 – 162_Checkbox")|Ohraničení|`CommonControls.CheckBoxBorder`|  
|![Zaškrtávací políčko](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 – 162_Checkbox")|Text|`CommonControls.CheckBoxText`|  
|![Zaškrtávací políčko](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 – 162_Checkbox")|Piktogram|`CommonControls.CheckBoxGlyph`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaškrtávací políčko zakázáno](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 – 163_CheckboxDisabled")|Pozadí|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Zaškrtávací políčko zakázáno](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 – 163_CheckboxDisabled")|Ohraničení|`CommonControls.CheckBoxBorderDisabled`|  
|![Zaškrtávací políčko zakázáno](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 – 163_CheckboxDisabled")|Text|`CommonControls.CheckBoxTextDisabled`|  
|![Zaškrtávací políčko zakázáno](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 – 163_CheckboxDisabled")|Piktogram|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaškrtávací políčko při najetí myší](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 – 164_CheckboxHover")|Pozadí|`CommonControls.CheckBoxBackgroundHover`|  
|![Zaškrtávací políčko při najetí myší](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 – 164_CheckboxHover")|Ohraničení|`CommonControls.CheckBoxBorderHover`|  
|![Zaškrtávací políčko při najetí myší](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 – 164_CheckboxHover")|Text|`CommonControls.CheckBoxTextHover`|  
|![Zaškrtávací políčko při najetí myší](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 – 164_CheckboxHover")|Piktogram|`CommonControls.CheckBoxGlyphHover`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknuté políčko](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 – 165_CheckboxPressed")|Pozadí|`CommonControls.CheckBoxBackgroundPressed`|  
|![Stisknuté políčko](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 – 165_CheckboxPressed")|Ohraničení|`CommonControls.CheckBoxBorderPressed`|  
|![Stisknuté políčko](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 – 165_CheckboxPressed")|Text|`CommonControls.CheckBoxTextPressed`|  
|![Stisknuté políčko](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 – 165_CheckboxPressed")|Piktogram|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Zaměřil**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaměření na zaškrtávací políčko](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 – 166_CheckboxFocused")|Pozadí|`CommonControls.CheckBoxBackgroundFocused`|  
|![Zaměření na zaškrtávací políčko](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 – 166_CheckboxFocused")|Ohraničení|`CommonControls.CheckBoxBorderFocused`|  
|![Zaměření na zaškrtávací políčko](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 – 166_CheckboxFocused")|Text|`CommonControls.CheckBoxTextFocused`|  
|![Zaměření na zaškrtávací políčko](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 – 166_CheckboxFocused")|Piktogram|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Přetáhněte pole nebo pole se seznamem  
 ![Rozevírací&#45;seznam&#47;Redline pole se seznamem](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 – 167_DropDownComboBoxRedline")  
  
Použití...  
rozevírací seznamy a pole se seznamem polí, které jsou součástí dokumentu kontejneru.  

Nepoužívejte...  
- pro uživatelské rozhraní, která není pole rozevíracího seznamu nebo pole se seznamem.  

- pro [rozevírací](../misc/shared-colors.md#BKMK_CommandDropDown) [seznam nebo pole se seznamem](../misc/shared-colors.md#BKMK_CommandComboBox) na panelu příkazů.  
  
  **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozevírací&#45;pole&#47;se seznamem](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 – 168_DropDownComboBox")|Pozadí|`CommonControls.ComboBoxBackground`|  
|![Rozevírací&#45;pole&#47;se seznamem](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 – 168_DropDownComboBox")|Ohraničení|`CommonControls.ComboBoxBorder`|  
|![Rozevírací&#45;pole&#47;se seznamem](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 – 168_DropDownComboBox")|Text|`CommonControls.ComboBoxText`|  
|![Rozevírací&#45;pole&#47;se seznamem](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 – 168_DropDownComboBox")|Oddělovač|`CommonControls.ComboBoxSeparator`|  
|![Rozevírací&#45;pole&#47;se seznamem](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 – 168_DropDownComboBox")|Piktogram|`CommonControls.ComboBoxGlyph`|  
|![Rozevírací&#45;pole&#47;se seznamem](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 – 168_DropDownComboBox")|Piktogram na pozadí|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozevírací&#45;seznam&#47;se zakázal.](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 – 169_DropDownComboBoxDisabled")|Pozadí|`CommonControls.ComboBoxBackgroundDisabled`|  
|![Rozevírací&#45;seznam&#47;se zakázal.](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 – 169_DropDownComboBoxDisabled")|Ohraničení|`CommonControls.ComboBoxBorderDisabled`|  
|![Rozevírací&#45;seznam&#47;se zakázal.](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 – 169_DropDownComboBoxDisabled")|Text|`CommonControls.ComboBoxTextDisabled`|  
|![Rozevírací&#45;seznam&#47;se zakázal.](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 – 169_DropDownComboBoxDisabled")|Oddělovač|`CommonControls.ComboBoxSeparatorDisabled`|  
|![Rozevírací&#45;seznam&#47;se zakázal.](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 – 169_DropDownComboBoxDisabled")|Piktogram|`CommonControls.ComboBoxGlyphDisabled`|  
|![Rozevírací&#45;seznam&#47;se zakázal.](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 – 169_DropDownComboBoxDisabled")|Piktogram na pozadí|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozevírací&#45;pole&#47;se seznamem při najetí myší](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 – 170_DropDownComboBoxHover")|Pozadí|`CommonControls.ComboBoxBackgroundHover`|  
|![Rozevírací&#45;pole&#47;se seznamem při najetí myší](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 – 170_DropDownComboBoxHover")|Ohraničení|`CommonControls.ComboBoxBorderHover`|  
|![Rozevírací&#45;pole&#47;se seznamem při najetí myší](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 – 170_DropDownComboBoxHover")|Text|`CommonControls.ComboBoxTextHover`|  
|![Rozevírací&#45;pole&#47;se seznamem při najetí myší](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 – 170_DropDownComboBoxHover")|Oddělovač|`CommonControls.ComboBoxSeparatorHover`|  
|![Rozevírací&#45;pole&#47;se seznamem při najetí myší](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 – 170_DropDownComboBoxHover")|Piktogram|`CommonControls.ComboBoxGlyphHover`|  
|![Rozevírací&#45;pole&#47;se seznamem při najetí myší](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 – 170_DropDownComboBoxHover")|Piktogram na pozadí|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknuté políčko rozevíracího&#45;pole&#47;se seznamem](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 – 171_DropDownComboBoxPressed")|Pozadí|`CommonControls.ComboBoxBackgroundPressed`|  
|![Stisknuté políčko rozevíracího&#45;pole&#47;se seznamem](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 – 171_DropDownComboBoxPressed")|Ohraničení|`CommonControls.ComboBoxBorderPressed`|  
|![Stisknuté políčko rozevíracího&#45;pole&#47;se seznamem](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 – 171_DropDownComboBoxPressed")|Text|`CommonControls.ComboBoxTextPressed`|  
|![Stisknuté políčko rozevíracího&#45;pole&#47;se seznamem](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 – 171_DropDownComboBoxPressed")|Oddělovač|`CommonControls.ComboBoxSeparatorPressed`|  
|![Stisknuté políčko rozevíracího&#45;pole&#47;se seznamem](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 – 171_DropDownComboBoxPressed")|Piktogram|`CommonControls.ComboBoxGlyphPressed`|  
|![Stisknuté políčko rozevíracího&#45;pole&#47;se seznamem](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 – 171_DropDownComboBoxPressed")|Piktogram na pozadí|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Zaměřil**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozevírací&#45;pole&#47;se seznamem podle fokusu](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 – 172_DropDownComboBoxFocused")|Pozadí|`CommonControls.ComboBoxBackgroundFocused`|  
|![Rozevírací&#45;pole&#47;se seznamem podle fokusu](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 – 172_DropDownComboBoxFocused")|Ohraničení|`CommonControls.ComboBoxBorderFocused`|  
|![Rozevírací&#45;pole&#47;se seznamem podle fokusu](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 – 172_DropDownComboBoxFocused")|Text|`CommonControls.ComboBoxTextFocused`|  
|![Rozevírací&#45;pole&#47;se seznamem podle fokusu](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 – 172_DropDownComboBoxFocused")|Oddělovač|`CommonControls.ComboBoxSeparatorFocused`|  
|![Rozevírací&#45;pole&#47;se seznamem podle fokusu](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 – 172_DropDownComboBoxFocused")|Piktogram|`CommonControls.ComboBoxGlyphFocused`|  
|![Rozevírací&#45;pole&#47;se seznamem podle fokusu](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 – 172_DropDownComboBoxFocused")|Piktogram na pozadí|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Výběr textového vstupu**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozevírací&#45;seznam&#47;pro zadání textu v poli se seznamem](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 – 173_DropDownComboBoxTextInput")|Zvýraznění|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Stisknuté – zobrazení položek seznamu**  
  
|Komponenta|Prvek|Název tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Pozadí|`CommonControls.ComboBoxListBackground`|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Pozadí|`CommonControls.ComboBoxListBackgroundHover`|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Pozadí|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Pozadí|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Ohraničení|`CommonControls.ComboBoxListBorder`|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Ohraničení|`CommonControls.ComboBoxListBorderHover`|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Ohraničení|`CommonControls.ComboBoxListBorderPressed`|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Ohraničení|`CommonControls.ComboBoxListBorderFocused`|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Text položky|`CommonControls.ComboBoxListItemText`|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Text položky|`CommonControls.ComboBoxListItemTextHover`|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Text položky|`CommonControls.ComboBoxListItemTextPressed`|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Text položky|`CommonControls.ComboBoxListItemTextFocused`|  
|![Rozevírací&#45;seznam&#47;pro zobrazení seznamu polí se seznamem](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")|Stín pozadí|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Ovládací prvky tabulkových dat (grid)  
 Ovládací prvky tabulkových dat, označované také jako ovládací prvky mřížky, jsou běžné ovládací prvky pro Visual Studio, která slouží k zobrazení velkého objemu dat ve více sloupcích. Ovládací prvky standardní tabulkových dat najdete na více místech v rámci sady Visual Studio: panel nástrojů Seznam chyb, sestavy IntelliTrace a zobrazení paměti haldy, mimo jiné. Vždy používejte standardní tabulková data ovládací prvky k dispozici. V některých výjimečných případech nemusí mít přístup k ovládacím prvkům standardní tabulková data. V těchto situacích nepoužívejte následující názvy token k zajištění, že vaše uživatelské rozhraní je konzistentní s jinými ovládacími prvky tabulková data v sadě Visual Studio.  
  
 ![Redline ovládacího &#40;prvku&#41; mřížky tabelárních dat](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 – 197_TabularDataGridControlRedline")  
  
 Použití...  
 pro tabulkové nebo ovládací prvky mřížky.  
  
 Nepoužívejte...  
 pro uživatelské rozhraní, který není ovládacího prvku tabulky nebo tabulky.  
  
##### <a name="column-headers"></a>Záhlaví sloupců  
 Záhlaví sloupců se skládají z na pozadí, ohraničení, text nadpisu a volitelné piktogram obvykle se používá pro mřížku je seřazený podle tohoto sloupce.  
  
|Stav|Prvek|Název tokenu: Category.color|  
|-----------|-------------|--------------------------------|  
|Výchozí|Pozadí|`Header.Default`|  
|Výchozí|Popředí (Text)|`Environment.CommandBarTextActive`|  
|Výchozí|Popředí (piktogram)|`Header.Glyph`|  
|Výchozí|Ohraničení|`Header.SeparatorLine`|  
|Při najetí myší|Pozadí|`Header.MouseOver`|  
|Při najetí myší|Popředí (Text)|`Environment.CommandBarTextHover`|  
|Při najetí myší|Popředí (piktogram)|`Header.MouseOverGlyph`|  
|Při najetí myší|Ohraničení|`Header.SeparatorLine`|  
|Stisknutí|Pozadí|`CommonControls.CheckBoxBackgroundPressed`|  
|Stisknutí|Popředí (Text)|`CommonControls.CheckBoxBorderPressed`|  
|Stisknutí|Popředí (piktogram)|`CommonControls.CheckBoxTextPressed`|  
|Stisknutí|Ohraničení|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Položky seznamu  
 Položky seznamu se skládají z na pozadí a obsah. Obsah může být text nebo ikonu.  
  
|Stav|Prvek|Název tokenu: Category.color|  
|-----------|-------------|--------------------------------|  
|Výchozí|Pozadí|Transparentní|  
|Výchozí|Popředí (Text)|`Environment.CommandBarTextActive`|  
|Výchozí|Ohraničení|Žádná|  
|Vybraná (aktivní)|Pozadí|`TreeView.SelectedItemActive`|  
|Vybraná (aktivní)|Popředí (Text)|`TreeView.SelectedItemActiveText`|  
|Vybraná (aktivní)|Ohraničení|Žádná|  
|Vybraná (neaktivní)|Pozadí|`TreeView.SelectedItemInactive`|  
|Vybraná (neaktivní)|Popředí (Text)|`TreeView.SelectedItemInactiveText`|  
|Vybraná (neaktivní)|Ohraničení|Žádná|  
  
### <a name="manifest-designer"></a>Návrhář manifestu  
 Nástroj Manifest Designer je navržená jako způsob, jak bylo snazší upravit soubor manifestu v projektech pro systém Windows 8 a Windows Phone 8. Neplatí žádné sdílené architektuře k dispozici pro použití, může být vhodné pro tak, aby odpovídala návrhu rozložení a barvy orientace/navigačních karet a celkovou strukturu. Další informace o podrobnostech rozložení naleznete v tématu [layout for Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Redline návrháře manifestu](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 – 175_ManifestDesignerRedline")  
  
Použití...  
- pro profesionální návrháře využívající, které jsou podobné pro Nástroj Manifest Designer.  

- místo použití běžných ovládacích prvků kartě v horní části editoru v rámci dokumentu kontejneru.  

Nepoužívejte...  
- Pokud máte víc než šest karet.  

- pro všechny uživatelské rozhraní, která není strukturované jako nástroj Manifest Designer.  
  
|Stav|Komponenta|Prvek|Název tokenu: Category.color|  
|-----------|---------------|-------------|--------------------------------|  
|Výchozí (vybrané)|Tabulátor|Pozadí|`ManifestDesigner.TabActive`|  
|Výchozí (vybrané)|Tabulátor|Ohraničení|Žádná|  
|Výchozí (vybrané)|Podokno s popisem|Pozadí|`ManifestDesigner.DescriptionPane`|  
|Výchozí (vybrané)|Stránka obsahu|Pozadí|`ManifestDesigner.Background`|  
|Výchozí (vybrané)|Stránka obsahu|Dialogové okno text pomocné rutiny|`ManifestDesigner.WatermarkText`<br /><br /> Tento název tokenu se neshoduje s jeho funkci.|  
|Non vybraná|Tabulátor|Pozadí|`ManifestDesigner.Tab.Inactive`|  
|Při najetí myší|Tabulátor|Pozadí|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Označování  
 Visual Studio podporuje označování, které umožňuje uživateli deklarovat prohledávatelná klíčová slova pro účely sledování. Například projektových manažerů a vývojářů může používat Team Foundation Server (TFS) k označení pracovních položek. Následující tabulky poskytují názvy barev pro vlastní značku i "Zavřít ikonu" šifra, která se zobrazí při najetí myší a vybraných států.  
  
 ![Označování Redline](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 – 176_TaggingRedline")  
  
 Použití...  
 pro uživatelské rozhraní, který podporuje označování.  
  
 Nepoužívejte...  
 u ostatních typů uživatelského rozhraní.  
  
#### <a name="tag"></a>Značka  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303 – 177_Tag")<br /><br /> **Výchozí**|Pozadí|`Tag.Background`|  
|![Tag](../extensibility/ux-guidelines/media/0303-177-tag.png "0303 – 177_Tag")<br /><br /> **Výchozí**|Popředí (Text)|`Tag.Background`|  
|![Označit při najetí myší](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 – 178_TagHover")<br /><br /> **Přesunutí**|Pozadí|`Tag.HoverBackground`|  
|![Označit při najetí myší](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 – 178_TagHover")<br /><br /> **Přesunutí**|Popředí (Text)|`Tag.HoverBackgroundText`|  
|![Stisknutí značky](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 – 179_TagPressed")<br /><br /> **Stisknete**|Pozadí|`Tag.PressedBackground`|  
|![Stisknutí značky](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 – 179_TagPressed")<br /><br /> **Stisknete**|Popředí (Text)|`Tag.PressedBackgroundText`|  
|![Vybraná značka](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 – 180_TagSelected")<br /><br /> **Vyberte**|Pozadí|`Tag.SelectedBackground`|  
|![Vybraná značka](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 – 180_TagSelected")<br /><br /> **Vyberte**|Popředí (Text)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Piktogram (ikonu pro zavření)  
 **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Glyf &#40;značky&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 – 181_TagGlyph")<br /><br /> **Výchozí (označit jako výchozí)**|Pozadí|neuvedeno|  
|![Glyf &#40;značky&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 – 181_TagGlyph")<br /><br /> **Výchozí (označit jako výchozí)**|Popředí (piktogram)|`Tag.TagHoverGlyph`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Označit &#40;glyf&#41; při najetí myší](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 – 182_TagGlyphHover")<br /><br /> **Najeďte myší (výchozí značka)**|Pozadí|`Tag.TagHoverGlyphHoverBackground`|  
|![Označit &#40;glyf&#41; při najetí myší](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 – 182_TagGlyphHover")<br /><br /> **Najeďte myší (výchozí značka)**|Popředí (piktogram)|`Tag.TagHoverGlyphHover`|  
|![Označit &#40;glyf&#41; při najetí myší](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 – 182_TagGlyphHover")<br /><br /> **Najeďte myší (výchozí značka)**|Ohraničení|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Stisknete**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknutí&#41; glyfu značky &#40;](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 – 183_TagGlyphPressed")<br /><br /> **Stisknuté (označit jako výchozí)**|Pozadí|`Tag.TagHoverGlyphPressedBackground`|  
|![Stisknutí&#41; glyfu značky &#40;](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 – 183_TagGlyphPressed")<br /><br /> **Stisknuté (označit jako výchozí)**|Popředí (piktogram)|`Tag.TagHoverGlyphPressed`|  
|![Stisknutí&#41; glyfu značky &#40;](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 – 183_TagGlyphPressed")<br /><br /> **Stisknuté (označit jako výchozí)**|Ohraničení|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Vybraná značka/výchozí hodnota glyfu**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vybraná značka](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 – 184_TagSelected")<br /><br /> **Výchozí (vybraná značka)**|Pozadí|neuvedeno|  
|![Vybraná značka](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 – 184_TagSelected")<br /><br /> **Výchozí (vybraná značka)**|Popředí (piktogram)|`Tag.TagSelectedGlyph`|  
  
 **Výběr značky/glyfy po ukázání**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Značka vybraná při najetí myší](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 – 185_TagSelectedHover")<br /><br /> **Najeďte myší (vybraná značka)**|Pozadí|`Tag.TagSelectedGlyphHoverBackground`|  
|![Značka vybraná při najetí myší](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 – 185_TagSelectedHover")<br /><br /> **Najeďte myší (vybraná značka)**|Popředí (piktogram)|`Tag.TagSelectedGlyphHover`|  
|![Značka vybraná při najetí myší](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 – 185_TagSelectedHover")<br /><br /> **Najeďte myší (vybraná značka)**|Ohraničení|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Vybraná značka/stisknutí glyfu**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknutá vybraná značka](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 – 186_TagSelectedPressed")<br /><br /> **Stisknuté (vybraná značka)**|Pozadí|`Tag.TagSelectedGlyphPressedBackground`|  
|![Stisknutá vybraná značka](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 – 186_TagSelectedPressed")<br /><br /> **Stisknuté (vybraná značka)**|Foreground(Glyph)|`Tag.TagSelectedGlyphPressed`|  
|![Stisknutá vybraná značka](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 – 186_TagSelectedPressed")<br /><br /> **Stisknuté (vybraná značka)**|Ohraničení|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Prostředí  
  
#### <a name="background"></a>Pozadí  
 Na pozadí prostředí se skládá ze dvou vrstev. Spodní vrstva je plnou barvu, která zahrnuje celou integrovaného vývojového prostředí. Horní vrstvě vejde v rámci příkazu polici a mezi kanálů automatického skrytí okna nástroje na levých a pravých okrajů integrovaného vývojového prostředí. Od verze Visual Studio 2013 pozadí vrstvy horní a dolní nastavené na stejnou barvu v motivy tmavý a světlý motiv.  
  
 ![Redline na pozadí prostředí](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 – 187_ShellBackgroundRedline")  
  
 Použití...  
 pro míst, na které můžete chtít, aby na pozadí prostředí sady Visual Studio.  
  
Nepoužívejte...  
- jako výplň místa, které nejsou na pozadí plochy.  

- na pozadí, na kterém chcete umístit prvky popředí.  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|Dolní vrstvy|Pozadí|`Environment.EnvironmentBackground`|  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|Vrstvu na nejvyšší úrovni|Pozadí<br /><br /> *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Vrstvu na nejvyšší úrovni|Pozadí<br /><br /> *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Vrstvu na nejvyšší úrovni|Pozadí<br /><br /> *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Vrstvu na nejvyšší úrovni|Pozadí<br /><br /> *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Příkaz police  
 Dvě sady token názvů, které se používají pro pozadí příkaz police: nastavit jeden kde je umístěn řádku nabídek a jeden pro kde panely příkazů nacházejí. Pruhový graf konkrétní příkaz má svůj vlastní pozadí hodnot barev, které jsou popsány podrobněji v oddílu "panel příkazů". Řádek nabídek panelu a příkaz text je popsána v části panel nabídek a příkazů.  
  
 ![Redline police příkazu](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 – 188_CommandShelfRedline")  
  
Použití...  
- pro oblasti, kam umístit nabídek a panelů nástrojů.  

- se správnou kombinací názvu tokenu Background/popředí.  
  
  Nepoužívejte...  
  pro oblasti, které nejsou podobný police příkazu.  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|Panel nabídek|Pozadí<br /><br /> *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Panel nabídek|Pozadí<br /><br /> *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Panel nabídek|Pozadí<br /><br /> *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Panel příkazů|Pozadí<br /><br /> *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Panel příkazů|Pozadí<br /><br /> *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Panel příkazů|Pozadí<br /><br /> *Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Sada nástrojů  
 Panelu nástrojů je jedním z běžných okna nástrojů, které se nejčastěji používá v sadě Visual Studio. Je v podstatě ovládací prvek stromu se speciální motivu a styly použijí.  
  
 ![Redline nástrojů](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 – 189_ToolboxRedline")  
  
 Použití...  
 Při navrhování panelu nástrojů, kterou chcete vždy bylo v souladu s prostředí nástrojů.  
  
 Nepoužívejte...  
 pro cokoli, co není podobný panelu nástrojů uživatelského rozhraní nebo pokud si nejste jistí, jestli vaše uživatelské rozhraní bude mít problémy se změna barvy panelu prostředí.  
  
 **Výchozí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nadřazený uzel sady nástrojů](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 – 190_ToolboxParentNode")<br /><br /> **Nadřazený uzel**|Pozadí|`Environment.ToolboxContent`<br /><br /> Záhlaví<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Jednotlivé položky nebo celé okno, pokud žádné dostupné ovládací prvky|  
|![Podřízený uzel sady nástrojů](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 – 191_ToolboxChildNode")<br /><br /> **Podřízený uzel**|Pozadí|`Environment.ToolboxContent`<br /><br /> Záhlaví<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Jednotlivé položky nebo celé okno, pokud žádné dostupné ovládací prvky|  
|![Nadřazený uzel sady nástrojů](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 – 190_ToolboxParentNode")<br /><br /> **Nadřazený uzel**|Ohraničení|Žádná|  
|![Podřízený uzel sady nástrojů](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 – 191_ToolboxChildNode")<br /><br /> **Podřízený uzel**|Ohraničení|Žádná|  
|![Nadřazený uzel sady nástrojů](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 – 190_ToolboxParentNode")<br /><br /> **Nadřazený uzel**|Popředí (piktogram)|`Environment.ToolboxContent`|  
|![Podřízený uzel sady nástrojů](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 – 191_ToolboxChildNode")<br /><br /> **Podřízený uzel**|Popředí (piktogram)|`Environment.ToolboxContent`|  
|![Nadřazený uzel sady nástrojů](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 – 190_ToolboxParentNode")<br /><br /> **Nadřazený uzel**|Popředí (Text)|`Environment.ToolboxContent`|  
|![Podřízený uzel sady nástrojů](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 – 191_ToolboxChildNode")<br /><br /> **Podřízený uzel**|Popředí (Text)|`Environment.ToolboxContent`|  
  
 **Přesunutí**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Podřízený uzel panelu nástrojů při najetí myší](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 – 192_ToolboxChildNodeHover")<br /><br /> **Panel nástrojů – najeďte na podřízený uzel**|Pozadí|`Environment.ToolboxContentMouseOver`<br /><br /> Pouze jednotlivé položky|  
|![Podřízený uzel panelu nástrojů při najetí myší](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 – 192_ToolboxChildNodeHover")<br /><br /> **Panel nástrojů – najeďte na podřízený uzel**|Ohraničení|Žádná|  
|![Podřízený uzel panelu nástrojů při najetí myší](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 – 192_ToolboxChildNodeHover")<br /><br /> **Panel nástrojů – najeďte na podřízený uzel**|Popředí (Text)|`Environment.ToolboxContentMouseOver`<br /><br /> Pouze jednotlivé položky|  
  
 **Vyberte**  
  
|Komponenta|Prvek|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaměření nadřazeného uzlu panelu nástrojů](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 – 193_ToolboxParentNodeFocused")<br /><br /> **Zaměřený nadřazený uzel**|Pozadí|`TreeView.SelectedItemActive`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Zaměření podřízeného uzlu sady nástrojů](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 – 194_ToolboxChildNodeFocused")<br /><br /> **Prioritní podřízený uzel**|Pozadí|`TreeView.SelectedItemActive`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Zaměření nadřazeného uzlu panelu nástrojů](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 – 193_ToolboxParentNodeFocused")<br /><br /> **Zaměřený nadřazený uzel**|Ohraničení|`TreeView.FocusVisualBorder`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Zaměření podřízeného uzlu sady nástrojů](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 – 194_ToolboxChildNodeFocused")<br /><br /> **Prioritní podřízený uzel**|Ohraničení|`TreeView.FocusVisualBorder`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Zaměření nadřazeného uzlu panelu nástrojů](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 – 193_ToolboxParentNodeFocused")<br /><br /> **Zaměřený nadřazený uzel**|Popředí (piktogram)|`TreeView.SelectedItemActive`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Zaměření podřízeného uzlu sady nástrojů](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 – 194_ToolboxChildNodeFocused")<br /><br /> **Prioritní podřízený uzel**|Popředí (piktogram)|`TreeView.SelectedItemActive`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Zaměření nadřazeného uzlu panelu nástrojů](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 – 193_ToolboxParentNodeFocused")<br /><br /> **Zaměřený nadřazený uzel**|Popředí (Text)|`TreeView.SelectedItemActive`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Zaměření podřízeného uzlu sady nástrojů](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 – 194_ToolboxChildNodeFocused")<br /><br /> **Prioritní podřízený uzel**|Popředí (Text)|`TreeView.SelectedItemActive`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nevybraný nadřazený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 – 195_ToolboxParentNodeUnfocused")<br /><br /> **Nevybraný nadřazený uzel**|Pozadí|`TreeView.SelectedItemInactive`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Podřízený uzel panelu nástrojů nebyl vybrán.](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 – 196_ToolboxChildNodeUnfocused")<br /><br /> **Nevybraný podřízený uzel**|Pozadí|`TreeView.SelectedItemInactive`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nevybraný nadřazený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 – 195_ToolboxParentNodeUnfocused")<br /><br /> **Nevybraný nadřazený uzel**|Ohraničení|Žádná|  
|![Podřízený uzel panelu nástrojů nebyl vybrán.](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 – 196_ToolboxChildNodeUnfocused")<br /><br /> **Nevybraný podřízený uzel**|Ohraničení|Žádná|  
|![Nevybraný nadřazený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 – 195_ToolboxParentNodeUnfocused")<br /><br /> **Nevybraný nadřazený uzel**|Popředí (piktogram)|`TreeView.SelectedItemInactive`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Podřízený uzel panelu nástrojů nebyl vybrán.](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 – 196_ToolboxChildNodeUnfocused")<br /><br /> **Nevybraný podřízený uzel**|Popředí (piktogram)|`TreeView.SelectedItemInactive`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Nevybraný nadřazený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 – 195_ToolboxParentNodeUnfocused")<br /><br /> **Nevybraný nadřazený uzel**|Popředí (Text)|`TreeView.SelectedItemInactive`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
|![Podřízený uzel panelu nástrojů nebyl vybrán.](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 – 196_ToolboxChildNodeUnfocused")<br /><br /> **Nevybraný podřízený uzel**|Popředí (Text)|`TreeView.SelectedItemInactive`<br /><br /> Z kategorie [stromového zobrazení](../misc/shared-colors.md#BKMK_TreeView)|  
  
## <a name="color-value-reference"></a>Odkaz na hodnotu barvy  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|Komponenta|Částí|Prvek|Stav|Hlediska|Tmavě|Modrá|Vysoký kontrast|  
|Čáry oddělovače|||Výchozí|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|Piktogram rozšíření||Popředí|Výchozí|||||  
|Piktogram rozšíření||Popředí|Při najetí myší|||||  
|Piktogram rozšíření||Pozadí|Výchozí|||||  
|Piktogram rozšíření||Pozadí|Při najetí myší|||||  
|Piktogram rozšíření||Ohraničení|Výchozí|||||  
|Piktogram rozšíření||Ohraničení|Při najetí myší|||||