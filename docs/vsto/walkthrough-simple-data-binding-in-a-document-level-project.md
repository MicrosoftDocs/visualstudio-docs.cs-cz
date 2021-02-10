---
title: 'Návod: jednoduché datové vazby v projektech na úrovni dokumentu'
description: Naučte se základy datových vazeb v projektech na úrovni dokumentu a že jedno datové pole v SQL Server databázi je vázáno na pojmenovaný rozsah v aplikaci Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 31084703a581999a1f25bfc82db6c36d9e2cbf6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937405"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Návod: jednoduché datové vazby v projektech na úrovni dokumentu
  Tento návod ukazuje základy datové vazby v projektu na úrovni dokumentu. Jedno datové pole v databázi SQL Server je svázáno s pojmenovaným rozsahem v systém Microsoft Office Excel. Návod také ukazuje, jak přidat ovládací prvky, které umožňují procházet všechny záznamy v tabulce.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- Vytvoření zdroje dat pro projekt aplikace Excel.

- Přidávání ovládacích prvků do listu.

- Procházení záznamů databáze.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]:

- Přístup k serveru s ukázkovou databází Northwind SQL Server.

- Oprávnění ke čtení a zápisu do databáze SQL Server.

## <a name="create-a-new-project"></a>Vytvoření nového projektu
 V tomto kroku vytvoříte projekt sešitu aplikace Excel.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt sešitu aplikace Excel s názvem **moje jednoduchá datová vazba**, a to pomocí Visual Basic nebo C#. Ujistěte se, že je vybraná možnost **vytvořit nový dokument** . Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio otevře nový excelový sešit v návrháři a přidá projekt **Moje jednoduché datové vazby** do **Průzkumník řešení**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat
 Pomocí okna **zdroje dat** přidejte do projektu typovou datovou sadu.

### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat

1. Pokud není okno **zdroje dat** viditelné, zobrazte ho tak, že v řádku nabídek vyberete možnost **Zobrazit**  >  **ostatní**  >  **zdroje dat** Windows.

2. Zvolením možnosti **Přidat nový zdroj dat** spusťte **Průvodce konfigurací zdroje dat**.

3. Vyberte **databáze** a pak klikněte na **Další**.

4. Vyberte datové připojení k ukázce databáze Northwind SQL Server databázi nebo přidejte nové připojení pomocí tlačítka **nové připojení** .

5. Po vybrání nebo vytvoření připojení klikněte na **Další**.

6. Zrušte zaškrtnutí políčka Uložit připojení, pokud je vybráno, a poté klikněte na tlačítko **Další**.

7. Rozbalte uzel **tabulky** v okně **objekty databáze** .

8. Zaškrtněte políčko vedle tabulky **Customers (zákazníci** ).

9. Klikněte na **Finish** (Dokončit).

   Průvodce přidá tabulku **Customers** do okna **zdroje dat** . Také přidá do projektu typovou datovou sadu, která je viditelná v **Průzkumník řešení**.

## <a name="add-controls-to-the-worksheet"></a>Přidat ovládací prvky do listu
 V tomto návodu budete potřebovat dva pojmenované rozsahy a čtyři tlačítka na prvním listu. Nejprve přidejte tyto dva pojmenované rozsahy z okna **zdroje dat** tak, aby byly automaticky svázány se zdrojem dat. Dále přidejte tlačítka ze **sady nástrojů**.

### <a name="to-add-two-named-ranges"></a>Přidání dvou pojmenovaných rozsahů

1. Ověřte, že je v návrháři sady Visual Studio otevřený sešit *moje jednoduchá Data Binding.xlsx* , a zobrazí se **List1** .

2. Otevřete okno **zdroje dat** a rozbalte uzel **Customers (zákazníci** ).

3. Vyberte sloupec **CompanyName** a potom klikněte na šipku rozevíracího seznamu, která se zobrazí.

4. V rozevíracím seznamu vyberte **NamedRange** a potom přetáhněte sloupec **CompanyName** do buňky **a1**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Ovládací prvek s názvem `companyNameNamedRange` je vytvořen v buňce **a1**. Ve stejnou dobu <xref:System.Windows.Forms.BindingSource> `customersBindingSource` <xref:System.Data.DataSet> se do projektu přidají pouze pojmenované, adaptér s tabulkou a instance. Ovládací prvek je vázán na <xref:System.Windows.Forms.BindingSource> , který je zase svázán s <xref:System.Data.DataSet> instancí.

