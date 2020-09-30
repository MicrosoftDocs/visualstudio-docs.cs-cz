---
title: 'Návod: komplexní datové vazby v projektech na úrovni dokumentu'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7aba307bcd76cc055e42c11418d42f3dd0cfba1f
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584318"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Návod: komplexní datové vazby v projektech na úrovni dokumentu
  Tento názorný postup ukazuje základy komplexních datových vazeb v projektech na úrovni dokumentu. V systém Microsoft Officeovém listu aplikace Excel můžete navazovat více buněk na pole v databázi Northwind SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- Přidání zdroje dat do projektu sešitu.

- Přidání ovládacích prvků vázaných na data do listu.

- Uložení změn dat zpět do databáze.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]:

- Přístup k serveru s ukázkovou databází Northwind SQL Server.

- Oprávnění ke čtení a zápisu do databáze SQL Server.

## <a name="create-a-new-project"></a>Vytvoření nového projektu
 Prvním krokem je vytvoření projektu excelového sešitu.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt sešitu aplikace Excel s názvem **Moje složitá datová vazba**. V průvodci vyberte možnost **vytvořit nový dokument**.

     Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový excelový sešit v návrháři a přidá projekt **Moje komplexní datové vazby** do **Průzkumník řešení**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat
 Pomocí okna **zdroje dat** přidejte do projektu typovou datovou sadu.

### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat

1. Pokud není okno **zdroje dat** viditelné, zobrazte ho tak, že v řádku nabídek vyberete možnost **Zobrazit**  >  **ostatní**  >  **zdroje dat**Windows.

2. Zvolením možnosti **Přidat nový zdroj dat** spusťte **Průvodce konfigurací zdroje dat**.

3. Vyberte **databáze** a pak klikněte na **Další**.

4. Vyberte datové připojení k ukázce databáze Northwind SQL Server databázi nebo přidejte nové připojení pomocí tlačítka **nové připojení** .

5. Po vybrání nebo vytvoření připojení klikněte na **Další**.

6. Zrušte zaškrtnutí políčka Uložit připojení, pokud je vybráno, a poté klikněte na tlačítko **Další**.

7. Rozbalte uzel **tabulky** v okně **objekty databáze** .

8. Zaškrtněte políčko vedle tabulky **Employees (zaměstnanci** ).

9. Klikněte na **Finish** (Dokončit).

   Průvodce přidá tabulku **Employees** do okna **zdroje dat** . Také přidá do projektu typovou datovou sadu, která je viditelná v **Průzkumník řešení**.

## <a name="add-controls-to-the-worksheet"></a>Přidat ovládací prvky do listu
 List se zobrazí v tabulce **Employees** při otevření sešitu. Uživatelé budou moci provádět změny dat a pak tyto změny uložit zpět do databáze kliknutím na tlačítko.

 Chcete-li vytvořit svázání listu s tabulkou automaticky, můžete přidat <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek do listu z okna **zdroje dat** . Chcete-li dát uživateli možnost Uložit změny, přidejte <xref:System.Windows.Forms.Button> ovládací prvek ze sady **nástrojů**.

#### <a name="to-add-a-list-object"></a>Přidání objektu seznamu

1. Ověřte, že je sešit **Moje komplexních dat Binding.xlsx** otevřený v návrháři sady Visual Studio a zobrazí se **List1** .

2. Otevřete okno **zdroje dat** a vyberte uzel **zaměstnanci** .

3. Klikněte na šipku rozevíracího seznamu, která se zobrazí.

4. V rozevíracím seznamu vyberte **ListObject** .

5. Přetáhněte tabulku **Employees** do buňky **a6**.

     <xref:Microsoft.Office.Tools.Excel.ListObject>Ovládací prvek s názvem `EmployeesListObject` je vytvořen v buňce **a6**. Ve stejnou dobu <xref:System.Windows.Forms.BindingSource> `EmployeesBindingSource` <xref:System.Data.DataSet> se do projektu přidají pouze pojmenované, adaptér s tabulkou a instance. Ovládací prvek je vázán na <xref:System.Windows.Forms.BindingSource> , který je zase svázán s <xref:System.Data.DataSet> instancí.

### <a name="to-add-a-button"></a>Přidání tlačítka

1. Na kartě **běžné ovládací prvky** **panelu nástrojů**přidejte <xref:System.Windows.Forms.Button> ovládací prvek do buňky **a4** listu.

   Dalším krokem je přidání textu na tlačítko při otevření listu.

## <a name="initialize-the-control"></a>Inicializace ovládacího prvku
 Přidejte text k tlačítku v <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obslužné rutině události.

### <a name="to-initialize-the-control"></a>Inicializace ovládacího prvku

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **List1. vb** nebo **Sheet1.cs**a pak klikněte na **Zobrazit kód** v místní nabídce.

