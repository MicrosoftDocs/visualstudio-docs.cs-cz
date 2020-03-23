---
title: Sdílené barvy | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: brgeorge
ms.openlocfilehash: 421ff85831bb611b655de2bc35f01423b61921a2
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302404"
---
# <a name="shared-colors"></a>Sdílené barvy
Sem vložte úvod.  
  
## <a name="shared-colors"></a>Sdílené barvy  
 Při navrhování uživatelského rozhraní, které používá běžné prvky prostředí sady Visual Studio, nebo chcete, aby byl prvek rozhraní konzistentní s podobnými funkcemi, použijte existující názvy tokenů v souborech definice balíčku k výběru a přiřazení barev. Tím zajistíte, že vaše ui zůstane konzistentní s celkovým prostředím sady Visual Studio a že se automaticky aktualizuje při přidání nebo aktualizaci motivů.  
  
 Tento článek popisuje běžné prvky uživatelského rozhraní a názvy tokenů, které používají, na které můžete odkazovat při vytváření podobného uživatelského rozhraní. Konkrétní informace o tom, jak získat přístup k těmto tokenům barev, naleznete [v tématu VSColor Service](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Ujistěte se, že používáte názvy tokenů správně:  
  
- **Používejte názvy tokenů na základě funkce, nikoli na samotné barvě.** Společné sdílené barvy jsou přidruženy k určitým prvkům rozhraní a jsou určeny pouze pro stejné nebo podobné funkce. Například nepoužívejte znovu barvu lisovaného pole se seznamem pro animaci průběhu otáčení jen proto, že se vám barva líbí. Funkce pole se seznamem a animace se liší a pokud se změní barva přidružená k poli se seznamem, nemusí již být vhodnou barvou pro prvek animace. Konzistentní používání barev pomáhá orientovat uživatele a zabránit nejasnostem.  
  
- **Používejte barvy pozadí a textu ve správné kombinaci.** Barvy pozadí, které jsou určeny k použití s textem, budou mít přidruženou barvu textu. Nepoužívejte jiné barvy textu, než které jsou určeny pro toto pozadí. Pokud není přidružená barva textu, nepoužívejte tuto barvu pozadí pro žádný povrch, na kterém očekáváte zobrazení textu. Jiné kombinace barev textu a pozadí mohou mít za následek nečitelné rozhraní.  
  
- **Použijte ovládací barvy, které jsou vhodné pro jejich umístění.** V některých státech některé ovládací prvky sady Visual Studio nemají samostatné barvy ohraničení a pozadí. Místo toho, oni vyzvednout ty barvy z povrchů za nimi. Ujistěte se, že vždy používáte názvy tokenů, které jsou vhodné pro umístění, kam umísťujete ovládací prvek.  
  
> [!IMPORTANT]
> Nepoužívejte žetony nalezené v kategoriích "Úvodní stránka" nebo "Jablečný mošt"!  
  
### <a name="command-structures"></a>Struktury příkazů  
  
#### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Nabídky  
 Nabídky se mohou vyskytovat na několika místech v rámci sady Visual Studio 2013: na hlavním panelu nabídek, vloženém do oken dokumentů nebo nástrojů nebo při kliknutí pravým tlačítkem myši na různých místech v celém integrovaném prostředí. Implementace nabídek přidružených k jiným prvkům uživatelského rozhraní jsou popsány v části pro příslušný prvek. Vždy byste měli použít standardní implementaci nabídky poskytované prostředí sady Visual Studio. V některých výjimečných případech však nemusí mít přístup ke standardním nabídkám sady Visual Studio. V těchto situacích použijte následující názvy tokenů, abyste zajistili, že vaše ui je konzistentní s ostatními nabídkami v sadě Visual Studio.  
  
 ![Červená čára nabídek](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")  
  
Použít...  
- kdykoli potřebujete vytvořit vlastní nabídku.  
  
- Pokud máte novou komponentu uzly, které chcete, aby odpovídaly nabídky sady Visual Studio.  
  
Nepoužívejte ...  
samotnou barvu pozadí. Vždy používejte kombinaci pozadí a popředí, jak je uvedeno.  
  
##### <a name="menu-title"></a>Název nabídky  
 Názvy nabídek se skládají z pozadí, ohraničení a textu nadpisu a volitelného glyfu, obvykle když se nabídka nachází v panelu příkazů.  
  
 ![Červená čára názvu nabídky](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")  
  
Použít...  
při každém vytváření vlastního názvu nabídky.  
  
Nepoužívejte...  
- pro vše, co nechcete vždy odpovídat názvu nabídky.  
  
- v jakékoli kombinaci pozadí/popředí, než je uvedeno.  
  
  **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Výchozí název nabídky](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Název nabídky**|Pozadí|Žádný|  
|![Výchozí název nabídky](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Název nabídky**|Popředí (text)|`Environment.CommandBarTextActive`|  
|![Název nabídky s výchozím glyfem](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Název nabídky s glyfem**|Popředí (glyf)|`Environment.CommandBarMenuGlyph`|  
|![Název nabídky s výchozím glyfem](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Název nabídky s glyfem**|Ohraničení|Žádný|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Název nabídky při najetí přes](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Název nabídky**|Pozadí|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Název nabídky při najetí přes](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Název nabídky**|Popředí (text)|`Environment.CommandBarTextHover`|  
|![Název nabídky s glyfem na jevu](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Název nabídky s glyfem**|Popředí (glyf)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Název nabídky s glyfem na jevu](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Název nabídky s glyfem**|Ohraničení|`Environment.CommandBarBorder`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Název nabídky stisknut](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Název nabídky**|Pozadí|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Název nabídky stisknut](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Název nabídky**|Popředí (text)|`Environment.CommandBarTextActive`|  
|![Název nabídky s flyfy](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Název nabídky s glyfem**|Popředí (glyf)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Název nabídky s flyfy](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Název nabídky s glyfem**|Ohraničení|`Environment.CommandBarMenuBorder`<br /><br /> Pouze na levé, horní a pravé straně.|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Název nabídky se zakázaným glyfem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Název nabídky s glyfem**|Pozadí|Žádný|  
|![Název nabídky se zakázaným glyfem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Název nabídky s glyfem**|Popředí (text)|`Environment.CommandBarTextInactive`|  
|![Název nabídky se zakázaným glyfem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Název nabídky s glyfem**|Popředí (glyf)|`Environment.CommandBarTextInactive`|  
|![Název nabídky se zakázaným glyfem](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Název nabídky s glyfem**|Ohraničení|Žádný|  
  
##### <a name="menu"></a>Nabídka  
 Jednotlivá položka nabídky se skládá z textu nabídky a volitelné ikony, zaškrtávacího políčka nebo glyfu podnabídky. Jeho pozadí a barva textu se mění při přechodu. Tento token barev je dvojice pozadí/popředí.  
  
 ![Červené položky nabídky](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")  
  
 Použít...  
 pro všechny rozevírací seznamy, které jsou spuštěny z panelu nabídek nebo panelu příkazů.  
  
Nepoužívejte...  
- pro všechny rozevírací seznam, ke kterému dochází v jiném kontextu.  

- v jakékoli kombinaci pozadí/popředí, než je uvedeno.  
  
  **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Nabídka**|Pozadí|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Nabídka**|Popředí (text)|`Environment.CommandBarTextActive`|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Nabídka**|Popředí (glyf podnabídky)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Nabídka**|Ohraničení|`Environment.CommandBarMenuBorder`|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Nabídka**|Pozadí kanálu ikony|`Environment.CommandBarMenuIconBackground`|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Nabídka**|Oddělovač|`Environment.CommandBarMenuSeparator`|  
|![Výchozí nabídka](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Nabídka**|Stín|`Environment.DropShadowBackground`|  
|![Nabídka zaškrtnuta](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Zaškrtnuté**|Zaškrtnutí|`Environment.CommandBarCheckBox`|  
|![Nabídka zaškrtnuta](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **Zaškrtnuté**|Zkontrolujte pozadí značky|`Environment.CommandBarSelectedIcon`|  
|![Vybraná nabídka](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Vybráno**|Pozadí ikony|`Environment.CommandBarSelected`|  
|![Vybraná nabídka](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Vybráno**|Ohraničení ikony|`Environment.CommandBarSelectedBorder`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nabídka najetá přes](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Položka nabídky**|Pozadí|`Environment.CommandBarMenuItemMouseOver`|  
|![Nabídka najetá přes](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Položka nabídky**|Popředí (text)|`Environment.CommandBarMenuItemMouseOver`|  
|![Nabídka najetá přes](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Položka nabídky**|Popředí (glyf podnabídky)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![Nabídka je zaškrtnutá.](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Zaškrtnuté**|Zaškrtnutí|`Environment.CommandBarCheckBoxMouseOver`|  
|![Nabídka je zaškrtnutá.](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **Zaškrtnuté**|Zkontrolujte pozadí značky|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Nabídka je vybraná.](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Vybráno**|Pozadí ikony|`Environment.CommandBarHoverOverSelected`|  
|![Nabídka je vybraná.](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Vybráno**|Ohraničení ikony|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nabídka je zakázána.](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Položka nabídky|Popředí (text)|`Environment.CommandBarTextInactive`|  
|![Nabídka je zakázána.](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Položka nabídky|Popředí (glyf podnabídky)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Nabídka zakázána zaškrtnuto](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Zaškrtnuté|Zaškrtnutí|`Environment.CommandBarCheckBoxDisabled`|  
|![Nabídka zakázána zaškrtnuto](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> Zaškrtnuté|Zkontrolujte pozadí značky|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Panel příkazů  
 Panel příkazů se může zobrazit na více místech v integrovaném prostředí Sady Visual Studio, zejména na polici příkazů a vložený do oken nástrojů nebo dokumentů.  
  
 Obecně vždy používejte standardní implementaci panelu příkazů poskytovanou prostředím sady Visual Studio. Použití standardní mechanismus zajišťuje, že všechny vizuální podrobnosti se zobrazí správně a že interaktivní prvky, se bude chovat konzistentně s ostatními ovládacími prvky panelu příkazů sady Visual Studio. Pokud je však nutné vytvořit vlastní panel příkazů, ujistěte se, že styl správně pomocí následující názvy tokenů.  
  
 ![Červený řádek panelu příkazů](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![Červené tlačítko přetečení](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 Použít...  
 v místech, kde potřebujete vložený panel příkazů, ale nemůžete použít standardní implementaci panelu příkazů sady Visual Studio.  
  
Nepoužívejte...  
- pro prvky uživatelského rozhraní, které nejsou podobné panelu příkazů.  

- pro komponenty panelu příkazů jiné než ty, pro které jsou určeny názvy tokenů.  
  
##### <a name="command-bar-group"></a>Skupina panelu příkazů  
 Skupina panelu příkazů se skládá ze související sady ovládacích prvků panelu příkazů a může obsahovat libovolný počet tlačítek, rozdělených tlačítek, rozevíracích nabídek, polí se seznamem nebo nabídek. Barvy pro tyto ovládací prvky jsou regulovány samostatné názvy tokenů a jsou popsány jednotlivě jinde v této příručce. Oddělovací čára se používá k rozdělení skupiny panelu příkazů do souvisejících podskupin.  
  
 ![Červená čára skupiny panelu příkazů](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 Použít...  
 v místech, kde potřebujete vložený panel příkazů, ale nemůžete použít standardní implementaci panelu příkazů sady Visual Studio.  
  
Nepoužívejte...  
- pro prvky uživatelského rozhraní, které nejsou podobné panelu příkazů.  

- pro komponenty panelu příkazů jiné než ty, pro které jsou určeny názvy tokenů.  
  
  **Výchozí** (žádné jiné stavy)  
  
|Element|Název tokenu: Category.color|  
|-------------|--------------------------------|  
|Pozadí|`Environment.CommandBarGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|Ohraničení|`Environment.CommandBarToolBarBorder`|  
|Táhlo přetažení|`Environment.CommandBarDragHandle`|  
|Oddělovač|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Ikony příkazů  
 ![Červená čára ikony příkazu](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![Červená čára ikony příkazu](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 Použít...  
 pro všechna tlačítka, která budou umístěna na panelu příkazů.  
  
Nepoužívejte...  
- pro ovládací prvky, které mají své vlastní názvy tokenů.  

- v jakékoli kombinaci pozadí/popředí, než je uvedeno.  
  
  **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Výchozí ikona příkazu](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Výchozí**|Pozadí|Není k zato (dědí z pozadí panelu příkazů)|  
|![Výchozí ikona příkazu](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Výchozí**|Popředí (text)|`Environment.CommandBarTextActive`|  
|![Výchozí ikona příkazu](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Výchozí**|Ohraničení|Není dostupné.|  
|![Ve výchozím nastavení se vybrala ikona příkazu.](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Vybráno**|Pozadí|`Environment.CommandBarSelected`|  
|![Ve výchozím nastavení se vybrala ikona příkazu.](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Vybráno**|Popředí (text)|`Environment.CommandBarTextSelected`|  
|![Ve výchozím nastavení se vybrala ikona příkazu.](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Vybráno**|Ohraničení|`Environment.CommandBarSelectedBorder`|  
  
 **Najetí přes klávesnici a na klávesnici**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Najetí na ikonu příkazu](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standardní při najetí přes**|Pozadí|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Najetí na ikonu příkazu](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standardní při najetí přes**|Popředí (text)|`Environment.CommandBarTextHover`|  
|![Najetí na ikonu příkazu](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Standardní při najetí přes**|Ohraničení|`Environment.CommandBarBorder`|  
|![Ikona příkazu je vybraná jako na jenom](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Vybráno při najetí přes**|Pozadí|`Environment.CommandBarHoverOverSelected`|  
|![Ikona příkazu je vybraná jako na jenom](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Vybráno při najetí přes**|Popředí (text)|`Environment.CommandBarTextHoverOverSelected`|  
|![Ikona příkazu je vybraná jako na jenom](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Vybráno při najetí přes**|Ohraničení|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknutá ikona příkazu](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Ikona příkazu Stisknuto**|Pozadí|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Stisknutá ikona příkazu](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Ikona příkazu Stisknuto**|Popředí (text)|`Environment.CommandBarTextMouseDown`|  
|![Stisknutá ikona příkazu](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Ikona příkazu Stisknuto**|Ohraničení|`Environment.CommandBarBorder`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ikona příkazu je zakázána.](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Ikona příkazu Zakázáno**|Pozadí|Není k zato (dědí z pozadí panelu příkazů)|  
|![Ikona příkazu je zakázána.](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Ikona příkazu Zakázáno**|Popředí (text)|`Environment.CommandBarTextInactive`|  
|![Ikona příkazu je zakázána.](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Ikona příkazu Zakázáno**|Ohraničení|Není dostupné.|  
  
##### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a>Seznamem  
  
> [!IMPORTANT]
> Pole se seznamem jsou podobná rozevíracím seznamům, ale obsahují upravitelnou oblast textu. Pokud váš rozevírací soubor neobsahuje upravitelnou oblast textu, použijte barevné tokeny nalezené v [rozevíracím souboru](../misc/shared-colors.md#BKMK_CommandDropDown).  
  
 ![Červená čára pole se seznamem](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")  
  
Použít...  
- při vytváření vlastních polí se seznamem.  

- při vytváření ovládacího prvku panelu příkazů, který je podobný poli se seznamem.  

Nepoužívejte ...  
- pro cokoliv, co nechcete vždy odpovídat ui panelu příkazů.  

- když máte přístup k stylizované musetu se seznamem.  
  
  **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vstupní pole se seznamem](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Vstupní pole**|Pozadí|`Environment.ComboBoxBackground`|  
|![Vstupní pole se seznamem](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Vstupní pole**|Popředí (text)|`Environment.ComboBoxText`|  
|![Vstupní pole se seznamem](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Vstupní pole**|Ohraničení|`Environment.ComboBoxBorder`|  
|![Vstupní pole se seznamem](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Vstupní pole**|Oddělovač|Žádný oddělovač|  
|![Tlačítko&#45;spouštění pole se seznamem](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Rozevírací tlačítko**|Pozadí|Není k mno h(dědění)|  
|![Tlačítko&#45;spouštění pole se seznamem](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Rozevírací tlačítko**|Popředí (glyf)|`Environment.ComboBoxGlyph`|  
|![Seznam&#47;rozevírací&#45;seznamu dolů](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Rozevírací seznam**|Pozadí|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Seznam&#47;rozevírací&#45;seznamu dolů](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Rozevírací seznam**|Popředí (text)|`Environment.ComboBoxItemText`|  
|![Seznam&#47;rozevírací&#45;seznamu dolů](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Rozevírací seznam**|Ohraničení|`Environment.ComboBoxPopupBorder`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Pole se seznamem při přijetí](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Vstupní pole**|Pozadí|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Pole se seznamem při přijetí](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Vstupní pole**|Popředí (text)|`Environment.ComboBoxMouseOverText`|  
|![Pole se seznamem při přijetí](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Vstupní pole**|Ohraničení|`Environment.ComboBoxMouseOverBorder`|  
|![Pole se seznamem při přijetí](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Vstupní pole**|Oddělovač|`Environment.ComboBoxMouseOverSeparator`|  
|![Pole se seznamem&#47;tlačítko&#45;dolů při přijetí](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Rozevírací tlačítko**|Pozadí|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Pole se seznamem&#47;tlačítko&#45;dolů při přijetí](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Rozevírací tlačítko**|Popředí (glyf)|`Environment.ComboBoxMouseOverGlyph`|  
|![Pole se seznamem&#47;rozevírací&#45;seznamu při přiřazu](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Rozevírací seznam**|Pozadí (položka nabídky)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Pole se seznamem&#47;rozevírací&#45;seznamu při přiřazu](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Rozevírací seznam**|Popředí (text)|`Environment.ComboBoxItemMouseOverText`|  
|![Pole se seznamem&#47;rozevírací&#45;seznamu při přiřazu](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Rozevírací seznam**|Ohraničení (položka nabídky)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Focused**  
  
|Komponenta|Element|Název tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Zaměření na pole se seznamem](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Vstupní pole**|Pozadí|`Environment.ComboBoxFocusedBackground`|  
|![Zaměření na pole se seznamem](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Vstupní pole**|Popředí (text)|`Environment.ComboBoxFocusedText`|  
|![Zaměření na pole se seznamem](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Vstupní pole**|Ohraničení|`Environment.ComboBoxFocusedBorder`|  
|![Zaměření na pole se seznamem](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Vstupní pole**|Oddělovač|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Pole se seznamem&#47;zaostřené tlačítkem&#45;dolů](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Rozevírací tlačítko**|Pozadí|`Environment.ComboBoxFocusedButtonBackground`|  
|![Pole se seznamem&#47;zaostřené tlačítkem&#45;dolů](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Rozevírací tlačítko**|Popředí (glyf)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Stisknuté vstupní pole se seznamem](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Vstupní pole**|Pozadí|`Environment.ComboBoxMouseDownBackground`|  
|![Stisknuté vstupní pole se seznamem](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Vstupní pole**|Popředí (text)|`Environment.ComboBoxMouseDownText`|  
|![Stisknuté vstupní pole se seznamem](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Vstupní pole**|Ohraničení|`Environment.ComboBoxMouseDownBorder`|  
|![Stisknuté vstupní pole se seznamem](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Vstupní pole**|Oddělovač|`Environment.ComboBoxMouseDownSeparator`|  
|![Spouštěč&#47;stisknuté tlačítko&#45;dolů](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Rozevírací tlačítko**|Pozadí|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Spouštěč&#47;stisknuté tlačítko&#45;dolů](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Rozevírací tlačítko**|Popředí (glyf)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Element|Název tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Vstupní pole se seznamem je zakázáno.](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Vstupní pole**|Pozadí|`Environment.ComboBoxDisabledBackground`|  
|![Vstupní pole se seznamem je zakázáno.](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Vstupní pole**|Popředí (text)|`Environment.ComboBoxDisabledText`|  
|![Vstupní pole se seznamem je zakázáno.](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Vstupní pole**|Ohraničení|`Environment.ComboBoxDisabledBorder`|  
|![Vstupní pole se seznamem je zakázáno.](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Vstupní pole**|Oddělovač|Žádný oddělovač|  
|![Pole se seznamem&#47;vypnuté tlačítko&#45;down down](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Rozevírací tlačítko**|Pozadí|Žádný|  
|![Pole se seznamem&#47;vypnuté tlačítko&#45;down down](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Rozevírací tlačítko**|Popředí (glyf)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a>Rozevírací uzlovací  
  
> [!IMPORTANT]
> Rozevírací seznamy jsou podobné polím se seznamem, ale postrádají upravitelné oblasti textu. Pokud rozevírací seznam obsahuje upravitelnou oblast textu, použijte tokeny barev nalezené v [poli Seseznam](../misc/shared-colors.md#BKMK_CommandComboBox).  
  
 ![Přetažení&#45;redline](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")  
  
 Použít...  
 při vytváření vlastních ovládacích prvků rozevíracího seznamu.  
  
Nepoužívejte ...  
- pro cokoliv, co není podobné rozevíracímu seznamu.  

- pro pole se seznamem nebo rozdělená tlačítka.  
  
  **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozbalovací&#45;výběrové pole dolů](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Výběrové pole**|Pozadí|`Environment.DropDownBackground`|  
|![Rozbalovací&#45;výběrové pole dolů](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Výběrové pole**|Popředí (text)|`DropDownText`|  
|![Rozbalovací&#45;výběrové pole dolů](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Výběrové pole**|Ohraničení|`DropDownBorder`|  
|![Rozbalovací&#45;výběrové pole dolů](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Výběrové pole**|Oddělovač|Žádný oddělovač|  
|![Tlačítko&#45;dolů](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Rozevírací tlačítko**|Pozadí|Žádný|  
|![Tlačítko&#45;dolů](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Rozevírací tlačítko**|Popředí (glyf)|`Environment.DropDownGlyph`|  
|![Rozevírací&#45;rozevírací seznam](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Rozevírací seznam**|Pozadí|`Environment.DropDownPopupBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Rozevírací&#45;rozevírací seznam](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Rozevírací seznam**|Popředí (text)|`Environment.ComboBoxItemText`|  
|![Rozevírací&#45;rozevírací seznam](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Rozevírací seznam**|Ohraničení|`Environment.DropDownPopupBorder`|  
|![Rozevírací&#45;rozevírací seznam](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Rozevírací seznam**|Stín|`Environment.DropShadowBackground`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozbalovací&#45;výběrové pole při najetí přes](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Výběrové pole**|Pozadí|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Rozbalovací&#45;výběrové pole při najetí přes](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Výběrové pole**|Popředí (text)|`Environment.DropDownMouseOverText`|  
|![Rozbalovací&#45;výběrové pole při najetí přes](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Výběrové pole**|Ohraničení|`Environment.DropDownMouseOverBorder`|  
|![Rozbalovací&#45;výběrové pole při najetí přes](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Výběrové pole**|Oddělovač|`Environment.DropDownButtonMouseOverSeparator`|  
|![Tlačítko&#45;při najetí na tlačítko pro najetí](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Rozevírací tlačítko**|Pozadí|`Environment.DropDownButtonMouseOverBackground`|  
|![Tlačítko&#45;při najetí na tlačítko pro najetí](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Rozevírací tlačítko**|Popředí (glyf)|`Environment.DropDownMouseOverGlyph`|  
|![Rozevírací&#45;při najetí na jev](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Rozevírací seznam**|Pozadí (položka nabídky)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Rozevírací&#45;při najetí na jev](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Rozevírací seznam**|Popředí (text)|`Environment.ComboBoxItemMouseOverText`|  
|![Rozevírací&#45;při najetí na jev](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Rozevírací seznam**|Ohraničení (položka nabídky)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknuté pole výběru&#45;dolů](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Výběrové pole**|Pozadí|`Environment.DropDownMouseDownBackground`|  
|![Stisknuté pole výběru&#45;dolů](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Výběrové pole**|Popředí (text)|`Environment.DropDownMouseDownText`|  
|![Stisknuté pole výběru&#45;dolů](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Výběrové pole**|Ohraničení|`Environment.DropDownMouseDownBorder`|  
|![Stisknuté pole výběru&#45;dolů](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Výběrové pole**|Oddělovač|`Environment.DropDownButtonMouseDownSeparator`|  
|![Stisknuté tlačítko drop&#45;down](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Rozevírací tlačítko**|Pozadí|`Environment.DropDownButtonMouseDownBackground`|  
|![Stisknuté tlačítko drop&#45;down](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Rozevírací tlačítko**|Popředí (glyf)|`Environment.DropDownMouseDownGlyph`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozbalovací&#45;výběrové pole bylo zakázáno.](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Pozadí|`Environment.DropDownDisabledBackground`|  
|![Rozbalovací&#45;výběrové pole bylo zakázáno.](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Popředí (text)|`Environment.DropDownDisabledText`|  
|![Rozbalovací&#45;výběrové pole bylo zakázáno.](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Ohraničení|`Environment.DropDownDisabledBorder`|  
|![Rozbalovací&#45;výběrové pole bylo zakázáno.](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Oddělovač|Žádný oddělovač|  
|![Tlačítko&#45;down je vypnuté.](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Pozadí|Není dostupné.|  
|![Tlačítko&#45;down je vypnuté.](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Popředí (glyf)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Tlačítko Rozdělit  
 Rozdělená tlačítka sdílejí mnoho názvů tokenů s dalšími ovládacími prvky panelu příkazů, jako jsou tlačítka, nabídky a text panelu příkazů. Všechny potřebné akce a názvy tokenů rozevíracího tlačítka se zde opakují pro pohodlí. Rozevírací seznamy rozdělených tlačítek jsou implementace příkazů [.](../misc/shared-colors.md#BKMK_CommandMenus)  
  
 ![Červené tlačítko Rozdělení](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 Použít...  
 při vytváření vlastního tlačítka rozdělení.  
  
Nepoužívejte ...  
- pro jiné druhy tlačítek.  

- v jakékoli kombinaci pozadí/popředí, než je uvedeno.  
  
  **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko Rozdělit](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Tlačítko Rozdělit (výchozí)**|Pozadí|Žádný|  
|![Tlačítko Rozdělit](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Tlačítko Rozdělit (výchozí)**|Popředí (text)|`Environment.CommandBarTextActive`|  
|![Tlačítko Rozdělit](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Tlačítko Rozdělit (výchozí)**|Popředí (glyf)|`Environment.CommandBarSplitButtonGlyph`|  
|![Tlačítko Rozdělit](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Tlačítko Rozdělit (výchozí)**|Ohraničení|Není dostupné.|  
|![Tlačítko Rozdělit](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Tlačítko Rozdělit (výchozí)**|Oddělovač|Není dostupné.|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko Rozdělit při najetí mezi](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Tlačítko Rozdělit (při najetí)**|Pozadí|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Tlačítko Rozdělit při najetí mezi](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Tlačítko Rozdělit (při najetí)**|Popředí (text)|`Environment.CommandBarTextHover`|  
|![Tlačítko Rozdělit při najetí mezi](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Tlačítko Rozdělit (při najetí)**|Popředí (glyf)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Tlačítko Rozdělit při najetí mezi](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Tlačítko Rozdělit (při najetí)**|Ohraničení|`Environment.CommandBarBorder`|  
|![Tlačítko Rozdělit při najetí mezi](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Tlačítko Rozdělit (při najetí)**|Oddělovač|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko Rozdělit stisknuto](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Tlačítko Rozdělení (stisknuto)**|Pozadí|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Tlačítko Rozdělit stisknuto](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Tlačítko Rozdělení (stisknuto)**|Popředí (text)|`Environment.CommandBarTextMouseDown`|  
|![Tlačítko Rozdělit stisknuto](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Tlačítko Rozdělení (stisknuto)**|Popředí (glyf)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Tlačítko Rozdělit stisknuto](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Tlačítko Rozdělení (stisknuto)**|Ohraničení|`Environment.CommandBarBorder`|  
|![Tlačítko Rozdělit stisknuto](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Tlačítko Rozdělení (stisknuto)**|Oddělovač|Není dostupné.|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko Rozdělit je vypnuto.](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Tlačítko Rozdělit (zakázáno)**|Pozadí|Není dostupné.|  
|![Tlačítko Rozdělit je vypnuto.](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Tlačítko Rozdělit (zakázáno)**|Popředí (text)|`Environment.ComboBoxItemTextInactive`|  
|![Tlačítko Rozdělit je vypnuto.](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Tlačítko Rozdělit (zakázáno)**|Popředí (glyf)|`Environment.CommandBarTextInactive`|  
|![Tlačítko Rozdělit je vypnuto.](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Tlačítko Rozdělit (zakázáno)**|Ohraničení|Není dostupné.|  
|![Tlačítko Rozdělit je vypnuto.](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Tlačítko Rozdělit (zakázáno)**|Oddělovač|Není dostupné.|  
  
##### <a name="more-options-and-overflow-buttons"></a>Tlačítka "Další možnosti" a Přetečení  
 Tlačítko "Další možnosti" se používá, když lze přizpůsobit skupinu panelu příkazů přidáním nebo odebráním souvisejících tlačítek panelu příkazů. Tlačítko "Přetečení" se zobrazí, když je panel příkazů zkrácen kvůli nedostatku vodorovného prostoru, a po klepnutí se zobrazí nabídka obsahující tlačítka panelu příkazů, která nelze zobrazit. Barvy pro tato dvě tlačítka jsou řízeny stejnou sadou názvů tokenů.  
  
 ![Další možnosti redline](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 Použít...  
 pro vlastní tlačítka "Další možnosti" nebo Přetečení.  
  
 Nepoužívejte ...  
 pro tlačítka, která nemají podobné funkce jako tlačítko "Další možnosti" nebo Přetečení.  
  
 **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Další možnosti](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Další možnosti**|Pozadí|`Environment.CommandBarOptionsBackground`|  
|![Další možnosti](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Další možnosti**|Popředí (glyf)|`Environment.CommandBarOptionsGlyph`|  
|![Tlačítko přetečení](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Přetečení**|Pozadí|`Environment.CommandBarOptionsBackground`|  
|![Tlačítko přetečení](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Přetečení**|Popředí (glyf)|`Environment.CommandBarOptionsGlyph`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Další možnosti při najetí přes](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Další možnosti**|Pozadí|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Další možnosti při najetí přes](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Další možnosti**|Popředí (glyf)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Přetečení při vznášení](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Přetečení**|Pozadí|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Přetečení při vznášení](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Přetečení**|Popředí (glyf)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Další možnosti stisknuté](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Další možnosti**|Pozadí|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Další možnosti stisknuté](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Další možnosti**|Popředí (glyf)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Přetekli](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Přetečení**|Pozadí|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Přetekli](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Přetečení**|Popředí (glyf)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Okna dokumentu  
 Není nutné replikovat okna dokumentů, protože jsou poskytovány prostředím sady Visual Studio. Můžete se však rozhodnout, že chcete využít barvy použité v oknech dokumentu tak, aby vaše ui vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.  
  
 Při použití tokenů barev okna dokumentu musíte být opatrní, abyste je používali pouze pro podobné prvky a vždy ve dvojicích. Pokud tak neučiníte, budete mít neočekávané výsledky v ui.  
  
#### <a name="document-window-frame"></a>Rámeček okna dokumentu  
 Okna dokumentu mohou být ukotvena v prostředí IDE nebo plovoucí jako samostatné okno. Pokud je okno dokumentu plovoucí mimo ide, stále sedí v dokumentu dobře a má pozadí, ohraničení, text a tabulátor barvy, které jsou stejné jako když je součástí ide. Dokument je však v něm nasazený uvnitř rámečku, který má vlastní barvy pozadí, ohraničení a textu. Když jsou okna nástrojů ukotvena v dokumentu dobře, dědí chování a barvu pro své karty z názvů tokenů okna dokumentu.  
  
 ![Červená čára okna ukotveného dokumentu](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **Okno ukotveného dokumentu**  
  
 ![Červená čára plovoucího okna dokumentu](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **Plovoucí okno dokumentu**  
  
 Použít...  
 kdekoli vytváříte ui, které chcete, aby odpovídaly okno dokumentu.  
  
 Nepoužívejte ...  
 pro jakékoli ui, které nechcete automaticky změnit, pokud prostředí obsahuje aktualizaci motivu.  
  
 **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|Dokument: ukotvený nebo plovoucí|Pozadí|Závisí na typu dokumentu|  
|Dokument: ukotvený nebo plovoucí|Popředí (text)|Závisí na typu dokumentu|  
|Dokument: ukotvený nebo plovoucí|Ohraničení|`Environment.ToolWindowBorder`|  
|![Zaostřený snímek](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rám: plovoucí, zaostřený**|Pozadí|`Environment.ToolWindowFloatingFrame`|  
|![Zaostřený snímek](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rám: plovoucí, zaostřený**|Popředí (text)|`Environment.ToolWindowFloatingFrame`|  
|![Zaostřený snímek](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rám: plovoucí, zaostřený**|Popředí (glyf)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Zaostřený snímek](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rám: plovoucí, zaostřený**|Ohraničení|`Environment.MainWindowActiveDefaultBorder`|  
|![Zaostřený snímek](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Rám: plovoucí, zaostřený**|Ohraničení (glyf)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Nastavit na průhlednou|  
|![Rámeček rozostřený](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rám: plovoucí, nezaostřený**|Pozadí|`Environment.ToolWindowFloatingFrameInactive`|  
|![Rámeček rozostřený](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rám: plovoucí, nezaostřený**|Popředí (text)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Rámeček rozostřený](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rám: plovoucí, nezaostřený**|Popředí (glyf)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Rámeček rozostřený](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rám: plovoucí, nezaostřený**|Ohraničení|`Environment.MainWindowInactiveBorder`|  
|![Rámeček rozostřený](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Rám: plovoucí, nezaostřený**|Ohraničení (glyf)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Nastavit na průhlednou|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Snímek zaměřený na jev](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Rám: plovoucí, zaostřený**|Pozadí (glyf)|`Environment.RaftedWindowButtonHoverActive`|  
|![Snímek zaměřený na jev](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Rám: plovoucí, zaostřený**|Popředí (glyf)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Snímek zaměřený na jev](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Rám: plovoucí, zaostřený**|Ohraničení (glyf)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Rámeček nezaostřený na vznášení](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Rám: plovoucí, nezaostřený**|Pozadí (glyf)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Rámeček nezaostřený na vznášení](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Rám: plovoucí, nezaostřený**|Popředí (glyf)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Rámeček nezaostřený na vznášení](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Rám: plovoucí, nezaostřený**|Ohraničení (glyf)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknutý rám](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Rám: plovoucí, zaostřený**|Pozadí (glyf)|`Environment.RaftedWindowButtonDown`|  
|![Stisknutý rám](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Rám: plovoucí, zaostřený**|Popředí (glyf)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Stisknutý rám](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Rám: plovoucí, zaostřený**|Ohraničení (glyf)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Záložky dokumentů  
 Karty dokumentů jsou v kanálu karet, které označují, které dokumenty jsou aktuálně otevřené, spolu s nimiž se jedná o aktuální vybraný nebo aktivní dokument. Okna nástrojů lze také ukotvit v kanálu karty dokumentu, pokud je tam uživatel umístí. V takovém případě používají stejné barvy karty jako okna dokumentu. Pokud vytváříte ui, které chcete vždy odpovídat barvy okna dokumentu (včetně aktualizací motivu nebo pokud jsou nainstalovány nové motivy), pak odkazovat na tyto tokeny barev.  
  
 ![Červená čára karty Dokument](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")  
  
 Použít...  
 kdekoli vytváříte ui, které chcete přizpůsobit karty dokumentů a automaticky vyzvednout aktualizace motivů nebo nové barvy motivu.  
  
 Nepoužívejte ...  
 pro jakékoli ui, které nechcete změnit automaticky, když prostředí má aktualizaci motivu.  
  
##### <a name="open-document-tabs"></a>Otevření karet dokumentů  
 Každý otevřený dokument má v kanálu karty dokumentu kartu, která zobrazuje jeho název. Dokumenty mohou být vybrány nebo otevřeny na pozadí a jejich karty odrážejí tyto stavy:  
  
- Vybraná karta představuje dokument, který je aktuálně zobrazen v dokumentu dobře. Vybraná karta má ohraničení dokumentu, které dobře přesahuje horní okraj dokumentu.  
  
- Karty na pozadí jsou všechny karty dokumentů, které nejsou aktuálně vybranou kartou. Po kliknutí se stanou vybranou kartou a z těchto názvů tokenů získají všechny barvy pozadí, ohraničení a textu.  
  
  ![Otevřít kartu dokumentu jako červenou čáru](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
  Použít...  
  při vytváření vlastních karet dokumentů.  
  
  Nepoužívejte ...  
  - pro předběžné (náhledové) karty.  
  
- pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu.  
  
##### <a name="selected-tab"></a>Vybraná karta  
 **Focused**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vybraná karta zaměřená](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Vybraná karta dokumentu, zaměřená**|Pozadí|`Environment.FileTabSelectedGradientTop`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Vybraná karta zaměřená](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Vybraná karta dokumentu, zaměřená**|Popředí (text)|`Environment.FileTabSelectedText`|  
|![Vybraná karta zaměřená](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Vybraná karta dokumentu, zaměřená**|Ohraničení|`Environment.FileTabSelectedBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
|![Vybraná karta zaměřená](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Vybraná karta dokumentu, zaměřená**|Ohraničení dokumentu|`Environment.FileTabDocumentBorderBackground`|  
  
 **Rozostřený**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vybraná karta rozostřená](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Vybraná karta dokumentu, nezaostřená**|Pozadí|`Environment.FileTabInactiveGradientTop`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Vybraná karta rozostřená](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Vybraná karta dokumentu, nezaostřená**|Popředí (text)|`Environment.FileTabInactiveText`|  
|![Vybraná karta rozostřená](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Vybraná karta dokumentu, nezaostřená**|Ohraničení|`Environment.FileTabInactiveBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
|![Vybraná karta rozostřená](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Vybraná karta dokumentu, nezaostřená**|Ohraničení dokumentu|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Karta Pozadí  
 **Výchozí**  
  
|Komponenta|Element|Název tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Karta Pozadí](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Karta Pozadí je výchozí**|Pozadí|`Environment.FileTabBackground`|  
|![Karta Pozadí](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Karta Pozadí je výchozí**|Popředí (text)|`Environment.FileTabText`|  
|![Karta Pozadí](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Karta Pozadí je výchozí**|Ohraničení|`Environment.FileTabBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Karta Pozadí při najetí přes](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Karta Pozadí při najetí přes**|Pozadí|`Environment.FileTabHotGradientTop`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Karta Pozadí při najetí přes](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Karta Pozadí při najetí přes**|Popředí (text)|`Environment.FileTabHotText`|  
|![Karta Pozadí při najetí přes](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Karta Pozadí při najetí přes**|Ohraničení|`Environment.FileTabHotBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
##### <a name="preview-tab"></a>Karta Náhled  
 Karta Náhled se zobrazí na pravé straně kanálu karty dokumentu, když uživatel klepne na položku v okně nástroje Průzkumník řešení. Funguje jako náhled dokumentu a také dává uživateli možnost ponechat dokument otevřený na levé straně kanálu karty dokumentu. Současně lze otevřít pouze jednu otevřenou kartu náhledu. Karty náhledu mají pozadí i vybrané stavy, například otevřené karty, a lze je zaostřit nebo rozostřit v aktivním stavu.  
  
 ![Červená čára karty Náhled](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")  
  
 Použít...  
 kdekoli vytváříte předběžný náhled a chcete, aby nějaký prvek odpovídal aktuální barvě karty náhledu.  
  
Nepoužívejte ...  
- pro jakýkoli druh dokumentu nebo karty, která není prozatímní (náhled).  

- pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu.  
  
  **Vybraná karta náhledu: Zaostřeno**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Na kartu Náhled zaměřená](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Karta Fokus náhledu**|Pozadí|`Environment.FileTabProvisionalSelectedActive`|  
|![Na kartu Náhled zaměřená](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Karta Fokus náhledu**|Popředí (text)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Na kartu Náhled zaměřená](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Karta Fokus náhledu**|Ohraničení|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
|![Na kartu Náhled zaměřená](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Karta Fokus náhledu**|Ohraničení dokumentu|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Vybraná karta náhledu: Nezaostřeno**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozostřený kartě Náhled](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Karta Nezaostřený náhled**|Pozadí|`Environment.FileTabProvisionalSelectedInactive`|  
|![Rozostřený kartě Náhled](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Karta Nezaostřený náhled**|Popředí (text)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Rozostřený kartě Náhled](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Karta Nezaostřený náhled**|Ohraničení|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Rozostřený kartě Náhled](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Karta Nezaostřený náhled**|Ohraničení dokumentu|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Karta Náhled na pozadí: Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta Náhled na pozadí](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Karta Náhled na pozadí**|Pozadí|`Environment.FileTabProvisionalInactive`|  
|![Karta Náhled na pozadí](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Karta Náhled na pozadí**|Popředí (text)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Karta Náhled na pozadí](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Karta Náhled na pozadí**|Ohraničení|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
 **Karta Náhled na pozadí: Najeďte**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Náhled karty Pozadí při najetí přes](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Karta Náhled na pozadí při najetí přes**|Pozadí|`Environment.FileTabProvisionalHover`|  
|![Náhled karty Pozadí při najetí přes](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Karta Náhled na pozadí při najetí přes**|Popředí (text)|`Environment.FileTabProvisionalHoverForeground`|  
|![Náhled karty Pozadí při najetí přes](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Karta Náhled na pozadí při najetí přes**|Ohraničení|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
##### <a name="document-overflow-button"></a>Tlačítko přetečení dokumentu  
 Tlačítko přetečení dokumentu je k dispozici, pokud je otevřen jeden nebo více dokumentů, bez ohledu na to, zda je v aktuální konfiguraci svislé místo, aby se vešly všechny karty dokumentu. Rozevírací nabídka Přetečení dokumentu, která je řízena barvami **CommandBarMenu** (viz [Nabídky](../misc/shared-colors.md#BKMK_CommandMenus)), zobrazuje seznam všech otevřených dokumentů, viditelných i skrytých, a přetečení glyfů se mění v závislosti na tom, zda jsou všechny otevřené dokumenty zobrazeny v kanálu karet.  
  
 ![Přetečení redline](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")  
  
Použít...  
při vytváření vlastního tlačítka přetečení dokumentu.  

Nepoužívejte ...  
- pro uI, které není podobné tlačítko přetečení.  

- pro tlačítka přetečení panelu příkazů.  
  
  **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Přetečení](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Tlačítko přetečení dokumentu**|Pozadí|`Environment.DocWellOverflowButtonBackground`|  
|![Přetečení](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Tlačítko přetečení dokumentu**|Popředí (glyf)|`Environment.DocWellOverflowButtonGlyph`|  
|![Přetečení](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Tlačítko přetečení dokumentu**|Ohraničení|Není dostupné.|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Přetečení při vznášení](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Tlačítko přetečení dokumentu při najetí přes**|Pozadí|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Přetečení při vznášení](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Tlačítko přetečení dokumentu při najetí přes**|Popředí (glyf)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Přetečení při vznášení](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Tlačítko přetečení dokumentu při najetí přes**|Ohraničení|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Přetekli](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Tlačítko přetečení stlačeného dokumentu**|Pozadí|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Přetekli](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Tlačítko přetečení stlačeného dokumentu**|Popředí (glyf)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Přetekli](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Tlačítko přetečení stlačeného dokumentu**|Ohraničení|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Okna nástrojů  
 Není nutné replikovat okna nástrojů, protože jsou poskytovány prostředím sady Visual Studio. Můžete se však rozhodnout, že chcete využít barvy použité v oknech nástrojů tak, aby vaše ui vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.  
  
 ![Červená čára okna nástroje](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 Použít...  
 kdekoli vytváříte ui, které chcete, aby odpovídaly okna nástrojů.  
  
 Nepoužívejte ...  
 pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu.  
  
#### <a name="tool-window-frame"></a>Rám okna nástroje  
 Okna nástrojů v sadě Visual Studio se používají pro mnoho různých úkolů a mohou existovat v jednom z několika různých stavů. Pokud je okno nástroje otevřené, lze jej přiřadit k libovolné ze čtyř stran oblasti dokumentu. Okna nástrojů mohou také plavat mimo rozhraní IDE, což umožňuje jejich přemístění kdekoli na obrazovce uživatele. Plovoucí okna vždy sedět na vrcholu IDE. Nakonec mohou být okna nástrojů ukotvena jako okna dokumentu a v dokumentu se dobře zobrazí jako karta. Okna nástrojů, která byla ukotvena jako okna dokumentu, jsou částečně barevná pomocí názvů tokenů okna dokumentu.  
  
 ![Červený rámeček okna nástroje](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 Použít...  
 kdekoli vytváříte ui, které chcete, aby odpovídaly okna nástrojů.  
  
 Nepoužívejte ...  
 pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu.  
  
 **Ukotvený**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Okno nástroje ukotvené](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Pozadí|`Environment.ToolWindowBackground`|  
|![Okno nástroje ukotvené](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Ohraničení|`Environment.ToolWindowBorder`|  
  
 **Plovoucí: zaostřeno**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaostřené okno nástroje](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Pozadí|`Environment.ToolWindowBackground`|  
|![Zaostřené okno nástroje](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Ohraničení|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Plovoucí: rozostřený**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Okno nástroje rozostřené](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Pozadí|`Environment.ToolWindowBackground`|  
|![Okno nástroje rozostřené](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Ohraničení|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Záhlaví okna nástroje  
 Ohraničení záhlaví není skutečným ohraničením, ale tlustou čárou v horní části záhlaví. Nemá název tokenu pro jeho nezaostřený stav.  
  
 ![Červený řádek záhlaví okna nástroje](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 Použít...  
 kdekoli vytváříte ui, které chcete, aby odpovídaly okna nástrojů.  
  
 Nepoužívejte ...  
 pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu.  
  
 **Focused**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Záhlaví zaměřené](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Zaostřený záhlaví**|Pozadí|`Environment.TitleBarActiveGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Záhlaví zaměřené](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Zaostřený záhlaví**|Popředí (text)|`Environment.TitleBarActiveText`|  
|![Záhlaví zaměřené](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Zaostřený záhlaví**|Ohraničení|`Environment.TitleBarActiveBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
|![Záhlaví zaměřené](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Zaostřený záhlaví**|Táhlo přetažení|`Environment.TitleBarDragHandleActive`|  
  
 **Rozostřený**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Záhlaví rozostřené](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Nezaostřený záhlaví**|Pozadí|`Environment.TitleBarInactiveGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Záhlaví rozostřené](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Nezaostřený záhlaví**|Popředí (text)|`Environment.TitleBarInactiveText`|  
|![Záhlaví rozostřené](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Nezaostřený záhlaví**|Ohraničení|Není dostupné.|  
|![Záhlaví rozostřené](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Nezaostřený záhlaví**|Táhlo přetažení|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Tlačítka záhlaví  
 ![Červená čára záhlaví](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 Použít...  
 pro tlačítka, která se zobrazují v ui, která používá tokeny barev z záhlaví okna nástroje.  
  
Nepoužívejte ...  
- tlačítka, která se zobrazují v jiných umístěních.  

- v jakékoli kombinaci pozadí/popředí, než je uvedeno.  
  
  **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaostřené tlačítko záhlaví](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focused**|Pozadí|Není dostupné.|  
|![Zaostřené tlačítko záhlaví](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focused**|Popředí (glyf)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Zaostřené tlačítko záhlaví](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Focused**|Ohraničení|Není dostupné.|  
|![Tlačítko záhlaví rozostřené](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Rozostřený**|Pozadí|Není dostupné.|  
|![Tlačítko záhlaví rozostřené](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Rozostřený**|Popředí (glyf)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Tlačítko záhlaví rozostřené](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Rozostřený**|Ohraničení|Není dostupné.|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko záhlaví zaměřené na jev](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focused**|Pozadí|`Environment.ToolWindowButtonHoverActive`|  
|![Tlačítko záhlaví zaměřené na jev](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focused**|Popředí (glyf)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Tlačítko záhlaví zaměřené na jev](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Focused**|Ohraničení|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Tlačítko záhlaví rozostřené na jev](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Rozostřený**|Pozadí|`Environment.ToolWindowButtonHoverInactive`|  
|![Tlačítko záhlaví rozostřené na jev](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Rozostřený**|Popředí (glyf)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Tlačítko záhlaví rozostřené na jev](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Rozostřený**|Ohraničení|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko záhlaví zaostřené a stisknuté](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focused**|Pozadí|`Environment.ToolWindowButtonDown`|  
|![Tlačítko záhlaví zaostřené a stisknuté](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focused**|Popředí (glyf)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Tlačítko záhlaví zaostřené a stisknuté](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Focused**|Ohraničení|`Environment.ToolWindowButtonDownBorder`|  
|![Tlačítko záhlaví rozostřené a stisknuté](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Rozostřený**|Pozadí|`Environment.ToolWindowButtonDown`|  
|![Tlačítko záhlaví rozostřené a stisknuté](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Rozostřený**|Popředí (glyf)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Tlačítko záhlaví rozostřené a stisknuté](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Rozostřený**|Ohraničení|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Karty oken nástrojů  
 ![Červená karta okna nástroje](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 Použít...  
 kdekoli vytváříte ui, které chcete, aby odpovídaly okna nástrojů.  
  
 Nepoužívejte ...  
 pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu.  
  
 **Vybraná karta**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Na kartu okna nástroje](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Karta okna vybraného zaostřeného nástroje**|Pozadí|`Environment.ToolWindowTabSelectedTab`|  
|![Na kartu okna nástroje](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Karta okna vybraného zaostřeného nástroje**|Popředí (text)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Na kartu okna nástroje](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Karta okna vybraného zaostřeného nástroje**|Ohraničení|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta okna nástroje rozostřená](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Karta vybraného, nezaostřeného okna nástroje**|Pozadí|`Environment.ToolWindowTabSelectedTab`|  
|![Karta okna nástroje rozostřená](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Karta vybraného, nezaostřeného okna nástroje**|Popředí (text)|`Environment.ToolWindowTabSelectedText`|  
|![Karta okna nástroje rozostřená](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Karta vybraného, nezaostřeného okna nástroje**|Ohraničení|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
 **Karta Pozadí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta pozadí okna nástroje](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Karta okna nástroje Pozadí**|Pozadí|`Environment.ToolWindowTabGradientBegin`<br /><br /> Přechod se zastaví nastavena na stejnou hodnotu barvy v sadě Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> Přechod se zastaví nastavena na stejnou hodnotu barvy v sadě Visual Studio 2013.|  
|![Karta pozadí okna nástroje](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Karta okna nástroje Pozadí**|Popředí (text)|`Environment.ToolWindowTabText`|  
|![Karta pozadí okna nástroje](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Karta okna nástroje Pozadí**|Ohraničení|`Environment.ToolWindowTabBorder`|  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta pozadí okna nástroje při najetí přes](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okna nástroje pozadí při najetí přes**|Pozadí|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> Přechod se zastaví nastavena na stejnou hodnotu barvy v sadě Visual Studio 2013.<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> Přechod se zastaví nastavena na stejnou hodnotu barvy v sadě Visual Studio 2013.|  
|![Karta pozadí okna nástroje při najetí přes](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okna nástroje pozadí při najetí přes**|Popředí (text)|`Environment.ToolWindowTabMouseOverText`|  
|![Karta pozadí okna nástroje při najetí přes](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Karta okna nástroje pozadí při najetí přes**|Ohraničení|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Nastavte stejnou barvu jako pozadí.|  
  
#### <a name="auto-hide-tabs"></a>Automatické skrytí karet  
 ![Automatické&#45;skrytí červené čáry](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")  
  
 Použít...  
 kdekoli vytváříte ui, které chcete, aby odpovídaly auto-skryté karty okna nástroje.  
  
 Nepoužívejte ...  
 pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu.  
  
 **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Karta Automatické&#45;skrytí](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Výchozí karta automatického skrytí**|Pozadí|`Environment.AutoHideTabBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Karta Automatické&#45;skrytí](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Výchozí karta automatického skrytí**|Popředí (text)|`Environment.AutoHideTabText`|  
|![Karta Automatické&#45;skrytí](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Výchozí karta automatického skrytí**|Ohraničení|`Environment.AutoHideTabBorder`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Automatické&#45;skrýt kartu při najetí přes](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Automaticky skrýt kartu při najetí přes**|Pozadí|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Automatické&#45;skrýt kartu při najetí přes](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Automaticky skrýt kartu při najetí přes**|Popředí (text)|`Environment.AutoHideTabMouseOverText`|  
|![Automatické&#45;skrýt kartu při najetí přes](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Automaticky skrýt kartu při najetí přes**|Ohraničení|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Společné sdílené ovládací prvky  
 Při použití standardní visual studio panel příkazů ve vaší funkci, budete mít přístup k stylizované ovládací prvky prostředí a neměli byste znovu šablony těchto běžných ovládacích prvků. Pokud však potřebujete vytvořit vlastní panel příkazů, může být nutné vytvořit také vlastní ovládací prvky. V takovém případě nezapomeňte použít správné názvy tokenů pro každý z následujících ovládacích prvků tak, aby vaše rozhraní je konzistentní se zbytkem sady Visual Studio.  
  
#### <a name="search-box"></a>Vyhledávací pole  
 Kdykoli je to možné, použijte společný ovládací prvek hledání poskytované prostředí sady Visual Studio. Barvy vyhledávacího pole se nacházejí v kategorii "SearchControl" v souboru **ShellColors.pkgdef,** který obsahuje názvy tokenů pro vstupní pole, tlačítko akce, rozevírací tlačítko a rozevírací nabídku.  
  
 Vyhledávací pole může být jedním z několika stavů, z nichž některé se vzájemně vylučují:  
  
- "Focused" nebo "unfocused" označuje, zda je kurzor v textovém poli.  
  
- "Aktivní" nebo "neaktivní" označuje, zda uživatel zadal vyhledávací dotaz do textového pole.  
  
- "Najetí myší" znamená, že uživatel má myší na hledané pole (tento stav přepíše všechny ostatní stavy).  
  
- "Zakázáno" znamená, že funkce vyhledávání je vypnuta pro aktuální kontext.  
  
  ![Červené pole hledání](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")  
  
  Použít...  
  při navrhování vlastního vyhledávacího pole.  
  
  Nepoužívejte ...  
  - pro cokoliv, co není vyhledávací pole.  
  
- pro cokoliv, co nechcete vždy odpovídat ui vyhledávacího pole.  
  
  **Focused**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaměření na vstupní pole hledání](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Vstupní pole**|Pozadí|`SearchControl.FocusedBackground`|  
|![Zaměření na vstupní pole hledání](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Vstupní pole**|Popředí (text)|`SearchControl.FocusedBackground`|  
|![Zaměření na vstupní pole hledání](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Vstupní pole**|Ohraničení|`SearchControl.FocusedBorder`|  
|![Zaměření na vstupní pole hledání](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Vstupní pole**|Oddělovač|`SearchControl.FocusedDropDownSeparator`|  
|![Tlačítko akce hledání zaměřené](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Tlačítko Akce**|Pozadí|Žádný|  
|![Tlačítko akce hledání zaměřené](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Tlačítko Akce**|Popředí (Hledat glyf)|`SearchControl.SearchGlyph`|  
|![Tlačítko akce hledání zaměřené](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Tlačítko Akce**|Popředí (Stop glyf)|`SearchControl.StopGlyph`|  
|![Tlačítko akce hledání zaměřené](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Tlačítko Akce**|Popředí (Vymazat glyf)|`SearchControl.ClearGlyph`|  
|![Tlačítko akce hledání zaměřené](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Tlačítko Akce**|Ohraničení|Není dostupné.|  
|![Hledat&#45;zaostřené tlačítko dolů](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Rozevírací tlačítko**|Pozadí|`SearchControl.FocusedDropDownButton`|  
|![Hledat&#45;zaostřené tlačítko dolů](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Rozevírací tlačítko**|Popředí (glyf)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Hledat&#45;zaostřené tlačítko dolů](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Rozevírací tlačítko**|Ohraničení|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Rozostřený**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozostřené vyhledávací vstupní pole](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktivní vstupní pole**|Pozadí|`SearchControl.SearchActiveBackground`|  
|![Rozostřené vyhledávací vstupní pole](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktivní vstupní pole**|Popředí (text)|`SearchControl.SearchActiveBackground`|  
|![Rozostřené vyhledávací vstupní pole](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktivní vstupní pole**|Ohraničení|`SearchControl.UnfocusedBorder`|  
|![Rozostřené vyhledávací vstupní pole](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Aktivní vstupní pole**|Oddělovač|`SearchControl.DropDownSeparator`|  
|![Hledat vstupní pole nezaostřené a neaktivní](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Neaktivní vstupní pole**|Pozadí|`SearchControl.Unfocused`|  
|![Hledat vstupní pole nezaostřené a neaktivní](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Neaktivní vstupní pole**|Popředí (text)|`SearchControl.Unfocused`|  
|![Hledat vstupní pole nezaostřené a neaktivní](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Neaktivní vstupní pole**|Ohraničení|`SearchControl.UnfocusedBorder`|  
|![Hledat vstupní pole nezaostřené a neaktivní](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Neaktivní vstupní pole**|Oddělovač|`SearchControl.DropDownSeparator`|  
|![Tlačítko akce hledání rozostřené](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Tlačítko Akce**|Pozadí|Není dostupné.|  
|![Tlačítko akce hledání rozostřené](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Tlačítko Akce**|Popředí (Hledat glyf)|`SearchControl.SearchGlyph`|  
|![Tlačítko akce hledání rozostřené](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Tlačítko Akce**|Popředí (Stop glyf)|`SearchControl.StopGlyph`|  
|![Tlačítko akce hledání rozostřené](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Tlačítko Akce**|Popředí (Vymazat glyf)|`SearchControl.ClearGlyph`|  
|![Tlačítko akce hledání rozostřené](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Tlačítko Akce**|Ohraničení|Není dostupné.|  
|![Rozostřené tlačítko&#45;přetažení hledání](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Rozevírací tlačítko**|Pozadí|`SearchControl.UnfocusedDropDownButton`|  
|![Rozostřené tlačítko&#45;přetažení hledání](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Rozevírací tlačítko**|Popředí (glyf)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Rozostřené tlačítko&#45;přetažení hledání](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Rozevírací tlačítko**|Ohraničení|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknuto tlačítko akce Hledání](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Tlačítko Akce**|Pozadí|`SearchControl.ActionButtonMouseDown`|  
|![Stisknuto tlačítko akce Hledání](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Tlačítko Akce**|Popředí (glyf)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Stisknuto tlačítko akce Hledání](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Tlačítko Akce**|Ohraničení|`SearchControl.ActionButtonMouseDownBorder`|  
|![Hledat stisknuté tlačítko&#45;rozevírací&#45;](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Rozevírací tlačítko**|Pozadí|`SearchControl.MouseDownDropDownButton`|  
|![Hledat stisknuté tlačítko&#45;rozevírací&#45;](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Rozevírací tlačítko**|Popředí (glyf)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Hledat stisknuté tlačítko&#45;rozevírací&#45;](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Rozevírací tlačítko**|Ohraničení|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Zvýrazněno (pouze text)**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zvýraznění vstupního pole hledání](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Vstupní pole se zvýrazněným textem**|Pozadí|`SearchControl.Selection`|  
|![Zvýraznění vstupního pole hledání](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Vstupní pole se zvýrazněným textem**|Popředí (text)|`SearchControl.FocusedBackground`|  
|![Zvýraznění vstupního pole hledání](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Vstupní pole se zvýrazněným textem**|Ohraničení|Žádný|  
|![Zvýraznění vstupního pole hledání](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Vstupní pole se zvýrazněným textem**|Oddělovač|`SearchControl.FocusedDropDownSeparator`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vyhledávací vstupní pole bylo zakázáno.](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Vstupní pole**|Pozadí|`SearchControl.Disabled`|  
|![Vyhledávací vstupní pole bylo zakázáno.](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Vstupní pole**|Popředí (text)|`SearchControl.Disabled`|  
|![Vyhledávací vstupní pole bylo zakázáno.](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Vstupní pole**|Ohraničení|`SearchControl.DisabledBorder`|  
|![Vyhledávací vstupní pole bylo zakázáno.](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Vstupní pole**|Oddělovač|`SearchControl.DropDownSeparator`|  
|![Tlačítko akce hledání je zakázáno.](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Tlačítko Akce**|Pozadí|Žádný|  
|![Tlačítko akce hledání je zakázáno.](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Tlačítko Akce**|Popředí (glyf)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Tlačítko akce hledání je zakázáno.](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Tlačítko Akce**|Ohraničení|Žádný|  
|![Tlačítko Přetažení hledání&#45;vypnuto.](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Rozevírací tlačítko**|Pozadí|Žádný|  
|![Tlačítko Přetažení hledání&#45;vypnuto.](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Rozevírací tlačítko**|Popředí (glyf)|`SearchControl.DisabledDownButtonGlyph`|  
|![Tlačítko Přetažení hledání&#45;vypnuto.](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Rozevírací tlačítko**|Ohraničení|Žádný|  
  
##### <a name="search-drop-down-lists"></a>Hledat rozevírací seznamy  
 Rozevírací nabídka vyhledávacího pole má potenciál být o něco složitější než jiné rozevírací nabídky v sadě Visual Studio. Sekce "Navrhovaná hledání" a "možnosti vyhledávání" se mohou v nabídce objevit samostatně nebo společně a každá z nich je barevná samostatně. Čára také odděluje tyto dva oddíly, když se zobrazí společně a ohraničení obklopuje celou rozevírací nabídku.  
  
 ![Hledat&#45;redline](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
Použít...  
- při vytváření vlastního rozevíracího seznamu hledání.  

- správné názvy tokenů pro součásti správného seznamu.  

Nepoužívejte ...  
- pro rozevírací seznamy, které se zobrazují v jiných kontextech.  

- v jakékoli kombinaci pozadí/popředí, než je uvedeno.  
  
  **Výchozí (žádné jiné stavy)**  
  
|Element|Název tokenu: Category.color|  
|-------------|--------------------------------|  
|Ohraničení|`SearchControl.PopupBorder`|  
|Oddělovač|`SearchControl.PopupSectionHeaderSeparator`|  
|Stín|`Environment.DropShadowBackground`|  
  
 **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Navrhované hledání](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Navrhovaná hledání**|Pozadí|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Navrhované hledání](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Navrhovaná hledání**|Popředí (text)|`SearchControl.PopupItemText`|  
|![Zaškrtávací políčko Hledat](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Možnosti hledání (zaškrtávací políčko)**|Pozadí|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Možnosti hledání](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Možnosti hledání (odkaz)**|Pozadí|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Zaškrtávací políčko Hledat](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Možnosti hledání (zaškrtávací políčko)**|Popředí (text zaškrtávacího políčka)|`SearchControl.PopupCheckboxText`|  
|![Možnosti hledání](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Možnosti hledání (odkaz)**|Popředí (text zaškrtávacího políčka)|`SearchControl.PopupCheckboxText`|  
|![Zaškrtávací políčko Hledat](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Možnosti hledání (zaškrtávací políčko)**|Popředí (text odkazu)|`SearchControl.PopupButtonText`|  
|![Možnosti hledání](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Možnosti hledání (odkaz)**|Popředí (text odkazu)|`SearchControl.PopupButtonText`|  
|![Zaškrtávací políčko Hledat](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Možnosti hledání (zaškrtávací políčko)**|Pozadí záhlaví|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Možnosti hledání](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Možnosti hledání (odkaz)**|Pozadí záhlaví|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Zaškrtávací políčko Hledat](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Možnosti hledání (zaškrtávací políčko)**|Popředí (text záhlaví)|`SearchControl.PopupSectionHeaderText`|  
|![Možnosti hledání](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Možnosti hledání (odkaz)**|Popředí (text záhlaví)|`SearchControl.PopupSectionHeaderText`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hledání navrhované při najetí přes](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Navrhovaná hledání**|Pozadí|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Hledání navrhované při najetí přes](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Navrhovaná hledání**|Popředí (text)|`SearchControl.PopupMouseOverItemText`|  
|![Hledání navrhované při najetí přes](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Navrhovaná hledání**|Ohraničení|`SearchControl.PopupControlMouseOverBorder`|  
|![Vyhledávací zaškrtávací políčko při najetí přes](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Pozadí|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Možnosti hledání při najetí přes](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Možnosti hledání**|Pozadí|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Vyhledávací zaškrtávací políčko při najetí přes](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Popředí (text zaškrtávacího políčka)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Možnosti hledání při najetí přes](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Možnosti hledání**|Popředí (text zaškrtávacího políčka)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Vyhledávací zaškrtávací políčko při najetí přes](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Popředí (text odkazu)|`SearchControl.PopupButtonMouseDownText`|  
|![Možnosti hledání při najetí přes](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Možnosti hledání**|Popředí (text odkazu)|`SearchControl.PopupButtonMouseDownText`|  
|![Vyhledávací zaškrtávací políčko při najetí přes](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Ohraničení|`SearchControl.PopupControlMouseOverBorder`|  
|![Možnosti hledání při najetí přes](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Možnosti hledání**|Ohraničení|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hledání navrhované stisknuté](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Pozadí zaškrtávacího políčka|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Stisknuté možnosti hledání](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Možnosti hledání**|Pozadí zaškrtávacího políčka|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Hledání navrhované stisknuté](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Pozadí zaškrtávacího políčka|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Stisknuté možnosti hledání](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Možnosti hledání**|Pozadí zaškrtávacího políčka|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Hledání navrhované stisknuté](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Popředí (text zaškrtávacího políčka)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Stisknuté možnosti hledání](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Možnosti hledání**|Popředí (text zaškrtávacího políčka)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Hledání navrhované stisknuté](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Propojit pozadí|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Stisknuté možnosti hledání](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Možnosti hledání**|Propojit pozadí|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> I když se nepoužívá v moderním tematizovaném uzly, jsou přechodové zarážky a hodnoty pro toto pozadí.|  
|![Hledání navrhované stisknuté](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Navrhovaná hledání (zaškrtávací políčko)**|Popředí (text odkazu)|`SearchControl.PopupButtonMouseDownText`|  
|![Stisknuté možnosti hledání](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Možnosti hledání**|Popředí (text odkazu)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Hypertextový odkaz  
 Hypertextový odkaz je jeden ovládací prvek, který nemá dvojici popředí nebo pozadí. Ve všech případech použijte barvu hypertextového odkazu v popředí, která se na tmavém, šedém a bílém pozadí zobrazí správně. Pokud nepoužijete token barvy pro ovládací prvek hypertextového odkazu, zobrazí se výchozí barva systému pro "stisknuté", která bude blikat červeně. To je signál, že ovládací prvek nepoužívá token barvy správné prostředí.  
  
 ![Červená čára hypertextového odkazu](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 Použít...  
 když potřebujete vytvořit vlastní hypertextový odkaz.  
  
 Nepoužívejte ...  
 pro cokoliv, co není hypertextový odkaz.  
  
 **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Výchozí odkaz hypertextového odkazu](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")|Popředí (text)|`Environment.PanelHyperlink`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hypertextový odkaz na najetí přes](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")|Popředí (text)|`Environment.PanelHyperlinkHover`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hypertextový odkaz stisknutý](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")|Popředí (text)|`Environment.PanelHyperlinkPressed`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hypertextový odkaz je zakázán.](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")|Popředí (text)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Informační panel  
 Informační panely slouží k poskytnutí dalších informací o daném kontextu a vždy se zobrazují v horní části okna dokumentu nebo okna nástroje.  
  
 ![Červená čára informačního panelu](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")  
  
 Použít...  
 při vytváření vlastních informačních panelů.  
  
 Nepoužívejte ...  
 pro prvky uživatelského rozhraní, které nejsou podobné informačnímu panelu.  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Informační panel](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Informační panel**|Pozadí|`Environment.InfoBackground`|  
|![Informační panel](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Informační panel**|Popředí (text)|`Environment.InfoText`|  
|![Informační panel](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Informační panel**|Ohraničení|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Posuvník  
 Posuvníky jsou stylizovány prostředím sady Visual Studio a nebude nutné tématické. Můžete se však rozhodnout, že chcete využít barvy použité v posuvnících tak, aby vaše ui vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.  
  
 ![Červený pruh posouvání](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 Použít...  
 při vytváření ui, které chcete, aby odpovídaly Visual Studio posuvníky.  
  
 Nepoužívejte ...  
 pro cokoli, co nechcete vždy odpovídat scrollbar uI.  
  
 **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Posuvník](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Posuvník**|Posuvník|`Environment.ScrollBarBackground`|  
|![Posuvník](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Posuvník**|Popředí (palec)|`Environment.ScrollBarThumbBackground`|  
|![Šipka posuvníku](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Šipka posuvníku**|Pozadí|`Environment.ScrollBarArrowBackground`<br /><br /> Nastavte stejnou barvu jako posuvník.|  
|![Šipka posuvníku](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Šipka posuvníku**|Popředí (glyf)|`Environment.ScrollBarArrowGlyph`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Posuvník při přechodu](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Posuvník**|Posuvník|`Environment.ScrollBarBackground`|  
|![Posuvník při přechodu](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Posuvník**|Popředí (palec)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![Šipka posuvníku při přechodu](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Šipka posuvníku**|Pozadí|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Nastavte stejnou barvu jako posuvník.|  
|![Šipka posuvníku při přechodu](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Šipka posuvníku**|Popředí (glyf)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Posuvník stisknutý](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Posuvník**|Posuvník|`Environment.ScrollBarBackground`|  
|![Posuvník stisknutý](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Posuvník**|Popředí (palec)|`Environment.ScrollBarThumbPressedBackground`|  
|![Stisknutá šipka posuvníku](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Šipka posuvníku**|Pozadí|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Nastavte stejnou barvu jako posuvník.|  
|![Stisknutá šipka posuvníku](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Šipka posuvníku**|Popředí (glyf)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="tree-view"></a><a name="BKMK_TreeView"></a>Stromové zobrazení  
 Několik oken nástrojů, včetně Průzkumníka řešení, Průzkumníka serveru a zobrazení tříd, implementuje hierarchické organizační schéma, jehož barvy jsou řízeny názvy barev v kategorii TreeView. Všechny položky ve stromovém zobrazení mají barvy pozadí a textu. Položky, které mají vnořené podřízené prvky, mají také glyfy, které označují, zda je položka rozbalena nebo sbalena.  
  
 ![Červená čára stromového zobrazení](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")  
  
 Použít...  
 kdekoli potřebujete implementovat hierarchické organizační zobrazení.  
  
Nepoužívejte ...  
- pro cokoli, co není podobné stromové zobrazení.  

- v jakékoli kombinaci pozadí/popředí, než je uvedeno.  
  
  **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stromové zobrazení](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Pozadí|`TreeView.Background`|  
|![Stromové zobrazení](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Popředí (text)|`TreeView.Background`|  
|![Stromové zobrazení](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Popředí (glyf)|`TreeView.Glyph`|  
|![Stromové zobrazení](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Ohraničení|Žádný|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stromový pohled na vznášení](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Pozadí|`TreeView.Background`|  
|![Stromový pohled na vznášení](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Popředí (text)|`TreeView.Background`|  
|![Stromový pohled na vznášení](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Popředí (glyf)|`TreeView.GlyphMouseOver`|  
|![Stromový pohled na vznášení](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Ohraničení|Žádný|  
  
 **Přetažení**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Přetažení stromového zobrazení](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Pozadí|`TreeView.DragOverItem`|  
|![Přetažení stromového zobrazení](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Popředí (text)|`TreeView.DragOverItem`|  
|![Přetažení stromového zobrazení](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Popředí (glyf)|`TreeView.DragOverItemGlyph`|  
|![Přetažení stromového zobrazení](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Ohraničení|Žádný|  
  
 **Vybráno**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stromové zobrazení zaměřené](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|Pozadí|`TreeView.SelectedItemActive`|  
|![Stromové zobrazení zaměřené](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|Popředí (text)|`TreeView.SelectedItemActive`|  
|![Stromové zobrazení zaměřené](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|Popředí (glyf)|`TreeView.SelectedItemActiveGlyph`|  
|![Stromové zobrazení zaměřené](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Focused**|Ohraničení|`TreeView.FocusVisualBorder`|  
|![Stromové zobrazení rozostřené](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Rozostřený**|Pozadí|`TreeView.SelectedItemInactive`|  
|![Stromové zobrazení rozostřené](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Rozostřený**|Popředí (text)|`TreeView.SelectedItemInactive`|  
|![Stromové zobrazení rozostřené](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Rozostřený**|Popředí (glyf)|`TreeView.SelectedItemInactiveGlyph`|  
|![Stromové zobrazení rozostřené](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Rozostřený**|Ohraničení|Žádný|  
  
 **Najet přes vybranou položku**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stromové zobrazení zaměřené na vznášení](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|Pozadí|`TreeView.SelectedItemActive`|  
|![Stromové zobrazení zaměřené na vznášení](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|Popředí (text)|`TreeView.SelectedItemActive`|  
|![Stromové zobrazení zaměřené na vznášení](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|Popředí (glyf)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Stromové zobrazení zaměřené na vznášení](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Focused**|Ohraničení|Žádný`TreeView.FocusVisualBorder`|  
|![Stromové zobrazení nezaostřené na hover](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Rozostřený**|Pozadí|`TreeView.SelectedItemInactive`|  
|![Stromové zobrazení nezaostřené na hover](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Rozostřený**|Popředí (text)|`TreeView.SelectedItemInactive`|  
|![Stromové zobrazení nezaostřené na hover](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Rozostřený**|Popředí (glyf)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Stromové zobrazení nezaostřené na hover](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Rozostřený**|Ohraničení|Žádný|  
  
#### <a name="button-controls"></a>ovládací prvky tlačítek  
 ![Červená čára ovládání tlačítka](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 Použít...  
 pro tlačítka v dokumentu dobře, že chcete integrovat s motivy Sady Visual Studio (světlá, tmavá, modrá nebo systém vysoký kontrast motiv).  
  
 Nepoužívejte ...  
 pro tlačítka, která se zobrazí na vlastním pozadí, který není součástí motivu sady Visual Studio.  
  
 **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Tlačítko|`CommonControls.Button`|  
|![Tlačítko](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Ohraničení tlačítka|`CommonControls.ButtonBorder`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko bylo zakázáno.](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Tlačítko|`CommonControls.ButtonDisabled`|  
|![Tlačítko bylo zakázáno.](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Ohraničení tlačítka|`CommonControls.ButtonBorderDisabled`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko při najetí přes](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Tlačítko|`CommonControls.ButtonHover`|  
|![Tlačítko při najetí přes](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Ohraničení tlačítka|`CommonControls.ButtonBorderHover`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Stisknuté tlačítko](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Tlačítko|`CommonControls.ButtonPressed`|  
|![Stisknuté tlačítko](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Ohraničení tlačítka|`CommonControls.ButtonBorderPressed`|  
  
 **Focused**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tlačítko zaměřené](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Tlačítko|`CommonControls.ButtonFocused`|  
|![Tlačítko zaměřené](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Ohraničení tlačítka|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Ovládací prvky zaškrtávacího políčka  
 ![Zaškrtávací políčko červená čára](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")  
  
 Použít...  
 pro ovládací prvky zaškrtávacích pokoncích obsažených v dokumentu.  
  
 Nepoužívejte ...  
 pro jakékoli ui, které není ovládací prvek zaškrtávací políčko.  
  
 **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Políčko](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Pozadí|`CommonControls.CheckBoxBackground`|  
|![Políčko](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Ohraničení|`CommonControls.CheckBoxBorder`|  
|![Políčko](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Text|`CommonControls.CheckBoxText`|  
|![Políčko](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Glyfů|`CommonControls.CheckBoxGlyph`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaškrtávací políčko je zakázáno](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Pozadí|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Zaškrtávací políčko je zakázáno](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Ohraničení|`CommonControls.CheckBoxBorderDisabled`|  
|![Zaškrtávací políčko je zakázáno](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Text|`CommonControls.CheckBoxTextDisabled`|  
|![Zaškrtávací políčko je zakázáno](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Glyfů|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaškrtávací políčko při najetí přes](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Pozadí|`CommonControls.CheckBoxBackgroundHover`|  
|![Zaškrtávací políčko při najetí přes](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Ohraničení|`CommonControls.CheckBoxBorderHover`|  
|![Zaškrtávací políčko při najetí přes](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Text|`CommonControls.CheckBoxTextHover`|  
|![Zaškrtávací políčko při najetí přes](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Glyfů|`CommonControls.CheckBoxGlyphHover`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bylo stisknuto zaškrtávací políčko](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Pozadí|`CommonControls.CheckBoxBackgroundPressed`|  
|![Bylo stisknuto zaškrtávací políčko](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Ohraničení|`CommonControls.CheckBoxBorderPressed`|  
|![Bylo stisknuto zaškrtávací políčko](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Text|`CommonControls.CheckBoxTextPressed`|  
|![Bylo stisknuto zaškrtávací políčko](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Glyfů|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Focused**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Zaškrtávací políčko zaměřené](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Pozadí|`CommonControls.CheckBoxBackgroundFocused`|  
|![Zaškrtávací políčko zaměřené](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Ohraničení|`CommonControls.CheckBoxBorderFocused`|  
|![Zaškrtávací políčko zaměřené](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Text|`CommonControls.CheckBoxTextFocused`|  
|![Zaškrtávací políčko zaměřené](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Glyfů|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Ovládací prvky s vybalením/pole se seznamem  
 ![Rozbalit&#45;dolů&#47;pole se seznamem redline](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
Použít...  
pro rozevírací seznamy a seznamy, které jsou součástí dokumentu dobře.  

Nepoužívejte ...  
- pro jakékoli ui, které není rozevírací seznam nebo pole se seznamem.  

- pro [rozevírací](../misc/shared-colors.md#BKMK_CommandDropDown) seznam nebo [pole se seznamem](../misc/shared-colors.md#BKMK_CommandComboBox) na panelu příkazů.  
  
  **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozbalit&#45;dolů&#47;pole se seznamem](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Pozadí|`CommonControls.ComboBoxBackground`|  
|![Rozbalit&#45;dolů&#47;pole se seznamem](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Ohraničení|`CommonControls.ComboBoxBorder`|  
|![Rozbalit&#45;dolů&#47;pole se seznamem](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Text|`CommonControls.ComboBoxText`|  
|![Rozbalit&#45;dolů&#47;pole se seznamem](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Oddělovač|`CommonControls.ComboBoxSeparator`|  
|![Rozbalit&#45;dolů&#47;pole se seznamem](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Glyfů|`CommonControls.ComboBoxGlyph`|  
|![Rozbalit&#45;dolů&#47;pole se seznamem](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Pozadí glyfů|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Disabled** (Zakázáno)  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;dolů&#47;pole se seznamem zakázáno](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Pozadí|`CommonControls.ComboBoxBackgroundDisabled`|  
|![Drop&#45;dolů&#47;pole se seznamem zakázáno](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Ohraničení|`CommonControls.ComboBoxBorderDisabled`|  
|![Drop&#45;dolů&#47;pole se seznamem zakázáno](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Text|`CommonControls.ComboBoxTextDisabled`|  
|![Drop&#45;dolů&#47;pole se seznamem zakázáno](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Oddělovač|`CommonControls.ComboBoxSeparatorDisabled`|  
|![Drop&#45;dolů&#47;pole se seznamem zakázáno](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Glyfů|`CommonControls.ComboBoxGlyphDisabled`|  
|![Drop&#45;dolů&#47;pole se seznamem zakázáno](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Pozadí glyfů|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozbalit&#45;dolů&#47;pole se seznamem při hoveru](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Pozadí|`CommonControls.ComboBoxBackgroundHover`|  
|![Rozbalit&#45;dolů&#47;pole se seznamem při hoveru](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Ohraničení|`CommonControls.ComboBoxBorderHover`|  
|![Rozbalit&#45;dolů&#47;pole se seznamem při hoveru](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Text|`CommonControls.ComboBoxTextHover`|  
|![Rozbalit&#45;dolů&#47;pole se seznamem při hoveru](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Oddělovač|`CommonControls.ComboBoxSeparatorHover`|  
|![Rozbalit&#45;dolů&#47;pole se seznamem při hoveru](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Glyfů|`CommonControls.ComboBoxGlyphHover`|  
|![Rozbalit&#45;dolů&#47;pole se seznamem při hoveru](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Pozadí glyfů|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Spadnout&#45;dolů&#47;combo box stisknuto](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Pozadí|`CommonControls.ComboBoxBackgroundPressed`|  
|![Spadnout&#45;dolů&#47;combo box stisknuto](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Ohraničení|`CommonControls.ComboBoxBorderPressed`|  
|![Spadnout&#45;dolů&#47;combo box stisknuto](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Text|`CommonControls.ComboBoxTextPressed`|  
|![Spadnout&#45;dolů&#47;combo box stisknuto](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Oddělovač|`CommonControls.ComboBoxSeparatorPressed`|  
|![Spadnout&#45;dolů&#47;combo box stisknuto](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Glyfů|`CommonControls.ComboBoxGlyphPressed`|  
|![Spadnout&#45;dolů&#47;combo box stisknuto](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Pozadí glyfů|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Focused**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Drop&#45;dolů&#47;pole se seznamem zaměřené](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Pozadí|`CommonControls.ComboBoxBackgroundFocused`|  
|![Drop&#45;dolů&#47;pole se seznamem zaměřené](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Ohraničení|`CommonControls.ComboBoxBorderFocused`|  
|![Drop&#45;dolů&#47;pole se seznamem zaměřené](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Text|`CommonControls.ComboBoxTextFocused`|  
|![Drop&#45;dolů&#47;pole se seznamem zaměřené](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Oddělovač|`CommonControls.ComboBoxSeparatorFocused`|  
|![Drop&#45;dolů&#47;pole se seznamem zaměřené](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Glyfů|`CommonControls.ComboBoxGlyphFocused`|  
|![Drop&#45;dolů&#47;pole se seznamem zaměřené](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Pozadí glyfů|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Výběr vstupu textu**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Rozesílání&#45;dolů&#47;vstupu pole se seznamem](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")|Zvýraznit|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Lisované – zobrazení položky seznamu**  
  
|Komponenta|Element|Název tokenu: Color.category|  
|---------------|-------------|--------------------------------|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Pozadí|`CommonControls.ComboBoxListBackground`|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Pozadí|`CommonControls.ComboBoxListBackgroundHover`|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Pozadí|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Pozadí|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Ohraničení|`CommonControls.ComboBoxListBorder`|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Ohraničení|`CommonControls.ComboBoxListBorderHover`|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Ohraničení|`CommonControls.ComboBoxListBorderPressed`|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Ohraničení|`CommonControls.ComboBoxListBorderFocused`|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Text položky|`CommonControls.ComboBoxListItemText`|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Text položky|`CommonControls.ComboBoxListItemTextHover`|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Text položky|`CommonControls.ComboBoxListItemTextPressed`|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Text položky|`CommonControls.ComboBoxListItemTextFocused`|  
|![Rozepsat&#45;zobrazení seznamu se seznamem&#47;](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Stín pozadí|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Ovládací prvky tabulkových dat (mřížka)  
 Ovládací prvky tabulkových dat, označované také jako ovládací prvky mřížky, jsou běžné ovládací prvky pro sady Visual Studio, které lze použít k prezentaci velkého množství dat ve více sloupcích. Standardní ovládací prvky tabulkových dat lze nalézt na více místech v rámci sady Visual Studio: okno nástroje Seznam chyb, sestavy IntelliTrace a zobrazení haldy paměti. Vždy používejte standardní ovládací prvky tabulkových dat. V některých výjimečných případech pravděpodobně nemáte přístup ke standardním ovládacím prvkům tabulkových dat. V těchto situacích použijte následující názvy tokenů, abyste zajistili, že vaše rozhraní je konzistentní s ostatními ovládacími prvky tabulkových dat v sadě Visual Studio.  
  
 ![Ovládací prvek&#41;&#41; červené čáry&#41; ovládacího prvku tabulkových dat &#40;](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 Použít...  
 pro tabulkové ovládací prvky nebo ovládací prvky mřížky.  
  
 Nepoužívejte ...  
 pro jakékoli ui, které není tabulkové nebo mřížky ovládací prvek.  
  
##### <a name="column-headers"></a>Záhlaví sloupců  
 Záhlaví sloupců se skládají z pozadí, ohraničení, textu nadpisu a volitelného glyfu, který se obvykle používá při seřazení mřížky podle tohoto sloupce.  
  
|Stav|Element|Název tokenu: Category.color|  
|-----------|-------------|--------------------------------|  
|Výchozí|Pozadí|`Header.Default`|  
|Výchozí|Popředí (text)|`Environment.CommandBarTextActive`|  
|Výchozí|Popředí (glyf)|`Header.Glyph`|  
|Výchozí|Ohraničení|`Header.SeparatorLine`|  
|Hover|Pozadí|`Header.MouseOver`|  
|Hover|Popředí (text)|`Environment.CommandBarTextHover`|  
|Hover|Popředí (glyf)|`Header.MouseOverGlyph`|  
|Hover|Ohraničení|`Header.SeparatorLine`|  
|Pressed|Pozadí|`CommonControls.CheckBoxBackgroundPressed`|  
|Pressed|Popředí (text)|`CommonControls.CheckBoxBorderPressed`|  
|Pressed|Popředí (glyf)|`CommonControls.CheckBoxTextPressed`|  
|Pressed|Ohraničení|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Položky zobrazení seznamu  
 Položky zobrazení seznamu se skládají z pozadí a obsahu. Obsah může být text, ikona nebo obojí.  
  
|Stav|Element|Název tokenu: Category.color|  
|-----------|-------------|--------------------------------|  
|Výchozí|Pozadí|Průhlednost|  
|Výchozí|Popředí (text)|`Environment.CommandBarTextActive`|  
|Výchozí|Ohraničení|Žádný|  
|Vybráno (aktivní)|Pozadí|`TreeView.SelectedItemActive`|  
|Vybráno (aktivní)|Popředí (text)|`TreeView.SelectedItemActiveText`|  
|Vybráno (aktivní)|Ohraničení|Žádný|  
|Vybráno (neaktivní)|Pozadí|`TreeView.SelectedItemInactive`|  
|Vybráno (neaktivní)|Popředí (text)|`TreeView.SelectedItemInactiveText`|  
|Vybráno (neaktivní)|Ohraničení|Žádný|  
  
### <a name="manifest-designer"></a>Návrhář manifestu  
 Návrhář manifestu byl navržen jako způsob, jak usnadnit úpravy souboru manifestu v projektech Windows 8 a Windows Phone 8. I když není k dispozici žádná sdílená architektura pro spotřebu, může být vhodné, abyste odpovídali rozložení návrhu a barvy karet orientace/navigace a celkové struktury. Další informace o podrobnostech rozložení naleznete v [tématu Layout for Visual Studio](../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Redline návrháře manifestu](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
Použít...  
- pro návrháře, které jsou podobné Návrhář manifestu.  

- místo použití běžných ovládacích prvků tabulátoru v horní části editoru v dokumentu dobře.  

Nepoužívejte ...  
- pokud máte více než šest záložek.  

- pro jakékoli ui, které není strukturováno jako Návrhář manifestu.  
  
|Stav|Komponenta|Element|Název tokenu: Category.color|  
|-----------|---------------|-------------|--------------------------------|  
|Výchozí (vybráno)|Karta|Pozadí|`ManifestDesigner.TabActive`|  
|Výchozí (vybráno)|Karta|Ohraničení|Žádný|  
|Výchozí (vybráno)|Podokno Popis|Pozadí|`ManifestDesigner.DescriptionPane`|  
|Výchozí (vybráno)|Stránka obsahu|Pozadí|`ManifestDesigner.Background`|  
|Výchozí (vybráno)|Stránka obsahu|Text pomocníka dialogu|`ManifestDesigner.WatermarkText`<br /><br /> Tento název tokenu neodpovídá jeho funkci.|  
|Nevybráno|Karta|Pozadí|`ManifestDesigner.Tab.Inactive`|  
|Hover|Karta|Pozadí|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Označování  
 Visual Studio podporuje označování, které umožňuje uživateli deklarovat prohledávatelná klíčová slova pro účely sledování. Například projektoví manažeři a vývojáři mohou použít Team Foundation Server (TFS) k označení pracovních položek. Níže uvedené tabulky udávají názvy barev pro samotnou značku i glyf "zavřít ikonu", který se zobrazí v režimu umístění v měřítku a vybraných stavech.  
  
 ![Označení červené čáry](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")  
  
 Použít...  
 pro ui, které podporuje označování.  
  
 Nepoužívejte ...  
 pro jakýkoli jiný typ ui.  
  
#### <a name="tag"></a>Značka  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Značku](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Výchozí**|Pozadí|`Tag.Background`|  
|![Značku](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Výchozí**|Popředí (text)|`Tag.Background`|  
|![Značka při najetí přes](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Hover**|Pozadí|`Tag.HoverBackground`|  
|![Značka při najetí přes](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Hover**|Popředí (text)|`Tag.HoverBackgroundText`|  
|![Stisknutá značka](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Pressed**|Pozadí|`Tag.PressedBackground`|  
|![Stisknutá značka](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Pressed**|Popředí (text)|`Tag.PressedBackgroundText`|  
|![Značka byla vybrána.](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Vybráno**|Pozadí|`Tag.SelectedBackground`|  
|![Značka byla vybrána.](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Vybráno**|Popředí (text)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Glyf (ikona zavření)  
 **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#41;glyfů &#40;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Výchozí (výchozí značka)**|Pozadí|Není dostupné.|  
|![&#41;glyfů &#40;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Výchozí (výchozí značka)**|Popředí (glyf)|`Tag.TagHoverGlyph`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Značka &#40;&#41; při najetí](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Najetí přes (výchozí značka)**|Pozadí|`Tag.TagHoverGlyphHoverBackground`|  
|![Značka &#40;&#41; při najetí](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Najetí přes (výchozí značka)**|Popředí (glyf)|`Tag.TagHoverGlyphHover`|  
|![Značka &#40;&#41; při najetí](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Najetí přes (výchozí značka)**|Ohraničení|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag &#40;glyf&#41; stisknutí](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Stisknuto (výchozí značka)**|Pozadí|`Tag.TagHoverGlyphPressedBackground`|  
|![Tag &#40;glyf&#41; stisknutí](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Stisknuto (výchozí značka)**|Popředí (glyf)|`Tag.TagHoverGlyphPressed`|  
|![Tag &#40;glyf&#41; stisknutí](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Stisknuto (výchozí značka)**|Ohraničení|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Značka byla vybrána/glyph výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Značka byla vybrána.](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Výchozí (vybraná značka)**|Pozadí|Není dostupné.|  
|![Značka byla vybrána.](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Výchozí (vybraná značka)**|Popředí (glyf)|`Tag.TagSelectedGlyph`|  
  
 **Tag selected/glyph hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Značka vybraná při najetí přes](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Najetí přes (vybraný tag)**|Pozadí|`Tag.TagSelectedGlyphHoverBackground`|  
|![Značka vybraná při najetí přes](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Najetí přes (vybraný tag)**|Popředí (glyf)|`Tag.TagSelectedGlyphHover`|  
|![Značka vybraná při najetí přes](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Najetí přes (vybraný tag)**|Ohraničení|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Tag selected/glyph pressed**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Vybraný tag byl stisknutý.](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Stisknuto (značka vybrána)**|Pozadí|`Tag.TagSelectedGlyphPressedBackground`|  
|![Vybraný tag byl stisknutý.](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Stisknuto (značka vybrána)**|Popředí (glyf)|`Tag.TagSelectedGlyphPressed`|  
|![Vybraný tag byl stisknutý.](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Stisknuto (značka vybrána)**|Ohraničení|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Prostředí  
  
#### <a name="background"></a>Pozadí  
 Pozadí prostředí se skládá ze dvou vrstev. Spodní vrstva je plná barva, která pokrývá celé ide. Horní vrstva se vejde pod polici příkazu a mezi okno nástroje automaticky skrýt kanály na levém a pravém okraji ide. Od Visual Studia 2013 jsou horní a dolní vrstvy pozadí nastaveny na stejnou barvu v motivech Světlé a Tmavé.  
  
 ![Červená čára pozadí prostředí](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 Použít...  
 pro místa, která mají odpovídat pozadí prostředí sady Visual Studio.  
  
Nepoužívejte ...  
- jako výplň pro místa, která nejsou povrchy pozadí.  

- jako pozadí, na které chcete umístit prvky popředí.  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|Spodní vrstva|Pozadí|`Environment.EnvironmentBackground`|  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|Horní vrstva|Pozadí<br /><br /> *Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Horní vrstva|Pozadí<br /><br /> *Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Horní vrstva|Pozadí<br /><br /> *Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Horní vrstva|Pozadí<br /><br /> *Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Příkazová police  
 Pro pozadí policí příkazu se používají dvě sady názvů tokenů: jedna sada pro místo, kde je na řádku nabídek, a druhá pro místo, kde jsou tyče příkazů. Jednotlivé skupiny panelů příkazů mají vlastní hodnoty barev pozadí, které jsou podrobněji popsány v části "panel příkazů". Panel nabídek a text panelu příkazů je popsán v sekcích nabídek a panelu příkazů.  
  
 ![Redline police příkazu](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")  
  
Použít...  
- pro oblasti, kam umístíte nabídky nebo panely nástrojů.  

- se správnou kombinací názvů tokenů pozadí/ popředí.  
  
  Nepoužívejte ...  
  pro oblasti, které nejsou podobné příkazu police.  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|Nabídek|Pozadí<br /><br /> *Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Nabídek|Pozadí<br /><br /> *Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Nabídek|Pozadí<br /><br /> *Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Panel příkazů|Pozadí<br /><br /> *Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Panel příkazů|Pozadí<br /><br /> *Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Panel příkazů|Pozadí<br /><br /> *Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Sada nástrojů  
 Panel nástrojů je jedním z běžných oken nástrojů, který se nejčastěji používá v sadě Visual Studio. Jedná se v podstatě o stromový ovládací prvek se speciálním tématem a použitým stylem.  
  
 ![Červená čára panelu nástrojů](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")  
  
 Použít...  
 při navrhování okna nástroje, které chcete vždy konzistentní s panelem nástrojů skořepiny.  
  
 Nepoužívejte ...  
 pro cokoli, co není podobné uj.  
  
 **Výchozí**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nadřazený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nadřazený uzel**|Pozadí|`Environment.ToolboxContent`<br /><br /> Nadpisy<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Jednotlivé položky nebo celé okno, pokud nejsou k dispozici žádné ovládací prvky|  
|![Podřízený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Podřízený uzel**|Pozadí|`Environment.ToolboxContent`<br /><br /> Nadpisy<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Jednotlivé položky nebo celé okno, pokud nejsou k dispozici žádné ovládací prvky|  
|![Nadřazený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nadřazený uzel**|Ohraničení|Žádný|  
|![Podřízený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Podřízený uzel**|Ohraničení|Žádný|  
|![Nadřazený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nadřazený uzel**|Popředí (glyf)|`Environment.ToolboxContent`|  
|![Podřízený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Podřízený uzel**|Popředí (glyf)|`Environment.ToolboxContent`|  
|![Nadřazený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Nadřazený uzel**|Popředí (text)|`Environment.ToolboxContent`|  
|![Podřízený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Podřízený uzel**|Popředí (text)|`Environment.ToolboxContent`|  
  
 **Hover**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Podřízený uzel panelu nástrojů při najetí](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Panel nástrojů napodačit podřízený uzel**|Pozadí|`Environment.ToolboxContentMouseOver`<br /><br /> Pouze jednotlivé položky|  
|![Podřízený uzel panelu nástrojů při najetí](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Panel nástrojů napodačit podřízený uzel**|Ohraničení|Žádný|  
|![Podřízený uzel panelu nástrojů při najetí](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Panel nástrojů napodačit podřízený uzel**|Popředí (text)|`Environment.ToolboxContentMouseOver`<br /><br /> Pouze jednotlivé položky|  
  
 **Vybráno**  
  
|Komponenta|Element|Název tokenu: Category.color|  
|---------------|-------------|--------------------------------|  
|![Nadřazený uzel panelu nástrojů zaměřený](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Cílový nadřazený uzel**|Pozadí|`TreeView.SelectedItemActive`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Podřízený uzel panelu nástrojů zaměřený](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Soustředěný podřízený uzel**|Pozadí|`TreeView.SelectedItemActive`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Nadřazený uzel panelu nástrojů zaměřený](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Cílový nadřazený uzel**|Ohraničení|`TreeView.FocusVisualBorder`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Podřízený uzel panelu nástrojů zaměřený](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Soustředěný podřízený uzel**|Ohraničení|`TreeView.FocusVisualBorder`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Nadřazený uzel panelu nástrojů zaměřený](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Cílový nadřazený uzel**|Popředí (glyf)|`TreeView.SelectedItemActive`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Podřízený uzel panelu nástrojů zaměřený](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Soustředěný podřízený uzel**|Popředí (glyf)|`TreeView.SelectedItemActive`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Nadřazený uzel panelu nástrojů zaměřený](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Cílový nadřazený uzel**|Popředí (text)|`TreeView.SelectedItemActive`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Podřízený uzel panelu nástrojů zaměřený](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Soustředěný podřízený uzel**|Popředí (text)|`TreeView.SelectedItemActive`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Nezaostřený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nezaostřený nadřazený uzel**|Pozadí|`TreeView.SelectedItemInactive`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Nezaostřený podřízený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nezaostřený podřízený uzel**|Pozadí|`TreeView.SelectedItemInactive`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Nezaostřený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nezaostřený nadřazený uzel**|Ohraničení|Žádný|  
|![Nezaostřený podřízený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nezaostřený podřízený uzel**|Ohraničení|Žádný|  
|![Nezaostřený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nezaostřený nadřazený uzel**|Popředí (glyf)|`TreeView.SelectedItemInactive`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Nezaostřený podřízený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nezaostřený podřízený uzel**|Popředí (glyf)|`TreeView.SelectedItemInactive`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Nezaostřený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Nezaostřený nadřazený uzel**|Popředí (text)|`TreeView.SelectedItemInactive`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
|![Nezaostřený podřízený uzel panelu nástrojů](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Nezaostřený podřízený uzel**|Popředí (text)|`TreeView.SelectedItemInactive`<br /><br /> Ze [stromové](../misc/shared-colors.md#BKMK_TreeView) kategorie|  
  
## <a name="color-value-reference"></a>Odkaz na hodnotu barvy  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|Komponenta|Část|Element|Stav|Světlý|Tmavý|Blue|Vysoký kontrast|  
|Dělicí čáry|||Výchozí|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|Glyf expanderu||Popředí|Výchozí|||||  
|Glyf expanderu||Popředí|Hover|||||  
|Glyf expanderu||Pozadí|Výchozí|||||  
|Glyf expanderu||Pozadí|Hover|||||  
|Glyf expanderu||Ohraničení|Výchozí|||||  
|Glyf expanderu||Ohraničení|Hover|||||