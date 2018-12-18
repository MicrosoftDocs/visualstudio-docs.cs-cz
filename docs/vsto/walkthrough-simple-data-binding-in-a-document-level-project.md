---
title: 'Návod: Jednoduché datové vazby v projektech na úrovni dokumentu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25173e5c4d4aeb02045cf858ae1e093b7a04d2bb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824372"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Návod: Jednoduché datové vazby v projektech na úrovni dokumentu
  Tento návod ukazuje základní informace o datové vazby v projektech úrovni dokumentu. Jedno datové pole v databázi serveru SQL Server je vázán na pojmenované oblasti v aplikaci Microsoft Office Excel. Návod také ukazuje, jak přidat ovládací prvky, které vám umožní procházet všechny záznamy v tabulce.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- Vytváření zdroje dat pro projektu aplikace Excel.  
  
- Přidání ovládacích prvků na list.  
  
- Posouvání záznamů databáze.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Přístup k serveru s ukázkovou databází Northwind SQL Server.  
  
-   Oprávnění ke čtení a zápis do databáze serveru SQL Server.  
  
## <a name="create-a-new-project"></a>Vytvoření nového projektu  
 V tomto kroku vytvoříte projektu sešitu aplikace Excel.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1. Vytvořte projekt sešitu aplikace Excel s názvem **Moje jednoduché datové vazby**, buď ve Visual Basicu nebo C#. Ujistěte se, že **vytvoříte nový textový dokument** zaškrtnuto. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
   Visual Studio otevře nový sešit aplikace Excel v návrháři a přidá **Moje jednoduché datové vazby** projektu **Průzkumníka řešení**.  
  
## <a name="create-the-data-source"></a>Vytvoření zdroje dat  
 Použití **zdroje dat** okno pro přidání typové datové sady do projektu.  
  
### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1. Pokud **zdroje dat** okno se nezobrazuje, zobrazit ho tím, na panelu nabídek, výběrem **zobrazení** > **ostatní Windows**  >   **Zdroje dat**.  
  
2. Zvolte **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.  
  
3. Vyberte **databáze** a potom klikněte na tlačítko **Další**.  
  
4. Vyberte datové připojení k ukázkové databázi Northwind systému SQL Server, nebo přidejte nové připojení pomocí **nové připojení** tlačítko.  
  
5. Po připojení se vyberete nebo vytvoříte, klikněte na tlačítko **Další**.  
  
6. Uložit připojení, pokud je zaškrtnuto a pak klikněte na tlačítko Vymazat **Další**.  
  
7. Rozbalte **tabulky** uzlu **databázové objekty** okna.  
  
8. Zaškrtněte políčko vedle položky **zákazníkům** tabulky.  
  
9. Klikněte na tlačítko **Dokončit**.  
  
   Průvodce přidá **zákazníkům** tabulky **zdroje dat** okna. Také přidá typové datové sady do projektu, který se zobrazuje **Průzkumníka řešení**.  
  
## <a name="add-controls-to-the-worksheet"></a>Přidání ovládacích prvků na list  
 V tomto návodu budete potřebovat dva pojmenované oblasti a čtyři tlačítka na první sešit. Nejprve přidejte dva pojmenované oblasti od **zdroje dat** okna tak, aby se automaticky vázán na zdroj dat. V dalším kroku přidejte tlačítka z **nástrojů**.  
  
### <a name="to-add-two-named-ranges"></a>Chcete-li přidat dva pojmenované oblasti  
  
1.  Ověřte, že *Moje jednoduché Binding.xlsx Data* sešitu je otevřen v návrháři aplikace Visual Studio s **List1** zobrazí.  
  
2.  Otevřít **zdroje dat** okno a rozbalte **zákazníkům** uzlu.  
  
3.  Vyberte **CompanyName** sloupce a potom klikněte na šipku rozevíracího seznamu, který se zobrazí.  
  
4.  Vyberte **NamedRange** v rozevíracím seznamu a pak přetáhněte **CompanyName** sloupce do buňky **A1**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `companyNameNamedRange` se vytvoří v buňce **A1**. Ve stejnou dobu <xref:System.Windows.Forms.BindingSource> s názvem `customersBindingSource`, tabulka adaptéru a <xref:System.Data.DataSet> instance jsou přidány do projektu. Ovládací prvek vázaný <xref:System.Windows.Forms.BindingSource>, která je dále vázán na <xref:System.Data.DataSet> instance.  
  
