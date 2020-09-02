---
title: Sdílené barvy pro Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e31e5d9c3d1dc284694bd2db2a9f37d863462ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699933"
---
# <a name="shared-colors-for-visual-studio"></a>Sdílené barvy pro Visual Studio
Pokud navrhujete uživatelské rozhraní, které používá společné prvky prostředí sady Visual Studio, nebo chcete, aby element rozhraní byl konzistentní s podobnými funkcemi, použijte existující názvy tokenů v definičních souborech balíčku k výběru a přiřazení barev. Tím se zajistí, že vaše uživatelské rozhraní zůstane v souladu s celkovým prostředím sady Visual Studio a že se automaticky aktualizuje při přidání nebo aktualizaci motivů.

Tento článek popisuje běžné prvky uživatelského rozhraní a názvy tokenů, které používají, na které můžete odkazovat při sestavování podobného uživatelského rozhraní. Konkrétní informace o tom, jak získat přístup k těmto barevným tokenům, najdete v tématu [Služba VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Ujistěte se, že používáte názvy tokenů správně:

- **Použijte názvy tokenů založené na funkci, nikoli na samotné barvě.** Společné sdílené barvy jsou spojeny s konkrétními prvky rozhraní a jsou určeny pouze pro použití pro stejné nebo podobné funkce. Nepoužívejte například barvu stisknutého pole se seznamem pro animaci průběhu, protože jste chtěli barvu. Funkce pole se seznamem a animace se liší a pokud se barva přidružená k poli se seznamem změní, nemusí již být vhodnou barvou pro váš element animace. Konzistentní použití barev pomáhá orientovat uživatele a zabránit nejasnostem.

- **Používejte barvy pozadí a textu ve správné kombinaci.** Barvy pozadí, které se mají použít s textem, budou mít přidruženou barvu textu. Nepoužívejte barvy textu kromě těch, které jsou určeny pro dané pozadí. Pokud není k dispozici žádná barva textu, nepoužívejte tuto barvu pozadí pro všechny plochy, na kterých očekáváte zobrazení textu. Jiné kombinace barvy textu a pozadí můžou mít za následek nečitelný rozhraní.

- **Používejte barvy ovládacích prvků, které jsou vhodné pro jejich umístění.** V některých stavech některé ovládací prvky sady Visual Studio nemají samostatné barvy ohraničení a pozadí. Místo toho tyto barvy vyberou z povrchů za ně. Ujistěte se, že používáte vždy názvy tokenů, které jsou vhodné pro umístění, kam umístíte ovládací prvek.

> [!IMPORTANT]
> Nepoužívejte tokeny nacházející se v kategoriích "Úvodní stránka" nebo "jablečná".

## <a name="common-shared-controls"></a>Společné sdílené ovládací prvky

Použijete-li ve své funkci standardní panel příkazů sady Visual Studio, budete mít přístup k ovládacím prvkům ve stylu Shell. Tyto běžné ovládací prvky byste neměli znovu šablonovat. Pokud ale potřebujete vytvořit vlastní panel příkazů, možná budete muset vytvořit také vlastní ovládací prvky. V takovém případě nezapomeňte použít správné názvy tokenů pro každý z následujících ovládacích prvků tak, aby vaše uživatelské rozhraní bylo konzistentní se zbytkem sady Visual Studio.

### <a name="button-controls"></a>ovládací prvky tlačítek

![Redline ovládacího prvku tlačítko](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 – 155_ButtonControlRedline")

| Použít... | Nepoužívat... |
| --- | --- |
| ... pro tlačítka v dokumentaci dokumentu, které chcete integrovat s motivy sady Visual Studio (světlá, tmavě, modrá nebo motiv systému Vysoký kontrast). | ... pro tlačítka, která se zobrazí proti vlastnímu pozadí, které není součástí motivu sady Visual Studio. |

**Tlačítko: stav Standard**

![Tlačítko Standard](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03. Button. Standard")<br />Tlačítko Standard

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Tlačítko | `CommonControls.Button` |
| Ohraničení tlačítka | `CommonControls.ButtonBorder` |

**Tlačítko: výchozí stav**

![Výchozí tlačítko](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03. Button. Default")<br />Výchozí tlačítko

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonDefault` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderDefault` |

**Tlačítko: zakázaný stav**

![Zakázané tlačítko](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03. Button. disabled")<br />Zakázané tlačítko

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonDisabled` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderDisabled` |

**Tlačítko: stav přechodu myši**

![Tlačítko při najetí myší](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03. Button. najeďte")<br />Tlačítko při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonHover` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderHover` |

**Tlačítko: stisknutí stavu**

![Stisknuté tlačítko](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03. Button. stiskl")<br />Stisknuté tlačítko

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonPressed` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderPressed` |

**Tlačítko: soustředěný stav**

![Tlačítko s fokusem](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03. Button. prioritní")<br />Tlačítko s fokusem

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonFocused` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Ovládací prvky zaškrtávacích políček
![Zaškrtávací políčko (Redline)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303 – 161_CheckboxRedline")<br />Zaškrtávací políčko (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... pro ovládací prvky zaškrtávací políčko obsažené v dokumentaci dokumentu. | ... pro jakékoli uživatelské rozhraní, které není ovládacím prvkem zaškrtávací políčko. |

**Zaškrtávací políčko: výchozí stav**

![Zaškrtávací políčko](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303 – 162_Checkbox")<br />Výchozí Zaškrtávací políčko

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackground` |
| Ohraničení | `CommonControls.CheckBoxBorder` |
| Text | `CommonControls.CheckBoxText` |
| Zobrazovat | `CommonControls.CheckBoxGlyph` |

**Zaškrtávací políčko: zakázaný stav**

![Zakázané zaškrtávací políčko](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303 – 163_CheckboxDisabled")<br />Zakázané zaškrtávací políčko

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundDisabled` |
| Ohraničení | `CommonControls.CheckBoxBorderDisabled` |
| Text | `CommonControls.CheckBoxTextDisabled` |
| Zobrazovat | `CommonControls.CheckBoxGlyphDisabled` |

**Zaškrtávací políčko: stav přechodu myši**

 ![Zaškrtávací políčko při najetí myší](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303 – 164_CheckboxHover")<br />Zaškrtávací políčko při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundHover` |
| Ohraničení | `CommonControls.CheckBoxBorderHover` |
| Text | `CommonControls.CheckBoxTextHover` |
| Zobrazovat | `CommonControls.CheckBoxGlyphHover` |

**Zaškrtávací políčko: stisknuté – stav**

![Stisknuté políčko](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303 – 165_CheckboxPressed")<br />Stisknuté políčko

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundPressed` |
| Ohraničení | `CommonControls.CheckBoxBorderPressed` |
| Text | `CommonControls.CheckBoxTextPressed` |
| Zobrazovat | `CommonControls.CheckBoxGlyphPressed` |

**Zaškrtávací políčko: prioritní stav**

![Fokus – zaškrtávací políčko](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303 – 166_CheckboxFocused")<br />Fokus – zaškrtávací políčko

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundFocused` |
| Ohraničení | `CommonControls.CheckBoxBorderFocused` |
| Text | `CommonControls.CheckBoxTextFocused` |
| Zobrazovat | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Rozevírací seznamy a pole se seznamem
![Rozevírací seznam/pole se seznamem (Redline)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303 – 167_DropDownComboBoxRedline")<br />Rozevírací seznam/pole se seznamem (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... pro rozevírací seznamy a pole se seznamem v dokumentaci dokumentu. | ... pro jakékoli uživatelské rozhraní, které není rozevírací nebo pole se seznamem. |
| | ... pro [rozevírací](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) panely příkazů nebo [pole se seznamem](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Rozevírací seznamy a pole se seznamem: výchozí stav**

![Výchozí rozevírací seznam/pole se seznamem](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303 – 168_DropDownComboBox")<br />Výchozí rozevírací seznam/pole se seznamem

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackground` |
| Ohraničení | `CommonControls.ComboBoxBorder` |
| Text | `CommonControls.ComboBoxText` |
| Oddělovač | `CommonControls.ComboBoxSeparator` |
| Zobrazovat | `CommonControls.ComboBoxGlyph` |
| Pozadí glyfu | `CommonControls.ComboBoxGlyphBackground` |

**Rozevírací seznamy a pole se seznamem: zakázaný stav**

![Zakázaný rozevírací seznam/pole se seznamem](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303 – 169_DropDownComboBoxDisabled")<br />Zakázaný rozevírací seznam/pole se seznamem

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackgroundDisabled` |
| Ohraničení | `CommonControls.ComboBoxBorderDisabled` |
| Text | `CommonControls.ComboBoxTextDisabled` |
| Oddělovač | `CommonControls.ComboBoxSeparatorDisabled` |
| Zobrazovat | `CommonControls.ComboBoxGlyphDisabled` |
| Pozadí glyfu | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Rozevírací seznamy a pole se seznamem: stav přechodu myši**

![Rozevírací seznam nebo pole se seznamem při najetí myší](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303 – 170_DropDownComboBoxHover")<br />Rozevírací seznam nebo pole se seznamem při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackgroundHover` |
| Ohraničení | `CommonControls.ComboBoxBorderHover` |
| Text | `CommonControls.ComboBoxTextHover` |
| Oddělovač | `CommonControls.ComboBoxSeparatorHover` |
| Zobrazovat | `CommonControls.ComboBoxGlyphHover` |
| Pozadí glyfu | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Rozevírací seznamy a pole se seznamem: stisknutí stavu**

![Stisknutí rozevíracího seznamu/pole se seznamem](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303 – 171_DropDownComboBoxPressed")<br />Stisknutí rozevíracího seznamu/pole se seznamem

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackgroundPressed` |
| Ohraničení | `CommonControls.ComboBoxBorderPressed` |
| Text | `CommonControls.ComboBoxTextPressed` |
| Oddělovač | `CommonControls.ComboBoxSeparatorPressed` |
| Zobrazovat | `CommonControls.ComboBoxGlyphPressed` |
| Pozadí glyfu | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Rozevírací seznamy a pole se seznamem – zobrazení položky: stisknutí stav**

 ![Rozevírací seznam/okno se stisknutým seznamem – zobrazení položky seznamu](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303 – 174_DropDownComboBoxListView")<br />Rozevírací seznam/okno se stisknutým seznamem – zobrazení položky seznamu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Ohraničení | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Text položky | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Stín pozadí | `CommonControls.ComboBoxListBackgroundShadow` |

**Rozevírací seznamy a pole se seznamem: prioritní stav**

![Rozevírací seznam nebo pole se seznamem s fokusem](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303 – 172_DropDownComboBoxFocused")<br />Rozevírací seznam nebo pole se seznamem s fokusem

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackgroundFocused` |
| Ohraničení | `CommonControls.ComboBoxBorderFocused` |
| Text | `CommonControls.ComboBoxTextFocused` |
| Oddělovač | `CommonControls.ComboBoxSeparatorFocused` |
| Zobrazovat | `CommonControls.ComboBoxGlyphFocused` |
| Pozadí glyfu | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Rozevírací seznamy a pole se seznamem: Výběr textového vstupu**

![Rozevírací seznam/pole se seznamem – výběr vstupu textu](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303 – 173_DropDownComboBoxTextInput")<br />Rozevírací seznam/pole se seznamem – výběr vstupu textu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Zvýraznit | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Ovládací prvky tabulkových dat (Grid)
Ovládací prvky tabulkových dat, označované také jako ovládací prvky mřížky, jsou běžné ovládací prvky pro sadu Visual Studio, které lze použít k zobrazení velkých objemů dat ve více sloupcích. Standardní tabulkové datové ovládací prvky lze nalézt na více místech v sadě Visual Studio: okno Seznam chyb nástrojů, sestavy IntelliTrace a zobrazení haldy paměti, mimo jiné. Vždy používejte standardní dodané tabelární datové ovládací prvky. V některých vzácných instancích je možné, že nebudete mít přístup ke standardním tabulkovým datovým ovládacím prvkům. V těchto situacích použijte následující názvy tokenů, abyste zajistili, že vaše uživatelské rozhraní je konzistentní s jinými ovládacími prvky tabulkových dat v aplikaci Visual Studio.

![Ovládací prvek tabulková data/mřížka (Redline)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303 – 197_TabularDataGridControlRedline")<br />Ovládací prvek tabulková data/mřížka (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... pro tabulkové nebo mřížkové ovládací prvky. | ... pro jakékoli uživatelské rozhraní, které není tabulkové nebo mřížkový ovládací prvek. |

#### <a name="column-headers"></a>Záhlaví sloupců
Záhlaví sloupců se skládají z pozadí, ohraničení, textu nadpisu a volitelné glyfy, která se obvykle používá při řazení mřížky podle daného sloupce.

**Záhlaví sloupce: výchozí stav**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Header.Default` |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Popředí (glyf) | `Header.Glyph` |
| Ohraničení | `Header.SeparatorLine` |

**Záhlaví sloupce: stav přechodu myši**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Header.MouseOver` |
| Popředí (text) | `Environment.CommandBarTextHover` |
| Popředí (glyf) | `Header.MouseOverGlyph` |
| Ohraničení | `Header.SeparatorLine` |

**Záhlaví sloupce: stisknutí stavu**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundPressed` |
| Popředí (text) | `CommonControls.CheckBoxBorderPressed` |
| Popředí (glyf) | `CommonControls.CheckBoxTextPressed` |
| Ohraničení | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Položky zobrazení seznamu
 Položky zobrazení seznamu se skládají z pozadí a obsahu. Obsah může být text, ikona nebo obojí.

**Položky zobrazení seznamu: výchozí stav**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Průhlednost |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Ohraničení | Žádné |

**Položky zobrazení seznamu: aktivní stav**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemActive` |
| Popředí (text) | `TreeView.SelectedItemActiveText` |
| Ohraničení | Žádné |

**Položky zobrazení seznamu: neaktivní stav**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemInactive` |
| Popředí (text) | `TreeView.SelectedItemInactiveText` |
| Ohraničení | Žádné |

### <a name="ui-text"></a>Text uživatelského rozhraní

#### <a name="instructional-text"></a>Instruktážní text
Instruktážní text poskytuje výrazné hlavní vysvětlení toho, co dělat v dialogovém okně nebo na stránce dokumentu.

![Výchozí text instrukcí](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Výchozí text instrukcí

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Sekundární instruktážní text
V dokumentu stránky s velkým množstvím textu a ovládacích prvků používá text instrukcí jinou hodnotu barvy. Díky tomu je možné vyjádřit, které informace jsou nejdůležitější, a snížit celkovou hustotu prvků uživatelského rozhraní. (Viz také část níže na textu nápovědy.)

![Sekundární instruktážní text](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Sekundární instruktážní text

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Text nápovědy
Text nápovědy se zobrazí v prázdném ovládacím prvku pod ovládacím prvkem nebo na prázdné ploše dokumentu, který uživateli ukáže, co dělat dál. Text nápovědy můžete použít buď s použitím okna, nebo pomocí pozadí ovládacího prvku.

**Výchozí text nápovědy**

![Výchozí text nápovědy](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Výchozí text nápovědy

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Environment.ControlEditHintText` |

**Požadovaný text nápovědy**

![Požadovaný text nápovědy](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Požadovaný text nápovědy

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Environment.ControlRequiredHintText` |
| Pozadí | `Environment.ControlRequiredBackground` |

**Text ovládacího prvku vyhledávacího pole**

> Další barevné tokeny související s ovládacím prvkem hledání naleznete v [poli hledání](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) .

![Text ovládacího prvku vyhledávacího pole](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Text ovládacího prvku vyhledávacího pole

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hypertextový odkaz
Hypertextový odkaz je jeden ovládací prvek, který nemá dvojici na popředí a na pozadí. Ve všech případech použijte barvu hypertextového odkazu na popředí, která se zobrazí správně na tmavém, šedém a bílé pozadí. Pokud nepoužijete token barvy pro ovládací prvek hypertextový odkaz, zobrazí se výchozí systémová barva "stisknout", která bude blikat červeně. To je signál, že ovládací prvek nepoužívá správný token barvy prostředí.

![Hypertextový odkaz (Redline)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303 – 133_HyperlinkRedline")<br />Hypertextový odkaz (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... Když potřebujete vytvořit vlastní hypertextový odkaz. | ... cokoli, co není hypertextový odkaz. |

**Hypertextový odkaz: výchozí stav**

![Výchozí hypertextový odkaz](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303 – 134_Hyperlink")<br />Výchozí hypertextový odkaz

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Environment.PanelHyperlink` |

**Hypertextový odkaz: stav přechodu myši**

![Hypertextový odkaz při najetí myší](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303 – 135_HyperlinkHover")<br />Hypertextový odkaz při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Environment.PanelHyperlinkHover` |

**Hypertextový odkaz: stisknutý stav**

![Stisknutý hypertextový odkaz](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303 – 136_HyperlinkPressed")<br />Stisknutý hypertextový odkaz

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Environment.PanelHyperlinkPressed` |

**Hypertextový odkaz: zakázaný stav**

![Zakázaný hypertextový odkaz](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303 – 137_HyperlinkDisabled")<br />Zakázaný hypertextový odkaz

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infobars
Infobars slouží k poskytnutí dalších informací o daném kontextu a vždy se zobrazí v horní části okna dokumentu nebo nástroje.

![Informační panel (Redline)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303 – 138_InfobarRedline")<br />Informační panel (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... Při vytváření vlastních infobars. | ... pro prvky uživatelského rozhraní, které nejsou podobné informačnímu panelu. |

**Informační panel: výchozí stav**

![Výchozí informační panel](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303 – 139_Infobar")<br />Výchozí informační panel

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `InfoBar.InfoBarBackground` |
| Popředí (text) | `InfoBar.InfoBar` |
| Ohraničení | `InfoBar.InfoBarBorder` |

**Tlačítko Zavřít informačního panelu ( &times; ): výchozí stav**

![Výchozí tlačítko pro zavření informačního panelu ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Výchozí tlačítko pro zavření informačního panelu ( &times; )

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `InfoBar.CloseButton` |
| Ohraničení | `InfoBar.CloseButtonBorder` |
| Zobrazovat | `InfoBar.CloseButtonGlyph` |

**Tlačítko Zavřít informačního panelu ( &times; ): stav přechodu myši**

![Tlačítko pro zavření informačního panelu &times; při najetí myší](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Tlačítko pro zavření informačního panelu &times; při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `InfoBar.CloseButtonHover` |
| Ohraničení | `InfoBar.CloseButtonHoverBorder` |
| Zobrazovat | `InfoBar.CloseButtonHoverGlyph` |

**Tlačítko Zavřít informačního panelu ( &times; ): stisknutý stav**

![Stisknuté tlačítko pro zavření informačního panelu ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Stisknuté tlačítko pro zavření informačního panelu ( &times; )

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `InfoBar.CloseButtonDown` |
| Ohraničení | `InfoBar.CloseButtonDownBorder` |
| Zobrazovat | `InfoBar.CloseButtonDownGlyph` |

**Tlačítko hypertextového odkazu informačního panelu: výchozí stav**

![Výchozí tlačítko hypertextového odkazu na informační panel](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Výchozí tlačítko hypertextového odkazu na informační panel

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `InfoBar.Hyperlink` |

**Tlačítko s hypertextovým odkazem na informační panel: stav přechodu**

![Tlačítko hypertextového odkazu na ukazateli při najetí myší](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Tlačítko hypertextového odkazu na ukazateli při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Infobar.HyperlinkMouseOver`<br />(S podtržením) |

**Tlačítko hypertextového odkazu informačního panelu: stisknutí stavu**

![Stisknuté tlačítko hypertextového odkazu na informační panel](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Stisknuté tlačítko hypertextového odkazu na informační panel

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Infobar.HyperlinkMouseDown`<br />(S podtržením) |

**Vložený hypertextový odkaz na informační panel (ve větě): výchozí stav**

![Výchozí vložené tlačítko hypertextového odkazu na informační panel](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Výchozí vložené tlačítko hypertextového odkazu na informační panel

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `InfoBar.Hyperlink` |

**Vložený hypertextový odkaz na informační panel (ve větě): stav přechodu myši**

![Vložené tlačítko hypertextový odkaz na informační panel při najetí myší](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Vložené tlačítko hypertextový odkaz na informační panel při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Infobar.HyperlinkMouseOver`<br />(S podtržením) |

**Vložený hypertextový odkaz na informační panel (ve větě): stisknutý stav**

![Stisknuté tlačítko vloženého hypertextového odkazu na informační panel](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Stisknuté tlačítko vloženého hypertextového odkazu na informační panel

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Infobar.HyperlinkMouseDown`<br />(S podtržením) |

**Tlačítko informačního panelu: výchozí stav**

![Výchozí tlačítko informačního panelu](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Výchozí tlačítko informačního panelu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `InfoBar.Button` |
| Popředí (text) | `InfoBar.Button` |
| Ohraničení | `InfoBar.ButtonBorder` |

**Tlačítko informačního panelu: stav přechodu myši**

![Tlačítko informačního panelu při najetí myší](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Tlačítko informačního panelu při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `InfoBar.ButtonMouseOver` |
| Popředí (text) | `InfoBar.ButtonMouseOver` |
| Ohraničení | `InfoBar.ButtonMouseOverBorder` |

**Tlačítko informačního panelu: stisknutí stavu**

![Tlačítko pro stisknutí informačního panelu](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Tlačítko pro stisknutí informačního panelu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `InfoBar.ButtonMouseDown` |
| Popředí (text) | `InfoBar.ButtonMouseDown` |
| Ohraničení | `InfoBar.ButtonMouseDownBorder` |

**Tlačítko informačního panelu: zakázaný stav**

![Zakázané tlačítko informačního panelu](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Zakázané tlačítko informačního panelu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `InfoBar.ButtonDisabled` |
| Popředí (text) | `InfoBar.ButtonDisabled` |
| Ohraničení | `InfoBar.ButtonDisabledBorder` |

**Tlačítko informačního panelu: prioritní stav**

![Prioritní tlačítko s informačním panelem](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Prioritní tlačítko s informačním panelem

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `InfoBar.ButtonFocus` |
| Popředí (text) | `InfoBar.ButtonFocus` |
| Ohraničení | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Posuvníky
Posuvníky jsou ve stylu pro prostředí sady Visual Studio a nemusí být tematicky. Můžete se ale rozhodnout, že chcete využít barvy používané v posuvníkech, aby se vaše uživatelské rozhraní vždy zobrazilo v souladu s touto částí prostředí sady Visual Studio.

![Posuvník (Redline)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303 – 140_ScrollbarRedline")<br />Posuvník (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... Při vytváření uživatelského rozhraní, které chcete porovnat s posuvníky sady Visual Studio. | ... pro cokoli, co nechcete vždy porovnávat s uživatelským rozhraním posuvníku. |

**Posuvník: výchozí stav**

![Výchozí posuvník](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303 – 141_Scrollbar")<br />Výchozí posuvník

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Posuvník | `Environment.ScrollBarBackground` |
| Popředí (palec) | `Environment.ScrollBarThumbBackground` |

**Posuvník: stav přechodu myši**

![Při najetí myší přejít na posuvník](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303 – 143_ScrollbarHover")<br />Při najetí myší přejít na posuvník

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Posuvník | `Environment.ScrollBarBackground` |
| Popředí (palec) | `Environment.ScrollBarThumbMouseOverBackground` |

*Posuvník: stisknutí stavu**

![Stisknuté procházení posuvníku](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303 – 145_ScrollbarPressed")<br />Stisknuté procházení posuvníku

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Posuvník | `Environment.ScrollBarBackground` |
| Popředí (palec) | `Environment.ScrollBarThumbPressedBackground` |

**Šipka posuvníku: výchozí stav**

![Výchozí šipka posuvníku](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303 – 142_ScrollbarArrow")<br />Výchozí šipka posuvníku

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ScrollBarArrowBackground`<br />(Nastaveno na stejnou barvu jako posuvník) |
| Popředí (glyf) | `Environment.ScrollBarArrowGlyph` |

**Šipka posuvníku: stav přechodu myši**

![Šipka posuvníku při najetí myší](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303 – 144_ScrollbarArrowHover")<br />Šipka posuvníku při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ScrollBarArrowMouseOverBackground`<br />(Nastaveno na stejnou barvu jako posuvník) |
| Popředí (glyf) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Šipka posuvníku: stisknutí stavu**

![Stisknutá šipka posuvníku](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303 – 146_ScrollbarArrowPressed")<br />Stisknutá šipka posuvníku

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ScrollBarArrowPressedBackground`<br />(Nastaveno na stejnou barvu jako posuvník) |
| Popředí (glyf) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Vyhledávací pole
Kdykoli je to možné, použijte běžný ovládací prvek vyhledávání poskytovaný prostředím Visual Studio. Barvy vyhledávacího pole se nacházejí v kategorii "SearchControl" v souboru **ShellColors. pkgdef** , který obsahuje názvy tokenů pro vstupní pole, tlačítko akce, tlačítko rozevíracího seznamu a rozevírací nabídku.

Vyhledávací pole může být jedním z několika stavů, z nichž některé se vzájemně vylučují:

- "Prioritní" nebo "bez fokusu" odkazuje na to, zda je kurzor v textovém poli.

- Možnost "aktivní" nebo "neaktivní" odkazuje na to, zda uživatel zadá vyhledávací dotaz do textového pole.

- "Najetí myší" znamená, že uživatel přejede myší na vyhledávací pole (Tento stav přepisuje všechny ostatní stavy).

- "Disabled" znamená, že funkce vyhledávání je pro aktuální kontext vypnutá.

![Vyhledávací pole (Redline)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303 – 110_SearchBoxRedline")<br />Vyhledávací pole (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... Při navrhování vlastního vyhledávacího pole. | ... pro cokoli, co není vyhledávací pole. |
| | ... cokoli, co nechcete vždy shodovat s uživatelským rozhraním vyhledávacího pole. |

**Vstupní pole s fokusem vyhledávání**

![Vstupní pole s fokusem vyhledávání](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303 – 111_SearchInputFieldFocused")<br />Vstupní pole s fokusem vyhledávání

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.FocusedBackground` |
| Popředí (text) | `SearchControl.FocusedBackground` |
| Ohraničení | `SearchControl.FocusedBorder` |
| Oddělovač | `SearchControl.FocusedDropDownSeparator` |

**Nevybrané vstupní pole aktivního hledání**

![Hledat vstupní pole nevybrané](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303 – 114_SearchInputFieldUnfocused")<br />Nevybrané vstupní pole aktivního hledání

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.SearchActiveBackground` |
| Popředí (text) | `SearchControl.SearchActiveBackground` |
| Ohraničení | `SearchControl.UnfocusedBorder` |
| Oddělovač | `SearchControl.DropDownSeparator` |

**Nevybrané vstupní pole pro neaktivní hledání**

![Nevybrané vstupní pole pro neaktivní hledání](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Nevybrané vstupní pole pro neaktivní hledání

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.Unfocused` |
| Popředí (text) | `SearchControl.Unfocused` |
| Ohraničení | `SearchControl.UnfocusedBorder` |
| Oddělovač | `SearchControl.DropDownSeparator` |

**Zvýrazněné vstupní pole hledání (jenom text)**

![Zvýrazněné vstupní pole hledání](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303 – 120_SearchInputFieldHighlight")<br />Zvýrazněné vstupní pole hledání

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.Selection` |
| Popředí (text) | `SearchControl.FocusedBackground` |
| Ohraničení | Žádné |
| Oddělovač | `SearchControl.FocusedDropDownSeparator` |

**Zakázané vstupní pole hledání**

![Zakázané vstupní pole hledání](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303 – 121_SearchInputFieldDisabled")<br />Zakázané vstupní pole hledání

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.Disabled` |
| Popředí (text) | `SearchControl.Disabled` |
| Ohraničení | `SearchControl.DisabledBorder` |
| Oddělovač | `SearchControl.DropDownSeparator` |

**Tlačítko akce cíleného vyhledávání**

![Fokus – tlačítko akce hledání](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303 – 112_SearchActionButtonFocused")<br />Tlačítko akce cíleného vyhledávání

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (piktogram pro hledání) | `SearchControl.SearchGlyph` |
| Popředí (zastavit glyf) | `SearchControl.StopGlyph` |
| Popředí (Vymazat glyf) | `SearchControl.ClearGlyph` |
| Ohraničení | – |

**Tlačítko akce hledání na nevybrané**

![Tlačítko akce hledání na nevybrané](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303 – 115_SearchActionButtonUnfocused")<br />Tlačítko akce hledání na nevybrané

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | – |
| Popředí (piktogram pro hledání) | `SearchControl.SearchGlyph` |
| Popředí (zastavit glyf) | `SearchControl.StopGlyph` |
| Popředí (Vymazat glyf) | `SearchControl.ClearGlyph` |
| Ohraničení | – |

**Stisknutí tlačítka akce hledání**

![Stisknutí tlačítka akce hledání](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Stisknutí tlačítka akce hledání

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.ActionButtonMouseDown` |
| Popředí (glyf) | `SearchControl.ActionButtonMouseDownGlyph` |
| Ohraničení | `SearchControl.ActionButtonMouseDownBorder` |

**Zakázané tlačítko akce hledání**

![Tlačítko akce hledání je zakázané.](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303 – 122_SearchActionButtonDisabled")<br />Zakázané tlačítko akce hledání

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (glyf) | `SearchControl.ActionButtonDisabledGlyph` |
| Ohraničení | Žádné |

**Rozevírací tlačítko hledání s fokusem**

![Rozevírací tlačítko hledání s fokusem](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303 – 113_SearchDropdownButtonFocused")<br />Rozevírací tlačítko hledání s fokusem

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.FocusedDropDownButton` |
| Popředí (glyf) | `SearchControl.FocusedDropDownButtonGlyph` |
| Ohraničení | `SearchControl.FocusedDropDownButtonBorder` |

**Tlačítko rozevíracího seznamu pro výběr vyhledávání**

![Tlačítko rozevíracího seznamu pro výběr vyhledávání](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303 – 116_SearchDropdownButtonUnfocused")<br />Tlačítko rozevíracího seznamu pro výběr vyhledávání

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.UnfocusedDropDownButton` |
| Popředí (glyf) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Ohraničení | `SearchControl.UnfocusedDropDownButtonBorder` |

**Tlačítko pro kliknutí na tlačítko hledání**

![Tlačítko pro kliknutí na tlačítko hledání](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Tlačítko pro kliknutí na tlačítko hledání

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.MouseDownDropDownButton` |
| Popředí (glyf) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Ohraničení | `SearchControl.MouseDownDropDownButtonBorder` |

**Tlačítko rozevíracího seznamu zakázaného hledání**

![Tlačítko rozevíracího seznamu zakázaného hledání](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303 – 123_SearchDropdownButtonDisabled")<br />Tlačítko rozevíracího seznamu zakázaného hledání

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (glyf) | `SearchControl.DisabledDownButtonGlyph` |
| Ohraničení | Žádné |

#### <a name="search-drop-down-lists"></a>Hledání rozevíracích seznamů
Rozevírací nabídka vyhledávacího pole má potenciál v aplikaci Visual Studio mírně složitější než jiné rozevírací nabídky. Oddíly "navrhované hledání" a "možnosti hledání" se můžou v nabídce objevit samostatně nebo společně a každá z nich se bude barevně zobrazovat. Řádek také oddělí tyto dvě části, když se zobrazí společně a ohraničení celé rozevírací nabídky.

![Rozevírací seznam hledání (Redline)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303 – 124_SearchDropdownRedline")<br />Rozevírací seznam hledání (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... Když vytváříte vlastní rozevírací seznam hledání. | ... pro rozevírací seznamy, které se zobrazují v jiných kontextech. |
| ... správné názvy tokenů pro správné komponenty seznamu. | ... v jakékoliv kombinaci pozadí/popředí kromě zadaného. |

**Hledat v rozevíracím seznamu elementy**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Ohraničení | `SearchControl.PopupBorder` |
| Oddělovač | `SearchControl.PopupSectionHeaderSeparator` |
| Vytváření | `Environment.DropShadowBackground` |

**Navrhovaná hledání: výchozí stav**

![Výchozí navrhovaná hledání](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303 – 125_SearchSuggested")<br />Výchozí navrhovaná hledání

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `SearchControl.PopupItemText` |

**Navrhovaná hledání: stav přechodu myši**

![Navrhované vyhledávání při najetí myší](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303 – 128_SearchSuggestedHover")<br />Navrhované vyhledávání při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `SearchControl.PopupMouseOverItemText` |
| Ohraničení | `SearchControl.PopupControlMouseOverBorder` |

**Možnosti hledání: výchozí stav**

![Zaškrtávací políčko hledání](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303 – 126_SearchCheckbox")<br />Výchozí možnosti hledání (zaškrtávací políčko)

![Možnosti hledání](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303 – 127_SearchOptions")<br />Výchozí možnosti hledání (odkaz)

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text zaškrtávacího políčka) | `SearchControl.PopupCheckboxText` |
| Popředí (text odkazu) | `SearchControl.PopupButtonText` |
| Pozadí záhlaví | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text záhlaví) | `SearchControl.PopupSectionHeaderText` |

**Možnosti hledání: stav přechodu myši**

![Možnosti hledání (zaškrtávací políčko) při najetí myší](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303 – 129_SearchCheckboxHover")<br />Možnosti hledání (zaškrtávací políčko) při najetí myší

![Možnosti vyhledávání (odkaz) při najetí myší](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303 – 130_SearchOptionsHover")<br />Možnosti vyhledávání (odkaz) při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text zaškrtávacího políčka) | `SearchControl.PopupCheckboxMouseDownText` |
| Popředí (text odkazu) | `SearchControl.PopupButtonMouseDownText` |
| Ohraničení | `SearchControl.PopupControlMouseOverBorder` |

**Možnosti hledání: stisknutí stavu**

![Stisknuté možnosti hledání (zaškrtávací políčko)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303 – 131_SearchSuggestedPressed")<br />Stisknuté možnosti hledání (zaškrtávací políčko)

![Stisknuté možnosti hledání (odkaz)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303 – 132_SearchOptionsPressed")<br />Stisknuté možnosti hledání (odkaz)

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí zaškrtávacího políčka | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text zaškrtávacího políčka) | `SearchControl.PopupCheckboxMouseDownText` |
| Pozadí odkazu | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text odkazu) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a> Stromová zobrazení
Několik oken nástrojů, včetně Průzkumník řešení, Průzkumník serveru a Zobrazení tříd, implementuje hierarchické organizační schéma, jejichž barvy jsou ovládány pomocí názvů barev v `TreeView` kategorii. Všechny položky ve stromovém zobrazení mají barvy pozadí a textu. Položky, které mají vnořené podřízené prvky, mají také glyfy, které označují, zda je položka rozbalená nebo sbalená.

![Stromové zobrazení (Redline)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303 – 147_TreeViewRedline")<br />Stromové zobrazení (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... kdekoli potřebujete implementovat hierarchické zobrazení organizace. | ... pro cokoli, co se neshoduje se stromovým zobrazením. |
| | ... v jakékoliv kombinaci pozadí/popředí kromě zadaného. |

**Položka stromového zobrazení: výchozí stav**

![Výchozí položka zobrazení stromu](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303 – 148_TreeView")<br />Výchozí položka zobrazení stromu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `TreeView.Background` |
| Popředí (text) | `TreeView.Background` |
| Popředí (glyf) | `TreeView.Glyph` |
| Ohraničení | Žádné |

**Položka stromového zobrazení: stav přechodu myši**

![Položka zobrazení stromu při najetí myší](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303 – 149_TreeViewHover")<br />Položka zobrazení stromu při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `TreeView.Background` |
| Popředí (text) | `TreeView.Background` |
| Popředí (glyf) | `TreeView.GlyphMouseOver` |
| Ohraničení | Žádné |

**Položka stromového zobrazení: přetažení přes stav**

![Položka zobrazení stromu při přetažení](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303 – 150_TreeViewDragOver")<br />Položka zobrazení stromu při přetažení

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `TreeView.DragOverItem` |
| Popředí (text) | `TreeView.DragOverItem` |
| Popředí (glyf) | `TreeView.DragOverItemGlyph` |
| Ohraničení | Žádné |

**Položka stromového zobrazení: vybraná, prioritní stav**

![Vybraná a prioritní položka zobrazení stromu](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303 – 151_TreeViewFocused")<br />Vybraná a prioritní položka zobrazení stromu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemActive` |
| Popředí (text) | `TreeView.SelectedItemActive` |
| Popředí (glyf) | `TreeView.SelectedItemActiveGlyph` |
| Ohraničení | `TreeView.FocusVisualBorder` |

**Položka stromového zobrazení: vybráno, Nevybráno, stav**

![Vybraná a nevýběrová položka zobrazení stromu](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303 – 152_TreeViewUnfocused")<br />Vybraná a nevýběrová položka zobrazení stromu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemInactive` |
| Popředí (text) | `TreeView.SelectedItemInactive` |
| Popředí (glyf) | `TreeView.SelectedItemInactiveGlyph` |
| Ohraničení | Žádné |

**Položka stromového zobrazení: najetí myší, vybráno a zaměření na stav**

![Vybraná a prioritní položka zobrazení stromu při najetí myší](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303 – 153_TreeViewFocusedHover")<br />Vybraná a prioritní položka zobrazení stromu při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemActive` |
| Popředí (text) | `TreeView.SelectedItemActive` |
| Popředí (glyf) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Ohraničení | `TreeView.FocusVisualBorder` |

**Položka stromového zobrazení: najeďte na vybraný a nevybraný stav**

![Vybraná a nevýběrová položka zobrazení stromu při najetí myší](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303 – 154_TreeViewUnfocusedHover")<br />Vybraná a nevýběrová položka zobrazení stromu při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemInactive` |
| Popředí (text) | `TreeView.SelectedItemInactive` |
| Popředí (glyf) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Ohraničení | Žádné |

## <a name="shell-appearance"></a>Vzhled prostředí

### <a name="background"></a>Pozadí
Pozadí prostředí se skládá ze dvou vrstev. Spodní vrstva je plná barva, která pokrývá celé rozhraní IDE. Horní vrstva se přizpůsobí pod police příkazu a mezi oknem nástrojů automaticky skrývá kanály pro levý a pravý okraj IDE. Horní a Dolní vrstva pozadí je nastavena na stejnou barvu v motivech světlé a tmavé.

![Pozadí prostředí sady Visual Studio (Redline)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303 – 187_ShellBackgroundRedline")<br />Pozadí prostředí sady Visual Studio (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... pro místa, kde chcete vyhledat pozadí prostředí sady Visual Studio. | ... jako výplň pro místa, která nejsou povrchy na pozadí. |
| | ... jako pozadí pro umístění prvků popředí. |

**Vzhled prostředí dolní vrstvy**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.EnvironmentBackground` |

**Vzhled prostředí horní vrstvy**

> Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Police příkazu
Pro pozadí příkazu se používají dvě sady názvů tokenů: jedna sada, pro kterou je panel nabídek umístěný, a druhý pro místo, kde se panely příkazů nacházejí. Jednotlivé skupiny panelů příkazů mají vlastní hodnoty barvy pozadí, které jsou podrobněji popsány v části "panel příkazů". Řádek nabídek a text panelu příkazů jsou popsány v oddílech nabídky a panelu příkazů v uvedeném pořadí.

![Redline (Visual Studio Command Policy)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303 – 188_CommandShelfRedline")<br />Redline (Visual Studio Command Policy)

| Použít... | Nepoužívat... |
| --- | --- |
| ... pro oblasti, kde umístíte nabídky nebo panely nástrojů. | ... pro oblasti, které nejsou podobné poli se zadáním příkazu. |
|... se správnou kombinací názvu tokenu Background/popředí. | |

**Panel nabídek pro police příkazu**

> Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Panel příkazů pro police příkazu**

> Přechodová zastávka se nastaví na stejnou hodnotu barvy v Visual Studio 2013 světlé a tmavé motivy.

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Návrhář manifestu
Manifest Designer byl navržen jako způsob, jak zjednodušit úpravu souboru manifestu v projektech se systémem Windows 8 a Windows Phone 8. I když není k dispozici žádné sdílené rozhraní pro použití, může být vhodné, abyste se shodovali s rozložením návrhu a barvami karet pro orientaci a navigaci a celkovou strukturou. Další informace o podrobnostech rozložení naleznete v tématu [layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Manifest Designer (Redline)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303 – 175_ManifestDesignerRedline")<br />Manifest Designer (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... pro návrháře, kteří jsou podobný návrháři manifestu. | ... Pokud máte více než šest karet. |
| ... místo použití běžných ovládacích prvků na kartě v horní části editoru v dokumentaci dokumentu. | ... pro jakékoli uživatelské rozhraní, které není strukturované jako Návrhář manifestu. |

**Vybraná karta návrháře manifestu: výchozí stav**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `ManifestDesigner.TabActive` |
| Ohraničení | Žádné |

**Podokno s vybraným popisem v Návrháři manifestu: výchozí stav**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `ManifestDesigner.DescriptionPane` |

**Stránka vybraného obsahu návrháře manifestu: výchozí stav**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `ManifestDesigner.Background` |
| Pomocný text dialogového okna | `ManifestDesigner.WatermarkText`<br />(Tento název tokenu se neshoduje s jeho funkcí.) |

**Karta návrháře manifestu: nevybraný stav**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `ManifestDesigner.Tab.Inactive` |

**Karta Návrhář manifestu: stav přechodu myši**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Struktury příkazů

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Nabídek
Nabídky se můžou vyskytovat na několika místech v sadě Visual Studio: hlavní panel nabídek, vložený v oknech dokument nebo nástroj, nebo klikněte pravým tlačítkem na různá místa v rámci IDE. Implementace nabídek přidružených k ostatním prvkům uživatelského rozhraní jsou popsány v části příslušného prvku. Vždy byste měli použít standardní implementaci nabídky poskytovanou prostředím Visual Studio. Nicméně v některých vzácných instancích byste neměli mít přístup ke standardním nabídkám sady Visual Studio. V těchto situacích použijte následující názvy tokenů, abyste zajistili, že vaše uživatelské rozhraní je konzistentní s jinými nabídkami v aplikaci Visual Studio.

![Nabídka sady Visual Studio (Redline)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303 – 000_MenuRedline")<br />Nabídka sady Visual Studio (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... Když potřebujete vytvořit vlastní nabídku.| ... samostatná barva pozadí. Vždy používat kombinaci pozadí/popředí podle zadání. |
| ... Pokud máte novou součást uživatelského rozhraní, která se má shodovat s nabídkami sady Visual Studio.| |

#### <a name="menu-titles"></a>Názvy nabídek
Názvy nabídek se skládají z pozadí, ohraničení a textu nadpisu a také z volitelné glyfy, většinou když se nabídka najde na panelu příkazů.

![Název nabídky (Redline)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303 – 001_MenuTitleRedline")<br />Název nabídky (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... vždy, když vytváříte vlastní název nabídky. | ... pro cokoli, co nechcete vždy shodovat s názvem nabídky. |
| | ... v jakékoliv kombinaci pozadí/popředí kromě zadaného. |

**Název nabídky: výchozí stav**

![Výchozí název nabídky](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303 – 002_MenuTitleDefault")<br />Výchozí název nabídky

![Výchozí název nabídky s glyfem](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303 – 003_MenuTitleWithGlyphDefault")<br />Výchozí název nabídky s glyfem

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Popředí (glyf) | `Environment.CommandBarMenuGlyph` |
| Ohraničení | Žádné |

**Název nabídky: stav přechodu myši**

![Název nabídky při najetí myší](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303 – 004_MenuTitleHover")<br />Název nabídky při najetí myší

![Název nabídky s glyfem při najetí myší](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303 – 005_MenuTitleWithGlyphHover")<br />Název nabídky s glyfem při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.CommandBarTextHover` |
| Popředí (glyf) | `Environment.CommandBarMenuMouseOverGlyph` |
| Ohraničení | `Environment.CommandBarBorder` |

**Název nabídky: stisknutí stavu**

![Název stisknuté nabídky](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303 – 006_MenuTitlePressed")<br />Název stisknuté nabídky

![Název stisknuté nabídky s glyfem](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303 – 007_MenuTitleWithGlyphPressed")<br />Název stisknuté nabídky s glyfem

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Popředí (glyf) | `Environment.CommandBarMenuMouseDownGlyph` |
| Ohraničení | `Environment.CommandBarMenuBorder`<br />(Pouze levé, horní a pravé strany.) |

**Název nabídky: zakázaný stav**

![Název zakázané nabídky s glyfem](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303 – 008_MenuTitleWithGlyphDisabled")<br />Název zakázané nabídky s glyfem

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (text) | `Environment.CommandBarTextInactive` |
| Popředí (glyf) | `Environment.CommandBarTextInactive` |
| Ohraničení | Žádné |

#### <a name="menu-items"></a>Položky nabídky
Jednotlivá položka nabídky se skládá z textu nabídky a volitelné ikony, zaškrtávacího políčka nebo piktogramu podnabídky. Změní barvu pozadí a textu při najetí myší. Tento token barvy je dvojice pozadí/popředí.

![Položky nabídky Redline](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 – 009_MenuItemRedline")

| Použít... | Nepoužívat... |
|---|---|
| ... pro libovolný rozevírací seznam, který se spouští z panelu nabídek nebo panelu příkazů. | ... pro libovolný rozevírací seznam v jiném kontextu. |
| | ... v jakékoliv kombinaci pozadí/popředí kromě zadaného. |

**Položky nabídky: výchozí stav**

![Výchozí položky nabídky](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303 – 010_MenuDefault")<br />Výchozí položky nabídky

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Popředí (piktogram podnabídky) | `Environment.CommandBarMenuSubmenuGlyph` |
| Ohraničení | `Environment.CommandBarMenuBorder` |
| Pozadí kanálu ikon | `Environment.CommandBarMenuIconBackground` |
| Oddělovač | `Environment.CommandBarMenuSeparator` |
| Vytváření | `Environment.DropShadowBackground` |

**Položky nabídky: zaškrtnuté a vybrané stavy**

![Zaškrtnutá nabídka](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303 – 011_MenuChecked")<br />Položka kontrolované nabídky

![Vybraná nabídka](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303 – 012_MenuSelected")<br />Vybraná položka nabídky

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Značka zaškrtnutí | `Environment.CommandBarCheckBox` |
| Pozadí zaškrtnutí | `Environment.CommandBarSelectedIcon` |
| Pozadí ikony | `Environment.CommandBarSelected` |
| Ohraničení ikony | `Environment.CommandBarSelectedBorder` |

**Položky nabídky: stav přechodu myši**

![Najeďte do nabídky](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303 – 013_MenuHover")<br />Položka nabídky při najetí myší

![Kontrola najetí myší v nabídce](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303 – 014_MenuHoverChecked")<br />Zaškrtnutá položka nabídky při najetí myší

![Výběr myši v nabídce](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303 – 015_MenuHoverSelected")<br />Vybraná položka nabídky při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarMenuItemMouseOver` |
| Popředí (text) | `Environment.CommandBarMenuItemMouseOverText` |
| Popředí (piktogram podnabídky) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Značka zaškrtnutí | `Environment.CommandBarCheckBoxMouseOver` |
| Pozadí zaškrtnutí | `Environment.CommandBarHoverOverSelectedIcon` |
| Pozadí ikony | `Environment.CommandBarHoverOverSelected` |
| Ohraničení ikony | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Položky nabídky: zakázaný stav**

![Nabídka zakázaná](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303 – 016_MenuDisabled")<br />Zakázaná položka nabídky

![Zaškrtnutá nabídka zakázaná](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303 – 017_MenuDisabledChecked")<br />Zakázaná položka nabídky s označením zaškrtnutí

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Popředí (text) | `Environment.CommandBarTextInactive` |
| Popředí (piktogram podnabídky) | `Environment.CommandBarMenuSubmenuGlyph` |
| Značka zaškrtnutí | `Environment.CommandBarCheckBoxDisabled` |
| Pozadí zaškrtnutí | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Panely příkazů
Panel příkazů se může zobrazit na více místech v rámci integrovaného vývojového prostředí (IDE) sady Visual Studio, zejména v poli pro pole a v oknech nástrojů nebo dokumentu.

Obecně platí, že vždy použijte standardní implementaci panelu příkazů poskytované prostředím Visual Studio. Použití standardního mechanismu zajistí, že se všechny podrobnosti vizuálů zobrazí správně a že interaktivní prvky se budou chovat konzistentně s dalšími ovládacími prvky panelu příkazů sady Visual Studio. Pokud je ale potřeba vytvořit vlastní panel příkazů, ujistěte se, že je správně nakonfigurujete pomocí následujících názvů tokenů.

![Redline panelu příkazů](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303 – 018_CommandBarRedline")<br />Panel příkazů (Redline)

![Redline tlačítka přetečení](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303 – 019_OverflowButtonRedline")<br />Tlačítko přetečení (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... v místech, kde potřebujete vložený panel příkazů, ale nemůžete použít standardní implementaci panelu příkazů sady Visual Studio. | ... pro prvky uživatelského rozhraní, které nejsou podobné panelu příkazů. |
| | ... pro součásti panelu příkazů kromě těch, pro které jsou zadány názvy tokenů. |

#### <a name="command-bar-groups"></a>Skupiny panelů příkazů
Skupina panelů příkazů se skládá ze související sady ovládacích prvků panelu příkazů a může obsahovat libovolný počet tlačítek, rozdělená tlačítka, rozevírací nabídky, pole se seznamem nebo nabídky. Barvy pro tyto ovládací prvky jsou regulovány pomocí oddělených názvů tokenů a jsou popsány individuálně jinde v této příručce. Oddělovací čára se používá k rozdělení skupiny pruhů příkazů do souvisejících podskupin.

![Redline skupiny panelů příkazů](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303 – 020_CommandBarGroupRedline")<br />Skupina panelů příkazů (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... v místech, kde potřebujete vložený panel příkazů, ale nemůžete použít standardní implementaci panelu příkazů sady Visual Studio. | ... pro prvky uživatelského rozhraní, které nejsou podobné panelu příkazů. |
| | ... pro součásti panelu příkazů kromě těch, pro které jsou zadány názvy tokenů. |

**Skupina panelů příkazů: výchozí stav**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarGradientBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Ohraničení | `Environment.CommandBarToolBarBorder` |
| Přetáhněte popisovač | `Environment.CommandBarDragHandle` |
| Oddělovač | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Ikony příkazů
![Ikona příkazu Redline](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303 – 021_CommandIconRedline1")<br />Ikona příkazu (Redline)

![Ikona příkazu s textem Redline](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303 – 022_CommandIconRedline2")<br />Ikona příkazu s textem (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... pro všechna tlačítka, která budou umístěna na panelu příkazů. | ... pro ovládací prvky, které mají své vlastní názvy tokenů. |
| | ... v jakékoliv kombinaci pozadí/popředí kromě zadaného. |

**Ikona příkazu: výchozí stav**

![Výchozí ikona příkazu](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303 – 023_CommandIconDefault")<br />Výchozí ikona příkazu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Není k dispozici (dědí z pozadí panelu příkazů) |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Ohraničení | – |

**Ikona příkazu: výchozí stav, vybráno**

![Výchozí, vybraná ikona příkazu](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303 – 024_CommandIconDefaultSelected")<br />Výchozí, vybraná ikona příkazu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarSelected` |
| Popředí (text) | `Environment.CommandBarTextSelected` |
| Ohraničení | `Environment.CommandBarSelectedBorder` |

**Ikona příkazu: stavy najetí myší nebo fokus**

![Ikona příkazu při najetí myší nebo zaostření](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303 – 025_CommandIconHover")<br />Ikona příkazu při najetí myší nebo zaostření

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.CommandBarTextHover` |
| Ohraničení | `Environment.CommandBarBorder` |

**Ikona příkazu: stavy najetí myší nebo fokus, vybrané**

![Ikona vybraného příkazu při najetí myší nebo zaostření](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303 – 026_CommandIconHoverSelected")<br />Ikona vybraného příkazu při najetí myší nebo zaostření

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarHoverOverSelected` |
| Popředí (text) | `Environment.CommandBarTextHoverOverSelected` |
| Ohraničení | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Ikona příkazu: stisknutí stavu**

![Ikona stisknutého příkazu](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303 – 027_CommandIconPressed")<br />Ikona stisknutého příkazu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.CommandBarTextMouseDown` |
| Ohraničení | `Environment.CommandBarBorder` |

**Ikona příkazu: zakázaný stav**

![Ikona zakázaného příkazu](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303 – 028_CommandIconDisabled")<br />Ikona zakázaného příkazu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Není k dispozici (dědí z pozadí panelu příkazů) |
| Popředí (text) | `Environment.CommandBarTextInactive` |
| Ohraničení | – |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a> Pole se seznamem panelů příkazů

> [!IMPORTANT]
> Pole se seznamem jsou podobná rozevíracím seznamům, ale obsahují upravitelnou textovou oblast. Pokud vaše rozevírací seznam neobsahuje upravitelnou textovou oblast, použijte pro [rozevírací seznam panel příkazů](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)palety barev.

![Panel příkazů – pole se seznamem Redline](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303 – 029_ComboBoxRedline")<br />Pole se seznamem panelu příkazů (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... Při sestavování vlastních polí se seznamem. | ... cokoli, co nechcete, aby se vždy shodovalo s uživatelským rozhraním panelu příkazů. |
| ... Při vytváření ovládacího prvku panelu příkazů, který je podobný poli se seznamem. | ... Když máte přístup k poli se seznamem se stylem. |

**Vstupní pole pole se seznamem panelů příkazů: výchozí stav**

![Vstupní pole pole se seznamem panelu příkazů](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303 – 030_ComboBoxInputField")<br />Vstupní pole pole se seznamem panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ComboBoxBackground` |
| Popředí (text) | `Environment.ComboBoxText` |
| Ohraničení | `Environment.ComboBoxBorder` |
| Oddělovač | Bez oddělovače |

**Rozevírací tlačítko panelu příkazů: výchozí stav**

![Rozevírací tlačítko&#45;rozevíracího seznamu pole se seznamem](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303 – 031_ComboBoxDropdownButton")<br />Rozevírací tlačítko panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Není k dispozici (dědí z pozadí panelu příkazů) |
| Popředí (glyf) | `Environment.ComboBoxGlyph` |

**Rozevírací seznam panelu příkazů: výchozí stav**

![Rozevírací seznam panelu příkazů](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303 – 032_ComboBoxDropdownList")<br />Rozevírací seznam panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ComboBoxPopupBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.ComboBoxItemText` |
| Ohraničení | `Environment.ComboBoxPopupBorder` |

**Vstupní pole pole se seznamem panelu příkazů: stav přechodu myši**

![Vstupní pole pole se seznamem panelu příkazů při najetí myší](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303 – 033_ComboBoxInputFieldHover")<br />Vstupní pole pole se seznamem panelu příkazů při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.ComboBoxMouseOverText` |
| Ohraničení | `Environment.ComboBoxMouseOverBorder` |
| Oddělovač | `Environment.ComboBoxMouseOverSeparator` |

 **Rozevírací tlačítko panelu příkazů: stav najetí myší**

![Tlačítko rozevíracího seznamu na panelu příkazů při najetí myší](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303 – 034_ComboBoxDropdownButtonHover")<br />Tlačítko rozevíracího seznamu na panelu příkazů při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ComboBoxButtonMouseOverBackground` |
| Popředí (glyf) | `Environment.ComboBoxMouseOverGlyph` |

**Rozevírací seznam panelu příkazů: stav najetí myší**

 ![Rozevírací seznam panelu příkazů při najetí myší](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303 – 035_ComboBoxDropdownListHover")<br />Rozevírací seznam panelu příkazů při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Background (položka nabídky) | `Environment.ComboBoxItemMouseOverBackground` |
| Popředí (text) | `Environment.ComboBoxItemMouseOverText` |
| Border (položka nabídky) | `Environment.ComboBoxItemMouseOverBorder` |

 **Vstupní pole pole se seznamem panelu příkazů: prioritní stav**

![Pole se seznamem fokusu pro vstupní pole se seznamem panelů příkazů](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303 – 036_ComboBoxInputFieldFocused")<br />Pole se seznamem fokusu pro vstupní pole se seznamem panelů příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ComboBoxFocusedBackground` |
| Popředí (text) | `Environment.ComboBoxFocusedText` |
| Ohraničení | `Environment.ComboBoxFocusedBorder` |
| Oddělovač | `Environment.ComboBoxFocusedButtonSeparator` |

**Rozevírací tlačítko panelu příkazů: prioritní stav**

![Fokus – tlačítko rozevíracího seznamu na panelu příkazů](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303 – 037_ComboBoxDropdownButtonFocused")<br />Fokus – tlačítko rozevíracího seznamu na panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ComboBoxFocusedButtonBackground` |
| Popředí (glyf) | `Environment.ComboBoxFocusedGlyph` |

 **Vstupní pole pole se seznamem na panelu příkazů: stisknutý stav**

![Stisknuté vstupní pole pole se seznamem panelů příkazů](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303 – 038_ComboBoxInputFieldPressed")<br />Stisknuté vstupní pole pole se seznamem panelů příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ComboBoxMouseDownBackground` |
| Popředí (text) | `Environment.ComboBoxMouseDownText` |
| Ohraničení | `Environment.ComboBoxMouseDownBorder` |
| Oddělovač | `Environment.ComboBoxMouseDownSeparator` |

**Rozevírací tlačítko panelu příkazů: stisknutý stav**

![Stisknuté tlačítko rozevíracího seznamu na panelu příkazů](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303 – 039_ComboBoxDropdownButtonPressed")<br />Stisknuté tlačítko rozevíracího seznamu na panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ComboBoxButtonMouseDownBackground` |
| Popředí (glyf) | `Environment.ComboBoxMouseDownGlyph` |

**Vstupní pole pole se seznamem panelu příkazů: zakázaný stav**

![Zakázané vstupní pole pole se seznamem panelů příkazů](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303 – 041_ComboBoxInputFieldDisabled")<br />Zakázané vstupní pole pole se seznamem panelů příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ComboBoxDisabledBackground` |
| Popředí (text) | `Environment.ComboBoxDisabledText` |
| Ohraničení | `Environment.ComboBoxDisabledBorder` |
| Oddělovač | Bez oddělovače |

**Rozevírací tlačítko panelu příkazů: zakázaný stav**

![Tlačítko rozevíracího seznamu zakázaného panelu příkazů](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303 – 040_ComboBoxDropdownButtonDisabled")<br />Tlačítko rozevíracího seznamu zakázaného panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (glyf) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a> Rozevírací seznam panelu příkazů

> [!IMPORTANT]
> Rozevírací seznamy jsou podobné polím se seznamem, ale nemají upravovatelné textové oblasti. Pokud rozevírací seznam obsahuje upravitelnou textovou oblast, použijte pro pole [se seznamem panelu příkazů](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)paletové tokeny.

![Rozevírací seznam panelu příkazů (Redline)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303 – 042_DropdownRedline")<br />Rozevírací seznam panelu příkazů (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... Při vytváření vlastních ovládacích prvků rozevíracího seznamu. | ... pro cokoli, co není podobné rozevíracímu seznamu. |
| | ... pro pole se seznamem nebo rozdělená tlačítka. |

**Rozevírací pole pro výběr panelu příkazů: výchozí stav**

![Výchozí rozevírací pole pro výběr panelu příkazů](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303 – 043_DropdownSelectionField")<br />Výchozí rozevírací pole pro výběr panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.DropDownBackground` |
| Popředí (text) | `DropDownText` |
| Ohraničení | `DropDownBorder` |
| Oddělovač | Bez oddělovače |

**Rozevírací tlačítko panelu příkazů: výchozí stav**

![Výchozí tlačítko rozevíracího seznamu panelu příkazů](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303 – 044_DropdownButton")<br />Výchozí tlačítko rozevíracího seznamu panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (glyf) | `Environment.DropDownGlyph` |

**Rozevírací seznam panelu příkazů: výchozí stav**

![Výchozí rozevírací seznam panelu příkazů](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303 – 045_DropdownList")<br />Výchozí rozevírací seznam panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.DropDownPopupBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.ComboBoxItemText` |
| Ohraničení | `Environment.DropDownPopupBorder` |
| Vytváření | `Environment.DropShadowBackground` |

**Rozevírací pole pro výběr panelu příkazů: stav přechodu myši**

![Rozevírací pole pro výběr panelu příkazů při najetí myší](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303 – 046_DropdownSelectionFieldHover")<br />Rozevírací pole pro výběr panelu příkazů při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.DropDownMouseOverBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.DropDownMouseOverText` |
| Ohraničení | `Environment.DropDownMouseOverBorder` |
| Oddělovač | `Environment.DropDownButtonMouseOverSeparator` |

**Rozevírací tlačítko panelu příkazů: stav najetí myší**

![Tlačítko rozevíracího seznamu na panelu příkazů při najetí myší](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303 – 047_DropdownButtonHover")<br />Tlačítko rozevíracího seznamu na panelu příkazů při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.DropDownButtonMouseOverBackground` |
| Popředí (glyf) | `Environment.DropDownMouseOverGlyph` |

**Rozevírací seznam panelu příkazů: stav najetí myší**

![Rozevírací seznam panelu příkazů při najetí myší](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303 – 048_DropdownListHover")<br />Rozevírací seznam panelu příkazů při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Background (položka nabídky) | `Environment.ComboBoxItemMouseOverBackground` |
| Popředí (text) | `Environment.ComboBoxItemMouseOverText` |
| Border (položka nabídky) | `Environment.ComboBoxItemMouseOverBorder` |

 **Rozevírací pole pro výběr panelu příkazů: stisknutí stavu**

![Stisknutí pole výběru&#45;dolů](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303 – 049_DropdownSelectionFieldPressed")<br />Stisknuté pole výběru rozevíracího panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.DropDownMouseDownBackground` |
| Popředí (text) | `Environment.DropDownMouseDownText` |
| Ohraničení | `Environment.DropDownMouseDownBorder` |
| Oddělovač | `Environment.DropDownButtonMouseDownSeparator` |

**Rozevírací tlačítko panelu příkazů: stisknutý stav**

![Stisknuté tlačítko rozevíracího seznamu na panelu příkazů](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303 – 050_DropdownButtonPressed")<br />Stisknuté tlačítko rozevíracího seznamu na panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.DropDownButtonMouseDownBackground` |
| Popředí (glyf) | `Environment.DropDownMouseDownGlyph` |

**Rozevírací pole pro výběr panelu příkazů: zakázaný stav**

![Zakázané pole výběru v rozevíracím seznamu panelu příkazů](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303 – 051_DropdownSelectionFieldDisabled")<br />Zakázané pole výběru v rozevíracím seznamu panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.DropDownDisabledBackground` |
| Popředí (text) | `Environment.DropDownDisabledText` |
| Ohraničení | `Environment.DropDownDisabledBorder` |
| Oddělovač | Bez oddělovače |

**Rozevírací tlačítko panelu příkazů: zakázaný stav**

![Tlačítko rozevíracího seznamu zakázaného panelu příkazů](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303 – 052_DropdownButtonDisabled")<br />Tlačítko rozevíracího seznamu zakázaného panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | – |
| Popředí (glyf) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Tlačítka pro rozdělení panelu příkazů
Rozdělená tlačítka sdílejí mnoho názvů tokenů s jinými ovládacími prvky panelu příkazů, jako jsou tlačítka, nabídky a text panelu příkazů. Pro pohodlí se tady opakují všechny nezbytné názvy tokenů tlačítek a akcí. Rozevírací seznamy rozdělení na tlačítko jsou implementace [nabídek panelu příkazů](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Redline tlačítko rozdělení](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303 – 053_SplitButtonRedline")<br />Tlačítko rozdělení panelu příkazů (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... Když vytváříte vlastní tlačítko rozdělení. | ... pro jiné druhy tlačítek. |
| | ... v jakékoliv kombinaci pozadí/popředí kromě zadaného. |

**Tlačítko rozdělení panelu příkazů: výchozí stav**

![Výchozí panel příkazů – tlačítko rozdělení](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303 – 054_SplitButton")<br />Výchozí panel příkazů – tlačítko rozdělení

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Popředí (glyf) | `Environment.CommandBarSplitButtonGlyph` |
| Ohraničení | – |
| Oddělovač | – |

**Panel příkazů – tlačítko rozdělení: stav přechodu myši**

![Panel příkazů – tlačítko rozdělení při najetí myší](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303 – 055_SplitButtonHover")<br />Panel příkazů – tlačítko rozdělení při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.CommandBarTextHover` |
| Popředí (glyf) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Ohraničení | `Environment.CommandBarBorder` |
| Oddělovač | `Environment.CommandBarSplitButtonSeparator` |

**Tlačítko rozdělení panelu příkazů: stisknutý stav**

![Stisknuté tlačítko rozdělení panelu příkazů](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303 – 056_SplitButtonPressed")<br />Stisknuté tlačítko rozdělení panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.CommandBarTextMouseDown` |
| Popředí (glyf) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Ohraničení | `Environment.CommandBarBorder` |
| Oddělovač | – |

**Tlačítko rozdělení panelu příkazů: zakázaný stav**

![Zakázané tlačítko rozdělení panelu příkazů](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303 – 057_SplitButtonDisabled")<br />Zakázané tlačítko rozdělení panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | – |
| Popředí (text) | `Environment.ComboBoxItemTextInactive` |
| Popředí (glyf) | `Environment.CommandBarTextInactive` |
| Ohraničení | – |
| Oddělovač | – |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Panel příkazů – tlačítka Další možnosti a přetečení
Tlačítko Další možnosti se používá, když je skupina panelů příkazů přizpůsobitelná buď přidáním nebo odebráním souvisejících tlačítek panelu příkazů. Tlačítko přetečení se zobrazí, když je panel příkazů oříznutý z důvodu nedostatku horizontálního prostoru a kliknutím na položku zobrazí nabídku obsahující tlačítka panelu příkazů, která nelze zobrazit. Barvy těchto dvou tlačítek jsou ovládány stejnou sadou názvů tokenů.

![Panel příkazů – tlačítko Další možnosti (Redline)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303 – 058_MoreOptionsRedline")<br />Panel příkazů – tlačítko Další možnosti (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... pro vlastní tlačítka Další možnosti nebo přetečení. | ... pro tlačítka, která nemají podobné funkce jako tlačítko Další možnosti nebo přetečení. |

**Panel příkazů ' Další možnosti ' a ' přetečení ' tlačítka: výchozí stav**

![Výchozí panel příkazů – tlačítko Další možnosti](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303 – 059_MoreOptions")<br />Výchozí panel příkazů – tlačítko Další možnosti

![Výchozí tlačítko panelu příkazů přetečení](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303 – 060_Overflow")<br />Výchozí tlačítko panelu příkazů přetečení

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarOptionsBackground` |
| Popředí (glyf) | `Environment.CommandBarOptionsGlyph` |

**Panel příkazů – tlačítka Další možnosti a přetečení: stav přechodu myši**

![Panel příkazů: tlačítko Další možnosti při najetí myší](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303 – 061_MoreOptionsHover")<br />Panel příkazů: tlačítko Další možnosti při najetí myší

![Tlačítko přetečení panelu příkazů při najetí myší](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303 – 062_OverflowOptions")<br />Tlačítko přetečení panelu příkazů při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (glyf) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Panel příkazů tlačítko Další možnosti a přetečení: stisknutí stavu**

![Tlačítko Další možnosti stisknutého panelu příkazů](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303 – 063_MoreOptionsPressed")<br />Tlačítko Další možnosti stisknutého panelu příkazů

![Stisknuté přetečení](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303 – 064_OverflowPressed")<br />Stisknuté tlačítko přetečení panelu příkazů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (glyf) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Okna dokumentů
Není nutné replikovat okna dokumentů, protože jsou k dispozici v prostředí sady Visual Studio. Můžete se ale rozhodnout, že chcete využít barvy používané v oknech dokumentů, aby se vaše uživatelské rozhraní vždy zobrazilo v souladu s touto částí prostředí sady Visual Studio.

Při použití barevných tokenů okna dokumentu buďte opatrní, abyste je mohli používat pouze pro podobné prvky a vždy ve dvojicích. Pokud to neuděláte, můžou se v uživatelském rozhraní zobrazit neočekávané výsledky.

### <a name="document-window-frames"></a>Rámečky oken dokumentů
Okna dokumentu mohou být buď ukotvena v integrovaném vývojovém prostředí (IDE), nebo plovoucí jako samostatné okno. Když je okno dokumentu plovoucí mimo rozhraní IDE, stále je umístěno v dokumentaci dokumentu a má barvy pozadí, ohraničení, textu a tabulátoru, které jsou stejné jako v případě, že je součástí rozhraní IDE. Dokument však je umístěn uvnitř rámečku, který má vlastní pozadí, ohraničení a barvy textu. Když jsou okna nástrojů ukotvena v dokumentaci dokumentu, dědí chování a barvu jejich karet z názvů tokenů oken dokumentů.

![Okno ukotveného dokumentu (Redline)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303 – 065_DockedDocumentWindowRedline")<br />Okno ukotveného dokumentu (Redline)

![Plovoucí okno dokumentu (Redline)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303 – 066_FloatingDocumentWindowRedline")<br />Plovoucí okno dokumentu (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... kdekoli vytváříte uživatelské rozhraní, které chcete porovnat s oknem dokumentu. | ...  pro jakékoli uživatelské rozhraní, které nechcete automaticky změnit, pokud má prostředí aktualizaci motivu. |

**Okno ukotveného nebo plovoucího dokumentu: výchozí stav**

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | Závisí na typu dokumentu |
| Popředí (text) | Závisí na typu dokumentu |
| Ohraničení | `Environment.ToolWindowBorder` |

**Zaměření, plovoucí rámeček okna dokumentu: výchozí stav**

![Výchozí zaměření, plovoucí rámec okna dokumentu](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303 – 067_FrameFocused")<br />Výchozí zaměření, plovoucí rámec okna dokumentu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowFloatingFrame` |
| Popředí (text) | `Environment.ToolWindowFloatingFrame` |
| Popředí (glyf) | `Environment.RaftedWindowButtonActiveGlyph` |
| Ohraničení | `Environment.MainWindowActiveDefaultBorder` |
| Border (glyf) | `Environment.RaftedWindowButtonActiveBorder`<br />(Nastaveno na transparentní) |

**Bez fokusu, rámeček plovoucího okna dokumentu: výchozí stav**

![Výchozí Nevybraný, plovoucí rámec okna dokumentu](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303 – 068_FrameUnfocused")<br />Výchozí Nevybraný, plovoucí rámec okna dokumentu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowFloatingFrameInactive` |
| Popředí (text) | `Environment.ToolWindowFloatingFrameInactive` |
| Popředí (glyf) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Ohraničení | `Environment.MainWindowInactiveBorder` |
| Border (glyf) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Nastaveno na transparentní) |

**Zaměření, plovoucí rámec okna dokumentu: stav najetí myší**

![Zaměření, plovoucí rámeček okna dokumentu při najetí myší](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303 – 069_FrameFocusedHover")<br />Zaměření, plovoucí rámeček okna dokumentu při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí (glyf) | `Environment.RaftedWindowButtonHoverActive` |
| Popředí (glyf) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Border (glyf) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Bez fokusu, rámeček plovoucího okna dokumentu: stav najetí myší**

![Nefokusový rámeček plovoucího okna dokumentu při najetí myší](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303 – 070_FrameUnfocusedHover")<br />Nefokusový rámeček plovoucího okna dokumentu při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí (glyf) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Popředí (glyf) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Border (glyf) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Zaměření, plovoucí rámec okna dokumentu: stisknutí stavu**

![Zaměřený rámeček plovoucího okna dokumentu při stisknutí klávesy](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303 – 071_FrameFocusedPressed")<br />Zaměřený rámeček plovoucího okna dokumentu při stisknutí klávesy

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí (glyf) | `Environment.RaftedWindowButtonDown` |
| Popředí (glyf) | `Environment.RaftedWindowButtonDownGlyph` |
| Border (glyf) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Záložky dokumentů
Karty dokumentu sedí na kanálu karet, které označují aktuálně otevřené dokumenty, spolu s tím, která z nich je aktuální vybraný nebo aktivní dokument. Okna nástrojů lze také ukotvit na kanálu na kartě dokumentu, pokud je uživatel umístí do umístění. V takové situaci používají stejné barvy tabulátoru jako okna dokumentu. Pokud vytváříte uživatelské rozhraní, které chcete vždy srovnat s barvami okna dokumentu (včetně aktualizací motivu nebo v případě, že jsou nainstalovány nové motivy), pak na tyto barevné tokeny odkazují.

![Karty dokumentu (Redline)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303 – 072_DocumentTabRedline")<br />Karty dokumentu (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... kdekoliv vytváříte uživatelské rozhraní, které chcete porovnat s kartami dokumentů, a automaticky vyberou aktualizace motivů nebo nové barvy motivů. | ... pro jakékoli uživatelské rozhraní, které nechcete měnit automaticky, když má prostředí aktualizaci motivu. |

#### <a name="open-document-tabs"></a>Otevřít karty dokumentu
Každý otevřený dokument obsahuje kartu na kanálu na kartě dokumentu, která zobrazuje jeho název. Dokumenty mohou být buď vybrány, nebo otevřeny na pozadí a jejich karty odrážejí tyto stavy:

- Vybraná karta představuje dokument, který je aktuálně zobrazen v dokumentaci dokumentu. Vybraná karta má ohraničení dokumentu, které se rozšíří na horní okraj dokumentu.

- Karty na pozadí jsou jakékoli karty dokumentu, které nejsou aktuálně vybranou kartou. Po kliknutí se stanou vybranými kartami a získá všechny barvy pozadí, ohraničení a textu z názvů těchto tokenů.

![Otevřít kartu dokumentu (Redline)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303 – 073_OpenDocumentTabRedline")<br />Otevřít kartu dokumentu (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... Při vytváření vlastních karet dokumentů. | ... pro předběžné karty (Preview). |
| | ... pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu. |

**Vybraná, prioritní karta dokumentu**

![Vybraná, prioritní karta dokumentu](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303 – 074_SelectedTabFocused")<br />Vybraná, prioritní karta dokumentu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.FileTabSelectedGradientTop`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.FileTabSelectedText` |
| Ohraničení | `Environment.FileTabSelectedBorder`<br />(Nastaveno na stejnou barvu jako na pozadí.) |
| Ohraničení dokumentu | `Environment.FileTabDocumentBorderBackground` |

**Vybraná, karta nevybraného dokumentu**

![Vybraná, karta nevybraného dokumentu](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303 – 075_SelectedTabUnfocused")<br />Vybraná, karta nevybraného dokumentu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.FileTabInactiveGradientTop`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.FileTabInactiveText` |
| Ohraničení | `Environment.FileTabInactiveBorder`<br />(Nastaveno na stejnou barvu jako na pozadí.) |
| Ohraničení dokumentu | `Environment.FileTabInactiveDocumentBorderBackground` |

**Karta dokumentu na pozadí: výchozí stav**

![Výchozí karta dokumentu na pozadí](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303 – 076_BackgroundTab")<br />Výchozí karta dokumentu na pozadí

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.FileTabBackground` |
| Popředí (text) | `Environment.FileTabText` |
| Ohraničení | `Environment.FileTabBorder`<br />(Nastaveno na stejnou barvu jako na pozadí.) |

**Karta dokumentu na pozadí: stav přechodu myši**

![Karta dokumentu na pozadí při najetí myší](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303 – 077_BackgroundTabHover")<br />Karta dokumentu na pozadí při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.FileTabHotGradientTop`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.FileTabHotText` |
| Ohraničení | `Environment.FileTabHotBorder`<br />(Nastaveno na stejnou barvu jako na pozadí.) |

#### <a name="preview-tab"></a>Karta náhled
Také se nazývá "provizorní" karta. Karta Náhled se zobrazí na pravé straně kanálu na kartě dokumentu, když uživatel klikne na položku v okně nástroje Průzkumník řešení. Funguje jako náhled dokumentu a také umožňuje uživateli zachovat otevření dokumentu na levé straně kanálu na kartě dokumentu. V jednom okamžiku může být otevřená jenom jedna otevřená karta náhled. Karty Preview mají jak pozadí, tak vybrané stavy, například otevřené karty a můžou být v jejich aktivním stavu zaměřené nebo nefokusované.

![Karta náhled (Redline)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303 – 078_PreviewTabRedline")<br />Karta náhled (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... kdekoliv vytváříte dočasnou verzi Preview a chcete, aby některý prvek odpovídal aktuální barvě karty Preview. | ... pro libovolný druh dokumentu nebo tabulátoru, který není předběžný (Preview). |
| | ... pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu. |

**Prioritní, vybraná karta náhled**

![Prioritní, vybraná karta náhled](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303 – 079_PreviewTabFocused")<br />Prioritní, vybraná karta náhled

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.FileTabProvisionalSelectedActive` |
| Popředí (text) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Ohraničení | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Nastaveno na stejnou barvu jako na pozadí.) |
| Ohraničení dokumentu | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Bez fokusu, vybraná karta náhled**

![Bez fokusu, vybraná karta náhled](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303 – 080_PreviewTabUnfocused")<br />Bez fokusu, vybraná karta náhled

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.FileTabProvisionalSelectedInactive` |
| Popředí (text) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Ohraničení | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Ohraničení dokumentu | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Karta Náhled pozadí: výchozí stav**

![Výchozí karta Náhled pozadí](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303 – 081_PreviewBackgroundTab")<br />Výchozí karta Náhled pozadí

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.FileTabProvisionalInactive` |
| Popředí (text) | `Environment.FileTabProvisionalInactiveForeground` |
| Ohraničení | `Environment.FileTabProvisionalInactiveBorder`<br />(Nastaveno na stejnou barvu jako na pozadí.) |

**Karta náhledu pozadí: stav najetí myší**

![Karta náhledu pozadí při najetí myší](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303 – 082_PreviewBackgroundTabHover")<br />Karta náhledu pozadí při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.FileTabProvisionalHover` |
| Popředí (text) | `Environment.FileTabProvisionalHoverForeground` |
| Ohraničení | `Environment.FileTabProvisionalHoverBorder`<br />(Nastaveno na stejnou barvu jako na pozadí.) |

#### <a name="document-overflow-button"></a>Tlačítko přetečení dokumentu
Tlačítko přetečení dokumentu je k dispozici, pokud je otevřen jeden nebo více dokumentů, bez ohledu na to, zda je v aktuální konfiguraci k dispozici Svislá mezera, aby se všechny karty dokumentu vešly. Rozevírací nabídka přetečení dokumentu, která je ovládána barvami [nabídky panelu příkazů](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) , zobrazuje seznam všech otevřených dokumentů, viditelné i skryté a glyf přetečení se mění v závislosti na tom, zda jsou všechny otevřené dokumenty zobrazeny v kanálu karet.

![Tlačítko přetečení dokumentu (Redline)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303 – 083_OverflowRedline")<br />Tlačítko přetečení dokumentu (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... Při vytváření vlastního tlačítka přetečení dokumentu. | ... pro uživatelské rozhraní, které se neshoduje s tlačítkem přetečení. |
| | ... pro tlačítka přetečení panelu příkazů. |

**Tlačítko přetečení dokumentu: výchozí stav**

![Výchozí tlačítko přetečení dokumentu](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303 – 084_Overflow")<br />Výchozí tlačítko přetečení dokumentu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.DocWellOverflowButtonBackground` |
| Popředí (glyf) | `Environment.DocWellOverflowButtonGlyph` |
| Ohraničení | – |

**Tlačítko přetečení dokumentu: stav najetí myší**

![Tlačítko přetečení dokumentu při najetí myší](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303 – 085_OverflowHover")<br />Tlačítko přetečení dokumentu při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Popředí (glyf) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Ohraničení | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Tlačítko přetečení dokumentu: stisknutý stav**

![Tlačítko přetečení dokumentu při stisknutí](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303 – 086_OverflowPressed")<br />Tlačítko přetečení dokumentu při stisknutí

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Popředí (glyf) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Ohraničení | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Označování
Visual Studio podporuje označování, které umožňuje uživateli deklarovat hledaná klíčová slova pro účely sledování. Například vedoucí projektu a vývojáři mohou použít Team Foundation Server (TFS) k označení pracovních položek. V tabulkách níže jsou uvedeny názvy barev pro samotnou značku a glyf "ikona zavřít", který se zobrazí při najetí myší a vybraných stavů.

![Označování v aplikaci Visual Studio (Redline)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303 – 176_TaggingRedline")<br />Označování v aplikaci Visual Studio (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... pro uživatelské rozhraní, které podporuje označování. | ... pro jakýkoli jiný typ uživatelského rozhraní. |

#### <a name="tags"></a>Značky

**Tag: výchozí stav**

![Výchozí značka](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303 – 177_Tag")<br />Výchozí značka

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Tag.Background` |
| Popředí (text) | `Tag.Background` |

**Tag: stav přechodu myši**

![Označit při najetí myší](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303 – 178_TagHover")<br />Označit při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Tag.HoverBackground` |
| Popředí (text) | `Tag.HoverBackgroundText` |

**Tag: stisknutí stavu**

![Stisknutá značka](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303 – 179_TagPressed")<br />Stisknutá značka

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Tag.PressedBackground` |
| Popředí (text) | `Tag.PressedBackgroundText` |

**Tag: vybraný stav**

![Vybraná značka](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303 – 180_TagSelected")<br />Vybraná značka

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Tag.SelectedBackground` |
| Popředí (text) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Zavřít ( &times; ) značka glyfu

**Close ( &times; ) – glyf značek: výchozí stav**

![Výchozí &times; glyf značky Close ()](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303 – 181_TagGlyph")<br />Výchozí &times; glyf značky Close ()

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | – |
| Popředí (glyf) | `Tag.TagHoverGlyph` |

**Close ( &times; ) – glyf značek: stav najetí myší**

![Zavřít ( &times; ) označit glyf při najetí myší](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303 – 182_TagGlyphHover")<br />Zavřít ( &times; ) označit glyf při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Tag.TagHoverGlyphHoverBackground` |
| Popředí (glyf) | `Tag.TagHoverGlyphHover` |
| Ohraničení | `Tag.TagHoverGlyphHoverBorder` |

**Close ( &times; ) – glyf značek: stisknutí stavu**

![Stisknutí značky Close ( &times; ) – glyf](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303 – 183_TagGlyphPressed")<br />Stisknutí značky Close ( &times; ) – glyf

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Tag.TagHoverGlyphPressedBackground` |
| Popředí (glyf) | `Tag.TagHoverGlyphPressed` |
| Ohraničení | `Tag.TagHoverGlyphPressedBorder` |

**Vybraná značka s &times; glyfem Close (): výchozí stav**

![Výchozí vybraná značka s &times; glyfem Close ()](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303 – 184_TagSelected")<br />Výchozí vybraná značka s &times; glyfem Close ()

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | – |
| Popředí (glyf) | `Tag.TagSelectedGlyph` |

**Vybraná značka s &times; glyfem Close (): stav najetí myší**

![Vybraná značka s &times; glyfem Close () při najetí myší](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303 – 185_TagSelectedHover")<br />Vybraná značka s &times; glyfem Close () při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Tag.TagSelectedGlyphHoverBackground` |
| Popředí (glyf) | `Tag.TagSelectedGlyphHover` |
| Ohraničení | `Tag.TagSelectedGlyphHoverBorder` |

**Vybraná značka s &times; glyfem Close (): stisknutý stav**

![Selected, stisknutá značka s &times; glyfem Close ()](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303 – 186_TagSelectedPressed")<br />Selected, stisknutá značka s &times; glyfem Close ()

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Tag.TagSelectedGlyphPressedBackground` |
| Popředí (glyf) | `Tag.TagSelectedGlyphPressed` |
| Ohraničení | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Okna nástrojů
Není nutné replikovat okna nástrojů, protože jsou k dispozici v prostředí sady Visual Studio. Můžete se ale rozhodnout, že chcete využít barvy používané v oknech nástrojů tak, aby se vaše uživatelské rozhraní vždy zobrazilo v souladu s touto částí prostředí sady Visual Studio.

![Okno nástrojů (Redline)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303 – 087_ToolWindowRedline")<br />Okno nástrojů (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... kdekoli vytváříte uživatelské rozhraní, které chcete porovnat s okny nástrojů. | ... pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu. |

### <a name="tool-window-frame"></a>Rám okna nástroje
Okna nástrojů v aplikaci Visual Studio se používají pro celou řadu různých úloh a mohou existovat v jednom z několika různých stavů. Je-li okno nástroje otevřeno, lze jej přiřadit k libovolné ze čtyř stran v oblasti dokumentu. Okna nástrojů můžou být také plovoucí mimo rozhraní IDE, což umožňuje jejich přemístění kdekoli v rámci obrazovky uživatele. Plovoucí okna se vždycky na IDE zasedat. Okna nástrojů lze nakonec ukotvit jako okna dokumentů a zobrazit jako kartu v dokumentaci dokumentu. Okna nástrojů, která jsou ukotvena jako okna dokumentů, jsou v části s použitím názvů tokenů oken dokumentu barevná.

![Rám okna nástroje (Redline)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303 – 088_ToolWindowFrameRedline")<br />Rám okna nástroje (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ...  kdekoli vytváříte uživatelské rozhraní, které chcete porovnat s okny nástrojů. | ... pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu. |

**Ukotvené okno nástrojů**

![Ukotvené okno nástrojů](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303 – 089_ToolWindowDocked")<br />Ukotvené okno nástrojů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowBackground` |
| Ohraničení | `Environment.ToolWindowBorder` |

**Plovoucí a prioritní okno nástrojů**

![Plovoucí a prioritní okno nástrojů](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303 – 090_ToolWindowFocused")<br />Plovoucí a prioritní okno nástrojů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowBackground` |
| Ohraničení | `Environment.MainWindowActiveDefaultBorder` |

**Plovoucí, nevybrané okno nástrojů**

![Plovoucí, nevybrané okno nástrojů](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303 – 091_ToolWindowUnfocused")<br />Plovoucí, nevybrané okno nástrojů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowBackground` |
| Ohraničení | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Okna podobné sadě nástrojů
Sada nástrojů je jedním z nejčastěji používaných běžných oken nástrojů v sadě Visual Studio. V podstatě se jedná o ovládací prvek stromu se speciálním motivem a použitým stylem.

![Okno podobné sadě nástrojů (Redline)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303 – 189_ToolboxRedline")<br />Okno podobné sadě nástrojů (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... Při navrhování okna nástroje, které chcete vždy konzistentně s panelem nástrojů prostředí. | ... pro cokoli, co není podobné uživatelskému rozhraní sady nástrojů, nebo pokud si nejste jistí, jestli vaše uživatelské rozhraní bude mít problémy, pokud se změní barvy sady nástrojů prostředí. |

**Uzly sady nástrojů: výchozí stav**

![Výchozí nadřazený uzel panelu nástrojů](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303 – 190_ToolboxParentNode")<br />Výchozí nadřazený uzel panelu nástrojů

![Výchozí podřízený uzel sady nástrojů](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303 – 191_ToolboxChildNode")<br />Výchozí podřízený uzel sady nástrojů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolboxContent`<br />Zcela |
| Pozadí | `Environment.ToolWindowBackground`<br />(Jednotlivé položky nebo celé okno, pokud nejsou k dispozici žádné ovládací prvky) |
| Ohraničení | Žádné |
| Popředí (glyf) | `Environment.ToolboxContent` |
| Popředí (text) | `Environment.ToolboxContent` |

**Podřízené uzly sady nástrojů: stav přechodu myši**

![Podřízený uzel panelu nástrojů při najetí myší](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303 – 192_ToolboxChildNodeHover")<br />Podřízený uzel panelu nástrojů při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolboxContentMouseOver`<br />(Pouze jednotlivé položky) |
| Ohraničení | Žádné |
| Popředí (text) | `Environment.ToolboxContentMouseOver`<br />(Pouze jednotlivé položky) |

**Vybrané uzly sady nástrojů: prioritní stav**

![Zaměření, vybraný nadřazený uzel sady nástrojů](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303 – 193_ToolboxParentNodeFocused")<br />Zaměření, vybraný nadřazený uzel sady nástrojů

![Zaměření, vybraný podřízený uzel sady nástrojů](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303 – 194_ToolboxChildNodeFocused")<br />Zaměření, vybraný podřízený uzel sady nástrojů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemActive`<br />Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Ohraničení | `TreeView.FocusVisualBorder`<br />Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Popředí (glyf) | `TreeView.SelectedItemActive`<br />Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Popředí (text) | `TreeView.SelectedItemActive`<br />Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Vybrané uzly sady nástrojů: nevybraný stav**

![Vybraný, nevybraný nadřazený uzel panelu nástrojů](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303 – 195_ToolboxParentNodeUnfocused")<br />Vybraný, nevybraný nadřazený uzel panelu nástrojů

![Vybraný, nevybraný podřízený uzel panelu nástrojů](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303 – 196_ToolboxChildNodeUnfocused")<br />Vybraný, nevybraný podřízený uzel panelu nástrojů

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemInactive`<br />Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Ohraničení | Žádné |
| Popředí (glyf) | `TreeView.SelectedItemInactive`<br />Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Popředí (text) | `TreeView.SelectedItemInactive`<br />Z kategorie [stromového zobrazení](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Panel nástrojů – záhlaví okna
Ohraničení záhlaví není pravý okraj, je to Tlustá čára v horní části záhlaví. Nemá název tokenu pro svůj nevybraný stav.

![Panel nástrojů – záhlaví okna (Redline)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303 – 092_ToolWindowTitleBarRedline")<br />Panel nástrojů – záhlaví okna (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... kdekoli vytváříte uživatelské rozhraní, které chcete porovnat s okny nástrojů. | ... pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu. |

**Prioritní záhlaví**

![Prioritní záhlaví](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303 – 093_TitleBarFocused")<br />Prioritní záhlaví

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.TitleBarActiveGradientBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.TitleBarActiveText` |
| Ohraničení | `Environment.TitleBarActiveBorder`<br />(Nastaveno na stejnou barvu jako na pozadí.) |
| Přetáhněte popisovač | `Environment.TitleBarDragHandleActive` |

**Nevybraný nadpisový řádek**

![Záhlaví bez fokusu](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303 – 094_TitleBarUnfocused")<br />Nevybraný nadpisový řádek

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.TitleBarInactiveGradientBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.TitleBarInactiveText` |
| Ohraničení | – |
| Přetáhněte popisovač | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Tlačítka pro záhlaví okna nástrojů
![Tlačítko záhlaví (Redline)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303 – 095_TitleBarButtonRedline")<br />Tlačítko záhlaví (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... pro tlačítka, která se zobrazí v uživatelském rozhraní, které používá tokeny barev z záhlaví okna nástrojů. | ... pro tlačítka, která se zobrazují v jiných umístěních. |
| | ... v jakékoliv kombinaci pozadí/popředí kromě zadaného. |

**Tlačítka s fokusem nadpisu: výchozí stav**

![Výchozí, prioritní tlačítka záhlaví](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303 – 096_TitleBarButtonFocused")<br />Výchozí, prioritní tlačítka záhlaví

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | – |
| Popředí (glyf) | `Environment.ToolWindowButtonActiveGlyph` |
| Ohraničení | – |

**Tlačítka záhlaví bez fokusu: výchozí stav**

![Výchozí nastavení, nevybrané tlačítko záhlaví](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303 – 097_TitleBarButtonUnfocused")<br />Výchozí nastavení, nevybrané tlačítko záhlaví

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | – |
| Popředí (glyf) | `Environment.ToolWindowButtonInactiveGlyph` |
| Ohraničení | – |

**Prioritní tlačítka záhlaví: stav přechodu myši**

![Zaměření tlačítek záhlaví při najetí myší](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303 – 098_TitleBarButtonFocusedHover")<br />Zaměření tlačítek záhlaví při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowButtonHoverActive` |
| Popředí (glyf) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Ohraničení | `Environment.ToolWindowButtonHoverActiveBorder` |

**Tlačítka záhlaví bez fokusu: stav najetí myší**

![Při najetí myší se nesoustředí tlačítka záhlaví](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303 – 099_TitleBarButtonUnfocusedHover")<br />Při najetí myší se nesoustředí tlačítka záhlaví

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowButtonHoverInactive` |
| Popředí (glyf) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Ohraničení | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Prioritní tlačítka záhlaví: stisknutí stavu**

![Zaměření tlačítek záhlaví na stisknutí](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303 – 100_TitleBarButtonFocusedPressed")<br />Zaměření tlačítek záhlaví na stisknutí

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowButtonDown` |
| Popředí (glyf) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Ohraničení | `Environment.ToolWindowButtonDownBorder` |

**Tlačítka záhlaví bez fokusu: stisknutí stavu**

![Při stisknutí tlačítek záhlaví bez fokusu](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303 – 101_TitleBarButtonUnfocusedPressed")<br />Při stisknutí tlačítek záhlaví bez fokusu

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowButtonDown` |
| Popředí (glyf) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Ohraničení | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Karty oken nástrojů
![Karta okna nástroje (Redline)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303 – 102_ToolWindowTabRedline")<br />Karta okna nástroje (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... kdekoli vytváříte uživatelské rozhraní, které chcete porovnat s okny nástrojů. | ... pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu. |

**Vybraná, karta okna nástrojů s fokusem**

![Vybraná, karta okna nástrojů s fokusem](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303 – 103_ToolWindowTabFocused")<br />Vybraná, karta okna nástrojů s fokusem

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowTabSelectedTab` |
| Popředí (text) | `Environment.ToolWindowTabSelectedActiveText` |
| Ohraničení | `Environment.ToolWindowTabSelectedBorder`<br />(Nastaveno na stejnou barvu jako na pozadí.) |

**Vybraná, karta okna nástrojů na nevybrané**

![Vybraná, karta okna nástrojů na nevybrané](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303 – 104_ToolWindowTabUnfocused")<br />Vybraná, karta okna nástrojů na nevybrané

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowTabSelectedTab` |
| Popředí (text) | `Environment.ToolWindowTabSelectedText` |
| Ohraničení | `Environment.ToolWindowTabSelectedBorder`<br />(Nastaveno na stejnou barvu jako na pozadí.) |

**Karta okna nástrojů na pozadí: výchozí stav**

![Výchozí karta okna nástrojů na pozadí](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303 – 105_ToolWindowBackgroundTab")<br />Výchozí karta okna nástrojů na pozadí

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Přechodové zarážky se nastaví na stejnou hodnotu barvy v Visual Studio 2013.) |
| Popředí (text) | `Environment.ToolWindowTabText` |
| Ohraničení | `Environment.ToolWindowTabBorder` |

**Karta okna nástrojů na pozadí: stav přechodu myši**

![Karta okna nástrojů na pozadí při najetí myší](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303 – 106_ToolWindowBackgroundTabHover")<br />Karta okna nástrojů na pozadí při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Přechodové zarážky se nastaví na stejnou hodnotu barvy v Visual Studio 2013.) |
| Popředí (text) | `Environment.ToolWindowTabMouseOverText` |
| Ohraničení | `Environment.ToolWindowTabMouseOverBorder`<br />(Nastaveno na stejnou barvu jako na pozadí.) |

### <a name="auto-hide-tabs"></a>Automaticky skrývat karty

![Automaticky skrývat karty (Redline)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 – 107_AutoHideRedline") Automaticky skrývat karty (Redline)

| Použít... | Nepoužívat... |
| --- | --- |
| ... kdekoli vytváříte uživatelské rozhraní, které chcete najít na kartách okna nástrojů pro automatické skrytí. | ... pro jakékoli uživatelské rozhraní, které nechcete změnit automaticky, pokud má prostředí aktualizaci motivu. |

**Automaticky skrývat karty: výchozí stav**

![Automaticky skrývat kartu výchozí](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303 – 108_AutoHideTab")<br />Automaticky skrývat kartu výchozí

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.AutoHideTabBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.AutoHideTabText` |
| Ohraničení | `Environment.AutoHideTabBorder` |

**Automaticky skrývat karty: stav najetí myší**

![Automaticky skrývat kartu při najetí myší](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303 – 109_AutoHideTabHover")<br />Automaticky skrývat kartu při najetí myší

| Prvek | Název tokenu: category. Color |
| --- | --- |
| Pozadí | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Zarážky přechodu pro tento token se nepoužívají v uživatelském rozhraní s motivem.) |
| Popředí (text) | `Environment.AutoHideTabMouseOverText` |
| Ohraničení | `Environment.AutoHideTabMouseOverBorder` |
