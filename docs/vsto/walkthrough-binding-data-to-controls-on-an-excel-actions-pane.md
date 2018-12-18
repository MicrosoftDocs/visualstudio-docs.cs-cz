---
title: 'Návod: Vytvoření vazby dat k ovládacím prvkům v podokně akcí aplikace Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8fbc1baa66dc98b2c5eec27c2a86e0fde3c5e967
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942644"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Návod: Vytvoření vazby dat k ovládacím prvkům v podokně akcí aplikace Excel
  Tento návod ukazuje vytváření datových vazeb k ovládacím prvkům v podokně Akce v aplikaci Microsoft Office Excel. Ovládací prvky ukazují záznamů master/detail relace mezi tabulkami v databázi serveru SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Přidání ovládacích prvků na list.  
  
-   Vytvoření ovládacího prvku podokna akcí.  
  
-   Přidání ovládacích prvků Windows Forms vázané na data do ovládacího prvku podokna akcí.  
  
-   Zobrazení podokna akcí při otevření aplikace.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Přístup k serveru s ukázkovou databází Northwind SQL Server.  
  
-   Oprávnění ke čtení a zápis do databáze serveru SQL Server.  
  
## <a name="create-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu sešitu aplikace Excel.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvořte projekt sešitu aplikace Excel s názvem **Moje podokně akcí aplikace Excel**. V průvodci vyberte **vytvoříte nový textový dokument**. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře nový sešit aplikace Excel v návrháři a přidá **Moje podokně akcí aplikace Excel** projektu **Průzkumníka řešení**.  
  
## <a name="add-a-new-data-source-to-the-project"></a>Přidat nový zdroj dat do projektu  
  
### <a name="to-add-a-new-data-source-to-the-project"></a>Chcete-li přidat nový zdroj dat do projektu  
  
1. Pokud **zdroje dat** okně není zobrazena, zobrazte ho tak, na panelu nabídek, výběrem **zobrazení** > **ostatní Windows**  >   **Zdroje dat**.  
  
2. Zvolte **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.  
  
3. Vyberte **databáze** a potom klikněte na tlačítko **Další**.  
  
4. Vyberte datové připojení k ukázkové databázi Northwind systému SQL Server, nebo přidejte nové připojení s použitím **nové připojení** tlačítko.  
  
5. Klikněte na tlačítko **Další**.  
  
6. Uložit připojení, pokud je zaškrtnuto a pak klikněte na tlačítko Vymazat **Další**.  
  
7. Rozbalte **tabulky** uzlu **databázové objekty** okna.  
  
8. Zaškrtněte políčko vedle položky **Dodavatelé** tabulky.  
  
9. Rozbalte **produkty** tabulce a vybrat **ProductName**, **KódDodavatele**, **QuantityPerUnit**, a **UnitPrice**.  
  
10. Klikněte na tlačítko **Dokončit**.  
  
    Průvodce přidá **dodavatelů** tabulky a **produkty** tabulky **zdroje dat** okno. Také přidá typové datové sady do projektu, který se zobrazuje **Průzkumníka řešení**.  
  
## <a name="add-controls-to-the-worksheet"></a>Přidání ovládacích prvků na list  
 V dalším kroku přidejte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku a <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku na první sešit.  
  
### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Chcete-li přidat ovládací prvek NamedRange a ovládacího prvku ListObject  
  
1.  Ověřte, že **Moje aplikace Excel akce Pane.xlsx** sešitu je otevřen v návrháři aplikace Visual Studio s `Sheet1` zobrazí.  
  
2.  V **zdroje dat** okna, rozbalte **Dodavatelé** tabulky.  
  
3.  Klikněte na šipku rozevíracího seznamu **název společnosti** uzlu a pak klikněte na tlačítko **NamedRange**.  
  
4.  Přetáhněte **název společnosti** z **zdroje dat** okno do buňky **A2** v `Sheet1`.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `CompanyNameNamedRange` je vytvořen a text \<NázevSpolečnosti > se zobrazí v buňce **A2**. Ve stejnou dobu <xref:System.Windows.Forms.BindingSource> s názvem `suppliersBindingSource`, tabulka adaptéru a <xref:System.Data.DataSet> jsou přidány do projektu. Ovládací prvek vázaný <xref:System.Windows.Forms.BindingSource>, která je dále vázán na <xref:System.Data.DataSet> instance.  
  
5.  V **zdroje dat** okna, procházejte minulé sloupce, které jsou pod správou **Dodavatelé** tabulky. V dolní části seznamu je **produkty** tabulky; je zde, protože je podřízeným prvkem **Dodavatelé** tabulky. Tuto možnost vyberte, **produkty** tabulky není ten, který je na stejné úrovni jako **Dodavatelé** tabulku a pak klikněte na šipku rozevíracího seznamu, který se zobrazí.  
  
