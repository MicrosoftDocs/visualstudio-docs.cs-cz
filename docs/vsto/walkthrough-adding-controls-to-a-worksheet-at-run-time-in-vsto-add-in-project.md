---
title: Přidat do listu ovládací prvky v době běhu v projektu doplňku VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5bf2610ca1f3f3767082bf50953f821d37d1af2a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253899"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>Návod: Přidání ovládacích prvků na list v době běhu v projektu doplňku VSTO
  Pomocí doplňku pro Excel VSTO můžete přidat ovládací prvky do libovolného otevřeného listu. Tento návod ukazuje, jak použít pás karet k tomu <xref:Microsoft.Office.Tools.Excel.Controls.Button> <xref:Microsoft.Office.Tools.Excel.NamedRange>, aby uživatelé mohli do listu přidat, a <xref:Microsoft.Office.Tools.Excel.ListObject> a. Informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

 **Platí pro:** Informace v tomto tématu se vztahují na projekty doplňku VSTO v Excelu. Další informace najdete v tématu [Dostupné funkce podle aplikace Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

 Tento návod znázorňuje následující úlohy:

- Poskytnutí uživatelského rozhraní (UI) pro přidání ovládacích prvků do listu.

- Přidávání ovládacích prvků do listu.

- Odebírání ovládacích prvků z listu.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Excel

## <a name="create-a-new-excel-vsto-add-in-project"></a>Vytvořit nový projekt doplňku VSTO pro Excel
 Začněte vytvořením projektu doplňku VSTO pro Excel.

### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Vytvoření nového projektu doplňku VSTO pro Excel

1. V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]aplikaci vytvořte projekt doplňku VSTO pro Excel s názvem **ExcelDynamicControls**. Další informace najdete v tématu [jak: Vytváření projektů Office v sadě Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

2. Přidejte odkaz na sestavení **Microsoft. Office. Tools. Excel. v 4.0. Utilities. dll** . Tento odkaz je nutný k programovému přidání ovládacího prvku model Windows Forms do listu později v tomto návodu.

## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Poskytněte uživatelské rozhraní pro přidání ovládacích prvků do listu.
 Přidejte vlastní kartu na pás karet aplikace Excel. Uživatelé mohou vybrat zaškrtávací políčka na kartě a přidat ovládací prvky do listu.

#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Poskytnutí uživatelského rozhraní pro přidání ovládacích prvků do listu

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte možnost **pás karet (vizuální Návrhář)** a pak klikněte na tlačítko **Přidat**.

     Soubor s názvem **Ribbon1.cs** nebo **Ribbon1. vb** se otevře v Návrháři pásu karet a zobrazí výchozí kartu a skupinu.

3. Na kartě **ovládací prvky pásu karet Office** na **panelu nástrojů**přetáhněte ovládací prvek CheckBox na **Group1**.

4. Klikněte na možnost **checkBox1** a vyberte ji.

5. V okně **vlastnosti** změňte následující vlastnosti.

    |Vlastnost|Value|
    |--------------|-----------|
    |**Název**|**Tlačítko**|
    |**Popisek**|**Tlačítko**|

6. Přidejte druhé zaškrtávací políčko do **Group1**a potom změňte následující vlastnosti.

    |Vlastnost|Value|
    |--------------|-----------|
    |**Název**|**NamedRange**|
    |**Popisek**|**NamedRange**|

7. Přidejte třetí zaškrtávací políčko do **Group1**a potom změňte následující vlastnosti.

    |Vlastnost|Value|
    |--------------|-----------|
    |**Název**|**ListObject**|
    |**Popisek**|**ListObject**|

## <a name="add-controls-to-the-worksheet"></a>Přidat ovládací prvky do listu
 Spravované ovládací prvky lze přidat pouze k položkám hostitele, které fungují jako kontejnery. Vzhledem k tomu, že projekty doplňku VSTO fungují v otevřeném sešitu, doplněk VSTO převede list na položku hostitele nebo získá existující položku hostitele před přidáním ovládacího prvku. Přidejte kód do obslužných rutin událostí kliknutí každého ovládacího prvku pro vygenerování <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelské položky, která je založena na otevřeném listu. Pak do aktuálního výběru <xref:Microsoft.Office.Tools.Excel.Controls.Button>v listu <xref:Microsoft.Office.Tools.Excel.NamedRange>přidejte, a <xref:Microsoft.Office.Tools.Excel.ListObject> a.

### <a name="to-add-controls-to-a-worksheet"></a>Přidání ovládacích prvků do listu

1. V Návrháři pásu karet dvakrát klikněte na **tlačítko**.

     V editoru kódu se otevře obslužná rutina událostiprotlačítkosezaškrtávacímpolíčkem<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> .

2. Proměnnou obslužné rutiny události nahraďte následujícím kódem. `Button_Click`

     Tento kód používá `GetVstoObject` metodu k získání položky hostitele, která představuje první list v sešitu, a následně <xref:Microsoft.Office.Tools.Excel.Controls.Button> přidá ovládací prvek do aktuálně vybrané buňky.

     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]

