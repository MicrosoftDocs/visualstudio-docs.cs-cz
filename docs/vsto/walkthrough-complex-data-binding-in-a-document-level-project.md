---
title: 'Návod: Rozšířené datové vazby v projektech na úrovni dokumentu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6886908f01ceaeb36ed83ba0970ef250873d69c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841881"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Návod: Rozšířené datové vazby v projektech na úrovni dokumentu
  Tento návod ukazuje základní informace o rozšířené datové vazby v projektech na úrovni dokumentu. Více buněk v listu aplikace Microsoft Office Excel můžete vázat na pole v databázi Northwind SQL serveru.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- Přidání zdroje dat do sešitu projektu.  
  
- Přidání ovládacích prvků vázaných na data na listu.  
  
- Ukládají se změny dat zpět do databáze.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Přístup k serveru s ukázkovou databází Northwind SQL Server.  
  
-   Oprávnění ke čtení a zápis do databáze serveru SQL Server.  
  
## <a name="create-a-new-project"></a>Vytvoření nového projektu  
 Prvním krokem je vytvoření projektu sešitu aplikace Excel.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvořte projekt sešitu aplikace Excel s názvem **Moje složité datové vazby**. V průvodci vyberte **vytvoříte nový textový dokument**.  
  
     Další informace najdete v tématu [postupy: vytváření projektů pro Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře nový sešit aplikace Excel v návrháři a přidá **Moje složité datové vazby** projektu **Průzkumníka řešení**.  
  
## <a name="create-the-data-source"></a>Vytvoření zdroje dat  
 Použití **zdroje dat** okno pro přidání typové datové sady do projektu.  
  
### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1. Pokud **zdroje dat** okno se nezobrazuje, zobrazit ho tím, na panelu nabídek, výběrem **zobrazení** > **ostatní Windows**  >   **Zdroje dat**.  
  
2. Zvolte **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.  
  
3. Vyberte **databáze** a potom klikněte na tlačítko **Další**.  
  
4. Vyberte datové připojení k ukázkové databázi Northwind systému SQL Server, nebo přidejte nové připojení s použitím **nové připojení** tlačítko.  
  
5. Po připojení se vyberete nebo vytvoříte, klikněte na tlačítko **Další**.  
  
6. Uložit připojení, pokud je zaškrtnuto a pak klikněte na tlačítko Vymazat **Další**.  
  
7. Rozbalte **tabulky** uzlu **databázové objekty** okna.  
  
8. Zaškrtněte políčko vedle položky **zaměstnanci** tabulky.  
  
9. Klikněte na tlačítko **Dokončit**.  
  
   Průvodce přidá **zaměstnanci** tabulky **zdroje dat** okna. Také přidá typové datové sady do projektu, který se zobrazuje **Průzkumníka řešení**.  
  
## <a name="add-controls-to-the-worksheet"></a>Přidání ovládacích prvků na list  
 Na listu se zobrazí **zaměstnanci** tabulky při otevření sešitu. Uživatelé budou moci měnit data a pak klepnutím na tlačítko Uložit tyto změny zpět do databáze.  
  
 Chcete-li vytvořit vazbu listu do tabulky automaticky, můžete přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku do listu z **zdroje dat** okno. Chcete-li umožnit uživateli uložit změny, přidejte <xref:System.Windows.Forms.Button> řízení z **nástrojů**.  
  
#### <a name="to-add-a-list-object"></a>Chcete-li přidat objekt seznamu  
  
1.  Ověřte, že **Moje komplexní Data Binding.xlsx** sešitu je otevřen v návrháři aplikace Visual Studio s **List1** zobrazí.  
  
2.  Otevřít **zdroje dat** okna a vyberte **zaměstnanci** uzlu.  
  
3.  Klikněte na šipku rozevíracího seznamu, který se zobrazí.  
  
4.  Vyberte **ListObject** v rozevíracím seznamu.  
  
5.  Přetáhněte **zaměstnanci** tabulky do buňky **A6**.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek s názvem `EmployeesListObject` se vytvoří v buňce **A6**. Ve stejnou dobu <xref:System.Windows.Forms.BindingSource> s názvem `EmployeesBindingSource`, tabulka adaptéru a <xref:System.Data.DataSet> instance jsou přidány do projektu. Ovládací prvek vázaný <xref:System.Windows.Forms.BindingSource>, která je dále vázán na <xref:System.Data.DataSet> instance.  
  
### <a name="to-add-a-button"></a>Přidání tlačítka  
  
1. Z **běžné ovládací prvky** karty **nástrojů**, přidat <xref:System.Windows.Forms.Button> ovládacího prvku do buňky **A4** listu.  
  
   Dalším krokem je přidání textu k tlačítku po otevření sešitu.  
  
## <a name="initialize-the-control"></a>Inicializovat ovládací prvek  
 Přidejte text pro tlačítko v <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obslužné rutiny události.  
  
### <a name="to-initialize-the-control"></a>Chcete-li inicializovat ovládací prvek  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Sheet1.vb** nebo **Sheet1.cs**a potom klikněte na tlačítko **zobrazit kód** v místní nabídce.  
  
2. Přidejte následující kód, který `Sheet1_Startup` metodu a nastavit text pro b tak`utton`.  
  
    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]  
  