6.  Klikněte na tlačítko **ListObject** v rozevíracím seznamu a pak přetáhněte **produkty** tabulky do buňky **A6** v `Sheet1`.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek s názvem `ProductNameListObject` se vytvoří v buňce **A6**. Ve stejnou dobu <xref:System.Windows.Forms.BindingSource> s názvem `productsBindingSource` a adaptér tabulky jsou přidány do projektu. Ovládací prvek vázaný <xref:System.Windows.Forms.BindingSource>, která je dále vázán na <xref:System.Data.DataSet> instance.  
  
7.  Pro C# pouze vyberte **suppliersBindingSource** na hlavní panel komponenty a změnit **modifikátory** vlastnost **interní** v **vlastnosti**  okna.  
  
## <a name="add-controls-to-the-actions-pane"></a>Přidání ovládacích prvků do podokna akcí  
 Dále je třeba prvek podokna akce, která má pole se seznamem.  
  
### <a name="to-add-an-actions-pane-control"></a>Chcete-li přidat ovládací prvek podokna akce  
  
1.  Vyberte **Moje podokně akcí aplikace Excel** projekt **Průzkumníka řešení**.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
3.  V **přidat novou položku** dialogu **ovládacího prvku podokna akcí**, pojmenujte ho **ActionsControl**a klikněte na tlačítko **přidat**.  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Chcete-li přidat ovládací prvky Windows Forms vázané na data na ovládací prvek podokna akce  
  
1.  Z **běžné ovládací prvky** karet **nástrojů**, přetáhněte <xref:System.Windows.Forms.ComboBox> ovládacího prvku do ovládacího prvku podokna akcí.  
  
2.  Změnit **velikost** vlastnost **171, 21**.  
  
3.  Změna velikosti uživatelského ovládacího prvku podle pole se seznamem.  
  
## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Vytvoření vazby ovládacího prvku v podokně Akce k datům  
 V této části budete nastavit zdroj dat <xref:System.Windows.Forms.ComboBox> ke stejnému zdroji dat, jako <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku na listu.  
  
### <a name="to-set-data-binding-properties-of-the-control"></a>Chcete-li nastavit vlastnosti datové vazby ovládacího prvku  
  
1.  Klikněte pravým tlačítkem na ovládací prvek podokna akce a potom klikněte na tlačítko **zobrazit kód**.  
  
2.  Přidejte následující kód, který <xref:System.Windows.Forms.UserControl.Load> události ovládacího prvku podokna akcí.  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  V C#, je nutné vytvořit obslužná rutina události `ActionsControl`. Tento kód v můžete umístit `ActionsControl` konstruktoru. Další informace o vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="show-the-actions-pane"></a>Zobrazit podokno akcí  
 V podokně Akce není zobrazen, dokud nepřidáte ovládacího prvku za běhu.  
  
#### <a name="to-show-the-actions-pane"></a>Chcete-li zobrazit podokno akcí  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na *ThisWorkbook.vb* nebo *ThisWorkbook.cs*a potom klikněte na tlačítko **zobrazit kód**.  
  
2.  Vytvořit novou instanci třídy uživatelského ovládacího prvku v `ThisWorkbook` třídy.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  V <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> obslužná rutina události `ThisWorkbook`, přidejte ovládací prvek do podokna akcí.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="test-the-application"></a>Testování aplikace  
 Nyní můžete otestovat dokumentu ověřte, že se otevře podokno akcí při otevření dokumentu, a zda mají ovládací prvky hlavní a podrobný vztah.  
  
### <a name="to-test-your-document"></a>K otestování vašeho dokumentu  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Potvrďte, že v podokně Akce je viditelný.  
  
3.  V rozevíracím seznamu vyberte společnost. Ověřte, zda název společnosti je uveden v <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku a, že jsou v uvedené podrobnosti o produktu <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku.  
  
4.  Vyberte různé společnosti, aby ověření názvu společnosti a podle potřeby změnit podrobnosti o produktu.  
  
## <a name="next-steps"></a>Další kroky  
 Tady jsou některé úlohy, které by mohl pocházet Další:  
  
-   Vazba dat k ovládacím prvkům v aplikaci Word. Další informace najdete v tématu [návod: vytvoření vazby dat s ovládacími prvky v podokně akcí aplikace Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   Nasazení projektu. Další informace najdete v tématu [nasazení řešení Office s použitím technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled podokna akcí](../vsto/actions-pane-overview.md)   
 [Postupy: Správa rozložení ovládacích prvků v podoknech akcí](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  