---
title: 'Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet'
titleSuffix: ''
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f311f35ba4a8c443f47941a905ee4cf4d3ebfb2
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585012"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet
  Pomocí Návrháře pásu karet můžete vytvořit vlastní kartu a následně na ni přidat a umístit ovládací prvky.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- [Vytváření podoken akcí](#BKMK_CreateActionsPanes)

- [Vytvořte vlastní kartu](#BKMK_CreateCustomTab).

- [Skryjte a zobrazte podokna akcí pomocí tlačítek na vlastní kartě](#BKMK_HideShowActionsPane).

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>Vytvoření projektu excelového sešitu
 Postup použití Návrháře pásu karet je skoro stejný pro všechny aplikace Office. V tomto příkladu se používá excelový sešit.

### <a name="to-create-an-excel-workbook-project"></a>Vytvoření projektu excelového sešitu

- Vytvořte projekt sešitu aplikace Excel s názvem **MyExcelRibbon**. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový sešit v návrháři a přidá projekt **MyExcelRibbon** do **Průzkumník řešení**.

## <a name="create-actions-panes"></a><a name="BKMK_CreateActionsPanes"></a> Vytváření podoken akcí
 Přidejte do projektu dvě vlastní podokna akcí. Později přidáte tlačítka, která zobrazují a skryjí tato podokna akcí na vlastní kartu.

### <a name="to-create-actions-panes"></a>Vytvoření podoken akcí

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte možnost **ActionsPaneControl**a pak zvolte možnost **Přidat**.

     V návrháři se otevře soubor **ActionsPaneControl1.cs** nebo **ActionsPaneControl1. vb** .

3. Na kartě **běžné ovládací prvky** **panelu nástrojů**přidejte popisek na plochu návrháře.

4. V okně **vlastnosti** nastavte vlastnost **text** vlastnosti Label1 na **podokno akce 1**.

5. Opakováním kroků 1 až 5 vytvořte druhé podokno akcí a popisek. Nastavte vlastnost **text** druhého popisku na **podokno akce 2**.

## <a name="create-a-custom-tab"></a><a name="BKMK_CreateCustomTab"></a> Vytvoření vlastní karty
 Jedním z pokynů pro návrh aplikací pro Office je, že uživatelé by měli mít vždycky kontrolu nad uživatelským rozhraním aplikace Office. Chcete-li přidat tuto funkci pro podokna akcí, můžete přidat tlačítka, která zobrazují a skryjí jednotlivá podokna akcí z vlastní karty na pásu karet. Chcete-li vytvořit vlastní kartu, přidejte položku **pás karet (vizuální Návrhář)** do projektu. Návrhář pomáhá přidat a umístit ovládací prvky, nastavit vlastnosti ovládacího prvku a zpracovat události ovládacího prvku.

### <a name="to-create-a-custom-tab"></a>Vytvoření vlastní karty

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte možnost **pás karet (vizuální Návrhář)**.

3. Změňte název nového pásu karet na **MyRibbon**a klikněte na **Přidat**.

     Otevře se soubor **MyRibbon.cs** nebo **MyRibbon. vb** v Návrháři pásu karet a zobrazí výchozí kartu a skupinu.

4. V Návrháři pásu karet vyberte výchozí kartu.

5. V okně **vlastnosti** rozbalte vlastnost **ControlID** a pak nastavte vlastnost **ControlIdType** na hodnotu **Custom (vlastní**).

6. Nastavte vlastnost **popisek** na **moji vlastní kartu**.

7. V Návrháři pásu karet vyberte možnost **Group1**.

8. V okně **vlastnosti** nastavte **popisek** na **Správce podokna akce**.

9. Na kartě **ovládací prvky pásu karet Office** přetáhněte **Toolbox**tlačítko na **Group1**.

10. Vyberte možnost **Button1**.

11. V okně **vlastnosti** nastavte **popisek** na **Zobrazit podokno akcí 1**.

12. Přidejte druhé tlačítko na **Group1**a nastavte vlastnost **popisek** tak, aby **zobrazovala podokno akcí 2**.

13. Na kartě **ovládací prvky pásu karet Office** přetáhněte **Toolbox**ovládací prvek **ToggleButton** na **Group1**.

14. Nastavte vlastnost **popisek** na **Skrýt podokno akcí**.

## <a name="hide-and-show-actions-panes-by-using-buttons-on-the-custom-tab"></a><a name="BKMK_HideShowActionsPane"></a> Skrytí a zobrazení podoken akcí pomocí tlačítek na vlastní kartě
 Posledním krokem je přidání kódu, který reaguje na uživatele. Přidejte obslužné rutiny události pro <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> události dvou tlačítek a <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> události přepínacího tlačítka. Přidejte kód do těchto obslužných rutin událostí, aby bylo možné povolit skrývání a zobrazování podoken akcí.

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Skrytí a zobrazení podoken akcí pomocí tlačítek na vlastní kartě

1. V **Průzkumník řešení**otevřete místní nabídku pro *MyRibbon.cs* nebo *MyRibbon. vb*a pak zvolte **Zobrazit kód**.

2. Do horní části třídy přidejte následující kód `MyRibbon` . Tento kód vytvoří dva objekty podokna akce.

     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]

3. Nahraďte metodu `MyRibbon_Load` následujícím kódem. Tento kód přidá objekty podokna akce do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> kolekce a skryje objekty ze zobrazení. Kód jazyka Visual C# také připojí delegáty k několika událostem ovládacího prvku pásu karet.

     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]

4. Do třídy přidejte následující tři metody obslužné rutiny události `MyRibbon` . Tyto metody zpracovávají <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> události dvou tlačítek a <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> události přepínacího tlačítka. Obslužné rutiny událostí pro Button1 a Button2 zobrazují podokna alternativních akcí. Obslužná rutina události pro toggleButton1 zobrazí a skryje podokno aktivní akce.

     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]

## <a name="test-the-custom-tab"></a>Testování vlastní karty
 Při spuštění projektu se spustí aplikace Excel a na pásu karet se zobrazí karta **Moje vlastní karta** . Kliknutím na tlačítka na **vlastní kartě** zobrazíte a skryjete podokna akcí.

### <a name="to-test-the-custom-tab"></a>Testování vlastní karty

1. Stisknutím klávesy **F5** spusťte projekt.

2. Vyberte kartu **Moje vlastní karta** .

3. Ve skupině **Správce podokna vlastní akce** vyberte možnost **Zobrazit podokno akcí 1**.

     Zobrazí se podokno akce a zobrazí se **podokno akce popisku 1**.

4. Vyberte možnost **Zobrazit podokno akcí 2**.

     Zobrazí se podokno akce a zobrazí se **podokno akce popisku 2**.

5. Klikněte na tlačítko **Skrýt podokno akcí**.

     Podokna akcí již nejsou viditelná.

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak přizpůsobit uživatelské rozhraní Office, najdete v těchto tématech:

- Přidejte kontextové uživatelské rozhraní do libovolného přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [Přehled podokna akcí](../vsto/actions-pane-overview.md).

- Rozšíříte standardní nebo vlastní systém Microsoft Office formulář aplikace Outlook. Další informace najdete v tématu [Návod: návrh oblasti formuláře aplikace Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Viz také
- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Přizpůsobení pásu karet pro Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Postupy: Změna pozice karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Přehled modelu objektů pásu karet](../vsto/ribbon-object-model-overview.md)