3. V **Průzkumník řešení**vyberte *Ribbon1.cs* nebo *Ribbon1. vb*.

4. V nabídce **zobrazení** klikněte na možnost **Návrhář**.

5. V Návrháři pásu karet poklikejte na **NamedRange**.

6. Proměnnou obslužné rutiny události nahraďte následujícím kódem. `NamedRange_Click`

     Tento kód používá `GetVstoObject` metodu k získání položky hostitele, která představuje první list v sešitu, a <xref:Microsoft.Office.Tools.Excel.NamedRange> definuje ovládací prvek pro aktuálně vybranou buňku nebo buňky.

     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]

7. V Návrháři pásu karet poklikejte na **ListObject**.

8. Proměnnou obslužné rutiny události nahraďte následujícím kódem. `ListObject_Click`

     Tento kód používá `GetVstoObject` metodu k získání položky hostitele, která představuje první list v sešitu, a <xref:Microsoft.Office.Tools.Excel.ListObject> definuje pro aktuálně vybranou buňku nebo buňky.

     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]

9. Přidejte následující příkazy do horní části souboru kódu pásu karet.

     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]

## <a name="remove-controls-from-the-worksheet"></a>Odebrat ovládací prvky z listu
 Ovládací prvky nejsou trvalé při uložení a zavření listu. Před uložením listu byste měli programově odebrat všechny vygenerované model Windows Forms ovládací prvky, nebo se po opětovném otevření sešitu zobrazí jenom obrys ovládacího prvku. Přidejte kód k <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> události, která odebere model Windows Forms ovládací prvky z kolekce Controls vygenerované položky hostitele. Další informace najdete v tématu [trvalé dynamické ovládací prvky v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

### <a name="to-remove-controls-from-the-worksheet"></a>Odebrání ovládacích prvků z listu

1. V **Průzkumník řešení**vyberte *ThisAddIn.cs* nebo *ThisAddIn. vb*.

2. V nabídce **zobrazení** klikněte na příkaz **Code (kód**).

3. Do `ThisAddIn` třídy přidejte následující metodu. Tento kód získá první list v sešitu a potom použije `HasVstoObject` metodu ke kontrole, zda má list vygenerovaný objekt list. Pokud objekt vygenerovaného listu obsahuje ovládací prvky, kód získá tento objekt list a provede iteraci v kolekci ovládacích prvků a odebere ovládací prvky.

     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]

4. V C#nástroji je nutné vytvořit obslužnou rutinu události pro <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> událost. Tento kód můžete umístit do `ThisAddIn_Startup` metody. Další informace o vytváření obslužných rutin událostí naleznete [v tématu How to: Vytváření obslužných rutin událostí v](../vsto/how-to-create-event-handlers-in-office-projects.md)projektech pro systém Office. Nahraďte `ThisAddIn_Startup` metodu následujícím kódem.

     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]

## <a name="test-the-solution"></a>Testování řešení
 Ovládací prvky můžete do listu přidat tak, že je vyberete z vlastní karty na pásu karet. Když list uložíte, tyto ovládací prvky se odeberou.

### <a name="to-test-the-solution"></a>K otestování řešení.

1. Stisknutím klávesy **F5** spusťte projekt.

2. Vyberte libovolnou buňku v List1.

3. Klikněte na kartu **Doplňky** .

4. Ve skupině **Group1** klikněte na **tlačítko**.

     Ve vybrané buňce se zobrazí tlačítko.

5. Vyberte v List1 jinou buňku.

6. Ve skupině **Group1** klikněte na **NamedRange**.

     Pro vybranou buňku je definován pojmenovaný rozsah.

7. Vyberte řadu buněk v List1.

8. Ve skupině **Group1** klikněte na **ListObject**.

     Pro vybrané buňky se přidá objekt seznamu.

9. Uložte list.

     Ovládací prvky, které jste přidali do List1, se již nezobrazují.

## <a name="next-steps"></a>Další kroky
 Další informace o ovládacích prvcích v excelových projektech doplňku VSTO najdete v tomto tématu:

- Další informace o tom, jak uložit ovládací prvky do listu, najdete v ukázce dynamické ovládací prvky aplikace Excel VSTO v tématu [ukázky vývoje pro Office a návody](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="see-also"></a>Viz také:
- [Řešení pro Excel](../vsto/excel-solutions.md)
- [Přehled ovládacích prvků Windows Forms v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Ovládací prvek ListObject](../vsto/listobject-control.md)
