---
title: 'Návod: Přidání ovládacích prvků na list za běhu v projektu doplňku VSTO'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b3671b00ecad0380dd38e770beeef703fa916fac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915695"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-runtime-in-vsto-add-in-project"></a>Návod: Přidání ovládacích prvků na list za běhu v projektu doplňku VSTO
  Můžete přidat ovládací prvky pro žádné otevřené listu s použitím doplňku VSTO v Excelu. Tento návod ukazuje, jak používat na pásu karet umožňující uživatelům přidávat <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange>a <xref:Microsoft.Office.Tools.Excel.ListObject> do listu. Informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **Platí pro:** informace v tomto tématu se vztahují na projekty doplňku VSTO pro Excel. Další informace najdete v tématu [Dostupné funkce podle aplikace Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Tento návod znázorňuje následující úlohy:  
  
- Poskytování uživatelského rozhraní (UI) k přidávání ovládacích prvků na list.  
  
- Přidání ovládacích prvků na list.  
  
- Odebrání ovládacích prvků z listu.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## <a name="create-a-new-excel-vsto-add-in-project"></a>Vytvoření nového projektu doplňku VSTO pro Excel  
 Začněte vytvořením projektu doplňku VSTO v Excelu.  
  
### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Chcete-li vytvořit nový projekt doplňku VSTO pro Excel  
  
1.  V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vytvoření projektu doplňku VSTO pro Excel s názvem **ExcelDynamicControls**. Další informace najdete v tématu [postupy: vytváření projektů pro Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Přidejte odkaz na **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** sestavení. Tento odkaz vyžaduje programové přidání ovládacího prvku Windows Forms do listu později v tomto názorném postupu.  
  
## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Zadejte uživatelské rozhraní k přidávání ovládacích prvků na list  
 Přidáte vlastní kartu na pásu karet Excelu. Uživatelé mohou vybrat zaškrtávací políčka na kartě k přidávání ovládacích prvků na list.  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>K poskytování uživatelského rozhraní k přidávání ovládacích prvků na list  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
2.  V **přidat novou položku** dialogu **pás karet (vizuální návrhář)** a potom klikněte na tlačítko **přidat**.  
  
     Soubor s názvem **Ribbon1.cs** nebo **Ribbon1.vb** se otevře v Návrháři pásu karet a zobrazí výchozí kartu a skupinu.  
  
3.  Z **ovládací prvky Ribbon Office** karty **nástrojů**, přetáhněte ovládací prvek CheckBox do **group1**.  
  
4.  Klikněte na tlačítko **CheckBox1** ji vyberte.  
  
5.  V **vlastnosti** okně změnit následující vlastnosti.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**Tlačítko**|  
    |**Popisek**|**Tlačítko**|  
  
6.  Přidejte druhý zaškrtnutím políčka **group1**a potom změňte následující vlastnosti.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**NamedRange**|  
    |**Popisek**|**NamedRange**|  
  
7.  Třetí zaškrtávací políčko k přidání **group1**a potom změňte následující vlastnosti.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**Jméno**|**ListObject**|  
    |**Popisek**|**ListObject**|  
  
## <a name="add-controls-to-the-worksheet"></a>Přidání ovládacích prvků na list  
 Spravované ovládací prvky můžete přidat jenom do hostitelské položky, které fungují jako kontejnery. Protože projekty doplňků VSTO pracovat s libovolný otevřít sešit, doplňku VSTO hostitelská položka převede do listu, nebo získá existující položku hostitele před přidáním ovládacího prvku. Přidejte kód do obslužné rutiny událostí klikněte na každého ovládacího prvku pro generování <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelský objekt, který je založen na otevřené listy. Pak přidejte <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange>a <xref:Microsoft.Office.Tools.Excel.ListObject> na aktuální výběr v listu.  
  
### <a name="to-add-controls-to-a-worksheet"></a>Přidání ovládacích prvků na list  
  
1.  V Návrháři pásu karet klikněte dvakrát na **tlačítko**.  
  
     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Obslužná rutina události **tlačítko** zaškrtávacího políčka se otevře v editoru kódu.  
  
2.  Nahradit `Button_Click` obslužné rutiny události s následujícím kódem.  
  
     Tento kód používá `GetVstoObject` metodu k získání hostitelská položka, která představuje první listu v sešitu a pak přidá <xref:Microsoft.Office.Tools.Excel.Controls.Button> ovládací prvek pro aktuálně vybranou buňku.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]  
  
3.  V **Průzkumníka řešení**vyberte *Ribbon1.cs* nebo *Ribbon1.vb*.  
  
4.  Na **zobrazení** nabídky, klikněte na tlačítko **návrháře**.  
  
5.  V Návrháři pásu karet klikněte dvakrát na **NamedRange**.  
  
6.  Nahradit `NamedRange_Click` obslužné rutiny události s následujícím kódem.  
  
     Tento kód používá `GetVstoObject` metodu k získání hostitelská položka, která představuje první listu v sešitu a pak definuje <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek pro aktuálně vybranou buňku nebo buňky.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]  
  
