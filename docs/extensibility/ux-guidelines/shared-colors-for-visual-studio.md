---
title: Sdílené barvy pro visual studio | Dokumenty společnosti Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e31e5d9c3d1dc284694bd2db2a9f37d863462ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699933"
---
# <a name="shared-colors-for-visual-studio"></a>Sdílené barvy pro Visual Studio
Při navrhování uživatelského rozhraní, které používá běžné prvky prostředí sady Visual Studio, nebo chcete, aby byl prvek rozhraní konzistentní s podobnými funkcemi, použijte existující názvy tokenů v souborech definice balíčku k výběru a přiřazení barev. Tím zajistíte, že vaše ui zůstane konzistentní s celkovým prostředím sady Visual Studio a že se automaticky aktualizuje při přidání nebo aktualizaci motivů.

Tento článek popisuje běžné prvky uživatelského rozhraní a názvy tokenů, které používají, na které můžete odkazovat při vytváření podobného uživatelského rozhraní. Konkrétní informace o tom, jak získat přístup k těmto tokenům barev, naleznete [v tématu VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Ujistěte se, že používáte názvy tokenů správně:

- **Používejte názvy tokenů na základě funkce, nikoli na samotné barvě.** Společné sdílené barvy jsou přidruženy k určitým prvkům rozhraní a jsou určeny pouze pro stejné nebo podobné funkce. Například nepoužívejte znovu barvu lisovaného pole se seznamem pro animaci průběhu otáčení jen proto, že se vám barva líbí. Funkce pole se seznamem a animace se liší a pokud se změní barva přidružená k poli se seznamem, nemusí to být vhodná barva pro prvek animace. Konzistentní používání barev pomáhá orientovat uživatele a zabránit nejasnostem.

- **Používejte barvy pozadí a textu ve správné kombinaci.** Barvy pozadí, které jsou určeny k použití s textem, budou mít přidruženou barvu textu. Nepoužívejte jiné barvy textu, než které jsou určeny pro toto pozadí. Pokud není k dispozici přidružená barva textu, nepoužívejte tuto barvu pozadí pro žádný povrch, na kterém očekáváte zobrazení textu. Jiné kombinace barev textu a pozadí mohou mít za následek nečitelné rozhraní.

- **Použijte ovládací barvy, které jsou vhodné pro jejich umístění.** V některých státech některé ovládací prvky sady Visual Studio nemají samostatné barvy ohraničení a pozadí. Místo toho, oni vyzvednout ty barvy z povrchů za nimi. Ujistěte se, že vždy používáte názvy tokenů, které jsou vhodné pro umístění, kam umísťujete ovládací prvek.

> [!IMPORTANT]
> Nepoužívejte tokeny nalezené v kategoriích "Úvodní stránka" nebo "Jablečný mošt".

## <a name="common-shared-controls"></a>Společné sdílené ovládací prvky

Když ve své funkci použijete standardní panel příkazů sady Visual Studio, budete mít přístup k ovládacím prvkům prostředí stylu. Tyto běžné ovládací prvky byste neměli znovu šablonu. Pokud však potřebujete vytvořit vlastní panel příkazů, může být nutné vytvořit také vlastní ovládací prvky. V takovém případě nezapomeňte použít správné názvy tokenů pro každý z následujících ovládacích prvků tak, aby vaše rozhraní je konzistentní se zbytkem sady Visual Studio.

### <a name="button-controls"></a>ovládací prvky tlačítek

![Červená čára ovládání tlačítka](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... pro tlačítka v dokumentu dobře, že chcete integrovat s motivy Sady Visual Studio (světlá, tmavá, modrá nebo systém vysoký kontrast motiv). | ... pro tlačítka, která se zobrazí na vlastním pozadí, který není součástí motivu sady Visual Studio. |

**Tlačítko: standardní stav**

![Standardní tlačítko](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Standardní tlačítko

| Element | Název tokenu: Category.color |
| --- | --- |
| Tlačítko | `CommonControls.Button` |
| Ohraničení tlačítka | `CommonControls.ButtonBorder` |

**Tlačítko: výchozí stav**

![Výchozí tlačítko](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Výchozí")<br />Výchozí tlačítko

| Element | Název tokenu: Category.color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonDefault` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderDefault` |

**Tlačítko: zakázaný stav**

![Zakázané tlačítko](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Zakázáno")<br />Zakázané tlačítko

| Element | Název tokenu: Category.color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonDisabled` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderDisabled` |

**Tlačítko: stav najetí**

![Tlačítko při najetí přes](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Tlačítko při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonHover` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderHover` |

**Tlačítko: stisknutý stav**

![Stisknuté tlačítko](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Stisknuté tlačítko

| Element | Název tokenu: Category.color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonPressed` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderPressed` |

**Tlačítko: zaostřený stav**

![Zaostřené tlačítko](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Zaostřeno")<br />Zaostřené tlačítko

| Element | Název tokenu: Category.color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonFocused` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Ovládací prvky zaškrtávacího políčka
![Zaškrtávací políčko (červená čára)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Zaškrtávací políčko (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... pro ovládací prvky zaškrtávacích pokoncích obsažených v dokumentu. | ... pro libovolné ui, které není ovládací prvek zaškrtávací políčko. |

**Zaškrtávací políčko: výchozí stav**

![Políčko](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Výchozí zaškrtávací políčko

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackground` |
| Ohraničení | `CommonControls.CheckBoxBorder` |
| Text | `CommonControls.CheckBoxText` |
| Glyfů | `CommonControls.CheckBoxGlyph` |

**Zaškrtávací políčko: zakázaný stav**

![Zakázané zaškrtávací políčko](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Zakázané zaškrtávací políčko

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundDisabled` |
| Ohraničení | `CommonControls.CheckBoxBorderDisabled` |
| Text | `CommonControls.CheckBoxTextDisabled` |
| Glyfů | `CommonControls.CheckBoxGlyphDisabled` |

**Zaškrtávací políčko: stav najetí mezi disky**

 ![Zaškrtávací políčko při najetí přes](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Zaškrtávací políčko při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundHover` |
| Ohraničení | `CommonControls.CheckBoxBorderHover` |
| Text | `CommonControls.CheckBoxTextHover` |
| Glyfů | `CommonControls.CheckBoxGlyphHover` |

**Zaškrtávací políčko: stisknutý stav**

![Lisované zaškrtávací políčko](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Lisované zaškrtávací políčko

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundPressed` |
| Ohraničení | `CommonControls.CheckBoxBorderPressed` |
| Text | `CommonControls.CheckBoxTextPressed` |
| Glyfů | `CommonControls.CheckBoxGlyphPressed` |

**Zaškrtávací políčko: zaměřený stav**

![Zaškrtávací políčko Cílené](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Zaškrtávací políčko Cílené

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundFocused` |
| Ohraničení | `CommonControls.CheckBoxBorderFocused` |
| Text | `CommonControls.CheckBoxTextFocused` |
| Glyfů | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Rozevírací seznamy a seznamy
![Rozevírací seznam/seznam (červená čára)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Rozevírací seznam/seznam (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... pro rozevírací seznamy a seznamy v dokumentu dobře. | ... pro jakékoli ui, které není rozevírací seznam nebo pole se seznamem. |
| | ... pro [rozevírací seznamy panelu](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) příkazů nebo [pole se seznamem](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Rozevírací seznamy a seznamy: výchozí stav**

![Výchozí rozevírací seznam/seznam](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Výchozí rozevírací seznam/seznam

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackground` |
| Ohraničení | `CommonControls.ComboBoxBorder` |
| Text | `CommonControls.ComboBoxText` |
| Oddělovač | `CommonControls.ComboBoxSeparator` |
| Glyfů | `CommonControls.ComboBoxGlyph` |
| Pozadí glyfů | `CommonControls.ComboBoxGlyphBackground` |

**Rozevírací seznamy a seznamy: zakázaný stav**

![Zakázaná rozevírací seznam/seznam](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Zakázaná rozevírací seznam/seznam

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackgroundDisabled` |
| Ohraničení | `CommonControls.ComboBoxBorderDisabled` |
| Text | `CommonControls.ComboBoxTextDisabled` |
| Oddělovač | `CommonControls.ComboBoxSeparatorDisabled` |
| Glyfů | `CommonControls.ComboBoxGlyphDisabled` |
| Pozadí glyfů | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Rozevírací seznamy a seznamy: stav přijetí**

![Rozevírací seznam/pole se seznamem při najetí](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Rozevírací seznam/pole se seznamem při najetí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackgroundHover` |
| Ohraničení | `CommonControls.ComboBoxBorderHover` |
| Text | `CommonControls.ComboBoxTextHover` |
| Oddělovač | `CommonControls.ComboBoxSeparatorHover` |
| Glyfů | `CommonControls.ComboBoxGlyphHover` |
| Pozadí glyfů | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Rozevírací seznamy a seznamy: lisovaný stav**

![Lisované rozevírací rámeček/seznam](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Lisované rozevírací rámeček/seznam

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackgroundPressed` |
| Ohraničení | `CommonControls.ComboBoxBorderPressed` |
| Text | `CommonControls.ComboBoxTextPressed` |
| Oddělovač | `CommonControls.ComboBoxSeparatorPressed` |
| Glyfů | `CommonControls.ComboBoxGlyphPressed` |
| Pozadí glyfů | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Zobrazení položek seznamu rozevíracích seznamů a seznamů: stav stisknutí**

 ![Rozevírací seznam/pole se seznamem stisknuté zobrazení položky seznamu](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Rozevírací seznam/pole se seznamem stisknuté zobrazení položky seznamu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Ohraničení | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Text položky | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Stín pozadí | `CommonControls.ComboBoxListBackgroundShadow` |

**Rozevírací seznamy a seznamy: zaměřený stav**

![Rozevírací seznam/seznam se zaostřením](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Rozevírací seznam/seznam se zaostřením

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackgroundFocused` |
| Ohraničení | `CommonControls.ComboBoxBorderFocused` |
| Text | `CommonControls.ComboBoxTextFocused` |
| Oddělovač | `CommonControls.ComboBoxSeparatorFocused` |
| Glyfů | `CommonControls.ComboBoxGlyphFocused` |
| Pozadí glyfů | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Rozevírací seznamy a pole se seznamem: výběr zadávání textu**

![Výběr vstupu textu rozevíracího pole/pole se seznamem](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Výběr vstupu textu rozevíracího pole/pole se seznamem

| Element | Název tokenu: Category.color |
| --- | --- |
| Zvýraznit | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Ovládací prvky tabulkových dat (mřížka)
Ovládací prvky tabulkových dat, označované také jako ovládací prvky mřížky, jsou běžné ovládací prvky pro sady Visual Studio, které lze použít k prezentaci velkého množství dat ve více sloupcích. Standardní ovládací prvky tabulkových dat lze nalézt na více místech v rámci sady Visual Studio: okno nástroje Seznam chyb, sestavy IntelliTrace a zobrazení haldy paměti. Vždy používejte standardní ovládací prvky tabulkových dat. V některých výjimečných případech pravděpodobně nemáte přístup ke standardním ovládacím prvkům tabulkových dat. V těchto situacích použijte následující názvy tokenů, abyste zajistili, že vaše rozhraní je konzistentní s ostatními ovládacími prvky tabulkových dat v sadě Visual Studio.

![Tabulkové ovládání dat/mřížky (červená čára)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Tabulkové ovládání dat/mřížky (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... pro tabulkové ovládací prvky nebo ovládací prvky mřížky. | ... pro jakékoli ui, které není tabulkové nebo mřížky ovládací prvek. |

#### <a name="column-headers"></a>Záhlaví sloupců
Záhlaví sloupců se skládají z pozadí, ohraničení, textu nadpisu a volitelného glyfu, který se obvykle používá při seřazení mřížky podle tohoto sloupce.

**Záhlaví sloupce: výchozí stav**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Header.Default` |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Popředí (glyf) | `Header.Glyph` |
| Ohraničení | `Header.SeparatorLine` |

**Záhlaví sloupce: stav najetí přes**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Header.MouseOver` |
| Popředí (text) | `Environment.CommandBarTextHover` |
| Popředí (glyf) | `Header.MouseOverGlyph` |
| Ohraničení | `Header.SeparatorLine` |

**Záhlaví sloupce: stav stisknutí**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundPressed` |
| Popředí (text) | `CommonControls.CheckBoxBorderPressed` |
| Popředí (glyf) | `CommonControls.CheckBoxTextPressed` |
| Ohraničení | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Položky zobrazení seznamu
 Položky zobrazení seznamu se skládají z pozadí a obsahu. Obsah může být text, ikona nebo obojí.

**Položky zobrazení seznamu: výchozí stav**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Průhlednost |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Ohraničení | Žádný |

**Položky zobrazení seznamu: aktivní stav**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemActive` |
| Popředí (text) | `TreeView.SelectedItemActiveText` |
| Ohraničení | Žádný |

**Položky zobrazení seznamu: neaktivní stav**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemInactive` |
| Popředí (text) | `TreeView.SelectedItemInactiveText` |
| Ohraničení | Žádný |

### <a name="ui-text"></a>Text v uj

#### <a name="instructional-text"></a>Instruktážní text
Instruktážní text poskytuje hlavní hlavní vysvětlení toho, co dělat v dialogu nebo na stránce dokumentu.

![Výchozí instruktážní text](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Výchozí instruktážní text

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Sekundární instruktážní text
Na stránkách dokumentu se spoustou textu a ovládacích prvků používá nějaký instruktážní text jinou hodnotu barvy. To pomáhá sdělit, které informace jsou nejdůležitější a snížit celkovou hustotu prvků uživatelského rozhraní. (Viz také níže uvedená část textu nápovědy.)

![Sekundární instruktážní text](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Sekundární instruktážní text

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Text nápovědy
Text nápovědy se zobrazí v prázdném ovládacím prvku, pod ovládacím prvkem nebo na prázdném povrchu dokumentu, aby uživateli ukázal, co má dělat dál. Text nápovědy můžete použít s pozadím okna nebo ovládacího prvku.

**Výchozí text nápovědy**

![Výchozí text nápovědy](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Výchozí text nápovědy

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.ControlEditHintText` |

**Povinný text nápovědy**

![Povinný text nápovědy](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Povinný text nápovědy

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.ControlRequiredHintText` |
| Pozadí | `Environment.ControlRequiredBackground` |

**Text ovládacího prvku vyhledávacího pole**

> Viz [Vyhledávací pole](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) pro další barevné tokeny související s ovládacím prvkem Hledat.

![Text ovládacího prvku vyhledávacího pole](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Text ovládacího prvku vyhledávacího pole

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hypertextový odkaz
Hypertextový odkaz je jeden ovládací prvek, který nemá dvojici popředí nebo pozadí. Ve všech případech použijte barvu hypertextového odkazu v popředí, která se na tmavém, šedém a bílém pozadí zobrazí správně. Pokud pro ovládací prvek hypertextového odkazu nepoužijete token barev, zobrazí se výchozí barva systému pro "stisknuté", která bude blikat červeně. To je signál, že ovládací prvek nepoužívá token barvy správné prostředí.

![Hypertextový odkaz (červená čára)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hypertextový odkaz (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... když potřebujete vytvořit vlastní hypertextový odkaz. | ... pro cokoliv, co není hypertextový odkaz. |

**Hypertextový odkaz: výchozí stav**

![Výchozí hypertextový odkaz](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Výchozí hypertextový odkaz

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.PanelHyperlink` |

**Hypertextový odkaz: stav najetí**

![Hypertextový odkaz na najetí přes](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Hypertextový odkaz na najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.PanelHyperlinkHover` |

**Hypertextový odkaz: stav stisknutí**

![Lisovaný hypertextový odkaz](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Lisovaný hypertextový odkaz

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.PanelHyperlinkPressed` |

**Hypertextový odkaz: zakázaný stav**

![Zakázaný hypertextový odkaz](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Zakázaný hypertextový odkaz

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Informační panely
Informační panely slouží k poskytnutí dalších informací o daném kontextu a vždy se zobrazují v horní části okna dokumentu nebo okna nástroje.

![Informační panel (červená čára)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Informační panel (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... při vytváření vlastních informačních panelů. | ... pro prvky uživatelského rozhraní, které nejsou podobné informačnímu panelu. |

**Informační panel: výchozí stav**

![Výchozí informační panel](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Výchozí informační panel

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.InfoBarBackground` |
| Popředí (text) | `InfoBar.InfoBar` |
| Ohraničení | `InfoBar.InfoBarBorder` |

**Tlačítko Zavřít&times;informačního panelu ( ) : výchozí stav**

![Výchozí tlačítko Zavřít&times;informačního panelu ( )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Výchozí tlačítko Zavřít&times;informačního panelu ( )

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.CloseButton` |
| Ohraničení | `InfoBar.CloseButtonBorder` |
| Glyfů | `InfoBar.CloseButtonGlyph` |

**Tlačítko Zavřít&times;informačního panelu ( ) : stav najetí přes**

![Tlačítko Zavřít&times;informačního panelu ( ) při najetí](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Tlačítko Zavřít&times;informačního panelu ( ) při najetí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.CloseButtonHover` |
| Ohraničení | `InfoBar.CloseButtonHoverBorder` |
| Glyfů | `InfoBar.CloseButtonHoverGlyph` |

**Tlačítko Zavřít&times;informačního panelu ( ) : stisknutý stav**

![Stisknuté tlačítko&times;Zavřít informační panel ( )](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Stisknuté tlačítko&times;Zavřít informační panel ( )

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.CloseButtonDown` |
| Ohraničení | `InfoBar.CloseButtonDownBorder` |
| Glyfů | `InfoBar.CloseButtonDownGlyph` |

**Tlačítko hypertextového odkazu informačního panelu: výchozí stav**

![Výchozí tlačítko hypertextového odkazu informačního panelu](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Výchozí tlačítko hypertextového odkazu informačního panelu

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `InfoBar.Hyperlink` |

**Tlačítko hypertextového odkazu informačního panelu: stav najetí přes**

![Tlačítko hypertextového odkazu informačního panelu při najetí přes](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Tlačítko hypertextového odkazu informačního panelu při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Infobar.HyperlinkMouseOver`<br />(S podtržením) |

**Tlačítko hypertextového odkazu informačního panelu: stisknutý stav**

![Stisknuté tlačítko hypertextového odkazu informačního panelu](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Stisknuté tlačítko hypertextového odkazu informačního panelu

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Infobar.HyperlinkMouseDown`<br />(S podtržením) |

**Inline hypertextový odkaz infopanelu (ve větě): výchozí stav**

![Výchozí tlačítko hypertextového odkazu inline informačního panelu](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Výchozí tlačítko hypertextového odkazu inline informačního panelu

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `InfoBar.Hyperlink` |

**Inline hypertextový odkaz infopanelu (ve větě): stav najetého řádku**

![Tlačítko vaktivního hypertextového odkazu informačního panelu při najetí přes](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Tlačítko vaktivního hypertextového odkazu informačního panelu při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Infobar.HyperlinkMouseOver`<br />(S podtržením) |

**Inline hypertextový odkaz infopanelu (ve větě): stisknutý stav**

![Stisknuté tlačítko vaktivního hypertextového odkazu na informační panel](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Stisknuté tlačítko vaktivního hypertextového odkazu na informační panel

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Infobar.HyperlinkMouseDown`<br />(S podtržením) |

**Tlačítko Informační panel: výchozí stav**

![Tlačítko výchozího informačního panelu](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Tlačítko výchozího informačního panelu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.Button` |
| Popředí (text) | `InfoBar.Button` |
| Ohraničení | `InfoBar.ButtonBorder` |

**Tlačítko Informační panel: stav najetí přes**

![Tlačítko Informační panel při najetí přes](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Tlačítko Informační panel při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.ButtonMouseOver` |
| Popředí (text) | `InfoBar.ButtonMouseOver` |
| Ohraničení | `InfoBar.ButtonMouseOverBorder` |

**Tlačítko Informační panel: stisknutý stav**

![Stisknuté tlačítko informačního panelu](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Stisknuté tlačítko informačního panelu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.ButtonMouseDown` |
| Popředí (text) | `InfoBar.ButtonMouseDown` |
| Ohraničení | `InfoBar.ButtonMouseDownBorder` |

**Tlačítko Informační panel: zakázaný stav**

![Zakázané tlačítko informačního panelu](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Zakázané tlačítko informačního panelu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.ButtonDisabled` |
| Popředí (text) | `InfoBar.ButtonDisabled` |
| Ohraničení | `InfoBar.ButtonDisabledBorder` |

**Tlačítko Informační panel: zaostřený stav**

![Tlačítko Na informační panel](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Tlačítko Na informační panel

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.ButtonFocus` |
| Popředí (text) | `InfoBar.ButtonFocus` |
| Ohraničení | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Posuvníky
Posuvníky jsou stylizovány prostředím sady Visual Studio a nebude nutné tématické. Můžete se však rozhodnout, že chcete využít barvy použité v posuvnících tak, aby vaše ui vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.

![Posuvník (červená čára)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Posuvník (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... při vytváření ui, které chcete, aby odpovídaly Visual Studio posuvníky. | ... pro vše, co nechcete vždy odpovídat posuvník uI. |

**Posuvník: výchozí stav**

![Výchozí posuvník](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Výchozí posuvník

| Element | Název tokenu: Category.color |
| --- | --- |
| Posuvník | `Environment.ScrollBarBackground` |
| Popředí (palec) | `Environment.ScrollBarThumbBackground` |

**Posuvník: stav přechodu**

![Posuvník při přechodu](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Posuvník při přechodu

| Element | Název tokenu: Category.color |
| --- | --- |
| Posuvník | `Environment.ScrollBarBackground` |
| Popředí (palec) | `Environment.ScrollBarThumbMouseOverBackground` |

*Posuvník: stav stisknutí**

![Stisknutý posuvník](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Stisknutý posuvník

| Element | Název tokenu: Category.color |
| --- | --- |
| Posuvník | `Environment.ScrollBarBackground` |
| Popředí (palec) | `Environment.ScrollBarThumbPressedBackground` |

**Šipka posuvníku: výchozí stav**

![Výchozí šipka posuvníku](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Výchozí šipka posuvníku

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ScrollBarArrowBackground`<br />(Nastavte stejnou barvu jako posuvník.) |
| Popředí (glyf) | `Environment.ScrollBarArrowGlyph` |

**Šipka posuvníku: stav přechodu**

![Šipka posuvníku při přechodu](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Šipka posuvníku při přechodu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ScrollBarArrowMouseOverBackground`<br />(Nastavte stejnou barvu jako posuvník.) |
| Popředí (glyf) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Šipka posuvníku: stav stisknutí**

![Stisknutá šipka posuvníku](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Stisknutá šipka posuvníku

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ScrollBarArrowPressedBackground`<br />(Nastavte stejnou barvu jako posuvník.) |
| Popředí (glyf) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Vyhledávací pole
Kdykoli je to možné, použijte společný ovládací prvek hledání poskytované prostředí sady Visual Studio. Barvy vyhledávacího pole se nacházejí v kategorii "SearchControl" v souboru **ShellColors.pkgdef,** který obsahuje názvy tokenů pro vstupní pole, tlačítko akce, rozevírací tlačítko a rozevírací nabídku.

Vyhledávací pole může být jedním z několika stavů, z nichž některé se vzájemně vylučují:

- "Focused" nebo "unfocused" označuje, zda je kurzor v textovém poli.

- "Aktivní" nebo "neaktivní" označuje, zda uživatel zadal vyhledávací dotaz do textového pole.

- "Najetí myší" znamená, že uživatel má myší na hledané pole (tento stav přepíše všechny ostatní stavy).

- "Zakázáno" znamená, že funkce vyhledávání je vypnuta pro aktuální kontext.

![Vyhledávací pole (červená čára)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Vyhledávací pole (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... při navrhování vlastního vyhledávacího pole. | ... pro cokoliv, co není vyhledávací pole. |
| | ... pro vše, co nechcete, aby vždy odpovídaly vyhledávací pole UI. |

**Pole pro cílené hledání**

![Pole pro cílené hledání](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Pole pro cílené hledání

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.FocusedBackground` |
| Popředí (text) | `SearchControl.FocusedBackground` |
| Ohraničení | `SearchControl.FocusedBorder` |
| Oddělovač | `SearchControl.FocusedDropDownSeparator` |

**Pole pro aktivní vyhledávání, které není zaostřeno, aktivní**

![Rozostřené vyhledávací vstupní pole](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Pole pro aktivní vyhledávání, které není zaostřeno, aktivní

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.SearchActiveBackground` |
| Popředí (text) | `SearchControl.SearchActiveBackground` |
| Ohraničení | `SearchControl.UnfocusedBorder` |
| Oddělovač | `SearchControl.DropDownSeparator` |

**Nezaostřené, neaktivní vyhledávací vstupní pole**

![Nezaostřené, neaktivní vyhledávací vstupní pole](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Nezaostřené, neaktivní vyhledávací vstupní pole

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.Unfocused` |
| Popředí (text) | `SearchControl.Unfocused` |
| Ohraničení | `SearchControl.UnfocusedBorder` |
| Oddělovač | `SearchControl.DropDownSeparator` |

**Zvýrazněné vyhledávací vstupní pole (pouze text)**

![Zvýrazněné vyhledávací vstupní pole](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Zvýrazněné vyhledávací vstupní pole

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.Selection` |
| Popředí (text) | `SearchControl.FocusedBackground` |
| Ohraničení | Žádný |
| Oddělovač | `SearchControl.FocusedDropDownSeparator` |

**Zakázané vyhledávací vstupní pole**

![Zakázané vyhledávací vstupní pole](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Zakázané vyhledávací vstupní pole

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.Disabled` |
| Popředí (text) | `SearchControl.Disabled` |
| Ohraničení | `SearchControl.DisabledBorder` |
| Oddělovač | `SearchControl.DropDownSeparator` |

**Tlačítko akce cíleného hledání**

![Tlačítko akce hledání zaměřené](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Tlačítko akce cíleného hledání

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádný |
| Popředí (Hledat glyf) | `SearchControl.SearchGlyph` |
| Popředí (Stop glyf) | `SearchControl.StopGlyph` |
| Popředí (Vymazat glyf) | `SearchControl.ClearGlyph` |
| Ohraničení | Není dostupné. |

**Tlačítko akce nezaostřeného hledání**

![Tlačítko akce nezaostřeného hledání](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Tlačítko akce nezaostřeného hledání

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není dostupné. |
| Popředí (Hledat glyf) | `SearchControl.SearchGlyph` |
| Popředí (Stop glyf) | `SearchControl.StopGlyph` |
| Popředí (Vymazat glyf) | `SearchControl.ClearGlyph` |
| Ohraničení | Není dostupné. |

**Tlačítko akce hledání stisknuté**

![Tlačítko akce hledání stisknuté](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Tlačítko akce hledání stisknuté

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.ActionButtonMouseDown` |
| Popředí (glyf) | `SearchControl.ActionButtonMouseDownGlyph` |
| Ohraničení | `SearchControl.ActionButtonMouseDownBorder` |

**Zakázané tlačítko akce hledání**

![Tlačítko akce hledání je zakázáno.](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Zakázané tlačítko akce hledání

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádný |
| Popředí (glyf) | `SearchControl.ActionButtonDisabledGlyph` |
| Ohraničení | Žádný |

**Rozevírací tlačítko Cílené hledání**

![Rozevírací tlačítko Cílené hledání](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Rozevírací tlačítko Cílené hledání

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.FocusedDropDownButton` |
| Popředí (glyf) | `SearchControl.FocusedDropDownButtonGlyph` |
| Ohraničení | `SearchControl.FocusedDropDownButtonBorder` |

**Rozevírací tlačítko Nezaostřené hledání**

![Rozevírací tlačítko Nezaostřené hledání](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Rozevírací tlačítko Nezaostřené hledání

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.UnfocusedDropDownButton` |
| Popředí (glyf) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Ohraničení | `SearchControl.UnfocusedDropDownButtonBorder` |

**Stisknuté rozevírací tlačítko Hledání**

![Stisknuté rozevírací tlačítko Hledání](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Stisknuté rozevírací tlačítko Hledání

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.MouseDownDropDownButton` |
| Popředí (glyf) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Ohraničení | `SearchControl.MouseDownDropDownButtonBorder` |

**Zakázané tlačítko rozevíracího panelu hledání**

![Zakázané tlačítko rozevíracího panelu hledání](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Zakázané tlačítko rozevíracího panelu hledání

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádný |
| Popředí (glyf) | `SearchControl.DisabledDownButtonGlyph` |
| Ohraničení | Žádný |

#### <a name="search-drop-down-lists"></a>Hledat rozevírací seznamy
Rozevírací nabídka vyhledávacího pole má potenciál být o něco složitější než jiné rozevírací nabídky v sadě Visual Studio. Oddíly "navrhovaná hledání" a "možnosti vyhledávání" se mohou v nabídce zobrazit samostatně nebo společně a každá z nich je barevná samostatně. Čára také odděluje tyto dva oddíly, když se zobrazí společně a ohraničení obklopuje celou rozevírací nabídku.

![Rozevírací seznam Hledat (červená čára)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Rozevírací seznam Hledat (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... při vytváření vlastního rozevíracího seznamu hledání. | ... pro rozevírací seznamy, které se zobrazují v jiných kontextech. |
| ... správné názvy tokenů pro součásti správného seznamu. | ... v jakékoli kombinaci pozadí/popředí, než je uvedeno. |

**Hledat prvky rozevíracího seznamu**

| Element | Název tokenu: Category.color |
| --- | --- |
| Ohraničení | `SearchControl.PopupBorder` |
| Oddělovač | `SearchControl.PopupSectionHeaderSeparator` |
| Stín | `Environment.DropShadowBackground` |

**Navrhovaná hledání: výchozí stav**

![Výchozí navrhovaná hledání](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Výchozí navrhovaná hledání

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `SearchControl.PopupItemText` |

**Navrhovaná hledání: stav najetého na jev**

![Doporučená hledání při najetí přes](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Doporučená hledání při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `SearchControl.PopupMouseOverItemText` |
| Ohraničení | `SearchControl.PopupControlMouseOverBorder` |

**Možnosti hledání: výchozí stav**

![Zaškrtávací políčko Hledat](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Výchozí možnosti hledání (zaškrtávací políčko)

![Možnosti hledání](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Výchozí možnosti hledání (odkaz)

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text zaškrtávacího políčka) | `SearchControl.PopupCheckboxText` |
| Popředí (text odkazu) | `SearchControl.PopupButtonText` |
| Pozadí záhlaví | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text záhlaví) | `SearchControl.PopupSectionHeaderText` |

**Možnosti hledání: stav najetí přes**

![Možnosti hledání (zaškrtávací políčko) při najetí přes](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Možnosti hledání (zaškrtávací políčko) při najetí přes

![Možnosti hledání (odkaz) při najetí](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Možnosti hledání (odkaz) při najetí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text zaškrtávacího políčka) | `SearchControl.PopupCheckboxMouseDownText` |
| Popředí (text odkazu) | `SearchControl.PopupButtonMouseDownText` |
| Ohraničení | `SearchControl.PopupControlMouseOverBorder` |

**Možnosti hledání: stisknutý stav**

![Možnosti lisovaného hledání (zaškrtávací políčko)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Možnosti lisovaného hledání (zaškrtávací políčko)

![Možnosti hledání stisknuté (odkaz)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Možnosti hledání stisknuté (odkaz)

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí zaškrtávacího políčka | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text zaškrtávacího políčka) | `SearchControl.PopupCheckboxMouseDownText` |
| Propojit pozadí | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text odkazu) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a>Stromové pohledy
Několik oken nástrojů, včetně Průzkumníka řešení, Průzkumníka serveru a zobrazení tříd, implementuje hierarchické organizační schéma, jehož barvy jsou řízeny názvy barev v `TreeView` kategorii. Všechny položky ve stromovém zobrazení mají barvy pozadí a textu. Položky, které mají vnořené podřízené prvky, mají také glyfy, které označují, zda je položka rozbalena nebo sbalena.

![Stromové zobrazení (červená čára)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Stromové zobrazení (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... kdekoli potřebujete implementovat hierarchické organizační zobrazení. | ... pro cokoli, co není podobné stromové zobrazení. |
| | ... v jakékoli kombinaci pozadí/popředí, než je uvedeno. |

**Položka stromového zobrazení: výchozí stav**

![Výchozí položka stromového zobrazení](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Výchozí položka stromového zobrazení

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.Background` |
| Popředí (text) | `TreeView.Background` |
| Popředí (glyf) | `TreeView.Glyph` |
| Ohraničení | Žádný |

**Položka stromového zobrazení: stav přijet**

![Stromová položka při najetí přes](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Stromová položka při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.Background` |
| Popředí (text) | `TreeView.Background` |
| Popředí (glyf) | `TreeView.GlyphMouseOver` |
| Ohraničení | Žádný |

**Položka stromového zobrazení: přetažení přes stav**

![Stromové zobrazení při přetažení](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Stromové zobrazení při přetažení

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.DragOverItem` |
| Popředí (text) | `TreeView.DragOverItem` |
| Popředí (glyf) | `TreeView.DragOverItemGlyph` |
| Ohraničení | Žádný |

**Položka stromového zobrazení: vybraná, zaostřený stav**

![Vybraná a zaměřená položka stromového zobrazení](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Vybraná a zaměřená položka stromového zobrazení

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemActive` |
| Popředí (text) | `TreeView.SelectedItemActive` |
| Popředí (glyf) | `TreeView.SelectedItemActiveGlyph` |
| Ohraničení | `TreeView.FocusVisualBorder` |

**Položka stromového zobrazení: vybraný, nezaostřený stav**

![Vybraná a nezaostřená položka stromového zobrazení](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Vybraná a nezaostřená položka stromového zobrazení

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemInactive` |
| Popředí (text) | `TreeView.SelectedItemInactive` |
| Popředí (glyf) | `TreeView.SelectedItemInactiveGlyph` |
| Ohraničení | Žádný |

**Položka stromového zobrazení: prvek v satoh, vybraný a zaměřený stav**

![Vybraná a zaměřená položka stromového zobrazení při najetí přes](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Vybraná a zaměřená položka stromového zobrazení při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemActive` |
| Popředí (text) | `TreeView.SelectedItemActive` |
| Popředí (glyf) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Ohraničení | `TreeView.FocusVisualBorder` |

**Položka stromového zobrazení: prvek vsazený, vybraný a nezaostřený stav**

![Vybraná a nezaostřená položka stromového zobrazení při najetí přes](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Vybraná a nezaostřená položka stromového zobrazení při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemInactive` |
| Popředí (text) | `TreeView.SelectedItemInactive` |
| Popředí (glyf) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Ohraničení | Žádný |

## <a name="shell-appearance"></a>Vzhled skořepiny

### <a name="background"></a>Pozadí
Pozadí prostředí se skládá ze dvou vrstev. Spodní vrstva je plná barva, která pokrývá celé ide. Horní vrstva se vejde pod polici příkazu a mezi okno nástroje automaticky skrýt kanály na levém a pravém okraji ide. Horní a dolní vrstvy pozadí jsou nastaveny na stejnou barvu v motivech Světlá a Tmavá.

![Pozadí prostředí visual studio (červená čára)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Pozadí prostředí visual studio (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... pro místa, kde chcete odpovídat pozadí prostředí sady Visual Studio. | ... jako výplň pro místa, která nejsou povrchy pozadí. |
| | ... jako pozadí pro umístění prvků popředí. |

**Vzhled skořepiny spodní vrstvy**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.EnvironmentBackground` |

**Vzhled skořepiny horní vrstvy**

> Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Příkazová police
Pro pozadí policí příkazu se používají dvě sady názvů tokenů: jedna sada pro místo, kde je na řádku nabídek, a druhá pro místo, kde jsou tyče příkazů. Jednotlivé skupiny panelů příkazů mají vlastní hodnoty barev pozadí, které jsou podrobněji popsány v části "panel příkazů". Panel nabídek a text panelu příkazů je popsán v sekcích nabídek a panelu příkazů.

![Police příkazů visual studia (červená čára)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Police příkazů visual studia (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... pro oblasti, kam umístíte nabídky nebo panely nástrojů. | ... pro oblasti, které nejsou podobné příkazu police. |
|... se správnou kombinací názvů tokenů pozadí a popředí. | |

**Panel nabídek Police příkazu**

> Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Panel příkazů příkazového police**

> Přechod se zastaví na stejnou hodnotu barvy v motivech Visual Studio 2013 Světlé a Tmavé.

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Návrhář manifestu
Návrhář manifestu byl navržen jako způsob, jak usnadnit úpravy souboru manifestu v projektech Windows 8 a Windows Phone 8. I když není k dispozici žádná sdílená architektura pro spotřebu, může být vhodné, abyste odpovídali rozložení návrhu a barvy karet orientace/navigace a celkové struktury. Další informace o podrobnostech rozložení naleznete v [tématu Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Návrhář manifestu (červená čára)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Návrhář manifestu (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... pro návrháře, které jsou podobné Návrhář manifestu. | ... pokud máte více než šest záložek. |
| ... místo použití běžných ovládacích prvků tabulátoru v horní části editoru v dokumentu dobře. | ... pro jakékoli ui, které není strukturováno jako Návrhář manifestu. |

**Vybraná karta Návrhář manifestu: výchozí stav**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `ManifestDesigner.TabActive` |
| Ohraničení | Žádný |

**Podokno vybraného popisu Návrháře manifestu: výchozí stav**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `ManifestDesigner.DescriptionPane` |

**Stránka vybraného obsahu Návrháře manifestu: výchozí stav**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `ManifestDesigner.Background` |
| Text pomocníka dialogu | `ManifestDesigner.WatermarkText`<br />(Tento název tokenu neodpovídá jeho funkci.) |

**Karta Návrhář manifestu: nevybraný stav**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `ManifestDesigner.Tab.Inactive` |

**Karta Návrhář manifestu: stav najetí přes**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Struktury příkazů

### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Nabídky
Nabídky se mohou vyskytovat na několika místech v sadě Visual Studio: na hlavním panelu nabídek, vloženém do oken dokumentů nebo nástrojů, nebo při kliknutí pravým tlačítkem myši na různých místech v celém integrovaném prostředí. Implementace nabídek přidružených k jiným prvkům uživatelského rozhraní jsou popsány v části pro příslušný prvek. Vždy byste měli použít standardní implementaci nabídky poskytované prostředí sady Visual Studio. V některých výjimečných případech však nemusí mít přístup ke standardním nabídkám sady Visual Studio. V těchto situacích použijte následující názvy tokenů, abyste zajistili, že vaše ui je konzistentní s ostatními nabídkami v sadě Visual Studio.

![Nabídka Visual Studia (červená čára)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Nabídka Visual Studia (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... když potřebujete vytvořit vlastní nabídku.| ... samotnou barvu pozadí. Vždy používejte kombinaci pozadí a popředí, jak je uvedeno. |
| ... Pokud máte novou komponentu uzly, které chcete, aby odpovídaly nabídky sady Visual Studio.| |

#### <a name="menu-titles"></a>Názvy nabídek
Názvy nabídek se skládají z pozadí, ohraničení a textu nadpisu a volitelného glyfu, obvykle když se nabídka nachází v panelu příkazů.

![Název nabídky (červená čára)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Název nabídky (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... při každém vytváření vlastního názvu nabídky. | ... pro vše, co nechcete vždy odpovídat názvu nabídky. |
| | ... v jakékoli kombinaci pozadí/popředí, než je uvedeno. |

**Název nabídky: výchozí stav**

![Výchozí název nabídky](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Výchozí název nabídky

![Výchozí název nabídky s glyfem](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Výchozí název nabídky s glyfem

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádný |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Popředí (glyf) | `Environment.CommandBarMenuGlyph` |
| Ohraničení | Žádný |

**Název nabídky: stav najetí přes**

![Název nabídky při najetí přes](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Název nabídky při najetí přes

![Název nabídky s glyfem na jevu](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Název nabídky s glyfem na jevu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.CommandBarTextHover` |
| Popředí (glyf) | `Environment.CommandBarMenuMouseOverGlyph` |
| Ohraničení | `Environment.CommandBarBorder` |

**Název nabídky: stisknutý stav**

![Název nabídky stisknuté](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Název nabídky stisknuté

![Název nabídky stisknuté glyfem](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Název nabídky stisknuté glyfem

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Popředí (glyf) | `Environment.CommandBarMenuMouseDownGlyph` |
| Ohraničení | `Environment.CommandBarMenuBorder`<br />(Pouze levé, horní a pravé strany.) |

**Název nabídky: zakázaný stav**

![Zakázaný název nabídky s glyfem](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Zakázaný název nabídky s glyfem

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádný |
| Popředí (text) | `Environment.CommandBarTextInactive` |
| Popředí (glyf) | `Environment.CommandBarTextInactive` |
| Ohraničení | Žádný |

#### <a name="menu-items"></a>Položky nabídky
Jednotlivá položka nabídky se skládá z textu nabídky a volitelné ikony, zaškrtávacího políčka nebo glyfu podnabídky. Jeho pozadí a barva textu se mění při přechodu. Tento token barev je dvojice pozadí/popředí.

![Červené položky nabídky](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Použít... | Nepoužívejte ... |
|---|---|
| ... pro všechny rozevírací seznamy, které jsou spuštěny z panelu nabídek nebo příkazového řádku. | ... pro všechny rozevírací seznamy v jiném kontextu. |
| | ... v jakékoli kombinaci pozadí/popředí, než je uvedeno. |

**Položky nabídky: výchozí stav**

![Výchozí položky nabídky](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Výchozí položky nabídky

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Popředí (glyf podnabídky) | `Environment.CommandBarMenuSubmenuGlyph` |
| Ohraničení | `Environment.CommandBarMenuBorder` |
| Pozadí kanálu ikony | `Environment.CommandBarMenuIconBackground` |
| Oddělovač | `Environment.CommandBarMenuSeparator` |
| Stín | `Environment.DropShadowBackground` |

**Položky nabídky: zaškrtnuté a vybrané stavy**

![Nabídka zaškrtnuta](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Zaškrtnutá položka nabídky

![Vybraná nabídka](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Vybraná položka nabídky

| Element | Název tokenu: Category.color |
| --- | --- |
| Zaškrtnutí | `Environment.CommandBarCheckBox` |
| Zkontrolujte pozadí značky | `Environment.CommandBarSelectedIcon` |
| Pozadí ikony | `Environment.CommandBarSelected` |
| Ohraničení ikony | `Environment.CommandBarSelectedBorder` |

**Položky nabídky: stav najetí přes**

![Nabídka najetá přes](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Položka nabídky při najetí přes

![Nabídka je zaškrtnutá.](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Zaškrtnutá položka nabídky při najetí přes

![Nabídka je vybraná.](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Vybraná položka nabídky při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMenuItemMouseOver` |
| Popředí (text) | `Environment.CommandBarMenuItemMouseOverText` |
| Popředí (glyf podnabídky) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Zaškrtnutí | `Environment.CommandBarCheckBoxMouseOver` |
| Zkontrolujte pozadí značky | `Environment.CommandBarHoverOverSelectedIcon` |
| Pozadí ikony | `Environment.CommandBarHoverOverSelected` |
| Ohraničení ikony | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Položky nabídky: zakázaný stav**

![Nabídka je zakázána.](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Zakázaná položka nabídky

![Nabídka zakázána zaškrtnuto](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Zakázaná položka nabídky se zaškrtnutím

| Element | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.CommandBarTextInactive` |
| Popředí (glyf podnabídky) | `Environment.CommandBarMenuSubmenuGlyph` |
| Zaškrtnutí | `Environment.CommandBarCheckBoxDisabled` |
| Zkontrolujte pozadí značky | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Panely příkazů
Panel příkazů se může zobrazit na více místech v integrovaném prostředí Sady Visual Studio, zejména na polici příkazů a vložený do oken nástrojů nebo dokumentů.

Obecně vždy používejte standardní implementaci panelu příkazů poskytovanou prostředím sady Visual Studio. Použití standardní mechanismus zajišťuje, že všechny vizuální podrobnosti se zobrazí správně a že interaktivní prvky, se bude chovat konzistentně s ostatními ovládacími prvky panelu příkazů sady Visual Studio. Pokud je však nutné vytvořit vlastní panel příkazů, ujistěte se, že styl správně pomocí následující názvy tokenů.

![Červený řádek panelu příkazů](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Panel příkazů (červená čára)

![Červené tlačítko přetečení](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Tlačítko přetečení (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... v místech, kde potřebujete vložený panel příkazů, ale nemůžete použít standardní implementaci panelu příkazů sady Visual Studio. | ... pro prvky uživatelského rozhraní, které nejsou podobné panelu příkazů. |
| | ... pro komponenty panelu příkazů jiné než ty, pro které jsou určeny názvy tokenů. |

#### <a name="command-bar-groups"></a>Skupiny panelů příkazů
Skupina panelu příkazů se skládá ze související sady ovládacích prvků panelu příkazů a může obsahovat libovolný počet tlačítek, rozdělených tlačítek, rozevíracích nabídek, polí se seznamem nebo nabídek. Barvy pro tyto ovládací prvky jsou regulovány samostatné názvy tokenů a jsou popsány jednotlivě jinde v této příručce. Oddělovací čára se používá k rozdělení skupiny panelu příkazů do souvisejících podskupin.

![Červená čára skupiny panelu příkazů](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Skupina panelu příkazů (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... v místech, kde potřebujete vložený panel příkazů, ale nemůžete použít standardní implementaci panelu příkazů sady Visual Studio. | ... pro prvky uživatelského rozhraní, které nejsou podobné panelu příkazů. |
| | ... pro komponenty panelu příkazů jiné než ty, pro které jsou určeny názvy tokenů. |

**Skupina panelu příkazů: výchozí stav**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarGradientBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Ohraničení | `Environment.CommandBarToolBarBorder` |
| Táhlo přetažení | `Environment.CommandBarDragHandle` |
| Oddělovač | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Ikony příkazů
![Červená čára ikony příkazu](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Ikona příkazu (červená čára)

![Ikona příkazu s červenou čarou textu](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Ikona příkazu s textem (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... pro všechna tlačítka, která budou umístěna na panelu příkazů. | ... pro ovládací prvky, které mají své vlastní názvy tokenů. |
| | ... v jakékoli kombinaci pozadí/popředí, než je uvedeno. |

**Ikona příkazu: výchozí stav**

![Výchozí ikona příkazu](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Ikona výchozího příkazu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není k zato (dědí z pozadí panelu příkazů) |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Ohraničení | Není dostupné. |

**Ikona příkazu: výchozí stav, vybraný**

![Výchozí, ikona vybraného příkazu](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Výchozí, ikona vybraného příkazu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarSelected` |
| Popředí (text) | `Environment.CommandBarTextSelected` |
| Ohraničení | `Environment.CommandBarSelectedBorder` |

**Ikona příkazu: stavy najetí nebo zaostření**

![Ikona příkazu při najetí nebo fokusu](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Ikona příkazu při najetí nebo fokusu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.CommandBarTextHover` |
| Ohraničení | `Environment.CommandBarBorder` |

**Ikona příkazu: stavy najetí nebo zaostření, vybraná**

![Ikona vybraného příkazu při umístění na jev nebo fokus](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Ikona vybraného příkazu při umístění na jev nebo fokus

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarHoverOverSelected` |
| Popředí (text) | `Environment.CommandBarTextHoverOverSelected` |
| Ohraničení | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Ikona příkazu: stisknutý stav**

![Ikona příkazu Stisknuto](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Ikona příkazu Stisknuto

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.CommandBarTextMouseDown` |
| Ohraničení | `Environment.CommandBarBorder` |

**Ikona příkazu: zakázaný stav**

![Ikona příkazu Zakázáno](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Ikona příkazu Zakázáno

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není k zato (dědí z pozadí panelu příkazů) |
| Popředí (text) | `Environment.CommandBarTextInactive` |
| Ohraničení | Není dostupné. |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a>Pole se seznamem panelu příkazů

> [!IMPORTANT]
> Pole se seznamem jsou podobná rozevíracím seznamům, ale obsahují upravitelnou oblast textu. Pokud rozevírací nabídku neobsahuje upravitelnou oblast textu, použijte pro [rozevírací rozevírací nabídku panelu příkazů](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)barevné tokeny .

![Červená čára se seznamem panelu příkazů](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Pole se seznamem panelu příkazů (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... při vytváření vlastních polí se seznamem. | ... pro cokoliv, co nechcete vždy odpovídat ui panelu příkazů. |
| ... při vytváření ovládacího prvku panelu příkazů, který je podobný poli se seznamem. | ... když máte přístup k stylizované musetu se seznamem. |

**Vstupní pole se seznamem panelu příkazového řádku: výchozí stav**

![Vstupní pole se seznamem panelu panelu příkazového panelu](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Vstupní pole se seznamem panelu panelu příkazového panelu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxBackground` |
| Popředí (text) | `Environment.ComboBoxText` |
| Ohraničení | `Environment.ComboBoxBorder` |
| Oddělovač | Žádný oddělovač |

**Rozevírací tlačítko panelu příkazů: výchozí stav**

![Tlačítko&#45;spouštění pole se seznamem](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Rozevírací tlačítko panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není k zato (dědí z pozadí panelu příkazů) |
| Popředí (glyf) | `Environment.ComboBoxGlyph` |

**Rozevírací seznam panelu příkazů: výchozí stav**

![Rozevírací seznam panelu příkazů](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Rozevírací seznam panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxPopupBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.ComboBoxItemText` |
| Ohraničení | `Environment.ComboBoxPopupBorder` |

**Vstupní pole se seznamem panelu panelu příkazového řádku: stav najetí přes**

![Vstupní pole se seznamem panelu příkazového řádku při najetí přes](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Vstupní pole se seznamem panelu příkazového řádku při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.ComboBoxMouseOverText` |
| Ohraničení | `Environment.ComboBoxMouseOverBorder` |
| Oddělovač | `Environment.ComboBoxMouseOverSeparator` |

 **Rozevírací tlačítko panelu příkazů: stav najetého řádku**

![Rozevírací tlačítko panelu příkazů při najetí přes](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Rozevírací tlačítko panelu příkazů při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxButtonMouseOverBackground` |
| Popředí (glyf) | `Environment.ComboBoxMouseOverGlyph` |

**Rozevírací seznam panelu příkazů: stav najetého řádku**

 ![Rozevírací seznam panelu příkazů při najetí přes](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Rozevírací seznam panelu příkazů při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí (položka nabídky) | `Environment.ComboBoxItemMouseOverBackground` |
| Popředí (text) | `Environment.ComboBoxItemMouseOverText` |
| Ohraničení (položka nabídky) | `Environment.ComboBoxItemMouseOverBorder` |

 **Vstupní pole se seznamem panelu příkazového panelu: zaostřený stav**

![Zaostřené vstupní pole se seznamem panelu panelu příkazů](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Zaostřené vstupní pole se seznamem panelu panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxFocusedBackground` |
| Popředí (text) | `Environment.ComboBoxFocusedText` |
| Ohraničení | `Environment.ComboBoxFocusedBorder` |
| Oddělovač | `Environment.ComboBoxFocusedButtonSeparator` |

**Rozevírací tlačítko panelu příkazů: zaostřený stav**

![Rozevírací tlačítko Panel příkazů – ostře](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Rozevírací tlačítko Panel příkazů – ostře

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxFocusedButtonBackground` |
| Popředí (glyf) | `Environment.ComboBoxFocusedGlyph` |

 **Vstupní pole se seznamem panelu příkazového panelu: stav stisknutí**

![Vstupní pole pole se seznamem panelu příkazů](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Vstupní pole pole se seznamem panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxMouseDownBackground` |
| Popředí (text) | `Environment.ComboBoxMouseDownText` |
| Ohraničení | `Environment.ComboBoxMouseDownBorder` |
| Oddělovač | `Environment.ComboBoxMouseDownSeparator` |

**Rozevírací tlačítko panelu příkazů: stisknutý stav**

![Rozevírací tlačítko panelu příkazů](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Rozevírací tlačítko panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxButtonMouseDownBackground` |
| Popředí (glyf) | `Environment.ComboBoxMouseDownGlyph` |

**Vstupní pole se seznamem panelu příkazového panelu: zakázaný stav**

![Zakázané vstupní pole pole se seznamem panelu příkazů](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Zakázané vstupní pole pole se seznamem panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxDisabledBackground` |
| Popředí (text) | `Environment.ComboBoxDisabledText` |
| Ohraničení | `Environment.ComboBoxDisabledBorder` |
| Oddělovač | Žádný oddělovač |

**Rozevírací tlačítko panelu příkazů: zakázaný stav**

![Zakázané rozevírací tlačítko panelu příkazů](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Zakázané rozevírací tlačítko panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádný |
| Popředí (glyf) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a>Rozevírací rozevírací vyvisutých panelů

> [!IMPORTANT]
> Rozevírací seznamy jsou podobné polím se seznamem, ale postrádají upravitelné oblasti textu. Pokud rozevírací seznam obsahuje upravitelnou oblast textu, použijte tokeny barev pro [pole se seznamem panelů příkazů](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Rozevírací rozevírací řád panel příkazů (červená čára)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Rozevírací rozevírací řád panel příkazů (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... při vytváření vlastních ovládacích prvků rozevíracího seznamu. | ... pro cokoli, co není podobné rozevíracímu seznamu. |
| | ... pro pole se seznamem nebo rozdělená tlačítka. |

**Rozevírací pole panelu příkazů: výchozí stav**

![Výchozí rozevírací pole panelu příkazů](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Výchozí rozevírací pole panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownBackground` |
| Popředí (text) | `DropDownText` |
| Ohraničení | `DropDownBorder` |
| Oddělovač | Žádný oddělovač |

**Rozevírací tlačítko panelu příkazů: výchozí stav**

![Výchozí rozevírací tlačítko panelu příkazů](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Výchozí rozevírací tlačítko panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádný |
| Popředí (glyf) | `Environment.DropDownGlyph` |

**Rozevírací seznam panelu příkazů: výchozí stav**

![Výchozí rozevírací seznam panelu příkazů](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Výchozí rozevírací seznam panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownPopupBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.ComboBoxItemText` |
| Ohraničení | `Environment.DropDownPopupBorder` |
| Stín | `Environment.DropShadowBackground` |

**Rozevírací pole panelu příkazů: stav najetého řádku**

![Rozevírací pole panelu příkazů při najetí přes](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Rozevírací pole panelu příkazů při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownMouseOverBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.DropDownMouseOverText` |
| Ohraničení | `Environment.DropDownMouseOverBorder` |
| Oddělovač | `Environment.DropDownButtonMouseOverSeparator` |

**Rozevírací tlačítko panelu příkazů: stav najetého řádku**

![Rozevírací tlačítko panelu příkazů při najetí přes](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Rozevírací tlačítko panelu příkazů při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownButtonMouseOverBackground` |
| Popředí (glyf) | `Environment.DropDownMouseOverGlyph` |

**Rozevírací seznam panelu příkazů: stav najetého řádku**

![Rozevírací seznam panelu příkazů při najetí přes](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Rozevírací seznam panelu příkazů při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí (položka nabídky) | `Environment.ComboBoxItemMouseOverBackground` |
| Popředí (text) | `Environment.ComboBoxItemMouseOverText` |
| Ohraničení (položka nabídky) | `Environment.ComboBoxItemMouseOverBorder` |

 **Rozevírací pole panelu příkazů: stisknutý stav**

![Stisknuté pole výběru&#45;dolů](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Rozevírací pole panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownMouseDownBackground` |
| Popředí (text) | `Environment.DropDownMouseDownText` |
| Ohraničení | `Environment.DropDownMouseDownBorder` |
| Oddělovač | `Environment.DropDownButtonMouseDownSeparator` |

**Rozevírací tlačítko panelu příkazů: stisknutý stav**

![Rozevírací tlačítko panelu příkazů](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Rozevírací tlačítko panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownButtonMouseDownBackground` |
| Popředí (glyf) | `Environment.DropDownMouseDownGlyph` |

**Rozevírací pole panelu příkazů: zakázaný stav**

![Zakázané rozevírací pole panelu příkazů](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Zakázané rozevírací pole panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownDisabledBackground` |
| Popředí (text) | `Environment.DropDownDisabledText` |
| Ohraničení | `Environment.DropDownDisabledBorder` |
| Oddělovač | Žádný oddělovač |

**Rozevírací tlačítko panelu příkazů: zakázaný stav**

![Zakázané rozevírací tlačítko panelu příkazů](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Zakázané rozevírací tlačítko panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není dostupné. |
| Popředí (glyf) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Tlačítka rozdělení panelu příkazů
Rozdělená tlačítka sdílejí mnoho názvů tokenů s dalšími ovládacími prvky panelu příkazů, jako jsou tlačítka, nabídky a text panelu příkazů. Všechny potřebné akce a názvy tokenů rozevíracího tlačítka se zde opakují pro pohodlí. Rozevírací seznamy rozdělených tlačítek jsou implementace [nabídek panelu příkazů](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Červené tlačítko Rozdělení](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Tlačítko rozdělení panelu příkazů (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... při vytváření vlastního tlačítka rozdělení. | ... pro jiné druhy tlačítek. |
| | ... v jakékoli kombinaci pozadí/popředí, než je uvedeno. |

**Tlačítko rozdělení panelu příkazového řádku: výchozí stav**

![Výchozí tlačítko rozdělení panelu příkazů](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Výchozí tlačítko rozdělení panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádný |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Popředí (glyf) | `Environment.CommandBarSplitButtonGlyph` |
| Ohraničení | Není dostupné. |
| Oddělovač | Není dostupné. |

**Tlačítko rozdělení panelu příkazového řádku: stav najetí přes**

![Tlačítko rozdělení panelu příkazového řádku při najetí přes](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Tlačítko rozdělení panelu příkazového řádku při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.CommandBarTextHover` |
| Popředí (glyf) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Ohraničení | `Environment.CommandBarBorder` |
| Oddělovač | `Environment.CommandBarSplitButtonSeparator` |

**Tlačítko rozdělení panelu příkazového řádku: stisknutý stav**

![Stisknuté tlačítko rozdělení panelu příkazů](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Stisknuté tlačítko rozdělení panelu příkazů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.CommandBarTextMouseDown` |
| Popředí (glyf) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Ohraničení | `Environment.CommandBarBorder` |
| Oddělovač | Není dostupné. |

**Tlačítko rozdělení panelu příkazového řádku: zakázaný stav**

![Zakázané tlačítko rozdělení příkazového řádku](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Zakázané tlačítko rozdělení příkazového řádku

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není dostupné. |
| Popředí (text) | `Environment.ComboBoxItemTextInactive` |
| Popředí (glyf) | `Environment.CommandBarTextInactive` |
| Ohraničení | Není dostupné. |
| Oddělovač | Není dostupné. |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Tlačítka "Další možnosti" a Přetečení
Tlačítko "Další možnosti" se používá, když lze přizpůsobit skupinu panelu příkazů přidáním nebo odebráním souvisejících tlačítek panelu příkazů. Tlačítko "Přetečení" se zobrazí, když je panel příkazů zkrácen kvůli nedostatku vodorovného prostoru, a po klepnutí se zobrazí nabídka obsahující tlačítka panelu příkazů, která nelze zobrazit. Barvy pro tato dvě tlačítka jsou řízeny stejnou sadou názvů tokenů.

![Panel příkazů "Další možnosti" (červená čára)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Panel příkazů "Další možnosti" (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... pro vlastní tlačítka "Další možnosti" nebo Přetečení. | ... pro tlačítka, která nemají podobné funkce jako tlačítko "Další možnosti" nebo Přetečení. |

**Příkazový panel "Další možnosti" a Tlačítka Přetečení: výchozí stav**

![Výchozí panel příkazů Tlačítko Další možnosti](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Výchozí panel příkazů Tlačítko Další možnosti

![Výchozí panel příkazů Tlačítko Přetečení](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Výchozí panel příkazů Tlačítko Přetečení

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarOptionsBackground` |
| Popředí (glyf) | `Environment.CommandBarOptionsGlyph` |

**Příkazový panel "Další možnosti" a "Přetečení": stav najetí**

![Panel příkazů "Další možnosti" při najetí mezi obrázky](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Panel příkazů "Další možnosti" při najetí mezi obrázky

![Příkazový řádek "Přetečení" při najetí](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Příkazový řádek "Přetečení" při najetí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (glyf) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Příkazový panel "Další možnosti" a Tlačítka Přetečení: stisknutý stav**

![Stisknuté tlačítko Panel příkazů "Další možnosti"](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Stisknuté tlačítko Panel příkazů "Další možnosti"

![Přetekli](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Stisknuté tlačítko Panel příkazů Přetečení

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (glyf) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Okna dokumentu
Není nutné replikovat okna dokumentů, protože jsou k dispozici prostředí Sady Visual Studio. Můžete se však rozhodnout, že chcete využít barvy použité v oknech dokumentu tak, aby vaše ui vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.

Při použití tokenů barev okna dokumentu buďte opatrní, abyste je používali pouze pro podobné prvky a vždy ve dvojicích. Pokud tak neučiníte, může dojít k neočekávaným výsledkům v ui.

### <a name="document-window-frames"></a>Rámečky oken dokumentu
Okna dokumentu mohou být ukotvena v prostředí IDE nebo plovoucí jako samostatné okno. Pokud je okno dokumentu plovoucí mimo ide, stále sedí v dokumentu dobře a má pozadí, ohraničení, text a tabulátor barvy, které jsou stejné jako když je součástí ide. Dokument je však v něm nasazený uvnitř rámečku, který má vlastní barvy pozadí, ohraničení a textu. Když jsou okna nástrojů ukotvena v dokumentu dobře, dědí chování a barvu pro své karty z názvů tokenů okna dokumentu.

![Okno ukotveného dokumentu (červená čára)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Okno ukotveného dokumentu (červená čára)

![Plovoucí okno dokumentu (červená čára)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Plovoucí okno dokumentu (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... kdekoli vytváříte ui, které chcete shodovat s oknem dokumentu. | ...  pro jakékoli ui, které nechcete automaticky změnit, pokud prostředí obsahuje aktualizaci motivu. |

**Ukotvené nebo plovoucí okno dokumentu: výchozí stav**

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Závisí na typu dokumentu |
| Popředí (text) | Závisí na typu dokumentu |
| Ohraničení | `Environment.ToolWindowBorder` |

**Ostře zaostřený plovoucí rámeček okna dokumentu: výchozí stav**

![Výchozí zaostřený plovoucí rámeček okna dokumentu](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Výchozí zaostřený plovoucí rámeček okna dokumentu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowFloatingFrame` |
| Popředí (text) | `Environment.ToolWindowFloatingFrame` |
| Popředí (glyf) | `Environment.RaftedWindowButtonActiveGlyph` |
| Ohraničení | `Environment.MainWindowActiveDefaultBorder` |
| Ohraničení (glyf) | `Environment.RaftedWindowButtonActiveBorder`<br />(Nastavit na průhledný) |

**Nezaostřený plovoucí rámeček okna dokumentu: výchozí stav**

![Výchozí nezaostřený plovoucí rámeček okna dokumentu](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Výchozí nezaostřený plovoucí rámeček okna dokumentu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowFloatingFrameInactive` |
| Popředí (text) | `Environment.ToolWindowFloatingFrameInactive` |
| Popředí (glyf) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Ohraničení | `Environment.MainWindowInactiveBorder` |
| Ohraničení (glyf) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Nastavit na průhledný) |

**Ostře zaostřený plovoucí rámeček okna dokumentu: stav připisu**

![Zaostřený plovoucí rámeček okna dokumentu při najetí](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Zaostřený plovoucí rámeček okna dokumentu při najetí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí (glyf) | `Environment.RaftedWindowButtonHoverActive` |
| Popředí (glyf) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Ohraničení (glyf) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Nezaostřený plovoucí rámeček okna dokumentu: stav připisu**

![Nezaostřený plovoucí rámeček okna dokumentu při najetí](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Nezaostřený plovoucí rámeček okna dokumentu při najetí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí (glyf) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Popředí (glyf) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Ohraničení (glyf) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Ostře zaostřený plovoucí rámeček okna dokumentu: stisknutý stav**

![Zaostřený plovoucí rámeček okna dokumentu na stisknutí](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Zaostřený plovoucí rámeček okna dokumentu na stisknutí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí (glyf) | `Environment.RaftedWindowButtonDown` |
| Popředí (glyf) | `Environment.RaftedWindowButtonDownGlyph` |
| Ohraničení (glyf) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Záložky dokumentů
Karty dokumentů jsou v kanálu karet, které označují, které dokumenty jsou aktuálně otevřené, spolu s nimiž se jedná o aktuální vybraný nebo aktivní dokument. Okna nástrojů lze také ukotvit v kanálu karty dokumentu, pokud je tam uživatel umístí. V takovém případě používají stejné barvy karty jako okna dokumentu. Pokud vytváříte ui, které chcete vždy odpovídat barvy okna dokumentu (včetně aktualizací motivu nebo pokud jsou nainstalovány nové motivy), pak odkazovat na tyto tokeny barev.

![Karty dokumentů (červená čára)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Karty dokumentů (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... kdekoli vytváříte ui, které chcete přizpůsobit karty dokumentů a automaticky vyzvednout aktualizace motivů nebo nové barvy motivu. | ... pro jakékoli ui, které nechcete změnit automaticky, když prostředí má aktualizaci motivu. |

#### <a name="open-document-tabs"></a>Otevření karet dokumentů
Každý otevřený dokument má v kanálu karty dokumentu kartu, která zobrazuje jeho název. Dokumenty mohou být vybrány nebo otevřeny na pozadí a jejich karty odrážejí tyto stavy:

- Vybraná karta představuje dokument, který je aktuálně zobrazen v dokumentu dobře. Vybraná karta má ohraničení dokumentu, které dobře přesahuje horní okraj dokumentu.

- Karty na pozadí jsou všechny karty dokumentů, které nejsou aktuálně vybranou kartou. Po kliknutí se stanou vybranou kartou a z těchto názvů tokenů získají všechny barvy pozadí, ohraničení a textu.

![Otevřít kartu dokumentu (červená čára)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Otevřít kartu dokumentu (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... při vytváření vlastních karet dokumentů. | ... pro předběžné (náhledové) karty. |
| | ... pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu. |

**Vybraná karta s fokusem dokumentu**

![Vybraná karta s fokusem dokumentu](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Vybraná karta s fokusem dokumentu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabSelectedGradientTop`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.FileTabSelectedText` |
| Ohraničení | `Environment.FileTabSelectedBorder`<br />(Nastavte stejnou barvu jako pozadí.) |
| Ohraničení dokumentu | `Environment.FileTabDocumentBorderBackground` |

**Vybraná, nezaostřená karta dokumentu**

![Vybraná, nezaostřená karta dokumentu](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Vybraná, nezaostřená karta dokumentu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabInactiveGradientTop`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.FileTabInactiveText` |
| Ohraničení | `Environment.FileTabInactiveBorder`<br />(Nastavte stejnou barvu jako pozadí.) |
| Ohraničení dokumentu | `Environment.FileTabInactiveDocumentBorderBackground` |

**Karta Dokument pozadí: výchozí stav**

![Výchozí karta dokumentu na pozadí](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Výchozí karta dokumentu na pozadí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabBackground` |
| Popředí (text) | `Environment.FileTabText` |
| Ohraničení | `Environment.FileTabBorder`<br />(Nastavte stejnou barvu jako pozadí.) |

**Karta Dokumentu na pozadí: stav najetého jako Vichyt**

![Karta Dokument pozadí při najetí přes](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Karta Dokument pozadí při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabHotGradientTop`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.FileTabHotText` |
| Ohraničení | `Environment.FileTabHotBorder`<br />(Nastavte stejnou barvu jako pozadí.) |

#### <a name="preview-tab"></a>Karta Náhled
Také se nazývá "prozatímní" karta. Karta Náhled se zobrazí na pravé straně kanálu karty dokumentu, když uživatel klepne na položku v okně nástroje Průzkumník řešení. Funguje jako náhled dokumentu a také dává uživateli možnost ponechat dokument otevřený na levé straně kanálu karty dokumentu. Současně lze otevřít pouze jednu otevřenou kartu náhledu. Karty náhledu mají pozadí i vybrané stavy, například otevřené karty, a lze je zaostřit nebo rozostřit v aktivním stavu.

![Karta Náhled (červená čára)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Karta Náhled (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... kdekoli vytváříte předběžný náhled a chcete, aby nějaký prvek odpovídal aktuální barvě karty náhledu. | ... pro jakýkoli druh dokumentu nebo karty, která není prozatímní (náhled). |
| | ... pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu. |

**Zaostřená, vybraná karta náhledu**

![Zaostřená, vybraná karta náhledu](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Zaostřená, vybraná karta náhledu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabProvisionalSelectedActive` |
| Popředí (text) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Ohraničení | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Nastavte stejnou barvu jako pozadí.) |
| Ohraničení dokumentu | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Nezaostřená, vybraná karta náhledu**

![Nezaostřená, vybraná karta náhledu](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Nezaostřená, vybraná karta náhledu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabProvisionalSelectedInactive` |
| Popředí (text) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Ohraničení | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Ohraničení dokumentu | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Karta Náhled na pozadí: výchozí stav**

![Výchozí karta náhledu pozadí](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Výchozí karta náhledu pozadí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabProvisionalInactive` |
| Popředí (text) | `Environment.FileTabProvisionalInactiveForeground` |
| Ohraničení | `Environment.FileTabProvisionalInactiveBorder`<br />(Nastavte stejnou barvu jako pozadí.) |

**Karta Náhled na pozadí: stav najetého jako Vichřové**

![Karta Náhled pozadí při najetí přes](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Karta Náhled pozadí při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabProvisionalHover` |
| Popředí (text) | `Environment.FileTabProvisionalHoverForeground` |
| Ohraničení | `Environment.FileTabProvisionalHoverBorder`<br />(Nastavte stejnou barvu jako pozadí.) |

#### <a name="document-overflow-button"></a>Tlačítko přetečení dokumentu
Tlačítko přetečení dokumentu je k dispozici, pokud je otevřen jeden nebo více dokumentů, bez ohledu na to, zda je v aktuální konfiguraci svislé místo, aby se vešly všechny karty dokumentu. Rozevírací nabídka Přetečení dokumentu, která je řízena barvami [nabídky panelu příkazů,](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) zobrazuje seznam všech otevřených dokumentů, viditelných i skrytých, a přetečení glyfů se mění v závislosti na tom, zda jsou všechny otevřené dokumenty zobrazeny v kanálu karet.

![Tlačítko přetečení dokumentu (červená čára)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Tlačítko přetečení dokumentu (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... při vytváření vlastního tlačítka přetečení dokumentu. | ... pro ui, které není podobné tlačítko přetečení. |
| | ... pro tlačítka přetečení panelu příkazů. |

**Tlačítko přetečení dokumentu: výchozí stav**

![Výchozí tlačítko přetečení dokumentu](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Výchozí tlačítko přetečení dokumentu

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DocWellOverflowButtonBackground` |
| Popředí (glyf) | `Environment.DocWellOverflowButtonGlyph` |
| Ohraničení | Není dostupné. |

**Tlačítko přetečení dokumentu: stav najetí přes**

![Tlačítko přetečení dokumentu při najetí přes](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Tlačítko přetečení dokumentu při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Popředí (glyf) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Ohraničení | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Tlačítko přetečení dokumentu: stisknutý stav**

![Tlačítko přetečení dokumentu stisknutím tlačítka](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Tlačítko přetečení dokumentu stisknutím tlačítka

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Popředí (glyf) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Ohraničení | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Označování
Visual Studio podporuje označování, které umožňuje uživateli deklarovat prohledávatelná klíčová slova pro účely sledování. Například projektoví manažeři a vývojáři mohou použít Team Foundation Server (TFS) k označení pracovních položek. Níže uvedené tabulky udávají názvy barev pro samotnou značku i glyf "zavřít ikonu", který se zobrazí v režimu umístění v měřítku a vybraných stavech.

![Označování v sadě Visual Studio (červená čára)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Označování v sadě Visual Studio (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... pro ui, které podporuje označování. | ... pro jakýkoli jiný typ ui. |

#### <a name="tags"></a>Značky

**Značka: výchozí stav**

![Výchozí značka](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Výchozí značka

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.Background` |
| Popředí (text) | `Tag.Background` |

**Značka: stav najetí přes**

![Značka při najetí přes](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Značka při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.HoverBackground` |
| Popředí (text) | `Tag.HoverBackgroundText` |

**Značka: lisovaný stav**

![Lisovaná značka](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Lisovaná značka

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.PressedBackground` |
| Popředí (text) | `Tag.PressedBackgroundText` |

**Značka: vybraný stav**

![Vybraná značka](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Vybraná značka

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.SelectedBackground` |
| Popředí (text) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Zavřít&times;( ) tag glyf

**Zavřít&times;( ) tag glyf: výchozí stav**

![Výchozí glyf značky Zavřít (&times;)](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Výchozí glyf značky Zavřít (&times;)

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není dostupné. |
| Popředí (glyf) | `Tag.TagHoverGlyph` |

**Zavřít&times;( ) tag glyf: stav připisu**

![Zavřít&times;( ) tag glyf na hover](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Zavřít&times;( ) tag glyf na hover

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.TagHoverGlyphHoverBackground` |
| Popředí (glyf) | `Tag.TagHoverGlyphHover` |
| Ohraničení | `Tag.TagHoverGlyphHoverBorder` |

**Zavřít&times;( ) tag glyf: lisovaný stav**

![Stlačený&times;glyf značky Zavřít ( )](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Stlačený&times;glyf značky Zavřít ( )

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.TagHoverGlyphPressedBackground` |
| Popředí (glyf) | `Tag.TagHoverGlyphPressed` |
| Ohraničení | `Tag.TagHoverGlyphPressedBorder` |

**Vybraná značka&times;s glyfem Zavřít ( ) : výchozí stav**

![Výchozí vybraná značka&times;s glyfem Zavřít ( )](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Výchozí vybraná značka&times;s glyfem Zavřít ( )

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není dostupné. |
| Popředí (glyf) | `Tag.TagSelectedGlyph` |

**Vybraná značka&times;s glyfem Zavřít ( ) : stav přijet**

![Vybraná značka&times;s glyfem Zavřít ( ) při najetí](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Vybraná značka&times;s glyfem Zavřít ( ) při najetí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.TagSelectedGlyphHoverBackground` |
| Popředí (glyf) | `Tag.TagSelectedGlyphHover` |
| Ohraničení | `Tag.TagSelectedGlyphHoverBorder` |

**Vybraná značka&times;s glyfem Zavřít ( ) : stav stisknutí**

![Vybraná, stisknutá&times;značka s glyfem Zavřít ( ).](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Vybraná, stisknutá&times;značka s glyfem Zavřít ( ).

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.TagSelectedGlyphPressedBackground` |
| Popředí (glyf) | `Tag.TagSelectedGlyphPressed` |
| Ohraničení | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Okna nástrojů
Není nutné replikovat okna nástrojů, protože jsou k dispozici prostředí sady Visual Studio. Můžete se však rozhodnout, že chcete využít barvy použité v oknech nástrojů tak, aby vaše ui vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.

![Okno nástroje (červená čára)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Okno nástroje (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... kdekoli vytváříte ui, které chcete přizpůsobit oknům nástrojů. | ... pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu. |

### <a name="tool-window-frame"></a>Rám okna nástroje
Okna nástrojů v sadě Visual Studio se používají pro mnoho různých úkolů a mohou existovat v jednom z několika různých stavů. Pokud je okno nástroje otevřené, lze jej přiřadit k libovolné ze čtyř stran oblasti dokumentu. Okna nástrojů mohou také plavat mimo rozhraní IDE, což umožňuje jejich přemístění kdekoli na obrazovce uživatele. Plovoucí okna vždy sedět na vrcholu IDE. Nakonec mohou být okna nástrojů ukotvena jako okna dokumentu a v dokumentu se dobře zobrazí jako karta. Okna nástrojů, která byla ukotvena jako okna dokumentu, jsou částečně barevná pomocí názvů tokenů okna dokumentu.

![Rámeček okna nástroje (červená čára)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Rámeček okna nástroje (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ...  kdekoli vytváříte ui, které chcete přizpůsobit oknům nástrojů. | ... pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu. |

**Okno ukotveného nástroje**

![Okno ukotveného nástroje](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Okno ukotveného nástroje

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowBackground` |
| Ohraničení | `Environment.ToolWindowBorder` |

**Plovoucí okno nástroje s ostřem**

![Plovoucí okno nástroje s ostřem](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Plovoucí okno nástroje s ostřem

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowBackground` |
| Ohraničení | `Environment.MainWindowActiveDefaultBorder` |

**Plovoucí okno nástroje, které nezaostřeno**

![Plovoucí okno nástroje, které nezaostřeno](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Plovoucí okno nástroje, které nezaostřeno

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowBackground` |
| Ohraničení | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Okna jako panel nástrojů
Panel nástrojů je jedním z nejčastěji používaných běžných oken nástrojů v sadě Visual Studio. Je to v podstatě strom ovládací prvek se speciálním tématem a styling použít.

![Okno podobné panelu nástrojů (červená čára)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Okno podobné panelu nástrojů (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... při navrhování okna nástroje, které chcete vždy konzistentní s panelem nástrojů prostředí. | ... pro cokoli, co není podobné ujnonástrojů nástrojů, nebo pokud si nejste jisti, zda vaše uI bude mít problémy, pokud shell toolbox barvy změnit. |

**Uzly panelu nástrojů: výchozí stav**

![Výchozí nadřazený uzel panelu nástrojů](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Výchozí nadřazený uzel panelu nástrojů

![Výchozí podřízený uzel panelu nástrojů](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Výchozí podřízený uzel panelu nástrojů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolboxContent`<br />(Nadpisy) |
| Pozadí | `Environment.ToolWindowBackground`<br />(Jednotlivé položky nebo celé okno, pokud nejsou k dispozici žádné ovládací prvky) |
| Ohraničení | Žádný |
| Popředí (glyf) | `Environment.ToolboxContent` |
| Popředí (text) | `Environment.ToolboxContent` |

**Podřízené uzly panelu nástrojů: stav přijetí**

![Podřízený uzel panelu nástrojů při najetí](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Podřízený uzel panelu nástrojů při najetí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolboxContentMouseOver`<br />(Pouze jednotlivé položky) |
| Ohraničení | Žádný |
| Popředí (text) | `Environment.ToolboxContentMouseOver`<br />(Pouze jednotlivé položky) |

**Vybrané uzly panelu nástrojů: zaměřený stav**

![Fokus, vybraný nadřazený uzel panelu nástrojů](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Fokus, vybraný nadřazený uzel panelu nástrojů

![Fokus, vybraný podřízený uzel panelu nástrojů](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Fokus, vybraný podřízený uzel panelu nástrojů

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemActive`<br />Ze [stromové](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |
| Ohraničení | `TreeView.FocusVisualBorder`<br />Ze [stromové](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |
| Popředí (glyf) | `TreeView.SelectedItemActive`<br />Ze [stromové](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |
| Popředí (text) | `TreeView.SelectedItemActive`<br />Ze [stromové](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |

**Vybrané uzly panelu nástrojů: nezaostřený stav**

![Vybraný, nezaostřený nadřazený uzel panelu nástrojů](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Vybraný, nezaostřený nadřazený uzel panelu nástrojů

![Vybraný podřízený uzel panelu nástrojů nezaostřený](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Vybraný podřízený uzel panelu nástrojů nezaostřený

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemInactive`<br />Ze [stromové](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |
| Ohraničení | Žádný |
| Popředí (glyf) | `TreeView.SelectedItemInactive`<br />Ze [stromové](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |
| Popředí (text) | `TreeView.SelectedItemInactive`<br />Ze [stromové](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |

### <a name="tool-window-title-bar"></a>Záhlaví okna nástroje
Ohraničení záhlaví není skutečným ohraničením, je to tlustá čára v horní části záhlaví. Nemá název tokenu pro jeho nezaostřený stav.

![Záhlaví okna nástroje (červená čára)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Záhlaví okna nástroje (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... kdekoli vytváříte ui, které chcete přizpůsobit oknům nástrojů. | ... pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu. |

**Zaostřený záhlaví**

![Zaostřený záhlaví](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Zaostřený záhlaví

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.TitleBarActiveGradientBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.TitleBarActiveText` |
| Ohraničení | `Environment.TitleBarActiveBorder`<br />(Nastavte stejnou barvu jako pozadí.) |
| Táhlo přetažení | `Environment.TitleBarDragHandleActive` |

**Nezaostřený záhlaví**

![Záhlaví rozostřené](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Nezaostřený záhlaví

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.TitleBarInactiveGradientBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.TitleBarInactiveText` |
| Ohraničení | Není dostupné. |
| Táhlo přetažení | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Tlačítka záhlaví okna nástroje
![Tlačítko záhlaví (červená čára)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Tlačítko záhlaví (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... pro tlačítka, která se zobrazují v ui, která používá tokeny barev z záhlaví okna nástroje. | ... tlačítka, která se zobrazují v jiných umístěních. |
| | ... v jakékoli kombinaci pozadí/popředí, než je uvedeno. |

**Zaostřená tlačítka záhlaví: výchozí stav**

![Výchozí tlačítka nadpisu se zaměřením](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Výchozí tlačítka nadpisu se zaměřením

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není dostupné. |
| Popředí (glyf) | `Environment.ToolWindowButtonActiveGlyph` |
| Ohraničení | Není dostupné. |

**Nezaostřená tlačítka záhlaví: výchozí stav**

![Výchozí, rozostřená tlačítka záhlaví](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Výchozí, rozostřená tlačítka záhlaví

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není dostupné. |
| Popředí (glyf) | `Environment.ToolWindowButtonInactiveGlyph` |
| Ohraničení | Není dostupné. |

**Zaostřená tlačítka záhlaví: stav najetého řádku**

![Zaměřená tlačítka záhlaví při najetí přes](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Zaměřená tlačítka záhlaví při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowButtonHoverActive` |
| Popředí (glyf) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Ohraničení | `Environment.ToolWindowButtonHoverActiveBorder` |

**Nezaostřená tlačítka záhlaví: stav najetého řádku**

![Nezaostřená tlačítka záhlaví při najetí přes](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Nezaostřená tlačítka záhlaví při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowButtonHoverInactive` |
| Popředí (glyf) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Ohraničení | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Zaostřená tlačítka záhlaví: stisknutý stav**

![Zaměřená tlačítka záhlaví při stisknutí](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Zaměřená tlačítka záhlaví při stisknutí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowButtonDown` |
| Popředí (glyf) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Ohraničení | `Environment.ToolWindowButtonDownBorder` |

**Nezaostřená tlačítka záhlaví: stisknutý stav**

![Nezaostřená tlačítka záhlaví při stisknutí](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Nezaostřená tlačítka záhlaví při stisknutí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowButtonDown` |
| Popředí (glyf) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Ohraničení | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Karty oken nástrojů
![Karta okna nástroje (červená čára)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Karta okna nástroje (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... kdekoli vytváříte ui, které chcete přizpůsobit oknům nástrojů. | ... pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu. |

**Karta okna vybraného zaostřeného nástroje**

![Karta okna vybraného zaostřeného nástroje](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Karta okna vybraného zaostřeného nástroje

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowTabSelectedTab` |
| Popředí (text) | `Environment.ToolWindowTabSelectedActiveText` |
| Ohraničení | `Environment.ToolWindowTabSelectedBorder`<br />(Nastavte stejnou barvu jako pozadí.) |

**Karta vybraného, nezaostřeného okna nástroje**

![Karta vybraného, nezaostřeného okna nástroje](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Karta vybraného, nezaostřeného okna nástroje

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowTabSelectedTab` |
| Popředí (text) | `Environment.ToolWindowTabSelectedText` |
| Ohraničení | `Environment.ToolWindowTabSelectedBorder`<br />(Nastavte stejnou barvu jako pozadí.) |

**Karta okna nástroje pozadí: výchozí stav**

![Karta okna výchozího nástroje pozadí](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Karta okna výchozího nástroje pozadí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Přechod ové zarážky nastavené na stejnou hodnotu barvy v sadě Visual Studio 2013.) |
| Popředí (text) | `Environment.ToolWindowTabText` |
| Ohraničení | `Environment.ToolWindowTabBorder` |

**Karta okna nástroje pozadí: stav najetého jako: stav najetého**

![Karta okna nástroje pozadí při najetí přes](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Karta okna nástroje pozadí při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Přechod ové zarážky nastavené na stejnou hodnotu barvy v sadě Visual Studio 2013.) |
| Popředí (text) | `Environment.ToolWindowTabMouseOverText` |
| Ohraničení | `Environment.ToolWindowTabMouseOverBorder`<br />(Nastavte stejnou barvu jako pozadí.) |

### <a name="auto-hide-tabs"></a>Automatické skrytí karet

![Automatické skrytí karet (červená čára)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Automatické skrytí karet (červená čára)

| Použít... | Nepoužívejte ... |
| --- | --- |
| ... kdekoli vytváříte ui, které chcete přizpůsobit automaticky skrytým kartám okna nástrojů. | ... pro jakékoli ui, které nechcete změnit automaticky, pokud prostředí obsahuje aktualizaci motivu. |

**Automatické skrytí karet: výchozí stav**

![Výchozí karta automatického skrytí](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Výchozí karta automatického skrytí

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.AutoHideTabBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.AutoHideTabText` |
| Ohraničení | `Environment.AutoHideTabBorder` |

**Automatické skrytí karet: stav najetého jako Ujetého jako v**

![Automaticky skrýt kartu při najetí přes](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Automaticky skrýt kartu při najetí přes

| Element | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Přechod se zastaví pro tento token, který se nepoužívá v tematizovaném uzem.) |
| Popředí (text) | `Environment.AutoHideTabMouseOverText` |
| Ohraničení | `Environment.AutoHideTabMouseOverBorder` |
