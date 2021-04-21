---
title: 'Návod: svázání dat s ovládacími prvky v podokně akcí aplikace Excel'
description: Svázání dat s ovládacími prvky v podokně akcí v aplikaci Microsoft Excel. Ovládací prvky ukazují relaci hlavního/podrobností mezi tabulkami v SQL Server databázi.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 377c3405211c91712f8754131d8379c3dae7e820
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824546"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Návod: svázání dat s ovládacími prvky v podokně akcí aplikace Excel
  Tento návod ukazuje datovou vazbu k ovládacím prvkům v podokně akce v aplikaci systém Microsoft Office Excel. Ovládací prvky ukazují relaci hlavního/podrobností mezi tabulkami v SQL Server databázi.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- Přidávání ovládacích prvků do listu.

- Vytváření ovládacího prvku podokna akcí

- Přidání ovládacích prvků model Windows Forms vázaných na data do ovládacího prvku podokna akcí.

- Zobrazuje se podokno akce při otevření aplikace.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]:

- Přístup k serveru s ukázkovou databází Northwind SQL Server.

- Oprávnění ke čtení a zápisu do databáze SQL Server.

## <a name="create-the-project"></a>Vytvoření projektu
 Prvním krokem je vytvoření projektu excelového sešitu.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt sešitu aplikace Excel pomocí **podokna akce název v aplikaci Excel**. V průvodci vyberte možnost **vytvořit nový dokument**. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový excelový sešit v návrháři a přidá projekt **podokna akce aplikace Excel** do **Průzkumník řešení**.

## <a name="add-a-new-data-source-to-the-project"></a>Přidat do projektu nový zdroj dat

### <a name="to-add-a-new-data-source-to-the-project"></a>Přidání nového zdroje dat do projektu

1. Pokud není okno **zdroje dat** viditelné, zobrazte ho tak, že v řádku nabídek vyberete možnost **Zobrazit**  >  **ostatní**  >  **zdroje dat** Windows.

2. Zvolením možnosti **Přidat nový zdroj dat** spusťte **Průvodce konfigurací zdroje dat**.

3. Vyberte **databáze** a pak klikněte na **Další**.

4. Vyberte datové připojení k ukázce databáze Northwind SQL Server databázi nebo přidejte nové připojení pomocí tlačítka **nové připojení** .

5. Klikněte na **Next** (Další).

6. Pokud je vybraná možnost Uložit připojení, zrušte zaškrtnutí políčka a klikněte na tlačítko **Další**.

7. Rozbalte uzel **tabulky** v okně **objekty databáze** .

8. Zaškrtněte políčko vedle tabulky **Dodavatelé** .

9. Rozbalte tabulku **Products** a vyberte **NázevVýrobku**, **KódDodavatele**, **QuantityPerUnit** a **UnitPrice**.

10. Klikněte na **Finish** (Dokončit).

    Průvodce přidá tabulku **Dodavatelé** a **produkty** do okna **zdroje dat** . Také přidá do projektu typovou datovou sadu, která je viditelná v **Průzkumník řešení**.

## <a name="add-controls-to-the-worksheet"></a>Přidat ovládací prvky do listu
 Dále přidejte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek a <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek do prvního listu.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Přidání ovládacího prvku NamedRange a ovládacího prvku ListObject

1. Ověřte, že je v návrháři sady Visual Studio otevřený sešit **akcí aplikace Excel Pane.xlsx** sešit se `Sheet1` zobrazením.

2. V okně **zdroje dat** rozbalte tabulku **Dodavatelé** .

3. Klikněte na šipku rozevíracího seznamu v uzlu **název společnosti** a pak klikněte na **NamedRange**.

4. Přetáhněte **název společnosti** z okna **zdroje dat** do buňky **a2** v `Sheet1` .

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Vytvoří se ovládací prvek s názvem `CompanyNameNamedRange` a text \<CompanyName> se zobrazí v buňce **a2**. Ve stejnou dobu se <xref:System.Windows.Forms.BindingSource> `suppliersBindingSource` <xref:System.Data.DataSet> do projektu přidají pouze pojmenované, adaptér s tabulkou a. Ovládací prvek je vázán na <xref:System.Windows.Forms.BindingSource> , který je zase svázán s <xref:System.Data.DataSet> instancí.

5. V okně **zdroje dat** se posuňte dolů po sloupcích, které jsou v tabulce **Dodavatelé** . V dolní části seznamu je tabulka **produkty** . je to proto, že se jedná o podřízenou tabulku **dodavatelů** . Vyberte tuto tabulku **produktů** , nikoli tu, která je na stejné úrovni jako tabulka **Dodavatelé** , a potom klikněte na šipku rozevíracího seznamu, která se zobrazí.