7.  V Návrháři pásu karet klikněte dvakrát na **ListObject**.  
  
8.  Nahradit `ListObject_Click` obslužné rutiny události s následujícím kódem.  
  
     Tento kód používá `GetVstoObject` metodu k získání hostitelská položka, která představuje první listu v sešitu a pak definuje <xref:Microsoft.Office.Tools.Excel.ListObject> pro aktuálně vybranou buňku nebo buňky.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]  
  
9. Přidejte následující příkazy k hornímu okraji soubor kódu pásu karet.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]  
  
## <a name="remove-controls-from-the-worksheet"></a>Odebrání ovládacích prvků z listu  
 Ovládací prvky nejsou zachované při listu je uložit a zavřít. Všechny ovládací prvky Windows Forms generované byste měli odstranit prostřednictvím kódu programu předtím, než se uloží do listu, nebo pouze Přehled ovládacího prvku se zobrazí, když je sešit otevřít znovu. Přidejte kód, který <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> událost, která odebere ovládacích prvků Windows Forms z kolekce ovládacích prvků generovaných hostitelského objektu. Další informace najdete v tématu [uchování dynamických ovládacích prvků v dokumentech systému Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
### <a name="to-remove-controls-from-the-worksheet"></a>Chcete-li odebrat ovládací prvky z listu  
  
1.  V **Průzkumníka řešení**vyberte *ThisAddIn.cs* nebo *ThisAddIn.vb*.  
  
2.  Na **zobrazení** nabídky, klikněte na tlačítko **kód**.  
  
3.  Přidejte následující metodu do `ThisAddIn` třídy. Tento kód získá první listu v sešitu a použije je `HasVstoObject` metodu ke kontrole, jestli má list objekt vygenerovaný sešit. Pokud objekt vygenerovaný sešit obsahuje ovládací prvky, kód získá tento objekt list a Iteruje přes kolekci ovládacích prvků, odebrání ovládacích prvků.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]  
  
4.  V C#, je nutné vytvořit obslužná rutina události <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> událostí. Tento kód v můžete umístit `ThisAddIn_Startup` metody. Další informace o vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md). Nahradit `ThisAddIn_Startup` metodu s následujícím kódem.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]  
  
## <a name="test-the-solution"></a>Otestování řešení  
 Přidání ovládacích prvků na list tak, že je vyberete vlastní kartu na pásu karet. Pokud list uložíte, odeberou se tyto ovládací prvky.  
  
### <a name="to-test-the-solution"></a>Otestování řešení.  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Vyberte libovolnou buňku List1.  
  
3.  Klikněte na tlačítko **Add-Ins** kartu.  
  
4.  V **group1** klikněte na možnost **tlačítko**.  
  
     Tlačítko se zobrazí ve vybrané buňce.  
  
5.  Vyberte jinou buňku v List1.  
  
6.  V **group1** klikněte na možnost **NamedRange**.  
  
     Pojmenované oblasti je definována pro vybranou buňku.  
  
7.  Vyberte řady buněk v List1.  
  
8.  V **group1** klikněte na možnost **ListObject**.  
  
     Přidá se seznamu objektů pro vybrané buňky.  
  
9. Uložte list.  
  
     Ovládací prvky, které jste přidali do List1 už nebude zobrazovat.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o ovládacích prvcích v projekty doplňku VSTO pro Excel z tohoto tématu:  
  
-   Další informace o tom, jak uložit ovládacích prvků na list, najdete v článku VSTO pro Excel Add-in dynamické ovládací prvky ukázce kódu na [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="see-also"></a>Viz také:  
 [Řešení pro aplikaci Excel](../vsto/excel-solutions.md)   
 [Windows forms ovládacích prvků na dokumenty Office – přehled](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Namedrange – ovládací prvek](../vsto/namedrange-control.md)   
 [ListObject – ovládací prvek](../vsto/listobject-control.md)  
  
  