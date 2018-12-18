---
title: 'Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a0089880e143c3db8f260141d9936058bf35b1ce
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808869"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet
  Pomocí Návrháře pásu karet můžete vytvořit vlastní kartu a potom přidat a umístit ovládací prvky na něm.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
-   [Tvorba podoken akcí](#BKMK_CreateActionsPanes).  
  
-   [Vytvoření vlastní karty](#BKMK_CreateCustomTab).  
  
-   [Skrytí a zobrazení podokna akcí pomocí tlačítek na vlastní kartě](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="create-an-excel-workbook-project"></a>Vytvoření projektu sešitu aplikace Excel  
 Pokyny pro použití Návrháře pásu karet jsou téměř shodné pro všechny aplikace Office. Tento příklad používá Excelový sešit.  
  
### <a name="to-create-an-excel-workbook-project"></a>Vytvoření projektu sešitu aplikace Excel  
  
-   Vytvořte projekt sešitu aplikace Excel s názvem **MyExcelRibbon**. Další informace najdete v tématu [postupy: vytváření projektů pro Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře nový sešit v návrháři a přidá **MyExcelRibbon** projektu **Průzkumníka řešení**.  
  
##  <a name="BKMK_CreateActionsPanes"></a> Tvorba podoken akcí  
 Přidejte do projektu dvě vlastní podokna akcí. Později přidáte tlačítka, která zobrazení a skrytí těchto podoken akcí na vlastní kartu.  
  
### <a name="to-create-actions-panes"></a>Tvorba podoken akcí  
  
1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
2.  V **přidat novou položku** dialogu **ActionsPaneControl**a klikněte na tlačítko **přidat**.  
  
     **ActionsPaneControl1.cs** nebo **ActionsPaneControl1.vb** soubor se otevře v návrháři.  
  
3.  Z **běžné ovládací prvky** karty **nástrojů**, přidejte popisek na plochu návrháře.  
  
4.  V **vlastnosti** okno, nastaveno **Text** parametru Label1 hodnotu **podokno akcí 1**.  
  
5.  Opakujte kroky 1 až 5 a vytvořte tak druhé podokno s akcemi a popisek. Nastavte **Text** vlastnost druhého popisku na **podokno akcí 2**.  
  
##  <a name="BKMK_CreateCustomTab"></a> Vytvoření vlastní karty  
 Jedním z pokynů pro návrh aplikace Office je, že uživatelé by měli vždy mít ovládací prvek uživatelského rozhraní aplikace Office. Chcete-li přidat tuto funkci pro podokna akcí, můžete přidat tlačítka, které zobrazí a skryjí jednotlivá podokna akcí z vlastní karty na pásu karet. Chcete-li vytvořit vlastní karty, přidejte **pás karet (vizuální návrhář)** položky do projektu. Návrhář pomáhá přidat a umístit ovládací prvky, nastavit vlastnosti ovládacího prvku a zpracovat události ovládacího prvku.  
  
### <a name="to-create-a-custom-tab"></a>Vytvoření vlastní karty  
  
1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
2.  V **přidat novou položku** dialogu **pás karet (vizuální návrhář)**.  
  
3.  Změňte název nového pásu karet na **MyRibbon**a zvolte **přidat**.  
  
     **MyRibbon.cs** nebo **MyRibbon.vb** soubor se otevře v Návrháři pásu karet a zobrazí výchozí kartu a skupinu.  
  
4.  V Návrháři pásu karet vyberte výchozí kartu.  
  
5.  V **vlastnosti** okna, rozbalte **ControlId** vlastnost a poté nastavte **ControlIdType** vlastnost **vlastní**.  
  
6.  Nastavte **popisek** vlastnost **Moje vlastní karta**.  
  
7.  V Návrháři pásu karet zvolte **group1**.  
  
8.  V **vlastnosti** okno, nastavte **popisek** k **správce podokna akcí**.  
  
9. Z **ovládací prvky Ribbon Office** karty **nástrojů**, přetáhněte tlačítko na **group1**.  
  
10. Vyberte **button1**.  
  
11. V **vlastnosti** okno, nastavte **popisek** k **zobrazit podokno akcí 1**.  
  
12. Přidejte druhé tlačítko do **group1**a nastavte **popisek** vlastnost **zobrazit podokno akcí 2**.  
  
13. Z **ovládací prvky Ribbon Office** karty **nástrojů**, přetáhněte **ToggleButton** na ovládací prvek **group1**.  
  
14. Nastavte **popisek** vlastnost **skrýt podokno akcí**.  
  
##  <a name="BKMK_HideShowActionsPane"></a> Skrytí a zobrazení podokna akcí pomocí tlačítek na vlastní kartu  
 Posledním krokem je přidání kódu, který odpovídá uživateli. Přidání obslužné rutiny událostí pro <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> události dvou tlačítek a <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> události přepínacího tlačítka. Přidejte kód do těchto obslužných rutin událostí, abyste umožnili skrytí a zobrazení podokna akcí.  
  
### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Skrytí a zobrazení podokna akcí pomocí tlačítek na vlastní kartě  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro *MyRibbon.cs* nebo *MyRibbon.vb*a klikněte na tlačítko **zobrazit kód**.  
  
2.  Přidejte následující kód do horní části `MyRibbon` třídy. Tento kód vytvoří dva objekty podokna akcí.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]  
  
3.  Nahradit `MyRibbon_Load` metodu s následujícím kódem. Tento kód přidá podokno akcí podokno objektů do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> kolekce a skryje objekty ze zobrazení. Kód jazyka Visual C# také připisuje delegáty několika událostem ovládací prvek pásu karet.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]  
  
4.  Přidejte následující metody obslužné rutiny tři události, které `MyRibbon` třídy. Tyto metody zpracovávají <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> události dvou tlačítek a <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> události přepínacího tlačítka. Obslužné rutiny událostí pro button1 a BUTTON2 umožňují zobrazit alternativní podokna akcí. Obslužnou rutinu události pro toggleButton1 zobrazí a skryje podokno akcí.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]  
  
## <a name="test-the-custom-tab"></a>Testování vlastní karty  
 Při spuštění projektu, se spustí aplikace Excel a **Moje vlastní karta** kartě se zobrazí na pásu karet. Zvolte tlačítka na **Moje vlastní karta** pro zobrazování a skrytí podokna akcí.  
  
### <a name="to-test-the-custom-tab"></a>Testování vlastní karty  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Zvolte **Moje vlastní karta** kartu.  
  
3.  V **správce vlastního podokna akcí** skupině, zvolte **zobrazit podokno akcí 1**.  
  
     Zobrazí se popisek zobrazí podokno akcí **podokno akcí 1**.  
  
4.  Zvolte **zobrazit podokno akcí 2**.  
  
     Zobrazí se popisek zobrazí podokno akcí **podokno akcí 2**.  
  
5.  Zvolte **skrýt podokno akcí**.  
  
     Podokna akcí již nejsou viditelné.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o tom, jak přizpůsobit uživatelské rozhraní sady Office naleznete v těchto tématech:  
  
-   Přidejte uživatelské rozhraní založené na kontextu do jakéhokoli přizpůsobení úrovni dokumentu. Další informace najdete v tématu [přehled podokna akcí](../vsto/actions-pane-overview.md).  
  
-   Rozšiřte standardní nebo vlastní formulář aplikace Microsoft Office Outlook. Další informace najdete v tématu [návod: Návrh oblasti formuláře Outlooku](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Návrhář pásu karet](../vsto/ribbon-designer.md)   
 [Přizpůsobte pás karet pro aplikaci Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Postupy: Změna pozice karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md)   
 [Postupy: Přidání ovládacích prvků do zobrazení backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md)  
  
  