5.  Vyberte **CustomerID** sloupec **zdroje dat** okna a potom klikněte na šipku rozevíracího seznamu, který se zobrazí.  
  
6.  Klikněte na tlačítko **NamedRange** v rozevíracím seznamu a pak přetáhněte **CustomerID** sloupce do buňky **B1**.  
  
7.  Jiné <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `customerIDNamedRange` se vytvoří v buňce **B1**a vázaný k <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="to-add-four-buttons"></a>Chcete-li přidat čtyři tlačítka  
  
1. Z **běžné ovládací prvky** karty **nástrojů**, přidat <xref:System.Windows.Forms.Button> ovládacího prvku do buňky **A3** listu.  
  
    Toto tlačítko nazývalo `Button1`.  
  
2. Tak, aby byly názvy, jak je znázorněno, přidejte další tři tlačítka na následující buňky v tomto pořadí:  
  
   |Buňky|(Název)|  
   |----------|--------------|  
   |B3|BUTTON2|  
   |C3|Button3|  
   |D3|Button4|  
  
   Dalším krokem je přidání textu, tlačítek a v C# přidat obslužné rutiny událostí.  
  
## <a name="initialize-the-controls"></a>Inicializovat ovládací prvky  
 Nastavení textu tlačítka a přidejte obslužné rutiny událostí během <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> událostí.  
  
### <a name="to-initialize-the-controls"></a>Inicializovat ovládací prvky  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Sheet1.vb** nebo **Sheet1.cs**a potom klikněte na tlačítko **zobrazit kód** v místní nabídce.  
  
2. Přidejte následující kód, který `Sheet1_Startup` metody nastavte text pro každé tlačítko.  
  
    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3. Jenom v C#, přidejte obslužné rutiny události pro tlačítko klikněte na události `Sheet1_Startup` metody.  
  
    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
   Teď přidejte kód pro zpracování <xref:System.Windows.Forms.Control.Click> události tlačítka tak, aby uživatel může procházet záznamy.  
  
## <a name="add-code-to-enable-scrolling-through-the-records"></a>Přidejte kód umožňující posouvání záznamů  
 Přidejte kód, který <xref:System.Windows.Forms.Control.Click> obslužná rutina události z každé tlačítko pro procházení záznamů.  
  
### <a name="to-move-to-the-first-record"></a>Chcete-li přesunout na první záznam  
  
1.  Přidat obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `Button1` tlačítko a přidejte následující kód přesunout na první záznam:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
### <a name="to-move-to-the-previous-record"></a>Chcete-li přesunout na předchozí záznam  
  
1.  Přidat obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `Button2` tlačítko a přidejte následující kód k přesunutí pozici zpět o jednu:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
### <a name="to-move-to-the-next-record"></a>Chcete-li přesunout na další záznam  
  
1.  Přidat obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `Button3` tlačítko a přidejte následující kód k přechodu na pozici jednou:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
### <a name="to-move-to-the-last-record"></a>Chcete-li přesunout na poslední záznam  
  
1.  Přidat obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `Button4` tlačítko a přidejte následující kód přesunout na poslední záznam:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="test-the-application"></a>Testování aplikace  
 Nyní můžete otestovat sešitu, abyste měli jistotu, že při procházení záznamů v databázi.  
  
### <a name="to-test-your-workbook"></a>K otestování vašeho sešitu  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Potvrďte, že první záznam se zobrazí v buňkách **A1** a **B1**.  
  
3.  Klikněte na tlačítko **>** (`Button3`) tlačítko a potvrďte, že další záznam se zobrazí v buňce **A1** a **B1**.  
  
4.  Pomocí tlačítek jiné posuňte potvrďte, že záznam změní podle očekávání.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod ukazuje základní informace o vytvoření vazby pojmenované oblasti na pole v databázi. Tady jsou některé úlohy, které by mohl pocházet Další:  
  
-   Data do mezipaměti tak, aby ho můžete použít v režimu offline. Další informace najdete v tématu [jak: mezipaměti dat pro použití v režimu offline nebo na serveru](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Vytvoření vazby buňky do více sloupců v tabulce, místo na jedno pole. Další informace najdete v tématu [návod: rozšířené datové vazby v projektech na úrovni dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Použití <xref:System.Windows.Forms.BindingNavigator> ovládací prvek pro procházení záznamů. Další informace najdete v tématu [postupy: navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Viz také:  
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)   
 [Návod: Rozšířené datové vazby v projektech na úrovni dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  