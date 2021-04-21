---
title: Přehled modelu objektů pásu karet
description: Přečtěte si, jak Visual Studio Tools for Office modul runtime zveřejňuje objektový model silného typu, který můžete použít k získání a nastavení vlastností ovládacích prvků pásu karet za běhu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f053e87f8cdfd2bdf87bbdf4b7d115f6d9bbec26
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823987"
---
# <a name="ribbon-object-model-overview"></a>Přehled modelu objektů pásu karet
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Zpřístupňuje model objektu silného typu, který můžete použít k získání a nastavení vlastností ovládacích prvků pásu karet za běhu. Můžete například dynamicky naplnit ovládací prvky nabídky nebo zobrazit a skrýt ovládací prvky kontextové. Na pás karet můžete také přidat karty, skupiny a ovládací prvky, ale pouze před tím, než se pás karet načte do aplikace Office. Informace najdete v tématu [Nastavení vlastností, které jsou jen pro čtení](#SettingReadOnlyProperties).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Tento objektový model pásu karet se skládá hlavně z [třídy pásu](#RibbonClass)karet, [událostí pásu karet](#RibbonEvents)a [tříd ovládacích prvků pásu karet](#RibbonControlClasses).

## <a name="ribbon-class"></a><a name="RibbonClass"></a> Třída pásu karet
 Když přidáte novou položku **pásu karet (vizuální Návrhář)** do projektu, Visual Studio přidá do projektu třídu **pásu karet** . Třída **pásu karet** dědí z <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> třídy.

 Tato třída se zobrazí jako částečná třída, která je rozdělena mezi soubor kódu pásu karet a soubor kódu Návrháře pásu karet.

## <a name="ribbon-events"></a><a name="RibbonEvents"></a> Události pásu karet
 Třída **pásu karet** obsahuje následující tři události:

|Událost|Description|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Vyvolá se, když aplikace Office načte přizpůsobení pásu karet. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>Obslužná rutina události je automaticky přidána do souboru kódu pásu karet. Tuto obslužnou rutinu události použijte ke spuštění vlastního kódu při načtení pásu karet.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Umožňuje ukládat obrázky do mezipaměti při vlastním nastavení pásu karet. Pokud píšete kód pro ukládání imagí pásu karet do mezipaměti v této obslužné rutině, můžete získat mírné zvýšení výkonu. Další informace naleznete v tématu <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Vyvolá se při zavření instance pásu karet.|

## <a name="ribbon-controls"></a><a name="RibbonControlClasses"></a> Ovládací prvky pásu karet
 <xref:Microsoft.Office.Tools.Ribbon>Obor názvů obsahuje typ pro každý ovládací prvek, který se zobrazí ve skupině **ovládací prvky pásu karet Office** v **sadě nástrojů**.

 V následující tabulce je uveden typ každého `Ribbon` ovládacího prvku. Popis jednotlivých ovládacích prvků naleznete v tématu [Přehled pásu karet](../vsto/ribbon-overview.md).

|Název ovládacího prvku|Název třídy|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Tlačítko**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**Rozevírací**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Galerie**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Skupina**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Popisek**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Nabídka**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Oddělovač**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 <xref:Microsoft.Office.Tools.Ribbon>Obor názvů používá předponu na pásu karet pro tyto typy, aby se předešlo kolizi názvů s názvy tříd ovládacích prvků v <xref:System.Windows.Forms> oboru názvů.

 Když přidáte ovládací prvek do Návrháře pásu karet, Návrhář pásu karet deklaruje třídu pro tento ovládací prvek jako pole v souboru kódu Návrháře pásu karet.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Běžné úlohy s využitím vlastností ovládacích prvků pásu karet
 Každý `Ribbon` ovládací prvek obsahuje vlastnosti, které lze použít k provádění různých úloh, jako je například přiřazení popisku k ovládacímu prvku nebo skrytí a zobrazení ovládacích prvků.

 V některých případech se vlastnosti po načtení pásu karet nebo po přidání ovládacího prvku do dynamické nabídky stanou jen pro čtení. Další informace najdete v tématu [Nastavení vlastností, které jsou jen pro čtení](#SettingReadOnlyProperties).

 Následující tabulka popisuje některé úlohy, které můžete provádět pomocí `Ribbon` vlastností ovládacích prvků.

|Pro tuto úlohu:|Postupujte takto:|
|--------------------|--------------|
|Umožňuje skrýt nebo zobrazit ovládací prvek.|Použijte vlastnost Visible.|
|Povolí nebo zakáže ovládací prvek.|Použijte vlastnost Enabled.|
|Nastavte velikost ovládacího prvku.|Použijte vlastnost ControlSize.|
|Získá obrázek, který se zobrazí na ovládacím prvku.|Použijte vlastnost image.|
|Změní popisek ovládacího prvku.|Použijte vlastnost popisek.|
|Přidejte data definovaná uživatelem do ovládacího prvku.|Použijte vlastnost značky.|
|Získat položky v,, <xref:Microsoft.Office.Tools.Ribbon.RibbonBox> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> nebo<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> nad.|Použijte vlastnost Items.|
|Přidejte položky do <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> ovládacího prvku, nebo <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Použijte vlastnost Items.|
|Přidejte ovládací prvky do <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> .|Použijte vlastnost Items.<br /><br /> Chcete-li přidat ovládací prvky na kartu <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> po načtení pásu karet do aplikace sady Office, je nutné nastavit <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> vlastnost na **hodnotu true** , aby byl pás karet načten do aplikace Office. Informace najdete v tématu [Nastavení vlastností, které jsou jen pro čtení](#SettingReadOnlyProperties).|
|Získá vybranou položku a <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> ,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, nebo <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Použijte vlastnost SelectedItem. V případě <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> použijte <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> vlastnost.|
|Získá skupiny na <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> .|Použijte <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> vlastnost.|
|Zadejte počet řádků a sloupců, které se zobrazí v <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Použijte <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> vlastnosti a <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> .|

## <a name="set-properties-that-become-read-only"></a><a name="SettingReadOnlyProperties"></a> Nastavit vlastnosti, které se stanou jen pro čtení
 Některé vlastnosti lze nastavit pouze před tím, než se pás karet načte. K dispozici jsou tři místa pro nastavení těchto vlastností:

- V okně **vlastnosti** sady Visual Studio.

- V konstruktoru třídy **pásu karet** .

- V `CreateRibbonExtensibilityObject` metodě `ThisAddin` třídy, nebo v `ThisWorkbook` `ThisDocument` projektu.

  Dynamické nabídky poskytují určité výjimky. Můžete vytvořit nové ovládací prvky, nastavit jejich vlastnosti a pak je přidat do dynamické nabídky za běhu, a to i po načtení pásu karet obsahujícího nabídku.

  Vlastnosti ovládacích prvků, které lze přidat do dynamické nabídky, lze nastavit kdykoli.

  Další informace najdete v tématu [vlastnosti, které jsou jen pro čtení](#ReadOnlyProperties).

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Nastavení vlastností v konstruktoru pásu karet
 Můžete nastavit vlastnosti `Ribbon` ovládacího prvku v konstruktoru třídy **pásu karet** . Tento kód musí být uveden po volání `InitializeComponent` metody. Následující příklad přidá nové tlačítko do skupiny, pokud je aktuální čas 17:00 tichomořského času (UTC-8) nebo vyšší.

 Přidejte následující kód.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb" id="Snippet1":::

 V projektech v jazyce Visual C#, které jste upgradovali ze sady Visual Studio 2008, se konstruktor zobrazí v souboru kódu pásu karet.

 V Visual Basic projekty nebo v projektech Visual C#, které jste vytvořili v [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , se konstruktor zobrazí v souboru s kódem Návrháře pásu karet. Tento soubor má název *YourRibbonItem*. Designer. cs nebo *YourRibbonItem*. Designer. vb. Chcete-li zobrazit tento soubor v Visual Basic projekty, musíte nejprve kliknout na tlačítko **Zobrazit všechny soubory** v Průzkumník řešení.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Nastavení vlastností v metodě CreateRibbonExtensibilityObject
 Můžete nastavit vlastnosti `Ribbon` ovládacího prvku, pokud přepíšete `CreateRibbonExtensibilityObject` metodu do `ThisAddin` třídy, nebo v `ThisWorkbook` `ThisDocument` projektu. Další informace o této `CreateRibbonExtensibilityObject` metodě najdete v tématu [Přehled pásu karet](../vsto/ribbon-overview.md).

 Následující příklad nastaví vlastnosti pásu karet v `CreateRibbonExtensibilityObject` metodě `ThisWorkbook` třídy projektu excelového sešitu.

 Přidejte následující kód.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs" id="Snippet2":::

### <a name="properties-that-become-read-only"></a><a name="ReadOnlyProperties"></a> Vlastnosti, které se stanou jen pro čtení
 V následující tabulce jsou uvedeny vlastnosti, které lze nastavit pouze před tím, než se pás karet načte.

> [!NOTE]
> Vlastnosti ovládacích prvků můžete v případě dynamických nabídek kdykoli nastavit. Tato tabulka se v takovém případě nepoužívá.

|Vlastnost|Třída ovládacích prvků pásu karet|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Sloupců**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**dynamicky**,|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Globální**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Skupiny**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Název**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Řádků**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Karty**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Název**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Nastavení vlastností pro pásy karet, které se zobrazí v okně kontroly aplikace Outlook
 Nová instance pásu karet se vytvoří pokaždé, když uživatel otevře kontrolora, ve kterém se pás karet zobrazuje. Vlastnosti uvedené v tabulce výše však můžete nastavit pouze před vytvořením první instance pásu karet. Po vytvoření první instance se tyto vlastnosti stanou jen pro čtení, protože první instance definuje soubor XML, který aplikace Outlook používá k načtení pásu karet.

 Pokud máte podmíněnou logiku, která nastavuje některé z těchto vlastností na jinou hodnotu při vytváření jiných instancí pásu karet, nebude mít tento kód žádný vliv.

> [!NOTE]
> Zajistěte, aby byla vlastnost **Name** nastavena pro každý ovládací prvek, který přidáte na pás karet aplikace Outlook. Pokud přidáte ovládací prvek na pás karet Outlooku za běhu, musíte tuto vlastnost nastavit ve svém kódu. Pokud přidáte ovládací prvek na pás karet Outlook v době návrhu, vlastnost název se nastaví automaticky.

## <a name="ribbon-control-events"></a>Události ovládacího prvku pásu karet
 Každá třída ovládacího prvku obsahuje jednu nebo více událostí. Tyto události jsou popsány v následující tabulce.

|Událost|Description|
|-----------|-----------------|
|Klikněte na|Vyvolá se při kliknutí na ovládací prvek.|
|TextChanged|Vyvolá se v případě, že dojde ke změně textu pole pro úpravy nebo pole se seznamem.|
|ItemsLoading|Vyvolá se v případě, že sada Office požaduje kolekci položek ovládacího prvku. Sada Office ukládá kolekce položek do mezipaměti, dokud váš kód nezmění vlastnosti ovládacího prvku nebo zavoláte <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> metodu.|
|ButtonClick|Vyvolá se při kliknutí na tlačítko <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> nebo <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> .|
|SelectionChanged|Vyvolá se při <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> změně výběru nebo <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|
|DialogLauncherClick|Vyvolá se při kliknutí na ikonu spouštěče dialogového okna v pravém dolním rohu skupiny.|

 Obslužné rutiny událostí pro tyto události mají následující dva parametry.

|Parametr|Popis|
|---------------|-----------------|
|*použil*|<xref:System.Object>Který představuje ovládací prvek, který vyvolal událost.|
|*cerebrální*|Obsahující <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> <xref:Microsoft.Office.Core.IRibbonControl> . Tento ovládací prvek použijte pro přístup k libovolné vlastnosti, která není k dispozici v modelu objektu pásu karet, který poskytuje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|

## <a name="see-also"></a>Viz také
- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Návod: aktualizace ovládacích prvků na pásu karet v době běhu](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Přizpůsobení pásu karet pro Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Postupy: Export pásu karet z Návrháře pásu karet do XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Postupy: zobrazení chyb uživatelského rozhraní doplňku](../vsto/how-to-show-add-in-user-interface-errors.md)