3. Jenom v C#, přidejte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost, abyste `Sheet1_Startup` metody.  
  
    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]  
  
   Teď přidejte kód pro zpracování <xref:System.Windows.Forms.Control.Click> událost tlačítka.  
  
## <a name="save-changes-to-the-database"></a>Uložte změny do databáze  
 Všechny změny se provedly pro data existují pouze v místní datové sady, dokud jsou explicitně uložena zpět do databáze.  
  
### <a name="to-save-changes-to-the-database"></a>Uložte změny do databáze  
  
1.  Přidat obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `button`a přidejte následující kód k provedení všech změn, které byly provedeny v datové sadě zpět do databáze.  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]  
  
## <a name="test-the-application"></a>Testování aplikace  
 Nyní můžete otestovat sešit k ověření, že se zobrazí data podle očekávání a že můžete pracovat s daty v objektu seznamu.  
  
### <a name="to-test-the-data-binding"></a>Můžete otestovat vazbu dat  
  
-   Stisknutím klávesy **F5**.  
  
     Ověřte, že po otevření sešitu objekt seznam je vyplněn daty z **zaměstnanci** tabulky.  
  
### <a name="to-modify-data"></a>Úprava dat  
  
1.  Klikněte na buňku **B7**, který by měl obsahovat název **Davolio**.  
  
2.  Zadejte název **Anderson**a potom stiskněte klávesu **Enter**.  
  
### <a name="to-modify-a-column-header"></a>Chcete-li změnit záhlaví sloupce  
  
1.  Klikněte na buňku, která obsahuje hlavičku sloupce **LastName**.  
  
2.  Typ **příjmení**, včetně mezery mezi slovy dvě a potom stiskněte klávesu **Enter**.  
  
### <a name="to-save-data"></a>Chcete-li uložit data  
  
1.  Klikněte na tlačítko **Uložit** na listu.  
  
2.  Ukončete aplikaci Excel. Klikněte na tlačítko **ne** po zobrazení výzvy se uložit provedené změny.  
  
3.  Stisknutím klávesy **F5** spusťte projekt znovu.  
  
     Objekt seznam je vyplněn daty z **zaměstnanci** tabulky.  
  
4.  Všimněte si, že název v buňce **B7** je stále **Anderson**, které jsou data změnit provedli a uložili zpět do databáze. Záhlaví sloupce **LastName** má změnit zpět na původní podobě bez mezer, protože databáze není vázán na záhlaví sloupce a nebyla uložena změny provedené v listu.  
  
### <a name="to-add-new-rows"></a>Chcete-li přidat nové řádky  
  
1. Zvolte buňky uvnitř seznamu objektů.  
  
    Zobrazí se nový řádek v dolní části seznamu s hvězdičkou (**\\***) do první buňky nový řádek.  
  
2. V prázdném řádku, přidejte následující informace.  
  
   |EmployeeID|Příjmení|Jméno|Název|  
   |----------------|--------------|---------------|-----------|  
   |10|Šmídová|Šu|Prodejní manažer|  
  
### <a name="to-delete-rows"></a>Chcete-li odstranit řádky  
  
-   Klikněte pravým tlačítkem na číslo 16 (řádek 16) na levé listu a potom klikněte na tlačítko **odstranit**.  
  
### <a name="to-sort-the-rows-in-the-list"></a>Chcete-li seřadit řádky v seznamu  
  
1.  Zvolte buňky uvnitř seznamu.  
  
     Tlačítek se zobrazí v záhlaví jednotlivých sloupců.  
  
2.  Klikněte na tlačítko se šipkou v **příjmení** záhlaví sloupce.  
  
3.  Klikněte na tlačítko **seřadit vzestupně**.  
  
     Řádky jsou seřazená podle abecedy podle příjmení.  
  
### <a name="to-filter-information"></a>Pro filtrování informací  
  
1.  Zvolte buňky uvnitř seznamu.  
  
2.  Klikněte na tlačítko se šipkou v **název** záhlaví sloupce.  
  
3.  Klikněte na tlačítko **zástupce**.  
  
     V seznamu se zobrazí pouze řádky, které obsahují **prodejní zástupce** v **název** sloupce.  
  
4.  Klikněte na tlačítko se šipkou v **název** znovu záhlaví sloupce.  
  
5.  Klikněte na tlačítko **(vše)**.  
  
     Filtrování se odebere a zobrazí všechny řádky.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod ukazuje základy vazby tabulky v databázi s objektem seznamu. Tady jsou některé úlohy, které by mohl pocházet Další:  
  
-   Data do mezipaměti tak, aby ho můžete použít v režimu offline. Další informace najdete v tématu [jak: mezipaměti dat pro použití v režimu offline nebo na serveru](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Nasazení řešení. Další informace najdete v tématu [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
-   Vytvoření záznamů master/detail vztah mezi polem a tabulku. Další informace najdete v tématu [návod: vytvoření hlavního podrobný vztah pomocí datové sady v mezipaměti](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).  
  
## <a name="see-also"></a>Viz také:  
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)   
 [Návod: Jednoduché datové vazby v projektech na úrovni dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  