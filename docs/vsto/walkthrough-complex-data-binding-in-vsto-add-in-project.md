---
title: 'Návod: Rozšířené datové vazby v projektu doplňku VSTO'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af82d74c0e0a0446b759a06a9e874a39fc57b6fd
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672520"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Návod: Rozšířené datové vazby v projektu doplňku VSTO
  Vytvoření vazby dat k hostitelské ovládací prvky a ovládacích prvků Windows Forms v projekty doplňku VSTO. Tento návod ukazuje, jak přidat ovládací prvky na list aplikace Microsoft Office Excel a vytvoření vazby ovládacích prvků k datům v době běhu.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 Tento návod znázorňuje následující úlohy:

- Přidání <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku na list za běhu.

- Vytváření <xref:System.Windows.Forms.BindingSource> ovládací prvek, který připojí k instanci objektu dataset.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

-   Přístup ke spuštěné instanci systému SQL Server 2005 nebo SQL Server 2005 Express, který má `AdventureWorksLT` ukázkovou databázi k němu připojená. Můžete stáhnout `AdventureWorksLT` databáze z [webu CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Další informace o připojení databáze naleznete v následujících tématech:

    -   Připojení databáze pomocí SQL Server Management Studio nebo SQL Server Management Studio Express, naleznete v tématu [postupy: připojení databáze (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

    -   Připojení databáze pomocí příkazového řádku, naleznete v tématu [postupy: připojení souboru databáze pro SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Vytvoření nového projektu
 Prvním krokem je vytvoření projektu doplňku VSTO v Excelu.

### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt

1.  Vytvoření projektu doplňku VSTO pro Excel s názvem **naplnění listů z databáze**, buď ve Visual Basicu nebo C#.

     Další informace najdete v tématu [postupy: vytváření projektů pro Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře `ThisAddIn.vb` nebo `ThisAddIn.cs` soubor a přidá **naplnění listů z databáze** projektu **Průzkumníka řešení**.

## <a name="create-a-data-source"></a>Vytvoření zdroje dat
 Použití **zdroje dat** okno pro přidání typové datové sady do projektu.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Chcete-li přidat typové datové sady do projektu

1. Pokud **zdroje dat** okno se nezobrazuje, zobrazit ho tím, na panelu nabídek, výběrem **zobrazení** > **ostatní Windows**  >   **Zdroje dat**.

2. Zvolte **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.

3. Klikněte na tlačítko **databáze**a potom klikněte na tlačítko **Další**.

4. Pokud máte existující připojení, které `AdventureWorksLT` databázi, vyberte toto připojení a klikněte na tlačítko **Další**.

    V opačném případě klikněte na tlačítko **nové připojení**a použít **přidat připojení** dialogové okno pro vytvoření nového připojení. Další informace najdete v tématu [přidat nové připojení](../data-tools/add-new-connections.md).

5. V **uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na **Další**.

6. V **zvolte vaše databázové objekty** stránce, rozbalte **tabulky** a vyberte **adresu (SalesLT)**.

7. Klikněte na tlačítko **Dokončit**.

    *AdventureWorksLTDataSet.xsd* přidá soubor **Průzkumníka řešení**. Tento soubor definuje následující položky:

   - Typové datové sady s názvem `AdventureWorksLTDataSet`. Tato datová sada představuje obsah **adresu (SalesLT)** tabulky v databázi AdventureWorksLT.

   - TableAdapter s názvem `AddressTableAdapter`. Této třídy TableAdapter lze číst a zapisovat data `AdventureWorksLTDataSet`. Další informace najdete v tématu [TableAdapter – přehled](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Obě tyto objekty použijete později v tomto názorném postupu.

## <a name="create-controls-and-bind-controls-to-data"></a>Vytvoření ovládacích prvků a vytvoření vazby ovládacích prvků k datům
 V tomto návodu <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek zobrazí všechna data v tabulce vybrali ihned poté, co uživatel otevře sešit. Používá seznam objektů <xref:System.Windows.Forms.BindingSource> pro ovládací prvek připojení k databázi.

 Další informace o vázání ovládacích prvků na data, najdete v části [vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Chcete-li přidat objekt seznamu, datová sada a tabulky adaptéru

1.  V `ThisAddIn` třídy, deklarujte následující ovládacích prvků pro zobrazení `Address` tabulku `AdventureWorksLTDataSet` datové sady.

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2.  V `ThisAddIn_Startup` metodu, přidejte následující kód k inicializaci datovou sadu a datovou sadu naplnit informace z `AdventureWorksLTDataSet` datové sady.

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3.  Přidejte následující kód, který `ThisAddIn_Startup` metody. Tím se vygeneruje hostitelská položka, která rozšiřuje listu. Další informace najdete v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4.  Vytvořit rozsah a přidejte <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku.

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5.  Vytvoření vazby objektem seznamu k `AdventureWorksLTDataSet` pomocí <xref:System.Windows.Forms.BindingSource>. Předejte názvy sloupců, které chcete svázat s objektem seznamu.

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>Testování v aplikaci
 Při otevření aplikace Excel, <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek zobrazí data z `Address` tabulku `AdventureWorksLTDataSet` datové sady.

### <a name="to-test-the-vsto-add-in"></a>K otestování doplňku VSTO

-   Stisknutím klávesy **F5**.

     A <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek s názvem `addressListObject` se vytvoří v listu. Současně, objekt datovou sadu s názvem `adventureWorksLTDataSet` a <xref:System.Windows.Forms.BindingSource> s názvem `addressBindingSource` jsou přidány do projektu. <xref:Microsoft.Office.Tools.Excel.ListObject> Je vázán na <xref:System.Windows.Forms.BindingSource>, která je dále vázán na objektu dataset.

## <a name="see-also"></a>Viz také:

- [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)
- [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Postupy: naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Postupy: naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Postupy: naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Postupy: naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Postupy: procházení databázových záznamů na listu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Návod: Jednoduché datové vazby v projektech na úrovni dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Návod: Rozšířené datové vazby v projektech na úrovni dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Použití místních souborů databáze v přehled řešení pro systém Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md)
- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Použití místních souborů databáze v přehled řešení pro systém Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Přehled komponenty BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)