2. Přidejte následující kód do `Sheet1_Startup` metody pro nastavení textu pro b `utton` .

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. Pouze pro C# přidejte do metody obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `Sheet1_Startup` .

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   Nyní přidejte kód pro zpracování <xref:System.Windows.Forms.Control.Click> události tlačítka.

## <a name="save-changes-to-the-database"></a>Uložení změn do databáze
 Všechny změny provedené v datech existují pouze v místní datové sadě, dokud nebudou explicitně uloženy zpět do databáze.

### <a name="to-save-changes-to-the-database"></a>Uložení změn do databáze

1. Přidejte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `button` a přidejte následující kód pro potvrzení všech změn, které byly provedeny v datové sadě zpět do databáze.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>Testování aplikace
 Nyní můžete testovat sešit a ověřit tak, že se data zobrazují podle očekávání a že můžete manipulovat s daty v objektu list.

### <a name="to-test-the-data-binding"></a>Otestování datové vazby

- Stiskněte klávesu **F5**.

     Ověřte, že po otevření sešitu je objekt list vyplněn daty z tabulky **Employees** .

### <a name="to-modify-data"></a>Úprava dat

1. Klikněte na buňka **B7**, která by měla obsahovat jméno **Chvojková**.

2. Zadejte název **Anderson**a stiskněte klávesu **ENTER**.

### <a name="to-modify-a-column-header"></a>Úprava záhlaví sloupce

1. Klikněte na buňku, která obsahuje záhlaví sloupce **LastName**.

2. Zadejte **příjmení**, včetně mezery mezi dvěma slovy, a potom stiskněte klávesu **ENTER**.

### <a name="to-save-data"></a>Uložení dat

1. V listu klikněte na **Uložit** .

2. Ukončete aplikaci Excel. Po zobrazení výzvy k uložení změn, které jste provedli, klikněte na tlačítko **ne** .

3. Stisknutím klávesy **F5** spusťte projekt znovu.

     Objekt list je vyplněn daty z tabulky **Employees** .

4. Všimněte si, že název v buňce **B7** je stále **Anderson**, což je změna dat, kterou jste provedli a uložili zpět do databáze. Záhlaví sloupce **LastName** se změnilo zpátky na původní formulář bez místa, protože záhlaví sloupce není vázané na databázi a změny, které jste provedli v listu, se neuložily.

### <a name="to-add-new-rows"></a>Přidání nových řádků

1. Vyberte buňku v rámci objektu list.

    Na konci seznamu se zobrazí nový řádek s hvězdičkou ( **\*** ) v první buňce nového řádku.

2. Do prázdného řádku přidejte následující informace.

   |EmployeeID|LastName|FirstName|Nadpis|
   |----------------|--------------|---------------|-----------|
   |10|Ito|Šu|Sales Manager|

### <a name="to-delete-rows"></a>Odstranění řádků

- Pravým tlačítkem myši klikněte na číslo 16 (řádek 16) na levé straně listu a pak klikněte na **Odstranit**.

### <a name="to-sort-the-rows-in-the-list"></a>Řazení řádků v seznamu

1. Vyberte buňku v seznamu.

     V záhlaví každého sloupce se zobrazí tlačítka se šipkami.

2. Klikněte na tlačítko se šipkou v záhlaví sloupce **příjmení** .

3. Klikněte na **Seřadit vzestupně**.

     Řádky jsou seřazené abecedně podle příjmení.

### <a name="to-filter-information"></a>Filtrování informací

1. Vyberte buňku v seznamu.

2. Klikněte na tlačítko se šipkou v záhlaví sloupce **nadpisu** .

3. Klikněte na **zástupce prodeje**.

     V seznamu se zobrazí pouze řádky, které mají **Prodejní zástupce** ve sloupci **název** .

4. Znovu klikněte na tlačítko se šipkou v záhlaví sloupce **nadpisu** .

5. Klikněte na tlačítko **(vše)**.

     Filtrování se odebere a zobrazí se všechny řádky.

## <a name="next-steps"></a>Další kroky
 Tento názorný postup ukazuje základy vazby tabulky v databázi na objekt seznamu. Tady jsou některé úkoly, které mohou být další:

- Ukládat data do mezipaměti, aby je bylo možné použít offline. Další informace najdete v tématu [Postupy: ukládání dat do mezipaměti pro použití v režimu offline nebo na serveru](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Nasaďte řešení. Další informace najdete v tématu [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

- Vytvoří vztah hlavní a podrobnosti mezi polem a tabulkou. Další informace najdete v tématu [Návod: Vytvoření vztahu hlavní podrobnosti pomocí datové sady uložené v mezipaměti](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).

## <a name="see-also"></a>Viz také
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)
- [Návod: jednoduché datové vazby v projektech na úrovni dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
