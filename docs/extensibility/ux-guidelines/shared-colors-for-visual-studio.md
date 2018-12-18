---
title: Sdílené barvy pro sadu Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 19d628f2f83943b88a415699dddd78f033597983
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833340"
---
# <a name="shared-colors-for-visual-studio"></a>Sdílené barvy pro Visual Studio
Když vytváříte uživatelské rozhraní, které používá běžné prvky prostředí Visual Studio nebo prvek rozhraní konzistentní s podobnými funkcemi, například, vybrat a přiřadit barvy pomocí existující token názvy v souborech s definicí balíčku. Tím se zajistí, že vaše uživatelské rozhraní zůstane konzistentní s celkové prostředí sady Visual Studio a že se automaticky aktualizuje při přidávání nebo aktualizaci motivy.  

Tento článek popisuje obecné prvky uživatelského rozhraní a token názvy, které používají, které můžete využít při sestavování podobným uživatelským rozhraním. Konkrétní informace o tom, jak přístupové tokeny tyto barvy, naleznete v tématu [VSColor službu](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  

Nezapomeňte použít token názvy správně:  

-   **Používejte token názvy založené na funkce, nikoli na vlastní barvu.** Společné sdílené barvy jsou spojeny s prvky určité rozhraní a jsou určeny pouze pro stejné nebo podobné funkce. Například nepoužívejte soubory Barva při stisknutí tlačítka pole se seznamem pro animace průběhu pokryjte pouze z důvodu jako barva. Funkce pole se seznamem a animace jsou různé a pokud barvu přidružené změny pole se seznamem, může již být vhodnou barvu pro prvek animace. Konzistentní použití barev pomůže zorientovat uživatelům a zabránit nejasnostem.  

-   **Barvy textu a pozadí pomocí správné kombinace.** Barvy pozadí, které jsou určeny pro použití s textem bude mít k přidružené textového barvu. Nepoužívejte barvy textu, než který je určen pro pozadí. Pokud není k dispozici barva příslušný text, nepoužívejte tuto barvu pozadí svého povrchu, kdy očekáváte, že k zobrazení textu. Nečitelný rozhraní může způsobit jiné kombinace barev textu a pozadí.  

-   **Pomocí řízení barvy, které jsou vhodné pro jejich umístění.** V některých státech některé ovládací prvky Visual Studio nemají samostatné ohraničení a barvy pozadí. Místo toho že sbírání tyto barvy z plochy za nimi stojí. Ujistěte se, že vždy používáte token názvy, které jsou vhodné pro umístění, ve kterém jsou umístění ovládacího prvku.  

> [!IMPORTANT]
> Nepoužívejte tokeny, které jsou nalezeny v kategoriích "Úvodní stránka" nebo "Jablečného."  

## <a name="common-shared-controls"></a>Běžné ovládací prvky sdílené

Použijete-li ve své funkci standardní panel příkazů sady Visual Studio, budete mít přístup k ovládacích prvků prostředí stylem. Neměli byste re šablony tyto běžné ovládací prvky. Ale pokud budete muset sestavit vlastní příkazového řádku, potřebujete k vytváření vlastních ovládacích prvků. V takovém případě nezapomeňte použít správný token názvy pro každý z následujících ovládacích prvků tak, aby vaše uživatelské rozhraní je konzistentní se zbytkem pracovního sadě Visual Studio.

### <a name="button-controls"></a>ovládací prvky tlačítek

![Ovládací prvek tlačítko červená značka](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 155_ButtonControlRedline")

| Použití... | Nepoužívejte... |
| --- | --- |
| ... pro tlačítka a dokument, který chcete integrovat s motivy sady Visual Studio (světlo, tmavé, modrá nebo motiv Vysoký kontrast systému). | ... pro tlačítka, které zobrazí vlastní pozadí, které nejsou součástí sady Visual Studio tématu. |

**Tlačítka: standardní stav**

![Standardní tlačítko](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Standardní tlačítka

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Tlačítko | `CommonControls.Button` |
| Ohraničení tlačítka | `CommonControls.ButtonBorder` |

**Tlačítka: výchozí stav**

![Výchozí tlačítko](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Výchozí tlačítko

| Prvek | Název tokenu: Category.color | 
| --- | --- | 
| Tlačítko | `CommonControls.ButtonDefault` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderDefault` |

**Tlačítko: zakázaném stavu**  

![Tlačítko zakázané](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Zakázané tlačítko  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonDisabled` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderDisabled` |

**Tlačítka: Stav přechodu.**  

![Tlačítko na přechodu](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Tlačítko na přechodu.  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonHover` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderHover` |

**Tlačítka: stav při stisknutí tlačítka myši**  

![Stisknutého tlačítka](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Stisknutého tlačítka  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonPressed` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderPressed` |

**Tlačítka: podrobný stav**  

![Cílené tlačítko](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Cílené tlačítko  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Tlačítko | `CommonControls.ButtonFocused` |
| Ohraničení tlačítka | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Ovládací prvky zaškrtávacích políček  
![Zaškrtávací políčko (červená značka)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303 161_CheckboxRedline")<br />Zaškrtávací políčko (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... pro ovládací prvky políčko a obsažených v dokumentu. | ... pro všechny uživatelské rozhraní, která není políčko ovládacího prvku. |

**Zaškrtávací políčko: výchozí stav**  

![Zaškrtněte políčko](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303 162_Checkbox")<br />Zaškrtávací políčko Výchozí

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackground` |
| Ohraničení | `CommonControls.CheckBoxBorder` |
| Text | `CommonControls.CheckBoxText` |
| Piktogram | `CommonControls.CheckBoxGlyph` |

**Zaškrtávací políčko: stav Zakázáno**  

![Zakázané zaškrtávací políčko](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303 163_CheckboxDisabled")<br />Zakázané zaškrtávací políčko.  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundDisabled` |
| Ohraničení | `CommonControls.CheckBoxBorderDisabled` |
| Text | `CommonControls.CheckBoxTextDisabled` |
| Piktogram | `CommonControls.CheckBoxGlyphDisabled` |

**Zaškrtávací políčko: ukazatel stavu**  

 ![Zaškrtněte políčko při najetí myší](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303 164_CheckboxHover")<br />Zaškrtnutí políčka při přechodu myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundHover` |
| Ohraničení | `CommonControls.CheckBoxBorderHover` |
| Text | `CommonControls.CheckBoxTextHover` |
| Piktogram | `CommonControls.CheckBoxGlyphHover` |  

**Zaškrtávací políčko: stav stisknutí**  

![Při stisknutí tlačítka zaškrtávací políčko](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303 165_CheckboxPressed")<br />Při stisknutí tlačítka zaškrtávací políčko  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundPressed` |
| Ohraničení | `CommonControls.CheckBoxBorderPressed` |
| Text | `CommonControls.CheckBoxTextPressed` |
| Piktogram | `CommonControls.CheckBoxGlyphPressed` |  

**Zaškrtávací políčko: zaměřený státu**  

![Políčko zaměření](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303 166_CheckboxFocused")<br />Políčko zaměření  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundFocused` |
| Ohraničení | `CommonControls.CheckBoxBorderFocused` |
| Text | `CommonControls.CheckBoxTextFocused` |
| Piktogram | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Rozevírací seznamy a pole se seznamem polí
![Drop-down/pole se seznamem (červená značka)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")<br />Drop-down/pole se seznamem (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... pro rozevírací seznamy a pole se seznamem pole v dokumentu dobře. | ... pro všechny uživatelské rozhraní, které není pole rozevíracího seznamu nebo pole se seznamem. |  
| | ... pro panel příkazů [rozevírací nabídky](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) nebo [polí se seznamem](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Rozevírací seznamy a pole se seznamem polí: výchozí stav**  

![Výchozí drop-down/pole se seznamem](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303 168_DropDownComboBox")<br />Výchozí drop-down/pole se seznamem

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackground` |
| Ohraničení | `CommonControls.ComboBoxBorder` |
| Text | `CommonControls.ComboBoxText` |
| Oddělovač | `CommonControls.ComboBoxSeparator` |
| Piktogram | `CommonControls.ComboBoxGlyph` |
| Piktogram na pozadí | `CommonControls.ComboBoxGlyphBackground` |

**Rozevírací seznamy a pole se seznamem polí: stav Zakázáno**  

![Zakázané drop-down/pole se seznamem](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")<br />Zakázané drop-down/pole se seznamem

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackgroundDisabled` |
| Ohraničení | `CommonControls.ComboBoxBorderDisabled` |
| Text | `CommonControls.ComboBoxTextDisabled` |
| Oddělovač | `CommonControls.ComboBoxSeparatorDisabled` |
| Piktogram | `CommonControls.ComboBoxGlyphDisabled` |
| Piktogram na pozadí | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Rozevírací seznamy a pole se seznamem polí: ukazatel stavu**  

![Drop-down/pole se seznamem při přechodu](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")<br />Drop-down/pole se seznamem při přechodu myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackgroundHover` |
| Ohraničení | `CommonControls.ComboBoxBorderHover` |
| Text | `CommonControls.ComboBoxTextHover` |
| Oddělovač | `CommonControls.ComboBoxSeparatorHover` |
| Piktogram | `CommonControls.ComboBoxGlyphHover` |
| Piktogram na pozadí | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Rozevírací seznamy a pole se seznamem polí: stav stisknutí**  

![Stisknutí tlačítka drop-down/pole se seznamem](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")<br />Při stisknutí tlačítka drop-down/pole se seznamem  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackgroundPressed` |
| Ohraničení | `CommonControls.ComboBoxBorderPressed` |
| Text | `CommonControls.ComboBoxTextPressed` |
| Oddělovač | `CommonControls.ComboBoxSeparatorPressed` |
| Piktogram | `CommonControls.ComboBoxGlyphPressed` |
| Piktogram na pozadí | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Rozevírací seznamy a pole se seznamem polí zobrazení seznamu zboží: stav stisknutí**  

 ![Drop-down/seznamem stisknutí zobrazení seznamu zboží](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")<br />Drop-down/seznamem stisknutí zobrazení položek seznamu  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Ohraničení | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Text položky | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Stín pozadí | `CommonControls.ComboBoxListBackgroundShadow` |

**Rozevírací seznamy a pole se seznamem polí: zaměřený státu**  

![Drop-down/pole se seznamem se zaměřením](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")<br />Drop-down/pole se seznamem se zaměřením

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.ComboBoxBackgroundFocused` |
| Ohraničení | `CommonControls.ComboBoxBorderFocused` |
| Text | `CommonControls.ComboBoxTextFocused` |
| Oddělovač | `CommonControls.ComboBoxSeparatorFocused` |
| Piktogram | `CommonControls.ComboBoxGlyphFocused` |
| Piktogram na pozadí | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Rozevírací seznamy a pole se seznamem polí: výběr vstupního textu**  

![Výběr vstupní text drop-down/pole se seznamem](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")<br />Výběr vstupní text drop-down/pole se seznamem  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Zvýraznění | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Ovládací prvky tabulkových dat (grid)  
Ovládací prvky tabulkových dat, označované také jako ovládací prvky mřížky, jsou běžné ovládací prvky pro Visual Studio, která slouží k zobrazení velkého objemu dat ve více sloupcích. Ovládací prvky standardní tabulkových dat najdete na více místech v rámci sady Visual Studio: panel nástrojů Seznam chyb, sestavy IntelliTrace a zobrazení paměti haldy, mimo jiné. Vždy používejte standardní tabulková data ovládací prvky k dispozici. V některých výjimečných případech nemusí mít přístup k ovládacím prvkům standardní tabulková data. V těchto situacích nepoužívejte následující názvy token k zajištění, že vaše uživatelské rozhraní je konzistentní s jinými ovládacími prvky tabulková data v sadě Visual Studio.  

![Tabulková data/gridu (červená značka)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")<br />Tabulková data/gridu (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... pro tabulkový nebo ovládací prvky mřížky. | ... pro všechny uživatelské rozhraní, který není ovládací prvek Tabulkový nebo mřížky. |

#### <a name="column-headers"></a>Záhlaví sloupců  
Záhlaví sloupců se skládají z na pozadí, ohraničení, text nadpisu a volitelné piktogram obvykle se používá pro mřížku je seřazený podle tohoto sloupce.  

**Záhlaví sloupce: výchozí stav**

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Header.Default` |
| Popředí (Text) | `Environment.CommandBarTextActive` |
| Popředí (piktogram) | `Header.Glyph` |
| Ohraničení | `Header.SeparatorLine` |

**Záhlaví sloupce: ukazatel stavu**

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Header.MouseOver` |
| Popředí (Text) | `Environment.CommandBarTextHover` |
| Popředí (piktogram) | `Header.MouseOverGlyph` |
| Ohraničení | `Header.SeparatorLine` |

**Záhlaví sloupce: stav stisknutí**

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `CommonControls.CheckBoxBackgroundPressed` |
| Popředí (Text) | `CommonControls.CheckBoxBorderPressed` |
| Popředí (piktogram) | `CommonControls.CheckBoxTextPressed` |
| Ohraničení | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Položky seznamu  
 Položky seznamu se skládají z na pozadí a obsah. Obsah může být text nebo ikonu.  

**Seznam položek k zobrazení: výchozí stav**

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Transparentní |
| Popředí (Text) | `Environment.CommandBarTextActive` |
| Ohraničení | Žádné |

**Seznam položek k zobrazení: aktivní stav**

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemActive` |
| Popředí (Text) | `TreeView.SelectedItemActiveText` |
| Ohraničení | Žádné |

**Seznam položek k zobrazení: neaktivním stavu**

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemInactive` |
| Popředí (Text) | `TreeView.SelectedItemInactiveText` |
| Ohraničení | Žádné |  

### <a name="ui-text"></a>Text uživatelského rozhraní

#### <a name="instructional-text"></a>Návodný text
Instruktážní text poskytuje výrazný hlavní vysvětlení, co lze na stránce dialogové okno nebo dokument.

![Výchozí pokyny](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Výchozí pokyny

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Sekundární instruktážní text.
Na stránkách dokumentu s velké množství textu a ovládacích prvků instruktážní text používá hodnotu jinou barvu. To pomáhá předávat informace, které je nejdůležitější a snížit celkovou hustotu prvků uživatelského rozhraní. (Viz také pod částí v textu nápovědy.)

![Instruktážní text sekundární](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Sekundární instruktážní text.

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Text nápovědy
Text nápovědy se zobrazí v ovládacím prvku prázdné pod ovládací prvek nebo na povrchu prázdný dokument se uživateli zobrazí, jak postupovat. Text nápovědy můžete použít s pozadí okna nebo ovládacího prvku.

**Výchozí text nápovědy**

![Výchozí text nápovědy](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Výchozí text nápovědy

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.ControlEditHintText` |

**Text požadované nápovědy**

![Text nápovědy vyžaduje](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Text požadované nápovědy

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Environment.ControlRequiredHintText` |
| Pozadí | `Environment.ControlRequiredBackground` |

**Text ovládacího prvku pole hledání**

> Viz [vyhledávací pole](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) pro další tokeny barvu související ovládací prvek vyhledávání.

![Hledat text ovládacího prvku pole](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Text ovládacího prvku pole hledání

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hypertextový odkaz  
Hypertextový odkaz je jeden ovládací prvek, který nemá páru pozadí a popředí. Ve všech případech použijte barvu popředí hypertextový odkaz, který se zobrazí správně v tmavě šedé a bílé pozadí. Pokud nepoužíváte barevné tokenu pro ovládací prvek hypertextový odkaz, zobrazí se výchozí systém barvu "stisknutí", který bude červeně blikat. To je signál, že ovládací prvek není pomocí tokenu barva správné prostředí.  

![Hypertextový odkaz (červená značka)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303 133_HyperlinkRedline")<br />Hypertextový odkaz (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... Pokud potřebujete vytvořit vlastní hypertextový odkaz. | ... pro cokoli, co není hypertextový odkaz. |

**Hypertextového odkazu: výchozí stav**  

![Výchozí hypertextový odkaz](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303 134_Hyperlink")<br />Výchozí hypertextový odkaz

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (Text) | `Environment.PanelHyperlink` |

**Hypertextového odkazu: při přechodu stavu**

![Hypertextového odkazu při umístění kurzoru myši](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303 135_HyperlinkHover")<br />Hypertextový odkaz na přechodu.  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (Text) | `Environment.PanelHyperlinkHover` |

**Hypertextový odkaz: stát při stisknutí tlačítka**

![Při stisknutí tlačítka hypertextový odkaz](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303 136_HyperlinkPressed")<br />Při stisknutí tlačítka hypertextový odkaz  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (Text) | `Environment.PanelHyperlinkPressed` |

**Hypertextového odkazu: vypnutém stavu**

![Zakázaný odkaz](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303 137_HyperlinkDisabled")<br />Zakázaný odkaz  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (Text) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infobars  
Infobars se používají k poskytují další informace o daném kontextu a vždy se zobrazí v horní části okna dokumentu nebo panelu nástrojů.  

![Informační panel (červená značka)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303 138_InfobarRedline")<br />Informační panel (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... při vytváření vlastní infobars. | ... pro prvky uživatelského rozhraní, které nejsou podobné informační řádek. |

**Informační řádek: výchozí stav**

![Výchozí informačním](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303 139_Infobar")<br />Výchozí informační panel

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.InfoBarBackground` |
| Popředí (Text) | `InfoBar.InfoBar` |
| Ohraničení | `InfoBar.InfoBarBorder` |

**Informační panel zavřít (&times;) tlačítko: výchozí stav**

![Výchozí informační panel zavřít (&times;) tlačítko](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Informační panel zavřete výchozí (&times;) tlačítko

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.CloseButton` |
| Ohraničení | `InfoBar.CloseButtonBorder` |
| Piktogram | `InfoBar.CloseButtonGlyph` |

**Informační panel zavřít (&times;) tlačítko: ukazatel stavu**

![Informační panel zavřít (&times;) tlačítko na přechodu](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Informační panel zavřít (&times;) tlačítka na přechodu.

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.CloseButtonHover` |
| Ohraničení | `InfoBar.CloseButtonHoverBorder` |
| Piktogram | `InfoBar.CloseButtonHoverGlyph` |

**Informační panel zavřít (&times;) tlačítka: stav stisknutí**

![Klepnutí na informační panel zavřít (&times;) tlačítko](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Klepnutí na informační panel zavřít (&times;) tlačítko

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.CloseButtonDown` |
| Ohraničení | `InfoBar.CloseButtonDownBorder` |
| Piktogram | `InfoBar.CloseButtonDownGlyph` |

**Informační panel tlačítko hypertextového odkazu: výchozí stav**

![Výchozí tlačítko hypertextového odkazu informačním](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Výchozí tlačítko hypertextový odkaz informační panel

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `InfoBar.Hyperlink` |

**Informační panel tlačítko hypertextového odkazu: ukazatel stavu**

![Informační panel tlačítko hypertextového odkazu při přechodu](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Informační panel tlačítko hypertextového odkazu při přechodu myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Infobar.HyperlinkMouseOver`<br />(S podtržením) |

**Informační panel tlačítko hypertextového odkazu: stav stisknutí**

![Tlačítko stisknuté informačním hypertextový odkaz](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Tlačítko stisknuté informačním hypertextový odkaz

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Infobar.HyperlinkMouseDown`<br />(S podtržením) |

**Hypertextový odkaz vložený informačním panelu (v rámci věty): výchozí stav**

![Tlačítko výchozí vložené informačním hypertextový odkaz](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Tlačítko výchozí vložené informačním hypertextový odkaz

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `InfoBar.Hyperlink` |

**Hypertextový odkaz vložený informačním panelu (v rámci věty): ukazatel stavu**

![Informační panel vložený hypertextový odkaz tlačítko při přechodu](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Informační panel vložené tlačítko hypertextového odkazu při přechodu myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Infobar.HyperlinkMouseOver`<br />(S podtržením) |

**Hypertextový odkaz vložený informačním panelu (v rámci věty): stav stisknutí**

![Informačního panelu při stisknutí tlačítka myši tlačítko hypertextového odkazu vloženého](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Bylo stisknuto tlačítko hypertextového odkazu vloženého informační panel

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (text) | `Infobar.HyperlinkMouseDown`<br />(S podtržením) |

**Tlačítko informační panel: výchozí stav**

![Výchozí tlačítko informačním](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Výchozí tlačítko informační panel

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.Button` |
| Popředí (text) | `InfoBar.Button` |
| Ohraničení | `InfoBar.ButtonBorder` |

**Tlačítko informační panel: ukazatel stavu**

![Tlačítko informační panel při přechodu](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Tlačítko informační panel při přechodu myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.ButtonMouseOver` |
| Popředí (text) | `InfoBar.ButtonMouseOver` |
| Ohraničení | `InfoBar.ButtonMouseOverBorder` |

**Informační panel tlačítka: stav stisknutí**

![Tlačítko stisknuté informačním](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Tlačítko stisknuté informační panel

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.ButtonMouseDown` |
| Popředí (text) | `InfoBar.ButtonMouseDown` |
| Ohraničení | `InfoBar.ButtonMouseDownBorder` |

**Informační panel tlačítka: stav Zakázáno**

![Tlačítko zakázáno informačním](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Tlačítko zakázáno informační panel

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.ButtonDisabled` |
| Popředí (text) | `InfoBar.ButtonDisabled` |
| Ohraničení | `InfoBar.ButtonDisabledBorder` |

**Tlačítko informační panel: zaměřený státu**

![Podrobný informační panel tlačítko](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Podrobný informační panel tlačítko

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `InfoBar.ButtonFocus` |
| Popředí (text) | `InfoBar.ButtonFocus` |
| Ohraničení | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Posuvníky  
Posuvníky jsou použity v prostředí Visual Studio a nemusí být s motivem. Ale můžete se rozhodnout, že chcete využít barvy použité v posuvníky tak, aby vaše uživatelské rozhraní se vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.  

![Posuvník (červená značka)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303 140_ScrollbarRedline")<br />Posuvník (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... při vytváření uživatelského rozhraní, chcete-li najít Visual Studio posuvníky. | ... pro nic nechcete, aby vždy odpovídal posuvníku uživatelského rozhraní. |

**Posuvník: výchozí stav**  

![Posuvníku výchozí](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303 141_Scrollbar")<br />Výchozím nastavení posuvníku

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Posuvník | `Environment.ScrollBarBackground` |
| Popředí (palce) | `Environment.ScrollBarThumbBackground` |

**Posuvník: ukazatel stavu**

![Posuvník při najetí myší](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303 143_ScrollbarHover")<br />Posuvník na přechodu.

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Posuvník | `Environment.ScrollBarBackground` |
| Popředí (palce) | `Environment.ScrollBarThumbMouseOverBackground` |

*Posuvník: stav stisknutí**

![Při stisknutí tlačítka posuvníku](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303 145_ScrollbarPressed")<br />Stisknutí tlačítka posuvníku  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Posuvník | `Environment.ScrollBarBackground` |
| Popředí (palce) | `Environment.ScrollBarThumbPressedBackground` |

**Šipka posuvníku: výchozí stav**  

![Výchozí panel šipku](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303 142_ScrollbarArrow")<br />Výchozí pruh šipku

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ScrollBarArrowBackground`<br />(Nastavte na stejnou barvu jako posuvníku). |
| Popředí (piktogram) | `Environment.ScrollBarArrowGlyph` |

**Šipka posuvníku: ukazatel stavu**

![Posuvníku šipky při najetí myší](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303 144_ScrollbarArrowHover")<br />Šipky posuvníku panel při přechodu myší  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ScrollBarArrowMouseOverBackground`<br />(Nastavte na stejnou barvu jako posuvníku). |
| Popředí (piktogram) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Šipka posuvníku: stav stisknutí**  

![Při stisknutí tlačítka posuvníku panel šipka](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")<br />Klepnutí na šipku posuvníku panel

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ScrollBarArrowPressedBackground`<br />(Nastavte na stejnou barvu jako posuvníku). |
| Popředí (piktogram) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>Vyhledávací pole  
Kdykoli je to možné, použijte běžný ovládací prvek vyhledávání poskytovaných prostředím sady Visual Studio. Vyhledávací pole barvy se nacházejí v kategorii "SearchControl" **ShellColors.pkgdef** soubor, který obsahuje token názvy pro vstupní pole, tlačítko akce, tlačítko rozevíracího seznamu a rozevírací nabídky.  

Vyhledávací pole může být jedna z několika státy, z nichž některé se vzájemně vylučují:  

-   "Zaměřuje" nebo "bez fokusu" odkazuje na Určuje, jestli je kurzor v textovém poli.  

-   "Aktivní" nebo "neaktivní" odkazuje na tom, jestli uživatel zadal vyhledávací dotaz v textovém poli.  

-   "Při najetí myší" znamená, že uživatel má moused prostřednictvím vyhledávacího pole pomocí myši (Tento stav potlačí všechny ostatní stavy).  

-   "Zakázáno" znamená, že funkce vyhledávání je vypnuté pro aktuální kontext.  

![Vyhledávací pole (červená značka)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303 110_SearchBoxRedline")<br />Vyhledávací pole (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... Pokud vytváříte vlastní vyhledávací pole. | ... pro cokoli, co není vyhledávací pole. |
| | ... pro všechny položky, které nechcete vždy odpovídat hledání pole uživatelského rozhraní. |

**Zaměřený na pole pro hledání**

![Vstupní pole pro cílené hledání](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br />Zaměřený na pole pro hledání  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.FocusedBackground` |
| Popředí (Text) | `SearchControl.FocusedBackground` |
| Ohraničení | `SearchControl.FocusedBorder` |
| Oddělovač | `SearchControl.FocusedDropDownSeparator` |

**Vstupní pole nezaostřená, aktivní vyhledávání**

![Vstupní pole hledání bez fokusu](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br />Vstupní pole nezaostřená, aktivní vyhledávání

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.SearchActiveBackground` |
| Popředí (Text) | `SearchControl.SearchActiveBackground` |
| Ohraničení | `SearchControl.UnfocusedBorder` |
| Oddělovač | `SearchControl.DropDownSeparator` |

**Vstupní pole hledání nezaostřená, neaktivní**

![Vstupní pole nezaostřená, neaktivní hledání](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Vstupní pole hledání nezaostřená, neaktivní  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.Unfocused` |
| Popředí (Text) | `SearchControl.Unfocused` |
| Ohraničení | `SearchControl.UnfocusedBorder` |
| Oddělovač | `SearchControl.DropDownSeparator` |

**Vstupní pole zvýrazněného vyhledávání (pouze text)**

![Vstupní pole zvýrazněného vyhledávání](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br />Vstupní pole zvýrazněného vyhledávání

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.Selection` |
| Popředí (Text) | `SearchControl.FocusedBackground` |
| Ohraničení | Žádné |
| Oddělovač | `SearchControl.FocusedDropDownSeparator` |

**Vstupní pole hledání zakázané**

![Vstupní pole vyhledávání zakázáno](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br />Vstupní pole hledání zakázané

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.Disabled` |
| Popředí (Text) | `SearchControl.Disabled` |
| Ohraničení | `SearchControl.DisabledBorder` |
| Oddělovač | `SearchControl.DropDownSeparator` |

**Tlačítko akce cílené hledání.**

![Tlačítko vyhledat akce, zaměřuje](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br />Tlačítko akce cílené hledání.

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (piktogram vyhledávání) | `SearchControl.SearchGlyph` |
| Popředí (Zastavit piktogram) | `SearchControl.StopGlyph` |
| Popředí (Vymazat piktogram) | `SearchControl.ClearGlyph` |
| Ohraničení | Není k dispozici |

**Tlačítko akce nezaostřená vyhledávání**  

![Tlačítko akce nezaostřená hledání](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br />Tlačítko akce nezaostřená vyhledávání

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není k dispozici |
| Popředí (piktogram vyhledávání) | `SearchControl.SearchGlyph` |
| Popředí (Zastavit piktogram) | `SearchControl.StopGlyph` |
| Popředí (Vymazat piktogram) | `SearchControl.ClearGlyph` |
| Ohraničení | Není k dispozici |

**Stisknutí tlačítka akce hledání**

![Tlačítko akce při stisknutí tlačítka Hledat](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Stisknutí tlačítka akce hledání

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.ActionButtonMouseDown` |
| Popředí (piktogram) | `SearchControl.ActionButtonMouseDownGlyph` |
| Ohraničení | `SearchControl.ActionButtonMouseDownBorder` |

**Tlačítko akce zakázané hledání**

![Tlačítko hledání akce zakázané](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br />Tlačítko akce zakázané hledání

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (piktogram) | `SearchControl.ActionButtonDisabledGlyph` |
| Ohraničení | Žádné |

**Tlačítko rozevíracího seznamu Cílené hledání.**

![Tlačítko rozevíracího seznamu Cílené hledání](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br />Tlačítko rozevíracího seznamu Cílené hledání.

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.FocusedDropDownButton` |
| Popředí (piktogram) | `SearchControl.FocusedDropDownButtonGlyph` |
| Ohraničení | `SearchControl.FocusedDropDownButtonBorder` |

**Tlačítko rozevíracího seznamu nezaostřená hledání**

![Tlačítko rozevíracího seznamu hledání nezaostřená](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br />Tlačítko rozevíracího seznamu nezaostřená hledání

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.UnfocusedDropDownButton` |
| Popředí (piktogram) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Ohraničení | `SearchControl.UnfocusedDropDownButtonBorder` |

**Klepnutí na tlačítko rozevíracího seznamu hledání**

![Rozevírací tlačítko stisknuté hledání](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Klepnutí na tlačítko rozevíracího seznamu hledání

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.MouseDownDropDownButton` |
| Popředí (piktogram) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Ohraničení | `SearchControl.MouseDownDropDownButtonBorder` |

**Rozevírací tlačítko zakázáno vyhledávání**

![Rozevírací tlačítko Hledat zakázané](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br />Rozevírací tlačítko zakázáno vyhledávání

| Prvek | Název tokenu: Category.color |
| --- | --- |  
| Pozadí | Žádné |
| Popředí (piktogram) | `SearchControl.DisabledDownButtonGlyph` |
| Ohraničení | Žádné |

#### <a name="search-drop-down-lists"></a>Hledání rozevírací seznamy  
Rozevírací nabídky pole hledání se může být poněkud složitější než ostatní rozevírací nabídky v sadě Visual Studio. "Navrhované vyhledávání" a "možnosti hledání" oddíly mohou objevit samostatně nebo společně v nabídce a každý z nich je barevný samostatně. Řádek také odděluje tyto dva oddíly, když jsou uvedeny společně a ohraničení kolem celého rozevírací nabídky.  

![Rozevírací seznam hledání (červená značka)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303 124_SearchDropdownRedline")<br />Rozevírací seznam hledání (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... při vytváření rozevíracího seznamu vlastní vyhledávání. | ... pro rozevírací seznamy, které se zobrazí v jiných kontextech. |
| ... správný token názvy správný seznam komponent. | ... v libovolné kombinaci pozadí/popředí, jiné než určené. |

**Vyhledávání prvku rozevíracího seznamu**

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Ohraničení | `SearchControl.PopupBorder` |
| Oddělovač | `SearchControl.PopupSectionHeaderSeparator` |
| Stín | `Environment.DropShadowBackground` |

**Navrhované vyhledávání: výchozí stav**

![Výchozí hledání navrhované](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303 125_SearchSuggested")<br />Výchozí navrhovaná hledání  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `SearchControl.PopupItemText` |

**Navrhované vyhledávání: ukazatel stavu**

![Navrhované vyhledávání při přechodu](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br />Navrhovaná hledání při přechodu myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `SearchControl.PopupMouseOverItemText` |
| Ohraničení | `SearchControl.PopupControlMouseOverBorder` |

**Možnosti hledání: výchozí stav**

![Zaškrtávací políčko Hledat](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303 126_SearchCheckbox")<br />Výchozí možnosti hledání (zaškrtávací políčko)  

![Možnosti hledání](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303 127_SearchOptions")<br />Výchozí možnosti hledání (odkaz)  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (zaškrtávací políčko text) | `SearchControl.PopupCheckboxText` |
| Popředí (text odkazu) | `SearchControl.PopupButtonText` |
| Pozadí záhlaví | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (text záhlaví) | `SearchControl.PopupSectionHeaderText` |

**Možnosti hledání: ukazatel stavu**

![Vyhledávání možností (zaškrtávací políčko) při přechodu](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br />Možnosti vyhledávání (zaškrtávací políčko) při přechodu myší  

![Vyhledávání možností (propojení) při přechodu](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303 130_SearchOptionsHover")<br />Možnosti vyhledávání (propojení) při přechodu myší  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (zaškrtávací políčko text) | `SearchControl.PopupCheckboxMouseDownText` |
| Popředí (text odkazu) | `SearchControl.PopupButtonMouseDownText` |
| Ohraničení | `SearchControl.PopupControlMouseOverBorder` |

**Možnosti hledání: stav stisknutí**  

![Stisknutí tlačítka Možnosti vyhledávání (zaškrtávací políčko)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br />Stisknutí tlačítka Možnosti vyhledávání (zaškrtávací políčko)   

![Stisknutí tlačítka Možnosti hledání (odkaz)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303 132_SearchOptionsPressed")<br />Stisknutí tlačítka Možnosti hledání (odkaz)  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí zaškrtávacího políčka | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (zaškrtávací políčko text) | `SearchControl.PopupCheckboxMouseDownText` |
| Odkaz na pozadí | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (text odkazu) | `SearchControl.PopupButtonMouseDownText` |

###  <a name="BKMK_TreeView"></a> Zobrazení stromu  
Hierarchické organizační schéma, jehož barvy jsou řízeny názvy barev v provedení několika nástroj pro windows, včetně řešení aplikace Explorer, Průzkumník serveru a zobrazení tříd `TreeView` kategorii. Barvy textu a pozadí mají všechny položky ve stromovém zobrazení. Položky, které mají vnořené podřízené prvky mají také glyfy označující, zda položka rozbalená nebo sbalená.  

![Zobrazení stromové struktury (červená značka)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303 147_TreeViewRedline")<br />Zobrazení stromové struktury (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... kdekoli, budete muset implementovat hierarchické zobrazení organizační. | ... pro cokoli, co není podobný strom. |
| | ... v libovolné kombinaci pozadí/popředí, jiné než určené. |

**Položky zobrazení stromu: výchozí stav**

![Výchozí položky zobrazení stromu](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303 148_TreeView")<br />Výchozí položka stromového zobrazení

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.Background` |
| Popředí (Text) | `TreeView.Background` |
| Popředí (piktogram) | `TreeView.Glyph` |
| Ohraničení | Žádné |

**Položky zobrazení stromu: ukazatel stavu**

![Položky zobrazení stromu při přechodu](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303 149_TreeViewHover")<br />Položky zobrazení stromu při přechodu myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.Background` |  
| Popředí (Text) | `TreeView.Background` |
| Popředí (piktogram) | `TreeView.GlyphMouseOver` |
| Ohraničení | Žádné |

**Položky zobrazení stromu: přetáhněte přes stát**

![Stromové zobrazení zboží na táhnout přes](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303 150_TreeViewDragOver")<br />Přetažením vyberte položku zobrazení stromu v  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.DragOverItem` |
| Popředí (Text) | `TreeView.DragOverItem` |
| Popředí (piktogram) | `TreeView.DragOverItemGlyph` |
| Ohraničení | Žádné |

**Položky zobrazení stromu: vybrané, zaměřený stav**

![Vybrané a zaměřují položky zobrazení stromu](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303 151_TreeViewFocused")<br />Položky zobrazení stromu vybrané a zaměření

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemActive` |
| Popředí (Text) | `TreeView.SelectedItemActive` |
| Popředí (piktogram) | `TreeView.SelectedItemActiveGlyph` |
| Ohraničení | `TreeView.FocusVisualBorder` |

**Položky zobrazení stromu: nezaostřená vybraného stavu**  

![Položky zobrazení stromu vybrané a nezaostřená](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303 152_TreeViewUnfocused")<br />Položky zobrazení stromu vybrané a nezaostřená

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemInactive` |
| Popředí (Text) | `TreeView.SelectedItemInactive` |
| Popředí (piktogram) | `TreeView.SelectedItemInactiveGlyph` |
| Ohraničení | Žádné |

**Položky zobrazení stromu: při přechodu myší, vybrali a zaměřena stavu**

![Vybrané a zaměřený na přechodu položky zobrazení stromu](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br />Položky zobrazení stromu vybrané a zaměřený na přechodu.  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemActive` |
| Popředí (Text) | `TreeView.SelectedItemActive` |
| Popředí (piktogram) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Ohraničení | `TreeView.FocusVisualBorder` |

**Položky zobrazení stromu: aktivované vybrané a nezaostřená státu**

![Položky zobrazení stromu vybrané a nezaostřená při přechodu](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br />Položky zobrazení stromu vybrané a nezaostřená při přechodu myší  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemInactive` |
| Popředí (Text) | `TreeView.SelectedItemInactive` |
| Popředí (piktogram) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Ohraničení | Žádné |

## <a name="shell-appearance"></a>Vzhled prostředí

### <a name="background"></a>Pozadí  
Na pozadí prostředí se skládá ze dvou vrstev. Spodní vrstva je plnou barvu, která zahrnuje celou integrovaného vývojového prostředí. Horní vrstvě vejde v rámci příkazu polici a mezi kanálů automatického skrytí okna nástroje na levých a pravých okrajů integrovaného vývojového prostředí. Horní a dolní vrstvy pozadí jsou nastaveny na stejnou barvu v motivech světlé a tmavé.  

![Visual Studio shell pozadí (červená značka)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303 187_ShellBackgroundRedline")<br />Visual Studio shell pozadí (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... pro místa, kam chcete odpovídat na pozadí prostředí sady Visual Studio. | ... jako výplň pro místa, která nejsou pozadí plochy. |
| | ... jako umístit prvky popředí na pozadí. |

**Vzhled prostředí dolní vrstva**

| Prvek | Název tokenu: Category.color |
| --- | --- |  
| Pozadí | `Environment.EnvironmentBackground` |

**Vzhled prostředí horní vrstva**

> Přechod zastaví nastavenou na hodnotu barvy v aplikaci Visual Studio 2013 světla a tmavé motivy.

| Prvek | Název tokenu: Category.color |
| --- | --- |  
| Pozadí | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |  

### <a name="command-shelf"></a>Příkaz police  
Dvě sady token názvů, které se používají pro pozadí příkaz police: nastavit jeden kde je umístěn řádku nabídek a jeden pro kde panely příkazů nacházejí. Pruhový graf konkrétní příkaz má svůj vlastní pozadí hodnot barev, které jsou popsány podrobněji v oddílu "panel příkazů". Řádek nabídek panelu a příkaz text je popsána v části panel nabídek a příkazů.  

![Visual Studio příkaz police (červená značka)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303 188_CommandShelfRedline")<br />Visual Studio příkaz police (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... pro oblasti umístění nabídek nebo panelů nástrojů. | ... pro oblasti, které nejsou podobné příkazu police. |
|... s kombinací pozadí/popředí správný název tokenu. | |

**Příkazový řádek nabídek police**

> Přechod zastaví nastavenou na hodnotu barvy v aplikaci Visual Studio 2013 světla a tmavé motivy.

| Prvek | Název tokenu: Category.color |
| --- | --- |  
| Pozadí | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

** Příkaz police příkaz panel **

> Přechod zastaví nastavenou na hodnotu barvy v aplikaci Visual Studio 2013 světla a tmavé motivy.

| Prvek | Název tokenu: Category.color |
| --- | --- |  
| Pozadí | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Návrhář manifestu  
Nástroj Manifest Designer je navržená jako způsob, jak bylo snazší upravit soubor manifestu v projektech pro systém Windows 8 a Windows Phone 8. Neplatí žádné sdílené architektuře k dispozici pro použití, může být vhodné pro tak, aby odpovídala návrhu rozložení a barvy orientace/navigačních karet a celkovou strukturu. Další informace o rozložení podrobnosti najdete v tématu [rozložení pro sadu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  

![Návrhář manifestu (červená značka)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303 175_ManifestDesignerRedline")<br />Návrhář manifestu (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... pro designery, které jsou podobné manifestu Návrhář. | ... máte-li více než šest karet. |
| namísto použití běžné ovládací prvky karty v horní části editoru v dokumentu... dobře. | ... pro všechny uživatelské rozhraní, který není strukturován podobně jako návrháři manifestu. |

**Vybraná karta v manifestu Designer: výchozí stav**

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `ManifestDesigner.TabActive` |
| Ohraničení | Žádné |

**Podokno vybrané popis manifestu Designer: výchozí stav**

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `ManifestDesigner.DescriptionPane` |

**Manifestu Návrhář vybraného obsahu stránky: výchozí stav**

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `ManifestDesigner.Background` |
| Dialogové okno text pomocné rutiny | `ManifestDesigner.WatermarkText`<br />(Tento název tokenu neodpovídá jeho funkce.) |

**Karta manifestu Designer: nevybrané státu**

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `ManifestDesigner.Tab.Inactive` |

**Karta manifestu Designer: ukazatel stavu**

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Příkaz struktury  

###  <a name="BKMK_CommandMenus"></a> Nabídky  
Nabídek může dojít v několika místech v rámci sady Visual Studio: hlavní nabídek vložený v dokumentu nebo nástroje systému windows, nebo klikněte pravým tlačítkem na různých místech v celém rozhraní IDE. Implementace nabídky spojené s další prvky uživatelského rozhraní jsou popsány v části pro odpovídající prvek. Vždy byste měli používat standardní nabídky implementace poskytovaných prostředím sady Visual Studio. V některých výjimečných případech ale nebudete mít přístup k standardní nabídky sady Visual Studio. V těchto situacích nepoužívejte následující názvy token k zajištění, že vaše uživatelské rozhraní je v souladu s jiným nabídkám v sadě Visual Studio.  

![Visual Studio nabídky (červená značka)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303 000_MenuRedline")<br />Visual Studio nabídky (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... Pokud potřebujete vytvořit vlastní nabídku.| ... pouze barvu pozadí. Vždy použijte kombinaci na pozadí a popředí uvedené. |
| ... když máte nové komponenty uživatelského rozhraní, který chcete najít v nabídkách sady Visual Studio.| |

#### <a name="menu-titles"></a>Nabídka titulů  
Názvy nabídek se skládají z na pozadí, ohraničení a text nadpisu, jakož i volitelný glyf, obvykle, když se nachází v nabídce v panelu příkazů.  

![Název nabídky (červená značka)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303 001_MenuTitleRedline")<br />Název nabídky (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... vždy, když vytváříte název vlastní nabídky. | ... pro všechny položky, které nechcete, aby vždy odpovídal název nabídky. |
| | ... v libovolné kombinaci pozadí/popředí, jiné než určené. |

**Název nabídky: výchozí stav**

![Výchozí název nabídky](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303 002_MenuTitleDefault")<br />Výchozí název nabídky

![Výchozí název nabídky glyfem](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")<br />Výchozí název nabídky glyfem

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (text) | `Environment.CommandBarTextActive` |
| Popředí (piktogramy) | `Environment.CommandBarMenuGlyph` |
| Ohraničení | Žádné |

**Název nabídky: ukazatel stavu**  

![Název nabídky při najetí myší](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303 004_MenuTitleHover")<br />Název nabídky při přechodu myší  

![Název nabídky glyfem při najetí myší](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")<br />Název nabídky glyfem při přechodu myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (text) | `Environment.CommandBarTextHover` |
| Popředí (piktogramy) | `Environment.CommandBarMenuMouseOverGlyph` |  
| Ohraničení | `Environment.CommandBarBorder` |

**Název nabídky: stav stisknutí**  

![Klepnutí na název nabídky](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303 006_MenuTitlePressed")<br />Název nabídky při stisknutí tlačítka myši

![Klepnutí na název nabídky glyfem](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")<br />Klepnutí na název nabídky glyfem

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.CommandBarTextActive` |
| Popředí (piktogram) | `Environment.CommandBarMenuMouseDownGlyph` |
| Ohraničení | `Environment.CommandBarMenuBorder`<br />(Pouze levé, horní a pravé straně.) |  

**Název nabídky: stav Zakázáno**  

![Název nabídky glyfem zakázán](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br />Název nabídky zakázáno glyfem

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (Text) | `Environment.CommandBarTextInactive` |
| Popředí (piktogram) | `Environment.CommandBarTextInactive` |
| Ohraničení | Žádné |

#### <a name="menu-items"></a>Položky nabídky
Individuální nabídky položky se skládá z text nabídky a volitelné ikony, zaškrtněte políčko nebo podnabídka glyfů. Jeho textu a pozadí Změna barvy při najetí myší. Tento token barva je pár na pozadí a popředí.  

![Červená značka položky nabídky](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 009_MenuItemRedline")  

| Použití... | Nepoužívejte... |
|---|---|
| ... pro všechny rozevírací seznam, je spuštěno z nabídek nebo na panel příkazů. | ... pro rozevírací seznam se v jiném kontextu. |
| | ... v libovolné kombinaci pozadí/popředí, jiné než určené. |

**Položky nabídky: výchozí stav**

![Výchozí položky nabídky](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303 010_MenuDefault")<br />Výchozí položky nabídky  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.CommandBarTextActive` |
| Popředí (podnabídky piktogram) | `Environment.CommandBarMenuSubmenuGlyph` |
| Ohraničení | `Environment.CommandBarMenuBorder` |
| Pozadí ikony kanálu | `Environment.CommandBarMenuIconBackground` |
| Oddělovač | `Environment.CommandBarMenuSeparator` |
| Stín | `Environment.DropShadowBackground` |

**Položky nabídky: zaškrtnuto a vybráno státy**  

![Nabídka zaškrtnutí](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303 011_MenuChecked")<br />Položky označené nabídky

![Nabídky vybrána](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303 012_MenuSelected")<br />Vybranou položku nabídky    

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Zaškrtávací políčko | `Environment.CommandBarCheckBox` |  
| Zaškrtávací políčko na pozadí | `Environment.CommandBarSelectedIcon` |  
| Pozadí ikony | `Environment.CommandBarSelected` |
| Okraj ikony | `Environment.CommandBarSelectedBorder` |

**Položky nabídky: ukazatel stavu**  

![Nabídky při najetí myší](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303 013_MenuHover")<br />Položka nabídky při přechodu myší

![Nabídky při najetí myší zaškrtnutí](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303 014_MenuHoverChecked")<br />Zkontrolovat položky nabídky při přechodu myší

![Nabídky při najetí myší vybraný](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303 015_MenuHoverSelected")<br />Vybranou položku nabídky při přechodu myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMenuItemMouseOver` |
| Popředí (Text) | `Environment.CommandBarMenuItemMouseOver` |
| Popředí (podnabídky piktogram) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Zaškrtávací políčko | `Environment.CommandBarCheckBoxMouseOver` |
| Zaškrtávací políčko na pozadí | `Environment.CommandBarHoverOverSelectedIcon` |
| Pozadí ikony | `Environment.CommandBarHoverOverSelected` |
| Okraj ikony | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Položky nabídky: stav Zakázáno**  

![Nabídka zakázané](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303 016_MenuDisabled")<br />Zakázaná položka nabídky

![Nabídky zakázáno zaškrtnutí](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303 017_MenuDisabledChecked")<br />Zakázaná položka nabídky se zaškrtnutím

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Popředí (Text) | `Environment.CommandBarTextInactive` |
| Popředí (podnabídky piktogram) | `Environment.CommandBarMenuSubmenuGlyph` |
| Zaškrtávací políčko | `Environment.CommandBarCheckBoxDisabled` |
| Zaškrtávací políčko na pozadí | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Panely příkazů  
Panel příkazů může zobrazit na více místech v rámci rozhraní IDE sady Visual Studio, zejména příkaz police a vložené v nástroj nebo dokumentu systému windows.  

Obecně platí vždy používejte implementace standardních příkazů panelu poskytovaných prostředím sady Visual Studio. Pomocí standardní mechanismus zajišťuje, že se správně zobrazí všechny podrobnosti o visual a interaktivní prvky, ke které přistupuje konzistentní s jinými ovládacími prvky sady Visual Studio příkazového řádku. Nicméně pokud je nutné, můžete vytvořit vlastní panel příkazů, ujistěte se, že správně pomocí následující token názvy stylu.  

![Panel příkazů červená značka](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303 018_CommandBarRedline")<br />Panel příkazů (červená linka)  

![Červená tlačítku přetečení značka](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303 019_OverflowButtonRedline")<br />Tlačítko přetečení (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... v místech, kde potřebujete panel aplikace vložený příkaz, ale nejsou schopny používat standardní implementaci panel příkazů sady Visual Studio. | ... pro prvky uživatelského rozhraní, které nejsou podobné panelu příkazů. |
| | ... pro komponenty panelu příkaz než ty, pro které jsou určeny názvy token. |

#### <a name="command-bar-groups"></a>Příkaz panel skupiny  
Příkaz pruhový graf se skládá ze sady související ovládací prvky stavového řádku příkaz a může obsahovat libovolný počet tlačítek rozdělení tlačítek, rozevíracích nabídek, pole se seznamem nebo nabídky. Barvy pro tyto ovládací prvky se budou řídit token názvy a jsou jednotlivě jinde popsaných v této příručce. Oddělovací čáry se používá k rozdělení skupiny panelu příkazů na související podskupiny.  

![Skupiny příkazového řádku červeně označit](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303 020_CommandBarGroupRedline")<br />Příkaz panel skupiny (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |  
| ... v místech, kde potřebujete panel aplikace vložený příkaz, ale nejsou schopny používat standardní implementaci panel příkazů sady Visual Studio. | ... pro prvky uživatelského rozhraní, které nejsou podobné panelu příkazů. |
| | ... pro komponenty panelu příkaz než ty, pro které jsou určeny názvy token. |

**Příkaz panel skupiny: výchozí stav**  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarGradientBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Ohraničení | `Environment.CommandBarToolBarBorder` |
| Úchyt pro přetažení | `Environment.CommandBarDragHandle` |
| Oddělovač | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Ikony příkazů  
![Červená ikona příkazu. značka](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303 021_CommandIconRedline1")<br />Ikonu příkazu (červená linka)  

![Červená ikona příkazu s textem linka](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303 022_CommandIconRedline2")<br />Příkaz ikony s textem (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... pro všechny tlačítka, který bude umístěn na panelu příkazů. | ... pro ovládací prvky, které mají své vlastní názvy token. |
| | ... v libovolné kombinaci pozadí/popředí, jiné než určené. |

**Ikona pro příkaz: výchozí stav**  

![Příkaz výchozí ikona](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303 023_CommandIconDefault")<br />Ikona výchozí příkaz

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není k dispozici (dědí nastavení z příkazového řádku na pozadí) |
| Popředí (Text) | `Environment.CommandBarTextActive` |
| Ohraničení | Není k dispozici |

**Ikona pro příkaz: Výchozí vybraný stav**

![Výchozí hodnota, ikonu vybraného příkazu](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br />Výchozí hodnota, ikonu vybraného příkazu  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarSelected` |
| Popředí (Text) | `Environment.CommandBarTextSelected` |
| Ohraničení | `Environment.CommandBarSelectedBorder` |

**Ikona pro příkaz: zaměření nebo přechodu států**  

![Ikonu příkazu na zaměření nebo přechodu](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303 025_CommandIconHover")<br />Ikonu příkazu na zaměření nebo přechodu.

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.CommandBarTextHover` |
| Ohraničení | `Environment.CommandBarBorder` |

**Ikona pro příkaz: zaměření nebo přechodu států, vybrané**

![Vybraná ikona příkazu na zaměření nebo přechodu](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br />Ikonu vybraného příkazu na zaměření nebo přechodu.

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarHoverOverSelected` |
| Popředí (Text) | `Environment.CommandBarTextHoverOverSelected` |
| Ohraničení | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Ikona pro příkaz: stav stisknutí**  

![Klepnutí na ikonu příkazu](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303 027_CommandIconPressed")<br />Ikona při stisknutí příkazu.

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.CommandBarTextMouseDown` |
| Ohraničení | `Environment.CommandBarBorder` |

**Ikona pro příkaz: stav Zakázáno**  

![Ikona zakázaného příkazu](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303 028_CommandIconDisabled")<br />Ikona zakázané příkazu.

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není k dispozici (dědí nastavení z příkazového řádku na pozadí) |
| Popředí (Text) | `Environment.CommandBarTextInactive` |
| Ohraničení | Není k dispozici |

####  <a name="BKMK_CommandComboBox"></a> Příkaz panel se seznamem

> [!IMPORTANT]
> Pole se seznamem se podobají rozevírací seznamy, ale zahrnují určitá oblast upravitelný text. Pokud rozevírací seznam na oblast upravitelný text neobsahuje, použít tokeny barvu pro [příkazový řádek rozevírací nabídky](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).  

![Červená značka příkazový řádek se seznamem](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303 029_ComboBoxRedline")<br />Příkazový řádek se seznamem (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... při vytváření vlastního pole se seznamem. | ... pro nic nechcete, aby vždy odpovídající příkaz pruhu uživatelského rozhraní. |
| ... při vytváření panel příkazů, který je podobně jako pole se seznamem. | ... Pokud máte přístup k Stylizovaný pole se seznamem. |

**Příkazového řádku pole se seznamem vstupu: výchozí stav**

![Příkazového řádku pole se seznamem vstupní](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303 030_ComboBoxInputField")<br />Příkazového řádku pole se seznamem vstupu  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxBackground` |
| Popředí (Text) | `Environment.ComboBoxText` |
| Ohraničení | `Environment.ComboBoxBorder` |
| Oddělovač | Žádný oddělovač |

**Příkaz panel rozevírací tlačítko: výchozí stav**  

![Rozevírací pole se seznamem&#45;tlačítko](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")<br />Tlačítko rozevíracího seznamu příkazového řádku

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není k dispozici (dědí nastavení z příkazového řádku na pozadí) |
| Popředí (piktogram) | `Environment.ComboBoxGlyph` |

**Příkaz panel rozevíracího seznamu: výchozí stav**

![Příkaz panel rozevíracího seznamu](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br />Příkaz panel rozevíracího seznamu

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxPopupBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.ComboBoxItemText` |
| Ohraničení | `Environment.ComboBoxPopupBorder` |

**Příkazového řádku pole se seznamem vstupu: ukazatel stavu**  

![Příkaz panel pole se seznamem vstupu při přechodu](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br />Příkaz panel pole se seznamem vstupu při přechodu myší  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.ComboBoxMouseOverText` |
| Ohraničení | `Environment.ComboBoxMouseOverBorder` |
| Oddělovač | `Environment.ComboBoxMouseOverSeparator` |

 **Příkaz panel rozevírací tlačítko: ukazatel stavu**  

![Příkaz panel rozevírací tlačítko při přechodu](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")<br />Příkaz panel rozevírací tlačítko při přechodu myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxButtonMouseOverBackground` |
| Popředí (piktogram) | `Environment.ComboBoxMouseOverGlyph` |

**Příkaz panel rozevíracího seznamu: ukazatel stavu**

 ![Příkaz panel rozevírací seznam při přechodu](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br />Příkaz panel rozevírací seznam při přechodu myší  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Na pozadí (položka nabídky) | `Environment.ComboBoxItemMouseOverBackground` |
| Popředí (Text) | `Environment.ComboBoxItemMouseOverText` |
| Ohraničení (položka nabídky) | `Environment.ComboBoxItemMouseOverBorder` |

 **Příkazového řádku pole se seznamem vstupu: zaměřený státu**  

![Zaměřený na příkazovém řádku vstupní pole se seznamem](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br />Zaměřený na příkazovém řádku pole se seznamem vstupu

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxFocusedBackground` |
| Popředí (Text) | `Environment.ComboBoxFocusedText` |
| Ohraničení | `Environment.ComboBoxFocusedBorder` |
| Oddělovač | `Environment.ComboBoxFocusedButtonSeparator` |

**Příkaz panel rozevírací tlačítko: zaměřený státu**  

![Zaměřený na příkazovém řádku tlačítko rozevíracího seznamu](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")<br />Cílené příkaz panel tlačítko rozevíracího seznamu

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxFocusedButtonBackground` |
| Popředí (piktogram) | `Environment.ComboBoxFocusedGlyph` |

 **Příkazového řádku pole se seznamem vstupu: stav stisknutí**  

![Stisknutí příkazového řádku vstupní pole se seznamem](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br />Stisknutí příkazového řádku pole se seznamem vstupu

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxMouseDownBackground` |
| Popředí (Text) | `Environment.ComboBoxMouseDownText` |
| Ohraničení | `Environment.ComboBoxMouseDownBorder` |
| Oddělovač | `Environment.ComboBoxMouseDownSeparator` |

**Příkaz panel rozevírací tlačítko: stav stisknutí**

![Příkaz panel rozevírací tlačítko stisknuté](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")<br />Příkaz panel rozevírací tlačítko stisknuté  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxButtonMouseDownBackground` |
| Popředí (piktogram) | `Environment.ComboBoxMouseDownGlyph` |

**Příkazového řádku pole se seznamem vstupu: stav Zakázáno**  

![Zakázat příkazový řádek vstupního pole se seznamem](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br />Zakázaný příkaz panel vstupní pole se seznamem  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ComboBoxDisabledBackground` |
| Popředí (Text) | `Environment.ComboBoxDisabledText` |
| Ohraničení | `Environment.ComboBoxDisabledBorder` |
| Oddělovač | Žádný oddělovač |

**Příkaz panel rozevírací tlačítko: stav Zakázáno**  

![Zakázat příkazový řádek rozevírací tlačítko](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")<br />Zakázaný příkaz panel tlačítko rozevíracího seznamu

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (piktogram) | `Environment.ComboBoxDisabledGlyph` |

####  <a name="BKMK_CommandDropDown"></a> Příkaz panel rozevírací seznamy

> [!IMPORTANT]
>  Rozevírací seznamy jsou podobné polích se seznamem, ale nemají upravitelný text oblastech. Pokud rozevírací seznam obsahuje na oblast upravitelný text, použijte pro tokeny barvu [příkazový řádek se seznamem](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).  

![Příkaz panel rozevíracího seznamu (červená značka)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303 042_DropdownRedline")<br />Příkaz panel rozevíracího seznamu (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... při vytváření vlastní rozevírací seznam ovládacích prvků. | ... pro cokoli, co není podobně jako rozevírací seznam. |
| | ... pro pole se seznamem nebo tlačítka Rozdělit. |   

**Příkaz panel Výběr rozevíracího pole: výchozí stav**  

![Výchozí příkaz panel Výběr rozevíracího pole](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303 043_DropdownSelectionField")<br />Výchozí příkaz panel Výběr rozevíracího seznamu pole  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownBackground` |
| Popředí (Text) | `DropDownText` |
| Ohraničení | `DropDownBorder` |
| Oddělovač | Žádný oddělovač |

**Příkaz panel rozevírací tlačítko: výchozí stav**

![Výchozí příkaz panel tlačítko rozevíracího seznamu](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303 044_DropdownButton")<br />Výchozí příkaz panel rozevírací tlačítko  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (piktogram) | `Environment.DropDownGlyph` |

**Příkaz panel rozevíracího seznamu: výchozí stav**

![Výchozí příkaz panel rozevíracího seznamu](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303 045_DropdownList")<br />Výchozí příkaz panel rozevíracího seznamu  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownPopupBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.ComboBoxItemText` |
| Ohraničení | `Environment.DropDownPopupBorder` |
| Stín | `Environment.DropShadowBackground` |

**Příkaz panel Výběr rozevíracího pole: ukazatel stavu**  

![Příkaz panel Výběr rozevíracího pole na přechodu](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br />Příkaz panel Výběr rozevíracího seznamu pole na přechodu.  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownMouseOverBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.DropDownMouseOverText` |
| Ohraničení | `Environment.DropDownMouseOverBorder` |
| Oddělovač | `Environment.DropDownButtonMouseOverSeparator` |

**Příkaz panel rozevírací tlačítko: ukazatel stavu**  

![Příkaz panel rozevírací tlačítko při přechodu](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303 047_DropdownButtonHover")<br />Příkaz panel rozevírací tlačítko při přechodu myší  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownButtonMouseOverBackground` |
| Popředí (piktogram) | `Environment.DropDownMouseOverGlyph` |

**Příkaz panel rozevíracího seznamu: ukazatel stavu**  

![Příkaz panel rozevírací seznam při přechodu](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303 048_DropdownListHover")<br />Příkaz panel rozevírací seznam při přechodu myší  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Na pozadí (položka nabídky) | `Environment.ComboBoxItemMouseOverBackground` |
| Popředí (Text) | `Environment.ComboBoxItemMouseOverText` |
| Ohraničení (položka nabídky) | `Environment.ComboBoxItemMouseOverBorder` |

 **Příkaz panel Výběr rozevíracího pole: stav stisknutí**  

![Vyřadit&#45;dolů pole výběru stisknutí](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br />Klepnutí na příkaz panel Výběr rozevíracího seznamu pole

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownMouseDownBackground` |
| Popředí (Text) | `Environment.DropDownMouseDownText` |
| Ohraničení | `Environment.DropDownMouseDownBorder` |
| Oddělovač | `Environment.DropDownButtonMouseDownSeparator` |

**Příkaz panel rozevírací tlačítko: stav stisknutí**

![Příkaz panel rozevírací tlačítko stisknuté](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")<br />Příkaz panel rozevírací tlačítko stisknuté  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownButtonMouseDownBackground` |
| Popředí (piktogram) | `Environment.DropDownMouseDownGlyph` |

**Příkaz panel Výběr rozevíracího pole: stav Zakázáno**  

![Zakázat příkazový řádek výběru v rozevíracím seznamu pole](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")<br />Zakázaný příkaz panel Výběr rozevíracího seznamu pole

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DropDownDisabledBackground` |
| Popředí (Text) | `Environment.DropDownDisabledText` |
| Ohraničení | `Environment.DropDownDisabledBorder` |
| Oddělovač | Žádný oddělovač |

**Příkaz panel rozevírací tlačítko: stav Zakázáno**

![Zakázat příkazový řádek rozevírací tlačítko](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")<br />Zakázaný příkaz panel tlačítko rozevíracího seznamu

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není k dispozici |
| Popředí (piktogram) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Panel příkazů rozdělit tlačítka
Tlačítka rozdělení sdílet s jinými ovládacími prvky příkazového řádku, jako jsou tlačítka, nabídky a panelu text příkazu mnoho názvů token. Všechny potřebné akce a tlačítkem rozevírací nabídky token názvy pro usnadnění práce tady opakují. Rozdělení tlačítko rozevírací seznamy jsou implementace [příkazový řádek nabídek](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).  

![Tlačítko rozdělení červená značka](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303 053_SplitButtonRedline")<br />Panel příkazů tlačítko rozdělení (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... při vytváření tlačítko Vlastní rozdělení. | ... pro další typy tlačítek. |
| | ... v libovolné kombinaci pozadí/popředí, jiné než určené. |

**Panel příkazů tlačítko rozdělení: výchozí stav**  

![Výchozí příkaz panel tlačítko rozdělení](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303 054_SplitButton")<br />Výchozí panel příkazů tlačítko rozdělení  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Žádné |
| Popředí (Text) | `Environment.CommandBarTextActive` |
| Popředí (piktogram) | `Environment.CommandBarSplitButtonGlyph` |
| Ohraničení | Není k dispozici |
| Oddělovač | Není k dispozici |

**Panel příkazů tlačítko rozdělení: ukazatel stavu**  

![Panel příkazů tlačítko při přechodu rozdělení](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303 055_SplitButtonHover")<br />Panel příkazů tlačítko při přechodu rozdělení

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.CommandBarTextHover` |
| Popředí (piktogram) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Ohraničení | `Environment.CommandBarBorder` |
| Oddělovač | `Environment.CommandBarSplitButtonSeparator` |

**Panel příkazů tlačítko rozdělení: stav stisknutí**  

![Bylo stisknuto tlačítko rozdělení panelu příkaz](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303 056_SplitButtonPressed")<br />Panel příkazů stisknuté tlačítko rozdělení  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.CommandBarTextMouseDown` |
| Popředí (piktogram) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Ohraničení | `Environment.CommandBarBorder` |
| Oddělovač | Není k dispozici |

**Panel příkazů tlačítko rozdělení: stav Zakázáno**

![Zakázat příkazový řádek tlačítko rozdělení](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br />Panel příkazů zakázáno tlačítko rozdělení

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není k dispozici |
| Popředí (Text) | `Environment.ComboBoxItemTextInactive` |
| Popředí (piktogram) | `Environment.CommandBarTextInactive` |
| Ohraničení | Není k dispozici |
| Oddělovač | Není k dispozici |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Panel "Další možnosti" a "Přetečení" příkazových tlačítek  
Tlačítko "Další možnosti" se používá při skupinou příkazů panelu přizpůsobitelné buď přidáním nebo odebráním související panelu příkazů. Tlačítko "Přetečení" se zobrazí, když je zkrácena kvůli nedostatku místa na vodorovné panel příkazů a při kliknutí zobrazí nabídku, která obsahuje panelu příkazů nelze zobrazit. Barvy pro tyto dvě tlačítka se řídí stejnou sadu token názvy.  

![Příkaz panel tlačítko 'Více možností' (červená značka)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303 058_MoreOptionsRedline")<br />Příkaz panel tlačítko 'Více možností' (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... pro vlastní "Další možnosti" nebo "Přetečení" tlačítka. | ... pro tlačítka, které nemají podobné funkce jako další možnosti nebo tlačítka "Přetečení". |

**Příkaz panel tlačítek "Přetečení" a další možnosti: výchozí stav**  

![Výchozí příkaz panel tlačítko 'Více možností'](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303 059_MoreOptions")<br />Výchozí panel příkazů tlačítko "Další možnosti"

![Výchozí příkaz panel tlačítko "Přetečení"](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303 060_Overflow")<br />Výchozí příkazového řádku "Přetečení" tlačítko

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarOptionsBackground` |
| Popředí (piktogram) | `Environment.CommandBarOptionsGlyph` |

**Příkaz panel tlačítek "Přetečení" a další možnosti: ukazatel stavu**

![Příkaz panel tlačítko "Další možnosti" při přechodu](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303 061_MoreOptionsHover")<br />Příkaz panel tlačítko 'Více možností' na přechodu.  

![Tlačítko "Přetečení" příkaz panel při přechodu](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303 062_OverflowOptions")<br />Příkazové tlačítko "Přetečení" panel na přechodu.   

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (piktogram) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Příkaz panel tlačítek "Přetečení" a další možnosti: stav stisknutí**  

![Stisknutí příkazového řádku tlačítko 'Více možností'](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303 063_MoreOptionsPressed")<br />Stisknutí příkazového řádku tlačítko "Další možnosti"  

![Přetečení stisknutí](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303 064_OverflowPressed")<br />Bylo stisknuto tlačítko "Přetečení" příkazového řádku  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (piktogram) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Okna dokumentů  
Vzhledem k tomu, že jsou poskytované Visual Studio prostředí není nutné replikovat windows dokumentu. Ale můžete se rozhodnout, že chcete využít barvy použité v dokumentu systému windows tak, aby vaše uživatelské rozhraní se vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.  

Při použití tokeny barvu okna dokumentu, nezapomeňte použít pouze pro podobné prvky a vždy ve dvojicích. Pokud neprovedete, můžete získat neočekávané výsledky v uživatelském rozhraní.  

### <a name="document-window-frames"></a>Rámečků oken dokumentu  
Okna dokumentu může být ukotven v integrovaném vývojovém prostředí nebo s plovoucí desetinnou čárkou jako samostatném okně. Když mimo rozhraní IDE je plovoucí okno dokumentu, je stále umístěn v dokumentu a a má pozadí, ohraničení, text a barvy oušek, které jsou stejné, jako když je součástí rozhraní IDE. Ale dokumentu se nachází uvnitř rámečku, který má svou vlastní pozadí ohraničení a barvy textu. Když okna nástrojů jsou ukotveny v kontejneru dokumentu, dědí chování a barvy pro jejich karty z tokenu názvy oken dokumentů.  

![Okno dokumentu ukotvený (červená značka)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")<br />Okno dokumentu ukotvený (červená linka)  

![Plovoucí okna dokumentu (červená značka)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")<br />Plovoucí okna dokumentu (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... kdekoli vytváříte uživatelské rozhraní, které chcete přiřadit v okně dokumentu. | ... pro všechny uživatelské rozhraní, které chcete změnit, pokud nechcete automaticky prostředí má aktualizace motivu. |

**Dokument ukotvený nebo plovoucí okno: výchozí stav**  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Závisí na typu dokumentu |
| Popředí (Text) | Závisí na typu dokumentu |
| Ohraničení | `Environment.ToolWindowBorder` |

**Cílené plovoucí rám okna dokumentu: výchozí stav**

![Výchozí zaměřený, plovoucí rám okna dokumentu](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303 067_FrameFocused")<br />Výchozí zaměřený, plovoucí rám okna dokumentu

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowFloatingFrame` |
| Popředí (Text) | `Environment.ToolWindowFloatingFrame` |
| Popředí (piktogram) | `Environment.RaftedWindowButtonActiveGlyph` |
| Ohraničení | `Environment.MainWindowActiveDefaultBorder` |
| Ohraničení (piktogram) | `Environment.RaftedWindowButtonActiveBorder`<br />(Nastavena na hodnotu průhledný) |

**Rámeček okna dokumentu nezaostřená, plovoucí: výchozí stav**  

![Výchozí rámeček okna dokumentu nezaostřená, plovoucí](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303 068_FrameUnfocused")<br />Výchozí dokument nezaostřená, plovoucí rám okna

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowFloatingFrameInactive` |
| Popředí (Text) | `Environment.ToolWindowFloatingFrameInactive` |
| Popředí (piktogram) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Ohraničení | `Environment.MainWindowInactiveBorder` |
| Ohraničení (piktogram) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Nastavena na hodnotu průhledný) |

**Cílené plovoucí rám okna dokumentu: ukazatel stavu**

![Cílené plovoucí rám okna dokumentu při přechodu](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303 069_FrameFocusedHover")<br />Cílené plovoucí rám okna dokumentu při přechodu myší  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Na pozadí (piktogram) | `Environment.RaftedWindowButtonHoverActive` |
| Popředí (piktogram) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Ohraničení (piktogram) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Rámeček okna dokumentu nezaostřená, plovoucí: ukazatel stavu**  

![Rámeček okna dokumentu nezaostřená, plovoucí při přechodu](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br />Nezaostřená plovoucí rám okna dokumentu při přechodu myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Na pozadí (piktogram) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Popředí (piktogram) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Ohraničení (piktogram) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Cílené plovoucí rám okna dokumentu: stav stisknutí**  

![Cílené plovoucí rám okna dokumentu na stroji](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303 071_FrameFocusedPressed")<br />Cílené plovoucí rám okna dokumentu na stroji

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Na pozadí (piktogram) | `Environment.RaftedWindowButtonDown` |
| Popředí (piktogram) | `Environment.RaftedWindowButtonDownGlyph` |
| Ohraničení (piktogram) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Záložky dokumentů  
Karty dokumentů se nacházejí v kanálu kartu označující dokumenty, které jsou právě otevřeny, a která z nich je aktuální vybraná nebo aktivní dokument. Okna nástrojů lze také ukotvit v kanálu kartu dokumentu, pokud existuje uživatel je umístí. V takovém případě používají stejné barvy karet jako okna dokumentu. Při vytváření uživatelského rozhraní, který chcete vždy odpovídat barvy okno dokumentu (včetně aktualizací motiv nebo pokud jsou nainstalovány nové motivy) a pak odkazovat na tyto barvy tokeny.  

![Karet dokumentů (červená značka)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303 072_DocumentTabRedline")<br />Karet dokumentů (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... kdekoli vytváříte uživatelské rozhraní, které chcete odpovídat karty dokumentů a automaticky získávají aktualizace motivu nebo nové barvy motivu. | ... pro všechny uživatelské rozhraní, které nechcete automaticky změnit, pokud má aktualizovat motiv v prostředí. |

#### <a name="open-document-tabs"></a>Karty otevřených dokumentů  
Každý otevřený dokument obsahuje kartu v kanálu kartu dokumentu, který se zobrazí její název. Dokumenty, můžete buď vybrat nebo otevřete na pozadí a jejich karty, aby odrážela tyto stavy:  

-   Vybraná karta představuje dokument, který je dobře zobrazeno v dokumentu. Vybraná karta má ohraničení dokumentu, který rozšiřuje dobře mezi horním okrajem dokumentu.  

-   Karty na pozadí jsou všechny karty dokumentů, které nejsou aktuálně vybraná karta. Po kliknutí na stát vybraná karta a získat všechny barvy ohraničení, textu a pozadí z těchto tokenů názvy.  

![Otevřít dokument karta (červená značka)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")<br />Otevřít dokument karta (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... při vytváření dokumentu vlastní karty. | ... pro karty prozatímní (Náhled). |
| | ... pro všechny uživatelské rozhraní, které nechcete automaticky změněna prostředí má aktualizace motivu. |

**Kartu dokumentu vybrané, zaměřený**  

![Vybrané, zaměřený na kartu dokumentu](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303 074_SelectedTabFocused")<br />Kartu dokumentu vybrané, zaměřený

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabSelectedGradientTop`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.FileTabSelectedText` |
| Ohraničení | `Environment.FileTabSelectedBorder`<br />(Nastavte na stejnou barvu jako pozadí). |
| Dokument ohraničení | `Environment.FileTabDocumentBorderBackground` |

**Dokument vybraný, nezaostřená kartu**

![Kartu dokumentu vybrané, nezaostřená](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br />Dokument vybraný, nezaostřená kartu

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabInactiveGradientTop`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.FileTabInactiveText` |
| Ohraničení | `Environment.FileTabInactiveBorder`<br />(Nastavte na stejnou barvu jako pozadí). |
| Dokument ohraničení | `Environment.FileTabInactiveDocumentBorderBackground` |

**Karta pozadí dokumentu: výchozí stav**  

![Výchozí pozadí dokumentu kartu](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303 076_BackgroundTab")<br />Karta dokument výchozí pozadí  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabBackground` |
| Popředí (Text) | `Environment.FileTabText` |
| Ohraničení | `Environment.FileTabBorder`<br />(Nastavte na stejnou barvu jako pozadí). |

**Karta pozadí dokumentu: ukazatel stavu**  

![Karta pozadí dokumentu při přechodu](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303 077_BackgroundTabHover")<br />Karta pozadí dokumentu při přechodu myší  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabHotGradientTop`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.FileTabHotText` |
| Ohraničení | `Environment.FileTabHotBorder`<br />(Nastavte na stejnou barvu jako pozadí). |

#### <a name="preview-tab"></a>Karta náhledu  
Také se nazývá "prozatímní" kartu. Na kartě preview se zobrazí na pravé straně kanálu kartu dokumentu po kliknutí na položku v panelu nástrojů Průzkumníku řešení. Funguje jako náhled dokumentu a také umožňuje uživateli možnost zachovat dokument otevřít na levé straně kanálu kartu dokumentu. Otevřenou kartou pouze jednu verzi preview může být najednou otevřený. Ve verzi Preview karty mají i na pozadí a vybraných států, jako jsou otevřené karty a může být zaměřené nebo bez fokusu v aktivním stavu.  

![Karty Náhled (červená značka)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303 078_PreviewTabRedline")<br />Karty Náhled (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... vždy vytváříte prozatímní náhled a má některé prvek tak, aby odpovídala aktuální barva karty Náhled. | ... pro jakýkoli druh dokladu nebo karty, která není prozatímní (Náhled). |
| | ... pro všechny uživatelské rozhraní, které nechcete automaticky změněna prostředí má aktualizace motivu. |

**Karty Náhled zaměřený, vybrané**  

![Karty Náhled zaměřený, vybrané](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303 079_PreviewTabFocused")<br />Karty Náhled zaměřený, vybrané

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabProvisionalSelectedActive` |
| Popředí (Text) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Ohraničení | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Nastavte na stejnou barvu jako pozadí). |
| Dokument ohraničení | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Karty Náhled nezaostřená, vybrané**  

![Karty Náhled vybrané, nezaostřená](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br />Karty Náhled nezaostřená, vybrané

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabProvisionalSelectedInactive` |
| Popředí (Text) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Ohraničení | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Dokument ohraničení | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Karty Náhled pozadí: výchozí stav**  

![Karty Náhled výchozí pozadí](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br />Karty Náhled výchozí pozadí  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabProvisionalInactive` |
| Popředí (Text) | `Environment.FileTabProvisionalInactiveForeground` |
| Ohraničení | `Environment.FileTabProvisionalInactiveBorder`<br />(Nastavte na stejnou barvu jako pozadí). |

**Karty Náhled pozadí: ukazatel stavu**  

![Karty Náhled pozadí při přechodu](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br />Karty Náhled pozadí při přechodu myší  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.FileTabProvisionalHover` |
| Popředí (Text) | `Environment.FileTabProvisionalHoverForeground` |
| Ohraničení | `Environment.FileTabProvisionalHoverBorder`<br />(Nastavte na stejnou barvu jako pozadí). |

#### <a name="document-overflow-button"></a>Dokument tlačítku přetečení  
Tlačítko přetečení dokument je k dispozici, pokud existuje jedna nebo více dokumentů otevřít, bez ohledu na to, zda je v aktuální konfiguraci podle všechny karty dokumentu svislé mezery. Rozevírací nabídky přetečení dokumentu, který je kontrolován [příkazový řádek nabídky](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) barvy, se zobrazí seznam všech otevřených dokumentů zobrazená i skrytá a přetečení glyf změny v závislosti na tom, zda jsou všechny otevřené dokumenty Zobrazí kartu kanálu.  

![Tlačítko přetečení dokument (červená značka)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303 083_OverflowRedline")<br />Tlačítko přetečení dokument (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... při vytváření dokumentu vlastní tlačítko přetečení. | ... pro uživatelské rozhraní, která není podobná k tlačítku přetečení. |
| | ... pro přetečení tlačítka panelu příkazů. |

**Tlačítko přetečení dokument: výchozí stav**  

![Tlačítko přetečení výchozí dokument](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303 084_Overflow")<br />Tlačítko přetečení výchozí dokument

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DocWellOverflowButtonBackground` |
| Popředí (piktogram) | `Environment.DocWellOverflowButtonGlyph` |
| Ohraničení | Není k dispozici |

**Tlačítko přetečení dokument: ukazatel stavu**

![Tlačítko přetečení dokumentu při přechodu](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303 085_OverflowHover")<br />Dokument přetečení tlačítka při najetí myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Popředí (piktogram) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Ohraničení | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Tlačítko přetečení dokument: stav stisknutí**  

![Tlačítko přetečení dokument na stroji](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303 086_OverflowPressed")<br />Tlačítko přetečení dokument při tisku

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Popředí (piktogram) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Ohraničení | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Označování  
Visual Studio podporuje označování, které umožňuje uživateli deklarovat prohledávatelná klíčová slova pro účely sledování. Například projektových manažerů a vývojářů může používat Team Foundation Server (TFS) k označení pracovních položek. Následující tabulky poskytují názvy barev pro vlastní značku i "Zavřít ikonu" šifra, která se zobrazí při najetí myší a vybraných států.  

![Tagování v sadě Visual Studio (červená značka)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303 176_TaggingRedline")<br />Tagování v sadě Visual Studio (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... pro uživatelské rozhraní, která podporuje tagování. | ... pro jakýkoli jiný typ uživatelského rozhraní. |

#### <a name="tags"></a>Značky  

**Značky: výchozí stav**

![Výchozí značka](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303 177_Tag")<br />Výchozí tag

| Prvek | Název tokenu: Category.color |
| --- | --- |  
| Pozadí | `Tag.Background` |
| Popředí (Text) | `Tag.Background` |

**Značka: stavu přechodu.**  

![Označit při najetí myší](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303 178_TagHover")<br />Značky na přechodu.  

| Prvek | Název tokenu: Category.color |
| --- | --- |  
| Pozadí | `Tag.HoverBackground` |
| Popředí (Text) | `Tag.HoverBackgroundText` |

**Značka: stisknutí státu**

![Stisknutí tlačítka značky](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303 179_TagPressed")<br />Při stisknutí tlačítka značka  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.PressedBackground` |
| Popředí (Text) | `Tag.PressedBackgroundText` |

**Značky: stav vybrané**

![Vybrané značky](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303 180_TagSelected")<br />Vybrané značky  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.SelectedBackground` |
| Popředí (Text) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Zavřít (&times;) značky glyfů

**Zavřít (&times;) značky glyfů: výchozí stav**

![Výchozí Zavřít (&times;) značky glyfů](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303 181_TagGlyph")<br />Výchozí Zavřít (&times;) značky glyfů

| Prvek | Název tokenu: Category.color |
| --- | --- |  
| Pozadí | Není k dispozici |
| Popředí (piktogram) | `Tag.TagHoverGlyph` |

**Zavřít (&times;) značky glyfů: ukazatel stavu**

![Zavřít (&times;) značky glyfů při přechodu](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303 182_TagGlyphHover")<br />Zavřít (&times;) značky glyfů v přechodu.

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.TagHoverGlyphHoverBackground` |
| Popředí (piktogram) | `Tag.TagHoverGlyphHover` |
| Ohraničení | `Tag.TagHoverGlyphHoverBorder` |

**Zavřít (&times;) značky glyfů: stav stisknutí**

![Stisknutí tlačítka Zavřít (&times;) značky glyfů](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303 183_TagGlyphPressed")<br />Stisknutí tlačítka Zavřít (&times;) značky glyfů

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.TagHoverGlyphPressedBackground` |
| Popředí (piktogram) | `Tag.TagHoverGlyphPressed` |
| Ohraničení | `Tag.TagHoverGlyphPressedBorder` |

**Vybrané značky se zavřít (&times;) glyfů: výchozí stav**

![Výchozí vybranou značku s Zavřít (&times;) – piktogram](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303 184_TagSelected")<br />Výchozí vybranou značku s Zavřít (&times;) – piktogram

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není k dispozici |
| Popředí (piktogram) | `Tag.TagSelectedGlyph` |

**Vybrané značky se zavřít (&times;) glyfů: ukazatel stavu**  

![Vybrané značky se zavřít (&times;) glyf při přechodu](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Vybrané značky se zavřít (&times;) glyfů v přechodu.  


| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.TagSelectedGlyphHoverBackground` |
| Popředí (piktogram) | `Tag.TagSelectedGlyphHover` |
| Ohraničení | `Tag.TagSelectedGlyphHoverBorder` |

**Vybrané značky se zavřít (&times;) glyfů: stav stisknutí**  

![Vybrané, značka s zavřít stisknutí (&times;) piktogram](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303 186_TagSelectedPressed")<br />Vybrané, značka s zavřít stisknutí (&times;) – piktogram

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Tag.TagSelectedGlyphPressedBackground` |
| Foreground(Glyph) | `Tag.TagSelectedGlyphPressed` |
| Ohraničení | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Nástroje systému windows  
Není nutné k replikaci nástroj systému windows, protože jsou poskytované Visual Studio prostředí. Ale můžete se rozhodnout, že chcete využít barvy použité v oknech nástrojů tak, aby vaše uživatelské rozhraní se vždy zobrazí konzistentní s touto částí prostředí sady Visual Studio.  

![Okno nástroje (červená značka)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303 087_ToolWindowRedline")<br />Okno nástroje (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... kdekoli vytváříte uživatelské rozhraní, které chcete přiřadit panel nástrojů. | ... pro všechny uživatelské rozhraní, které nechcete automaticky změněna prostředí má aktualizace motivu. |

### <a name="tool-window-frame"></a>Rámeček okna nástroje  
Okna nástrojů v sadě Visual Studio se používají pro celou řadu různých úloh a může existovat v jednom z několika různých stavů. Pokud je panel nástrojů otevřen, může být přiřazena k některému z čtyřech stranách oblasti dokumentu. Nástroje systému windows můžete také uvolnit mimo rozhraní IDE, odkud můžou přesunout kamkoli v rámci obrazovce uživatele. Plovoucí okna vždy nacházejí na integrovaném vývojovém prostředí. Nakonec panely nástrojů lze ukotvit jako dokument windows a zobrazí jako karty v dobře dokumentu. Okna nástrojů, které byly ukotvit jako dokument windows se zobrazí v části pomocí tokenu názvy oken dokumentů.  

![Rám okna nástroje (červená značka)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")<br />Rám okna nástroje (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... kdekoli vytváříte uživatelské rozhraní, které chcete přiřadit panel nástrojů. | ... pro všechny uživatelské rozhraní, které nechcete automaticky změněna prostředí má aktualizace motivu. |

**Ukotveném panelu nástrojů okna**  

![Ukotveném panelu nástrojů okna](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303 089_ToolWindowDocked")<br />Ukotveném panelu nástrojů okna  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowBackground` |
| Ohraničení | `Environment.ToolWindowBorder` |

**Plovoucí, zaměřený na okno nástroje**

![Plovoucí, zaměřený na okno nástroje](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303 090_ToolWindowFocused")<br />Plovoucí, zaměřený na okno nástroje

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowBackground` |
| Ohraničení | `Environment.MainWindowActiveDefaultBorder` |

**Plovoucí okno nástroje nezaostřená**  

![Nezaostřená, plovoucí okno nástroje](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303 091_ToolWindowUnfocused")<br />Plovoucí okno nástroje nezaostřená  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowBackground` |
| Ohraničení | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Podobných nástrojů systému windows
Panel nástrojů je jedním z nejčastěji používaných společné nástroje windows v sadě Visual Studio. Je v podstatě Stromový ovládací prvek s zvláštní motiv a styl použit.  

![Podobných nástrojů okna (červená značka)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303 189_ToolboxRedline")<br />Podobných nástrojů okna (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... když navrhujete okno nástroje, který chcete vždy odpovídat panelu prostředí. | ... pro cokoli, co není podobný panelu nástrojů uživatelského rozhraní nebo pokud si nejste jisti, zda vaše uživatelské rozhraní bude mít problémy se změnou barvy nástrojů prostředí. |

**Uzly nástrojů: výchozí stav**

![Výchozí uzel nadřazené nástrojů](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303 190_ToolboxParentNode")<br />Výchozí prvky nadřazeného uzlu

![Výchozí prvky podřízený uzel](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303 191_ToolboxChildNode")<br />Výchozí prvky podřízený uzel

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolboxContent`<br />(Položky) |
| Pozadí | `Environment.ToolWindowBackground`<br />(Jednotlivé položky nebo celé okno, pokud není k dispozici ovládací prvky) |
| Ohraničení | Žádné |
| Popředí (piktogram) | `Environment.ToolboxContent` |
| Popředí (Text) | `Environment.ToolboxContent` |

**Podřízené uzly nástrojů: ukazatel stavu**

![Podřízený uzel panelu nástrojů při najetí myší](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br />Podřízený uzel nástrojů při přechodu myší  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolboxContentMouseOver`<br />(Pouze pro jednotlivé položky) |
| Ohraničení | Žádné |
| Popředí (Text) | `Environment.ToolboxContentMouseOver`<br />(Pouze pro jednotlivé položky) |

**Vybrané uzly nástrojů: zaměřený státu**

![Nadřazený uzel zaměřený, vybraných nástrojů](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br />Nadřazený uzel zaměřený, vybraných nástrojů  

![Podřízený uzel zaměřený, vybraných nástrojů](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br />Podřízený uzel zaměřený, vybraných nástrojů

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemActive`<br />Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |
| Ohraničení | `TreeView.FocusVisualBorder`<br />Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |
| Popředí (piktogram) | `TreeView.SelectedItemActive`<br />Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |
| Popředí (Text) | `TreeView.SelectedItemActive`<br />Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |

**Vybrané uzly nástrojů: nezaostřená státu**

![Panel nástrojů vybraný, nezaostřená nadřazený uzel](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br />Panel nástrojů vybraný, nezaostřená nadřazený uzel  

![Panel nástrojů vybraný, nezaostřená podřízený uzel](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br />Panel nástrojů vybraný, nezaostřená podřízený uzel  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `TreeView.SelectedItemInactive`<br />Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |
| Ohraničení | Žádné |
| Popředí (piktogram) | `TreeView.SelectedItemInactive`<br />Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |
| Popředí (Text) | `TreeView.SelectedItemInactive`<br />Z [zobrazení stromové struktury](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorie |

### <a name="tool-window-title-bar"></a>Záhlaví okna nástroje  
Panel ohraničení nadpis není pravda ohraničení, je tlustou čárou v horní části záhlaví. Název tokenu pro jeho nezaostřená stát nemusí.  

![Záhlaví okna nástroje (červená značka)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")<br />Záhlaví okna nástroje (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... kdekoli vytváříte uživatelské rozhraní, které chcete přiřadit panel nástrojů. | ... pro všechny uživatelské rozhraní, které nechcete automaticky změněna prostředí má aktualizace motivu. |

**Cílené záhlaví**

![Cílené záhlaví](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303 093_TitleBarFocused")<br />Cílené záhlaví

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.TitleBarActiveGradientBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.TitleBarActiveText` |
| Ohraničení | `Environment.TitleBarActiveBorder`<br />(Nastavte na stejnou barvu jako pozadí). |
| Úchyt pro přetažení | `Environment.TitleBarDragHandleActive` |

**Záhlaví bez fokusu**  

![Záhlaví bez fokusu](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303 094_TitleBarUnfocused")<br />Záhlaví bez fokusu

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.TitleBarInactiveGradientBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.TitleBarInactiveText` |
| Ohraničení | Není k dispozici |
| Úchyt pro přetažení | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Nástroj tlačítek na panelu nadpisu okna  
![Záhlaví tlačítko (červená značka)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")<br />Záhlaví tlačítko (červená linka)  

| Použití... | Nepoužívejte... |
| --- | --- |
| ... pro tlačítka, která se zobrazí v uživatelském rozhraní, která používá tokeny barvu ze záhlaví okna nástroje. | ... pro tlačítka, které jsou zobrazeny na jiných místech. |
| | ... v libovolné kombinaci pozadí/popředí, jiné než určené. |

**Zaměřený na název tlačítka panelu: výchozí stav**

![Výchozí, zaměřený na název tlačítka panelu](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br />Výchozí tlačítka panelu zaměřený titul  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není k dispozici |
| Popředí (piktogram) | `Environment.ToolWindowButtonActiveGlyph` |
| Ohraničení | Není k dispozici |

**Nezaostřená název tlačítka panelu: výchozí stav**

![Výchozí hodnota, nezaostřená název tlačítka na panelu](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br />Výchozí nastavení tlačítek na panelu nadpisu nezaostřená    

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | Není k dispozici |
| Popředí (piktogram) | `Environment.ToolWindowButtonInactiveGlyph` |
| Ohraničení | Není k dispozici |

**Zaměřený na název tlačítka panelu: ukazatel stavu**  

![Název tlačítka panelu zaměřený na přechodu](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br />Tlačítek panelu titul zaměřený na přechodu.

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowButtonHoverActive` |
| Popředí (piktogram) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Ohraničení | `Environment.ToolWindowButtonHoverActiveBorder` |

**Nezaostřená název tlačítka panelu: ukazatel stavu**  

![Nezaostřená název tlačítka panelu při přechodu](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br />Nezaostřená název tlačítka panelu při přechodu myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowButtonHoverInactive` |
| Popředí (piktogram) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Ohraničení | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Zaměřený na název tlačítka panelu: stav stisknutí**

![Zaměřený na stisknutí tlačítek na panelu nadpisu](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br />Tlačítka na panelu titul zaměřený na stroji

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowButtonDown` |
| Popředí (piktogram) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Ohraničení | `Environment.ToolWindowButtonDownBorder` |

**Nezaostřená název tlačítka panelu: stav stisknutí**

![Nezaostřená název tlačítka panelu na stroji](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br />Nezaostřená název tlačítka panelu na stroji  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowButtonDown` |
| Popředí (piktogram) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Ohraničení | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Karty okna nástrojů  
![Okno Karta nástroje (červená značka)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303 102_ToolWindowTabRedline")<br />Okno Karta nástroje (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... kdekoli vytváříte uživatelské rozhraní, které chcete přiřadit panel nástrojů. | ... pro všechny uživatelské rozhraní, které nechcete automaticky změněna prostředí má aktualizace motivu. |

**Karta okna vybrané, úzce zaměřený nástroje**

![Vybrané, zaměřený okna Karta Nástroje](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br />Karta okna vybrané, úzce zaměřený nástroje

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowTabSelectedTab` |
| Popředí (Text) | `Environment.ToolWindowTabSelectedActiveText` |
| Ohraničení | `Environment.ToolWindowTabSelectedBorder`<br />(Nastavte na stejnou barvu jako pozadí). |

**Karta okna nástroje vybrané, bez fokusu**  

![Okno Karta nezaostřená, vybrané nástroje](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br />Karta okna nástroje vybrané, bez fokusu

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowTabSelectedTab` |
| Popředí (Text) | `Environment.ToolWindowTabSelectedText` |
| Ohraničení | `Environment.ToolWindowTabSelectedBorder`<br />(Nastavte na stejnou barvu jako pozadí). |

**Okno Karta Nástroje pro pozadí: výchozí stav**

![Výchozí pozadí nástroj okno Karta](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br />Okno Karta Nástroje pro výchozí pozadí  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Přechodu zastaví nastavenou na hodnotu barvy v aplikaci Visual Studio 2013.) |
| Popředí (Text) | `Environment.ToolWindowTabText` |
| Ohraničení | `Environment.ToolWindowTabBorder` |

**Okno Karta Nástroje pro pozadí: ukazatel stavu**

![Okno Karta nástroje pozadí při přechodu](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br />Karta okna nástroje na pozadí při najetí myší

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Přechodu zastaví nastavenou na hodnotu barvy v aplikaci Visual Studio 2013.) |
| Popředí (Text) | `Environment.ToolWindowTabMouseOverText` |
| Ohraničení | `Environment.ToolWindowTabMouseOverBorder`<br />(Nastavte na stejnou barvu jako pozadí). |  

### <a name="auto-hide-tabs"></a>Automatického skrytí karty  

![Automaticky skrýt karty (červená značka)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 107_AutoHideRedline")automaticky skrýt karty (červená linka)

| Použití... | Nepoužívejte... |
| --- | --- |
| ... kdekoli vytváříte uživatelské rozhraní, které chcete najít nástroj automaticky skrývat okno karty. | ... pro všechny uživatelské rozhraní, které nechcete automaticky změněna prostředí má aktualizace motivu. |

**Automaticky skrýt karty: výchozí stav**  

![Karta výchozí automatické skrytí](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303 108_AutoHideTab")<br />Výchozí kartu automatického schovávání

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.AutoHideTabBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.AutoHideTabText` |
| Ohraničení | `Environment.AutoHideTabBorder` |

**Automaticky skrýt karty: ukazatel stavu**

![Automaticky Skrýt kartu při přechodu](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303 109_AutoHideTabHover")<br />Karta automatického schovávání při najetí myší  

| Prvek | Název tokenu: Category.color |
| --- | --- |
| Pozadí | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Ukončení přechodu pro tento token není používán s motivy uživatelského rozhraní.) |
| Popředí (Text) | `Environment.AutoHideTabMouseOverText` |
| Ohraničení | `Environment.AutoHideTabMouseOverBorder` |