5. V okně **zdroje dat** vyberte sloupec **CustomerID** a potom klikněte na šipku rozevíracího seznamu, která se zobrazí.

6. V rozevíracím seznamu klikněte na **NamedRange** a potom přetáhněte sloupec **KódZákazníka** na buňku **B1**.

7. <xref:Microsoft.Office.Tools.Excel.NamedRange> `customerIDNamedRange` V buňce **B1** je vytvořen jiný ovládací prvek s názvem a svázán s <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-four-buttons"></a>Přidání čtyř tlačítek

1. Na kartě **běžné ovládací prvky** **panelu nástrojů** přidejte <xref:System.Windows.Forms.Button> ovládací prvek do buňky **a3** listu.

    Toto tlačítko má název `Button1` .

2. Přidejte tři další tlačítka do následujících buněk v tomto pořadí, aby se názvy zobrazovaly takto:

   |Mobilní telefon|(Název)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   Dalším krokem je přidání textu do tlačítek a v jazyce C# přidat obslužné rutiny událostí.

## <a name="initialize-the-controls"></a>Inicializovat ovládací prvky
 Nastavte text tlačítka a přidejte obslužné rutiny události během <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> události.

### <a name="to-initialize-the-controls"></a>Inicializace ovládacích prvků

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **List1. vb** nebo **Sheet1.cs** a pak klikněte na **Zobrazit kód** v místní nabídce.

2. Přidejte následující kód do `Sheet1_Startup` metody pro nastavení textu pro každé tlačítko.

    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]

3. Pouze pro C# přidejte obslužné rutiny události pro události kliknutí na tlačítko do `Sheet1_Startup` metody.

    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]

   Nyní přidejte kód pro zpracování <xref:System.Windows.Forms.Control.Click> událostí tlačítek, aby uživatel mohl procházet záznamy.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Přidejte kód, který umožní procházení záznamů.
 Přidejte kód do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro každé tlačítko pro přesun záznamů.

### <a name="to-move-to-the-first-record"></a>Přechod na první záznam

1. Přidejte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `Button1` tlačítka a přidejte následující kód, který se přesune k prvnímu záznamu:

     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]

### <a name="to-move-to-the-previous-record"></a>Přechod na předchozí záznam

1. Přidejte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `Button2` tlačítka a přidejte následující kód pro přesunutí pozice zpět o jednu:

     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]

### <a name="to-move-to-the-next-record"></a>Přechod na další záznam

1. Přidejte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `Button3` tlačítka a přidejte následující kód pro posunutí pozice o jednu:

     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]

### <a name="to-move-to-the-last-record"></a>Přechod na poslední záznam

1. Přidejte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `Button4` tlačítka a přidejte následující kód, který bude přesunut na poslední záznam:

     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]

## <a name="test-the-application"></a>Testování aplikace
 Nyní můžete otestovat sešit, abyste se ujistili, že můžete procházet záznamy v databázi.

### <a name="to-test-your-workbook"></a>Test sešitu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Potvrďte, že se první záznam zobrazuje v buňkách **a1** a **B1**.

3. Klikněte na **>** `Button3` tlačítko () a potvrďte, že se další záznam zobrazí v buňce **a1** a **B1**.

4. Kliknutím na další tlačítka posunu potvrďte, že se záznam mění podle očekávání.

## <a name="next-steps"></a>Další kroky
 Tento názorný postup ukazuje základy vazby pojmenovaného rozsahu na pole v databázi. Tady jsou některé úkoly, které mohou být další:

- Ukládat data do mezipaměti, aby je bylo možné použít offline. Další informace najdete v tématu [Postupy: ukládání dat do mezipaměti pro použití v režimu offline nebo na serveru](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Umožňuje navazovat buňky na více sloupců v tabulce místo do jednoho pole. Další informace najdete v tématu [Návod: složitá datová vazba v projektu na úrovni dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).

- Procházejte <xref:System.Windows.Forms.BindingNavigator> záznamy pomocí ovládacího prvku. Další informace najdete v tématu [Postup: navigace v datech pomocí ovládacího prvku BindingNavigator model Windows Forms](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Viz také
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)
- [Návod: komplexní datové vazby v projektech na úrovni dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
