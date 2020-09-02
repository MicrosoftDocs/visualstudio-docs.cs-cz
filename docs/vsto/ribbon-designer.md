---
title: Návrhář pásu karet
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e1c2941b0c088a832540fd3380c993fe2c380b44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985617"
---
# <a name="ribbon-designer"></a>Návrhář pásu karet
  Návrhář pásu karet je vizuální návrh plátna. Pomocí Návrháře pásu karet můžete do pásu karet aplikace systém Microsoft Office přidat vlastní karty, skupiny a ovládací prvky.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Chcete-li otevřít Návrháře pásu karet, přidejte položku **pásu karet (vizuální Návrhář)** do projektu. Pak můžete použít návrhové nástroje pro následující úkoly:

- [Návrh rozložení pásu karet](#DesigningRibbonLayout)

- [Zpracování událostí a nastavení vlastností ovládacího prvku](#HandleEventsSetProperties)

- [Přidání ovládacích prvků do zobrazení Backstage](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
> K dispozici jsou některé úkoly, které nelze provést pomocí Návrháře pásu karet. Další informace o těchto úlohách a o tom, jak je můžete provádět, najdete v tématu [Přehled pásu karet](../vsto/ribbon-overview.md).

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Přidat položku pásu karet (vizuální Návrhář) do projektu
 Chcete-li použít Návrhář pásu karet, přidejte do projektu novou položku **pásu karet (vizuální Návrhář)** . Další informace najdete v tématu [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md).

 Když přidáte novou položku **pásu karet (vizuální Návrhář)** , Visual Studio automaticky přidá do projektu následující soubory:

- Soubor kódu pásu karet. Tento soubor má název, který zadáte pro položku **pás karet (vizuální Návrhář)** v dialogovém okně **Přidat novou položku** . Přidejte kód pro zpracování událostí pásu karet do tohoto souboru.

- Soubor s kódem Návrháře pásu karet Tento soubor obsahuje kód vygenerovaný návrhářem pásu karet a neměl by být přímo upravován.

- Soubor prostředků. Tento soubor obsahuje hodnoty vlastností každého ovládacího prvku na pásu karet.

  Pokud již máte položku **pásu karet (vizuální Návrhář)** z jiného projektu, můžete ji znovu použít v aktuálním projektu pomocí dialogového okna **Přidat existující položku** .

## <a name="design-a-ribbon"></a><a name="DesigningRibbonLayout"></a> Návrh pásu karet
 Existují tři způsoby, jak otevřít Návrháře pásu karet:

- V **Průzkumník řešení**dvakrát klikněte na soubor kódu pásu karet.

- V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor kódu pásu karet a potom klikněte na tlačítko **Návrhář zobrazení**.

- V **Průzkumník řešení**vyberte soubor kódu pásu karet a v nabídce **zobrazení** klikněte na **Návrhář** .

  Návrhář pásu karet obsahuje výchozí kartu a skupinu. Výchozí kartu a skupinu můžete odebrat z Návrháře pásu karet. Pokud chcete výchozí skupinu odebrat, klikněte pravým tlačítkem na **Group1**a pak klikněte na **Odstranit**. Chcete-li odebrat výchozí kartu, klikněte pravým tlačítkem myši na prázdnou oblast návrhové plochy a poté klikněte na tlačítko **odebrat kartu pásu karet**.

  Do Návrháře pásu karet můžete také přidat vlastní karty, skupiny a ovládací prvky. Tyto ovládací prvky můžete najít v **sadě nástrojů**ve skupině **ovládací prvky pásu karet Office** . Existují tři způsoby, jak přidat ovládací prvky ze skupiny **ovládací prvky pásu karet Office** do Návrháře pásu karet:

- Přetáhněte ovládací prvek do příslušné oblasti v Návrháři pásu karet.

- Klikněte na ovládací prvek a potom klikněte na příslušnou oblast v Návrháři pásu karet.

- Vyberte příslušnou oblast v návrháři a pak dvakrát klikněte na ovládací prvek v **sadě nástrojů**.

### <a name="ribbon-design-workflow"></a>Pracovní postup návrhu pásu karet
 Pomocí těchto základních kroků můžete navrhnout rozložení pásu karet:

1. [Přidejte na pás karet vlastní kartu](#AddTabToRibbon).

2. [Přidejte skupiny na kartu](#AddGroupsToTab).

3. [Přidejte ovládací prvky do skupin](#AddControlsToGroups).

   Ovládací prvky lze přetáhnout pouze na skupiny; ovládací prvek nelze přetáhnout přímo na kartu nebo na pás karet. Skupiny je možné přetáhnout pouze na karty. skupinu nelze přetáhnout přímo na pás karet.

   Uspořádejte ovládací prvky jejich přetažením na správné pozice. Vlastnosti ovládacího prvku lze nastavit pomocí okna **vlastnosti** .

   Ovládací prvky nelze přetáhnout z jedné karty na druhou na pásu karet. Pokud chcete ovládací prvek přesunout na jinou kartu, je nutné použít příkaz **Vyjmout** pro odebrání ovládacího prvku z jedné karty a pak ovládací prvek vložit na jinou kartu. Pokud tento ovládací prvek vyjmete a vložíte, obslužná rutina události přestane fungovat. Můžete znovu připojit obslužnou rutinu události v okně **vlastnosti** . Další informace najdete v tématu [okno Vlastnosti](../ide/reference/properties-window.md).

### <a name="add-custom-tabs-to-the-ribbon"></a><a name="AddTabToRibbon"></a> Přidání vlastních karet na pás karet
 Existují tři způsoby, jak přidat vlastní kartu na pás karet:

- Přidejte kartu ze **sady nástrojů**.

- Klikněte pravým tlačítkem myši na Návrhář pásu karet a potom klikněte na tlačítko **Přidat kartu pásu karet**.

- Otevřete **Editor kolekce karet**a klikněte na tlačítko **Přidat**.

   Chcete-li otevřít **Editor kolekce karet**, v okně **vlastnosti** vyberte vlastnost **karty** a potom klikněte na tlačítko se třemi tečkami ![ASP.NET v nástroji Mobile Designer elipsa](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer").

  Po přidání karty můžete přidat skupiny, které obsahují ovládací prvky.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Odebrání vlastních karet z pásu karet
 Existují tři způsoby, jak z pásu karet odebrat vlastní kartu:

- Klikněte pravým tlačítkem myši na návrháře a potom klikněte na tlačítko **odebrat kartu pásu karet**.

- V podokně **příkazy** v okně **vlastnosti** klikněte na tlačítko **odebrat kartu pásu karet**.

- Otevřete **Editor kolekce karet**, vyberte kartu a klikněte na tlačítko **Odebrat**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Změna pozice karty na pásu karet
 Můžete změnit pořadí vlastních karet na pásu karet. Vlastní karty můžete také umístit před nebo za integrovanou kartu na pásu karet. Další informace najdete v tématu [Postup: Změna pozice karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Přizpůsobení vestavěných karet na pásu karet
 Integrovaná karta je karta, která již je na pásu karet aplikace systém Microsoft Office. Karta **data** je například Integrovaná karta v aplikaci Excel.

 Můžete přidat skupiny a ovládací prvky na integrovanou kartu. Ve výchozím nastavení se vlastní skupina zobrazí jako poslední skupina na předdefinované kartě, ale můžete ji přesunout před nebo po libovolné předdefinované skupiny na kartě.

 Předdefinované skupiny nemůžete odstranit.

 Podrobnosti o tom, jak přizpůsobit integrovanou kartu, najdete v tématu [How to: Customize a vestavěná karta](../vsto/how-to-customize-a-built-in-tab.md).

### <a name="add-groups-to-a-tab"></a><a name="AddGroupsToTab"></a> Přidání skupin na kartu
 Skupiny logicky organizují ovládací prvky na pásu karet. Přidejte skupiny do karet. Přidejte všechny ostatní ovládací prvky do skupiny.

### <a name="add-controls-to-groups"></a><a name="AddControlsToGroups"></a> Přidat ovládací prvky do skupin
 Přidejte do skupiny jeden nebo více ovládacích prvků. V následující tabulce jsou popsány jednotlivé ovládací prvky.

|Řízení|Popis|
|-------------|-----------------|
|**Box**|Kontejner, který organizuje ovládací prvky ve skupině. Do pole můžete přidat libovolný ovládací prvek s výjimkou oddělovače, skupiny nebo karty. Pole může být vodorovné nebo svislé.|
|**Tlačítko**|Tlačítko, které spustí akci. Tlačítko můžete přidat do skupiny, skupiny tlačítek, rozevíracího seznamu, galerie, nabídky nebo rozděleného tlačítka.|
|**ButtonGroup**|Skupina, která obsahuje jeden nebo více tlačítek, přepínací tlačítka, nabídky, rozdělená tlačítka a galerie. Skupinu tlačítek můžete přidat do skupiny nebo nabídky.|
|**Zaškrtávací políčko**|Pole, které je vybráno nebo vymazáno, chcete-li zapnout nebo vypnout možnost.|
|**ComboBox**|Pole pro úpravy s připojeným seznamem. Uživatelé můžou buď zadat nebo vybrat jejich výběr. V poli se zobrazí aktuální výběr. Použijte <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> vlastnost k přidání a odebrání položek za běhu před nebo po načtení pásu karet do aplikace Office.|
|**DropDown**|Seznam položek, které může uživatel vybrat. Uživatel nemůže v rozevíracím seznamu zadat novou položku.<br /><br /> K <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> Přidání položek do seznamu použijte vlastnost. Můžete přidávat a odebírat položky v době běhu.<br /><br /> K <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> Přidání tlačítek do seznamu použijte vlastnost. Po načtení pásu karet do aplikace Office však nelze přidávat a odebírat tlačítka v době běhu.|
|**EditBox**|Pole, ve kterém může uživatel zadat text.|
|**Galerie**|Nabídka, která představuje pole nebo mřížku vizuálních voleb, ze kterých mohou uživatelé vybírat Můžete ovládat rozložení výběrů v nabídce. Pomocí <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> vlastností a zadejte počet řádků a sloupců, které zobrazí položky a tlačítka Galerie.|
|**Popisek**|Text, který lze použít k identifikaci ovládacích prvků na pásu karet.|
|**Nabídka**|Rozevírací seznam, který může obsahovat některý z následujících ovládacích prvků:<br /><br /> – Tlačítko<br />– Zaškrtávací políčko<br />– Galerie<br />– Nabídka<br />-Split – tlačítko<br />– Přepínací tlačítko<br />– Oddělovač<br /><br /> Chcete-li přidat ovládací prvek do nabídky v Návrháři pásu karet, klikněte na šipku dolů v nabídce a zpřístupněte plochu návrhu nabídky. Pak můžete přetáhnout ovládací prvky pásu karet z **panelu nástrojů** do nabídky. Chcete-li uspořádat ovládací prvky, přetáhněte je na požadované pozice.<br /><br /> Chcete-li přidat ovládací prvky na kartu <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> po načtení pásu karet do aplikace sady Office, je nutné <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> před načtením pásu karet nastavit vlastnost na **hodnotu true** . Informace o tom, jak to provést, najdete v tématu [Přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md).|
|**Oddělovač**|Tenký pruh, který se používá k oddělení položek v seznamu. Po přidání do skupiny je pruh svisle. Po přidání do nabídky je pruh vodorovně.|
|**SplitButton**|Tlačítko s připojenou nabídkou Tlačítko rozdělení může obsahovat kterýkoli z následujících ovládacích prvků:<br /><br /> – Tlačítko<br />– Zaškrtávací políčko<br />– Galerie<br />– Nabídka<br />-Split – tlačítko<br />– Přepínací tlačítko<br />– Oddělovač<br /><br /> Podobně jako v nabídce má tlačítko rozdělení svoji vlastní návrhovou plochu. Nicméně na rozdíl od nabídky můžete pouze aktualizovat položky v rozděleném tlačítku před načtením pásu karet do aplikace sady Office. Informace o tom, jak aktualizovat položky v rozděleném tlačítku, najdete v tématu [Přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md).|
|**ToggleButton**|Tlačítko, které se zobrazí jako stisknuté nebo nestisknuté.|

## <a name="handle-events-and-setting-properties"></a><a name="HandleEventsSetProperties"></a> Zpracování událostí a nastavení vlastností
 Návrhář pásu karet umožňuje nastavit vlastnosti ovládacího prvku v době návrhu pomocí okna **vlastnosti** . Kromě toho pás karet zveřejňuje objektový model silného typu, který můžete použít k získání a nastavení vlastností ovládacích prvků pásu karet v době běhu.

 Poklikáním na libovolný ovládací prvek v Návrháři můžete otevřít obslužnou rutinu události pro výchozí událost ovládacího prvku. Obslužné rutiny událostí pro všechny ostatní události ovládacích prvků lze vytvořit pomocí okna **vlastnosti** .

 Události a vlastnosti pásu karet jsou umístěné v <xref:Microsoft.Office.Tools.Ribbon> oboru názvů. Položka **pás karet (vizuální Návrhář)** automaticky přidá odkaz na toto sestavení v projektu a vloží příslušný příkaz **using** nebo **Imports** v horní části souboru kódu pásu karet.

 Informace o zpracování událostí pásu karet a nastavení vlastností ovládacích prvků pásu karet za běhu naleznete v tématu [Přehled objektového modelu pásu karet](../vsto/ribbon-object-model-overview.md).

## <a name="customize-backstage-view"></a><a name="CustomizingMicrosoftOfficeButton"></a> Přizpůsobení zobrazení Backstage
 Pomocí Návrháře pásu karet můžete přidat ovládací prvky do nabídky, která se otevře po kliknutí na kartu **soubor** . Tato nabídka se nazývá zobrazení Backstage.

 Ovládací prvky nelze umístit před nebo za předdefinované ovládací prvky pomocí Návrháře pásu karet. Předdefinovaný ovládací prvek je ovládací prvek, který se již zobrazuje v zobrazení Backstage. Chcete-li umístit ovládací prvky před nebo po předdefinovaných ovládacích prvcích, je nutné použít pás karet XML. Další informace o **pásu karet (XML)** najdete v tématu [XML pásu karet](../vsto/ribbon-xml.md). Další informace o přizpůsobení zobrazení Backstage najdete v tématu [Úvod do zobrazení Backstage office 2010 pro vývojáře](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) a [přizpůsobení zobrazení Backstage Office 2010 pro vývojáře](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Informace o tom, jak přidat ovládací prvky do zobrazení Backstage, naleznete v tématu [How to: Add Controls to the Backstage View](../vsto/how-to-add-controls-to-the-backstage-view.md).

## <a name="accessibility-in-the-ribbon-designer"></a><a name="Accessibility"></a> Usnadnění v Návrháři pásu karet
 Pomocí klávesových zkratek lze přesouvat ovládací prvky v Návrháři pásu karet. Některé klávesové zkratky platí pro všechny ovládací prvky a některé se vztahují pouze na ovládací prvky, které mají nabídky.

 Klávesové zkratky, které se vztahují na všechny ovládací prvky, jsou uvedeny v následující tabulce.

|Akce|Klávesová zkratka|
|------------|-----------------------|
|Přesuňte ovládací prvek před předchozí ovládací prvek v seznamu.|**CTRL** + **Nahoru**<br /><br /> **CTRL** + **Vlevo**|
|Přesuňte ovládací prvek za další ovládací prvek v seznamu.|**CTRL** + **Dolů**<br /><br /> **CTRL** + **Vpravo**|
|Přesune výběr z jednoho ovládacího prvku do druhého ve stejné skupině. V případě rozevíracího panelu se pohybujte mezi nadřazeným ovládacím prvkem a ovládacími prvky v rozevíracím panelu.|**Nahoru**<br /><br /> **Dolů**|
|Iterujte před všemi ovládacími prvky.|**Karta**|
|Iterujte zpět všemi ovládacími prvky.|**Posun** + **Karta**|
|Odstraní vybraný ovládací prvek nebo sadu ovládacích prvků.|**Odstranit**|
|Zkopírujte vybrané ovládací prvky.|**CTRL** + Jazyk **C**|
|Vyjme vybrané ovládací prvky.|**CTRL** + **X**|
|Vloží ovládací prvky ze schránky.|**CTRL** + **Verze V**|
|Vyberte **sadu nástrojů**.|**CTRL** + **ALT** + **X**|
|Vyberte nadřazenou komponentu.|**Esc**|

 Klávesové zkratky, které se vztahují pouze na nabídku systém Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> a <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> jsou uvedeny v následující tabulce.

|Akce|Klávesová zkratka|
|------------|-----------------------|
|Vyberte nadřazený ovládací prvek, pokud je rozevírací panel otevřený a v rozevíracím panelu je vybrán ovládací prvek.|**Zbývá**|
|Pokud je rozevírací panel otevřený a je vybraný nadřazený ovládací prvek, zavřete rozevírací panel.|**Zbývá**|
|Otevřete rozevírací panel.|**Kliknutím**|
|Vyberte první ovládací prvek na rozevíracím panelu, pokud je rozbalovací panel otevřený.|**Kliknutím**|
|Zavřete rozevírací panel.|**Esc**|

## <a name="see-also"></a>Viz také

- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Pás karet – XML](../vsto/ribbon-xml.md)
- [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Postupy: Export pásu karet z Návrháře pásu karet do XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
