---
title: Návrhář pásu karet
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b85347b6bda0d42f7350d145baf2c824aa92a71c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820616"
---
# <a name="ribbon-designer"></a>Návrhář pásu karet
  Návrhář pásu karet je vizuální návrhové plátno. Chcete-li přidat vlastní karty, skupiny a ovládací prvky na pásu karet aplikace Microsoft Office pomocí Návrháře pásu karet.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Chcete-li otevřít Návrhář pásu karet, přidejte **pás karet (vizuální návrhář)** položky do projektu. Pak můžete použít nástroje návrhu pro následující úlohy:  
  
-   [Návrh rozložení pásu karet](#DesigningRibbonLayout)  
  
-   [Zpracování událostí a nastavit vlastnosti ovládacího prvku](#HandleEventsSetProperties)  
  
-   [Přidání ovládacích prvků do zobrazení Backstage](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  Zde jsou některé úkoly, které nelze provést pomocí Návrháře pásu karet. Další informace o těchto úlohách a způsob jejich provedení, najdete v části [přehled pásu karet](../vsto/ribbon-overview.md).  
  
 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak mohu: použití Návrháře pásu karet k přizpůsobení pásu karet v aplikaci Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Přidání položky pásu karet (vizuální návrhář) do projektu  
 Pokud chcete použít Návrhář pásu karet, přidejte novou **pás karet (vizuální návrhář)** položky do projektu. Další informace najdete v tématu [postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
 Když přidáte nový **pás karet (vizuální návrhář)** položky, sady Visual Studio automaticky přidá následující soubory do projektu:  
  
- Soubor kódu pásu karet. Tento soubor má název, který zadáte pro **pás karet (vizuální návrhář)** položky v **přidat novou položku** dialogové okno. Přidejte kód pro zpracování události pásu karet do tohoto souboru.  
  
- Soubor kódu Návrháře pásu karet. Tento soubor obsahuje kód generovaný návrhářem pásu karet a neměl by být upravován přímo.  
  
- Soubor prostředků. Tento soubor obsahuje hodnoty vlastností každého ovládacího prvku na pásu karet.  
  
  Pokud už máte **pás karet (vizuální návrhář)** položky z jiného projektu, jej můžete znovu použít v aktuálním projektu pomocí **přidat existující položku** dialogové okno.  
  
##  <a name="DesigningRibbonLayout"></a> Návrh pásu karet  
 Chcete-li otevřít Návrhář pásu karet třemi způsoby:  
  
- V **Průzkumníka řešení**, poklikejte na soubor kódu pásu karet.  
  
- V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor kódu pásu karet a potom klikněte na tlačítko **Návrhář zobrazení**.  
  
- V **Průzkumníka řešení**, vyberte soubor kódu pásu karet a potom klikněte na tlačítko **návrháře** na **zobrazení** nabídky.  
  
  Návrhář pásu karet obsahuje výchozí kartu a skupinu. Výchozí kartu a skupinu lze odebrat z Návrháře pásu karet. Chcete-li odebrat výchozí skupiny, klikněte pravým tlačítkem na **Group1**a potom klikněte na tlačítko **odstranit**. Chcete-li odebrat výchozí kartu, klikněte pravým tlačítkem na prázdnou oblast návrhové plochy a pak klikněte na tlačítko **odebrat kartu pásu karet**.  
  
  Můžete také přidat vlastní karty, skupiny a ovládací prvky do Návrháře pásu karet. Můžete najít tyto ovládací prvky v **nástrojů**v **ovládací prvky Ribbon Office** skupiny. Existují tři způsoby, jak přidat ovládací prvky z **ovládací prvky Ribbon Office** do Návrháře pásu karet:  
  
- Přetáhněte ovládací prvek pro příslušnou oblast v Návrháři pásu karet.  
  
- Klepněte na ovládací prvek a potom klikněte na příslušnou oblast v Návrháři pásu karet.  
  
- Vyberte příslušnou oblast v návrháři a potom dvakrát klikněte na panel ovládacího prvku v **nástrojů**.  
  
### <a name="ribbon-design-workflow"></a>Pracovní postup návrhu pásu karet  
 Postupujte podle těchto základních kroků pro návrh rozložení pásu karet:  
  
1. [Přidat vlastní kartu na pás karet](#AddTabToRibbon).  
  
2. [Přidání skupin na kartu](#AddGroupsToTab).  
  
3. [Přidání ovládacích prvků do skupin](#AddControlsToGroups).  
  
   Ovládací prvky lze vyřadit pouze na skupiny. ovládací prvek nelze přetáhnout přímo na kartu nebo na pásu karet. Skupiny mohou vyřadit pouze na karty; skupinu nelze přetáhnout přímo na pás karet.  
  
   Uspořádejte ovládací prvky jejich přetažením do správné polohy. Můžete nastavit vlastnosti ovládacího prvku pomocí **vlastnosti** okna.  
  
   Ovládací prvky nelze přetáhnout z jedné karty na jiný na pásu karet. Pokud chcete přesunout na jinou kartu ovládacího prvku, je nutné použít **Vyjmout** příkaz odebrat ovládací prvek z jedné karty a vložte ovládací prvek na jinou kartu. Pokud vyjmete ovládací prvek a vložíte jej, obslužná rutina události přestane fungovat. Obslužné rutiny události v se můžete připojit **vlastnosti** okna. Další informace najdete v tématu [okno vlastností](/visualstudio/ide/reference/properties-window).  
  
###  <a name="AddTabToRibbon"></a> Přidat vlastní karty na pás karet  
 Existují tři způsoby, jak přidat vlastní kartu na pás karet:  
  
- Přidejte kartu z **nástrojů**.  
  
- Klikněte pravým tlačítkem na Návrhář pásu karet a potom klikněte na tlačítko **přidat kartu pásu karet**.  
  
- Otevřít **kartu Editor kolekce**a potom klikněte na tlačítko **přidat**.  
  
   Otevřete **kartu Editor kolekce**v **vlastnosti** okna, vyberte **karty** vlastnost a potom klikněte na tlačítko se třemi tečkami ![technologie ASP.NET Mobile Návrháře Elipsa](../sharepoint/media/mwellipsis.gif "ASP.NET – Návrhář mobilních řešení Elipsa").  
  
  Po přidání karty můžete přidat skupiny obsahující ovládací prvky.  
  
#### <a name="remove-custom-tabs-from-the-ribbon"></a>Odebrat vlastní karty na pásu karet  
 Existují tři způsoby, jak odstranit vlastní kartu na pásu karet:  
  
-   Pravým tlačítkem myši klepněte Návrhář a potom klikněte na **odebrat kartu pásu karet**.  
  
-   V **příkazy** podokně **vlastnosti** okna, klikněte na tlačítko **odebrat kartu pásu karet**.  
  
-   Otevřít **kartu Editor kolekce**, vyberte kartu a potom klikněte na tlačítko **odebrat**.  
  
#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Změna umístění karty na pásu karet  
 Můžete změnit pořadí vlastních karet na pásu karet. Vlastní karty lze také umístit před nebo za integrovanou kartu na pásu karet. Další informace najdete v tématu [postupy: Změna pozice karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Přizpůsobení předdefinovaných karet na pásu karet  
 Vestavěná karta je karta, který je již na pásu karet aplikace Microsoft Office. Například **Data** karta je integrovanou kartou v aplikaci Excel.  
  
 Můžete přidat skupiny a ovládací prvky k předdefinované kartě. Ve výchozím nastavení se přizpůsobená skupina zobrazuje jako poslední skupina na integrované kartě, ale můžete jej přesunout před nebo za libovolnou integrovanou skupinu na kartě.  
  
 Předdefinované skupiny nelze odebrat.  
  
 Podrobnosti o tom, jak přizpůsobit předdefinovanou kartu, najdete v článku [postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md).  
  
###  <a name="AddGroupsToTab"></a> Přidání skupin na kartu  
 Skupiny logicky uspořádávají ovládací prvky na pásu karet. Přidejte skupiny do záložek. Přidejte všechny ostatní ovládací prvky do skupiny.  
  
###  <a name="AddControlsToGroups"></a> Přidání ovládacích prvků do skupin  
 Přidejte jeden nebo více ovládacích prvků do skupiny. Následující tabulka popisuje každý ovládací prvek.  
  
|Ovládací prvek|Popis|  
|-------------|-----------------|  
|**Pole**|Kontejner, který slouží k uspořádání ovládacích prvků ve skupině. Můžete přidat libovolný ovládací prvek k poli s výjimkou oddělovače, skupiny nebo kartu. Pole může být vodorovné nebo svislé.|  
|**Tlačítko**|Tlačítko, které spouští akci. Tlačítko můžete přidat do skupiny, skupiny přepínačů, rozevíracího seznamu, galerie, nabídky nebo tlačítko rozdělení.|  
|**ButtonGroup**|Skupina, která obsahuje jeden nebo více tlačítek, přepínacích tlačítek, nabídek, tlačítek rozdělení a galerií. Můžete přidat skupinu tlačítek ke skupině nebo nabídce.|  
|**CheckBox**|Pole, které zaškrtnutím nebo zrušením zaškrtnutí Zapne nebo vypne možnost.|  
|**ComboBox**|Pole úprav s připojeným seznamem. Uživatelům můžete zadat nebo vybírat své volby. V poli se zobrazí aktuální výběr. Použití <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> vlastnost přidávat a odebírat položky v době běhu, před nebo po načtení pásu do aplikace sady Office.|  
|**Rozevírací seznam**|Seznam položek, které může uživatel vybrat. Uživatele nelze zadat nové položky v rozevíracím seznamu.<br /><br /> Použití <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> vlastnost přidání položek do seznamu. Můžete přidávat a odebírat položky v době běhu.<br /><br /> Použití <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> vlastnost k přidání tlačítek do seznamu. Nelze však přidat a odebrat tlačítka v době spuštění po načtení pásu do aplikace sady Office.|  
|**Textové pole**|Pole, do kterého může uživatel zadat text.|  
|**Galerie**|Nabídka, která představuje pole nebo mřížku vizuálních voleb, ze kterých mohou uživatelé vybrat. Můžete řídit rozložení výběrů v nabídce. Použití <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> a <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> vlastnosti k určení počtu řádků a sloupců, které zobrazí položky a tlačítka v galerii.|  
|**Popisek**|Text, který můžete použít k identifikaci ovládacích prvků na pásu karet.|  
|**Nabídka**|Rozevírací seznam, který může obsahovat následující ovládací prvky:<br /><br /> – Tlačítko<br />– Zaškrtávací políčko<br />-Galerie<br />– Nabídka<br />– Tlačítko rozdělení<br />-Přepínací tlačítko<br />-Oddělovač<br /><br /> Chcete-li přidat ovládací prvek do nabídky v Návrháři pásu karet, klikněte na šipku dolů v nabídce k vystavení návrhové plochy nabídky. Potom můžete přetáhnout ovládací prvky pásu karet z **nástrojů** do nabídky. Chcete-li uspořádat ovládací prvky, přetáhněte je do požadované polohy.<br /><br /> Přidání ovládacích prvků <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> po načtení pásu do aplikace sady Office, je nutné nastavit <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> vlastnost **true** před načtením pásu karet. Informace o tom, jak to provést, najdete v tématu [přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md).|  
|**Oddělovač**|Tenký panel použitý k oddělení položek v seznamu. Když se přidá do skupiny, je panel je svislý. Když se přidá do nabídky je panel je vodorovný.|  
|**SplitButton**|Tlačítko s připojenou nabídkou. Tlačítko rozdělení může obsahovat žádný z následujících ovládacích prvků:<br /><br /> – Tlačítko<br />– Zaškrtávací políčko<br />-Galerie<br />– Nabídka<br />– Tlačítko rozdělení<br />-Přepínací tlačítko<br />-Oddělovač<br /><br /> Stejně jako nabídka má tlačítko rozdělení vlastní návrhovou plochu. Ale na rozdíl od nabídky lze aktualizovat pouze položky tlačítka rozdělení před načtením pásu karet do aplikace sady Office. Informace o tom, jak aktualizovat položky tlačítka rozdělení najdete v tématu [přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md).|  
|**ToggleButton**|Tlačítko, které se zobrazí stisknuté nebo nestisknuté.|  
  
##  <a name="HandleEventsSetProperties"></a> Zpracování událostí a nastavení vlastností  
 Návrhář pásu karet umožňuje nastavit vlastnosti ovládacího prvku v době návrhu pomocí **vlastnosti** okna. Na pásu karet navíc poskytuje model silně typovaných objektů, které můžete použít k získání a nastavení vlastností ovládacích prvků pásu karet za běhu.  
  
 Dvakrát klikněte na libovolný ovládací prvek v Návrháři můžete otevřít obslužnou rutinu události pro výchozí událost ovládacího prvku. Obslužné rutiny událostí pro všechny další události ovládacího prvku můžete vytvořit pomocí **vlastnosti** okna.  
  
 Pás karet událostí a vlastnosti jsou umístěny v <xref:Microsoft.Office.Tools.Ribbon> oboru názvů. **Pás karet (vizuální návrhář)** položek automaticky přidá odkaz na toto sestavení v projektu a vloží odpovídající **pomocí** nebo **importy** příkazu v horní části souboru s kódem pásu karet.  
  
 Informace o zpracování událostí na pásu karet a nastavení vlastností ovládacích prvků pásu karet za běhu, naleznete v tématu [přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md).  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a> Přizpůsobení zobrazení Backstage  
 Návrhář pásu karet můžete použít k přidávání ovládacích prvků do nabídky, které se otevře po kliknutí **souboru** kartu. Tato nabídka se nazývá zobrazení Backstage.  
  
 Ovládací prvky nelze umístit před nebo za vestavěné ovládací prvky pomocí Návrháře pásu karet. Předdefinovaný ovládací prvek je ovládací prvek, který se již nachází v zobrazení Backstage. Pokud chcete umístit ovládací prvky před nebo po vestavěných ovládacích prvcích, je nutné použít pás karet XML. Další informace o **pásu karet (XML)**, naleznete v tématu [kódu XML pásu karet](../vsto/ribbon-xml.md). Další informace o úpravách zobrazení Backstage naleznete v tématu [Úvod do zobrazení Office 2010 Backstage pro vývojáře](http://go.microsoft.com/fwlink/?LinkId=182189) a [přizpůsobení zobrazení Office 2010 Backstage pro vývojáře](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 Informace o tom, jak přidat ovládací prvky do zobrazení Backstage naleznete v tématu [postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
##  <a name="Accessibility"></a> Usnadnění přístupu v Návrháři pásu karet  
 Klávesové zkratky můžete použít k přesunutí ovládacích prvků v Návrháři pásu karet. Některé klávesové zkratky platí pro všechny ovládací prvky a některé jsou aplikovatelné pouze na ovládací prvky, které obsahují nabídky.  
  
 V následující tabulce jsou uvedeny klávesové zkratky, které platí pro všechny ovládací prvky.  
  
|Akce|Klávesová zkratka|  
|------------|-----------------------|  
|Přesuňte ovládací prvek před předchozí ovládací prvek v seznamu.|**CTRL**+**nahoru**<br /><br /> **CTRL**+**doleva**|  
|Přesuňte ovládací prvek za další ovládací prvek v seznamu.|**CTRL**+**dolů**<br /><br /> **CTRL**+**doprava**|  
|Přesuňte výběr z jednoho ovládacího prvku na jiný ve stejné skupině. Rozbalovací panel přesouvání mezi nadřazeným ovládacím prvkem a ovládací prvky na panelu rozevíracího seznamu.|**Nahoru**<br /><br /> **Dolů**|  
|Iterujte vpřed přes všechny ovládací prvky.|**Karta**|  
|Iterujte vzad přes všechny ovládací prvky.|**SHIFT**+**kartu**|  
|Odstraňte vybraný ovládací prvek nebo sadu ovládacích prvků.|**Delete**|  
|Kopírovat vybrané ovládací prvky.|**CTRL**+**C**|  
|Vyjměte vybrané ovládací prvky.|**CTRL**+**X**|  
|Vložit ovládací prvky ze schránky.|**CTRL**+**V**|  
|Vyberte **nástrojů**.|**CTRL**+**Alt**+**X**|  
|Vyberte nadřazenou součást.|**ESC**|  
  
 Klávesové zkratky, které se vztahují pouze k nabídce Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>, a <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> jsou uvedeny v následující tabulce.  
  
|Akce|Klávesová zkratka|  
|------------|-----------------------|  
|Vyberte nadřazený ovládací prvek, pokud je rozbalovací panel otevřený a ovládací prvek na panelu rozevíracího seznamu.|**doleva**|  
|Zavřete panel rozevíracího seznamu, pokud je rozbalovací panel otevřený a je vybrán nadřazený ovládací prvek.|**doleva**|  
|Otevřete rozbalovací panel.|**doprava**|  
|Pokud je rozbalovací panel otevřený, vyberte první ovládací prvek na panelu rozevíracího seznamu.|**doprava**|  
|Zavřete rozevírací panel.|**ESC**|  
  
## <a name="see-also"></a>Viz také:  
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Pás karet – XML](../vsto/ribbon-xml.md)   
 [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Postupy: Export pásu karet z Návrháře pásu karet do kódu XML pásu karet](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  