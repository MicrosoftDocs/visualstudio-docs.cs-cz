---
title: Přehled modelu objektů pásu karet
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25e34dcb38685a885ae0730740c25e1cb502e15c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910586"
---
# <a name="ribbon-object-model-overview"></a>Přehled modelu objektů pásu karet
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Poskytuje model silně typovaných objektů, které můžete použít k získání a nastavení vlastností ovládacích prvků pásu karet za běhu. Například můžete dynamicky naplnit ovládací prvky nabídky nebo zobrazení a skrytí ovládacích prvků kontextově. Také můžete přidat karty, skupiny a ovládací prvky na pás karet, ale pouze před načtení aplikací Office. Informace najdete v tématu [nastavit vlastnosti, které budou jen pro čtení](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Tento objektový model pásu karet se skládá převážně [pásu karet třídy](#RibbonClass), [pás karet událostí](#RibbonEvents), a [třídy ovládacích prvků pásu karet](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a> Třídě pásu karet  
 Když přidáte nový **pás karet (vizuální návrhář)** položky do projektu, Visual Studio přidá **pásu karet** třídy do projektu. **Pásu karet** třída dědí z <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> třídy.  
  
 Tato třída se zobrazí jako částečné třídy, která je rozdělená mezi soubor kódu pásu karet a soubor kódu Návrháře pásu karet.  
  
##  <a name="RibbonEvents"></a> Pás karet událostí  
 **Pásu karet** třída obsahuje následující tři události:  
  
|Událost|Popis|  
|-----------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Vyvolá se při načtení vlastního nastavení pásu karet aplikace Office. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> Obslužná rutina události je automaticky přidán do soubor kódu pásu karet. Pomocí této obslužné rutiny události pro spuštění vlastního kódu při načtení pásu karet.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Umožní vám mezipaměť imagí v přizpůsobení pásu karet při načtení pásu karet. Pokud píšete kód k ukládání do mezipaměti imagí pásu karet v této obslužné rutiny události můžete získat zisk snížený výkon. Další informace naleznete v tématu <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Vyvolá se při zavření instance pásu karet.|  
  
##  <a name="RibbonControlClasses"></a> Ovládací prvky pásu karet  
 <xref:Microsoft.Office.Tools.Ribbon> Obor názvů obsahuje typ pro každý ovládací prvek, který se zobrazí v **ovládací prvky Ribbon Office** skupinu **nástrojů**.  
  
 V následující tabulce jsou uvedeny typ pro každou `Ribbon` ovládacího prvku. Popis každého ovládacího prvku, naleznete v tématu [přehled pásu karet](../vsto/ribbon-overview.md).  
  
|Název ovládacího prvku|Název třídy|  
|------------------|----------------|  
|**Pole**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Tlačítko**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**Rozevírací seznam**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**Textové pole**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Galerie**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Skupiny**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Popisek**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Nabídka**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Oddělovač**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Karta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 <xref:Microsoft.Office.Tools.Ribbon> Obor názvů používá předpona "Pásu karet" pro tyto typy, aby se zabránilo kolize názvů s názvy tříd ovládacího prvku v <xref:System.Windows.Forms> oboru názvů.  
  
 Při přidání ovládacího prvku do Návrháře pásu karet Návrháře pásu karet deklaruje třídu pro tento ovládací prvek jako pole v souboru kódu Návrháře pásu karet.  
  
### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Běžné úlohy pomocí vlastností ovládacích prvků pásu karet  
 Každý `Ribbon` ovládací prvek obsahuje vlastnosti, které vám umožní provádět různé úlohy, jako je například přiřazení do ovládacího prvku popisek nebo skrytí a zobrazení ovládacích prvků.  
  
 V některých případech budou vlastnosti jen pro čtení po načtení pásu karet nebo poté, co ovládací prvek je přidán do dynamickou nabídku. Další informace najdete v tématu [nastavit vlastnosti, které budou jen pro čtení](#SettingReadOnlyProperties).  
  
 Následující tabulka popisuje některé úlohy, které můžete provést pomocí `Ribbon` vlastnosti ovládacího prvku.  
  
|Pro tuto úlohu:|postupujte takto:|  
|--------------------|--------------|  
|Skrytí nebo zobrazení ovládacího prvku.|Použijte vlastnost Visible.|  
|Povolí nebo zakáže ovládací prvek.|Použijte vlastnost Enabled.|  
|Nastavení velikosti ovládacího prvku.|Použijte vlastnost ControlSize.|  
|Získáte obrázek, který se zobrazí v ovládacím prvku.|Pomocí vlastnosti Image.|  
|Změna popisku ovládacího prvku.|Pomocí vlastnosti popisku.|  
|Přidání uživatelem definované datové do ovládacího prvku.|Použijte vlastnost Tag.|  
|Získat položky <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>, nebo<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> ovládací prvek.|Pomocí vlastnosti položky.|  
|Přidat položky, které chcete <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, nebo <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> ovládacího prvku.|Pomocí vlastnosti položky.|  
|Ovládací prvky <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Pomocí vlastnosti položky.<br /><br /> Přidání ovládacích prvků <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> po načtení pásu do aplikace sady Office, je nutné nastavit <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> vlastnost **true** před načtením pásu karet do aplikace sady Office. Informace najdete v tématu [nastavit vlastnosti, které budou jen pro čtení](#SettingReadOnlyProperties).|  
|Získat vybrané položky <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, nebo <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Pomocí vlastnosti SelectedItem. Pro <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, použijte <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> vlastnost.|  
|Získat skupiny <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Použití <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> vlastnost.|  
|Zadejte počet řádků a sloupců, které se zobrazují v <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Použití <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> a <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> vlastnosti.|  
  
##  <a name="SettingReadOnlyProperties"></a> Nastavit vlastnosti, které budou jen pro čtení  
 Některé vlastnosti lze nastavit pouze před na pásu karet. Chcete-li nastavit tyto vlastnosti třech místech:  
  
- V sadě Visual Studio **vlastnosti** okna.  
  
- V konstruktoru **pásu karet** třídy.  
  
- V `CreateRibbonExtensibilityObject` metodu `ThisAddin`, `ThisWorkbook`, nebo `ThisDocument` třídy vašeho projektu.  
  
  Dynamické nabídky poskytují některé výjimky. Můžete vytvořit nové ovládací prvky, nastavit jejich vlastnosti a pak je přidejte do dynamickou nabídku za běhu, i po načtení pásu karet, který obsahuje nabídku.  
  
  Kdykoli můžete nastavit vlastnosti ovládacích prvků, které přidáte do dynamickou nabídku.  
  
  Další informace najdete v tématu [vlastnosti, které budou jen pro čtení](#ReadOnlyProperties).  
  
### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Nastavit vlastnosti v konstruktoru na pásu karet  
 Můžete nastavit vlastnosti `Ribbon` ovládacího prvku v konstruktoru **pásu karet** třídy. Tento kód musí následovat po volání `InitializeComponent` metody. Následující příklad přidá nové tlačítko do skupiny, pokud je aktuální čas 17:00 tichomořského času (UTC-8) nebo novější.  
  
 Přidejte následující kód.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]  
  
 Ve Vizuálu C# projekty, které jste provedli upgrade z Visual Studio 2008, konstruktor se zobrazí v soubor kódu pásu karet.  
  
 V projektech Visual Basicu nebo ve Vizuálu C# projekty, které jste vytvořili v [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], konstruktor se zobrazí v souboru kódu Návrháře pásu karet. Tento soubor má název *YourRibbonItem*. Designer.cs nebo *YourRibbonItem*. Designer.vb. Pokud chcete zobrazit tento soubor v projektech Visual Basicu, musí nejprve klikněte **zobrazit všechny soubory** tlačítko v Průzkumníku řešení.  
  
### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Nastavit vlastnosti v CreateRibbonExtensibilityObject – metoda  
 Můžete nastavit vlastnosti `Ribbon` řídit při přepsání `CreateRibbonExtensibilityObject` metoda ve `ThisAddin`, `ThisWorkbook`, nebo `ThisDocument` třídy vašeho projektu. Další informace o `CreateRibbonExtensibilityObject` metodu, najdete v článku [přehled pásu karet](../vsto/ribbon-overview.md).  
  
 Následující příklad nastaví vlastnosti pásu karet `CreateRibbonExtensibilityObject` metodu `ThisWorkbook` třídy projektu sešitu aplikace Excel.  
  
 Přidejte následující kód.  
  
 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]  
  
###  <a name="ReadOnlyProperties"></a> Vlastnosti, které budou jen pro čtení  
 V následující tabulce jsou uvedeny vlastnosti, které lze nastavit pouze před na pásu karet.  
  
> [!NOTE]  
>  Kdykoli můžete nastavit vlastnosti ovládacích prvků na dynamické nabídky. Tato tabulka se nedá použít v tomto případě.  
  
|Vlastnost|Třída ovládacích prvků pásu karet|  
|--------------|--------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Má vlastnost ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**počet sloupců**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dynamické**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Globální**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Skupiny**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**maxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Jméno**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Pozice**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Počet řádků**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Karty**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Název**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Nastavit vlastnosti pro pásy karet, které se zobrazují v kontrol Outlooku  
 Pokaždé, když uživatel otevře je kontrola, ve kterém se zobrazí na pásu karet je vytvořena nová instance na pásu karet. Však můžete nastavit vlastnosti uvedené v předchozí tabulce pouze před vytvořením první instance na pásu karet. Po první je vytvořena instance, tyto vlastnosti budou jen pro čtení, protože první instance definuje souboru XML, který používá aplikace Outlook k načtení pásu karet.  
  
 Pokud máte podmíněnou logiku, která nastavuje některý z těchto vlastností na jinou hodnotu při vytváření dalších instancí na pásu karet, tento kód nebude mít žádný efekt.  
  
> [!NOTE]  
>  Ujistěte se, **název** je nastavena pro každý ovládací prvek, který přidáte do pásu karet aplikace Outlook. Pokud přidáte ovládací prvek do aplikace Outlook pásu karet za běhu, musíte tuto vlastnost nastavíte v kódu. Pokud přidáte ovládací prvek na pásu karet aplikace Outlook v době návrhu, je automaticky nastavit vlastnost Name.  
  
## <a name="ribbon-control-events"></a>Události ovládacích prvků pásu karet  
 Každá třída ovládací prvek obsahuje jeden nebo více událostí. Následující tabulka popisuje tyto události.  
  
|Událost|Popis|  
|-----------|-----------------|  
|Klikněte na...|Nastane, pokud dojde ke kliknutí na ovládací prvek.|  
|TextChanged.|Vyvolá se při změně textu textové pole nebo pole se seznamem.|  
|ItemsLoading|Nastane, pokud je kolekce položek ovládacího prvku požadoval Office. Office ukládá kolekce položek, dokud váš kód změní vlastnosti ovládacího prvku nebo volání <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> metody.|  
|ButtonClick|Nastane, pokud tlačítko v <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> nebo <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> dojde ke kliknutí na.|  
|SelectionChanged|Vyvolá se při výběru v <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> nebo <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> změny.|  
|DialogLauncherClick|Nastane, pokud dojde ke kliknutí na ikonu Spouštěče dialogového okna v pravém horním rohu skupiny.|  
  
 Obslužné rutiny událostí pro tyto události mají následující dva parametry.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*Odesílatel*|<xref:System.Object> , Která představuje ovládací prvek, který vyvolal událost.|  
|*e*|A <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> , která obsahuje <xref:Microsoft.Office.Core.IRibbonControl>. Jakákoli vlastnost, která není k dispozici v modelu objektů pásu karet poskytuje přístup k použití tohoto ovládacího prvku [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## <a name="see-also"></a>Viz také:  
 [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Návrhář pásu karet](../vsto/ribbon-designer.md)   
 [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Návod: Aktualizace ovládacích prvků na pásu karet za běhu](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Přizpůsobte pás karet pro aplikaci Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md)   
 [Postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Postupy: Export pásu karet z Návrháře pásu karet do kódu XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Postupy: Add-in zobrazení chyb uživatelského rozhraní](../vsto/how-to-show-add-in-user-interface-errors.md)  
 