6. V rozevíracím seznamu klikněte na **ListObject** a pak přetáhněte tabulku **Products** do buňky **a6** v `Sheet1` .

     <xref:Microsoft.Office.Tools.Excel.ListObject>Ovládací prvek s názvem `ProductNameListObject` je vytvořen v buňce **a6**. Současně <xref:System.Windows.Forms.BindingSource> `productsBindingSource` jsou do projektu přidány pojmenované a tabulkové adaptéry. Ovládací prvek je vázán na <xref:System.Windows.Forms.BindingSource> , který je zase svázán s <xref:System.Data.DataSet> instancí.

7. V případě C# vyberte **suppliersBindingSource** v zásobníku komponent a změňte vlastnost **modifikátory** na **interní** v okně **vlastnosti** .

## <a name="add-controls-to-the-actions-pane"></a>Přidání ovládacích prvků do podokna akce
 Dále budete potřebovat ovládací prvek podokna akce, který obsahuje pole se seznamem.

### <a name="to-add-an-actions-pane-control"></a>Přidání ovládacího prvku podokna akce

1. Vyberte projekt **podokna akce aplikace Excel** v **Průzkumník řešení**.

2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

3. V dialogovém okně **Přidat novou položku** vyberte možnost **ovládací prvek podokno akce**, pojmenujte ji **ActionsControl** a klikněte na tlačítko **Přidat**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Přidání ovládacích prvků model Windows Forms vázaných na data do ovládacího prvku podokna akcí

1. Z karet **běžných ovládacích prvků** na **panelu nástrojů** přetáhněte <xref:System.Windows.Forms.ComboBox> ovládací prvek do ovládacího prvku podokno akcí.

2. Změňte vlastnost **Size** na **171, 21**.

3. Změňte velikost uživatelského ovládacího prvku tak, aby odpovídal poli se seznamem.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Navázání ovládacího prvku v podokně akce na data
 V této části nastavíte zdroj dat na <xref:System.Windows.Forms.ComboBox> stejný zdroj dat jako <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek na listu.

### <a name="to-set-data-binding-properties-of-the-control"></a>Nastavení vlastností datové vazby ovládacího prvku

1. Klikněte pravým tlačítkem myši na ovládací prvek podokna akce a poté klikněte na možnost **Zobrazit kód**.

2. Do <xref:System.Windows.Forms.UserControl.Load> události ovládacího prvku podokno akcí přidejte následující kód.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs" id="Snippet1":::

3. V jazyce C# je nutné vytvořit obslužnou rutinu události pro `ActionsControl` . Tento kód můžete umístit do `ActionsControl` konstruktoru. Další informace o vytváření obslužných rutin událostí najdete v tématu [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs" id="Snippet2":::

## <a name="show-the-actions-pane"></a>Zobrazit podokno akcí
 Podokno akce není viditelné, dokud nepřidáte ovládací prvek za běhu.

#### <a name="to-show-the-actions-pane"></a>Zobrazení podokna akce

1. V **Průzkumník řešení** klikněte pravým tlačítkem na *ThisWorkbook. vb* nebo *ThisWorkbook. cs* a pak klikněte na **Zobrazit kód**.

2. Vytvořte ve třídě novou instanci uživatelského ovládacího prvku `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet3":::

3. V <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> obslužné rutině události ovládacího `ThisWorkbook` prvku přidejte ovládací prvek do podokna akce.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet4":::

## <a name="test-the-application"></a>Testování aplikace
 Nyní můžete testovat dokument a ověřit tak, že se podokno akce otevře při otevření dokumentu a že ovládací prvky mají relaci hlavního/podrobností.

### <a name="to-test-your-document"></a>Testování dokumentu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Potvrďte, že je podokno akce viditelné.

3. V seznamu vyberte společnost. Ověřte, zda je název společnosti uveden v <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacím prvku a zda jsou uvedeny podrobnosti o produktu v <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacím prvku.

4. Vyberte různé společnosti a ověřte podle potřeby změnu názvu společnosti a podrobností o produktu.

## <a name="next-steps"></a>Další kroky
 Tady jsou některé úkoly, které mohou být další:

- Umožňuje svázat data s ovládacími prvky ve Wordu. Další informace najdete v tématu [Návod: svázání dat s ovládacími prvky v podokně akcí aplikace Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

- Nasazení projektu. Další informace najdete v tématu [nasazení řešení pro systém Office pomocí technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Viz také
- [Přehled podokna akcí](../vsto/actions-pane-overview.md)
- [Postupy: Správa rozložení ovládacích prvků v podoknech akcí](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
