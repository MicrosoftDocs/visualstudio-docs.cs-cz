---
title: 'Návod: Jednoduché datové vazby v projektu doplňku VSTO'
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
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0373bcba5cecbbc47451f3ad050ba0ea44a12246
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672662"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Návod: Jednoduché datové vazby v projektu doplňku VSTO

Vytvoření vazby dat k hostitelské ovládací prvky a ovládacích prvků Windows Forms v projekty doplňku VSTO. Tento návod ukazuje, jak přidat ovládací prvky do dokumentu aplikace Microsoft Office Word a vytvoření vazby ovládacích prvků k datům za běhu.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

Tento návod znázorňuje následující úlohy:

-   Přidávání <xref:Microsoft.Office.Tools.Word.ContentControl> do dokumentu za běhu.

-   Vytváření <xref:System.Windows.Forms.BindingSource> ovládací prvek, který připojí k instanci objektu dataset.

-   Umožňuje uživateli procházet záznamy a zobrazení v ovládacím prvku.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

-   Přístup ke spuštěné instanci systému SQL Server 2005 nebo SQL Server 2005 Express, který má `AdventureWorksLT` ukázkovou databázi k němu připojená. Můžete stáhnout `AdventureWorksLT` databáze z [webu CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Další informace o připojení databáze naleznete v následujících tématech:

    -   Připojení databáze pomocí SQL Server Management Studio nebo SQL Server Management Studio Express, naleznete v tématu [postupy: připojení databáze (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

    -   Připojení databáze pomocí příkazového řádku, naleznete v tématu [postupy: připojení souboru databáze pro SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Prvním krokem je vytvoření projektu doplňku VSTO pro Word.

### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt

1.  Vytvoření projektu doplňku VSTO pro Word s názvem **naplnění dokumenty z databáze**, buď ve Visual Basicu nebo C#.

     Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře *ThisAddIn.vb* nebo *ThisAddIn.cs* soubor a přidá **naplnění dokumenty z databáze** projektu **Průzkumníka řešení** .

2.  Pokud váš projekt cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], přidejte odkaz na *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* sestavení. Tento odkaz vyžaduje programové přidání ovládacích prvků Windows Forms k dokumentu dál v tomto názorném postupu.

## <a name="create-a-data-source"></a>Vytvoření zdroje dat

Použití **zdroje dat** okno pro přidání typové datové sady do projektu.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Chcete-li přidat typové datové sady do projektu

1. Pokud **zdroje dat** okno se nezobrazuje, zobrazit ho tím, na panelu nabídek, výběrem **zobrazení** > **ostatní Windows**  >   **Zdroje dat**.

2. Zvolte **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.

3. Klikněte na tlačítko **databáze**a potom klikněte na tlačítko **Další**.

4. Pokud máte existující připojení, které `AdventureWorksLT` databázi, vyberte toto připojení a klikněte na tlačítko **Další**.

    V opačném případě klikněte na tlačítko **nové připojení**a použít **přidat připojení** dialogové okno pro vytvoření nového připojení. Další informace najdete v tématu [přidat nové připojení](../data-tools/add-new-connections.md).

5. V **uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na **Další**.

6. V **zvolte vaše databázové objekty** stránce, rozbalte **tabulky** a vyberte **zákazníků (SalesLT)**.

7. Klikněte na tlačítko **Dokončit**.

    *AdventureWorksLTDataSet.xsd* přidá soubor **Průzkumníka řešení**. Tento soubor definuje následující položky:

   - Typové datové sady s názvem `AdventureWorksLTDataSet`. Tato datová sada představuje obsah **zákazníků (SalesLT)** tabulky v databázi AdventureWorksLT.

   - TableAdapter s názvem `CustomerTableAdapter`. Této třídy TableAdapter lze číst a zapisovat data `AdventureWorksLTDataSet`. Další informace najdete v tématu [TableAdapter – přehled](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Obě tyto objekty použijete později v tomto názorném postupu.

## <a name="create-controls-and-binding-controls-to-data"></a>Vytvoření ovládacích prvků a vazba ovládacích prvků k datům

Rozhraní pro zobrazení záznamů databáze v tomto návodu je základní a vytvoří se přímo dokumentu. Jeden <xref:Microsoft.Office.Tools.Word.ContentControl> zobrazuje záznam izolované databáze na čas a dva <xref:Microsoft.Office.Tools.Word.Controls.Button> ovládací prvky umožňují procházet záznamy vpřed a zpět. Ovládací prvek obsahu používá <xref:System.Windows.Forms.BindingSource> pro připojení k databázi.

Další informace o vázání ovládacích prvků na data, najdete v části [vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-the-interface-in-the-document"></a>Chcete-li vytvořit rozhraní v dokumentu

1.  V `ThisAddIn` třídy, deklarujte následující ovládací prvky pro zobrazení a posuňte se `Customer` tabulku `AdventureWorksLTDataSet` databáze.

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2.  V `ThisAddIn_Startup` metodu, přidejte následující kód, který inicializovat datové sady, vyplňte datovou sadu s údaji ze `AdventureWorksLTDataSet` databáze.

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3.  Přidejte následující kód, který `ThisAddIn_Startup` metody. Tím se vygeneruje hostitelská položka, která rozšiřuje dokument. Další informace najdete v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4.  Definujte několik rozsahů na začátku dokumentu. Tyto rozsahy určit, kam chcete vložit text a umístit ovládací prvky.

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5.  Přidání ovládacích prvků rozhraní do dříve definovaného rozsahu.

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6.  Vytvoření vazby na ovládací prvek obsahu `AdventureWorksLTDataSet` pomocí <xref:System.Windows.Forms.BindingSource>. Pro C# vývojáři, přidání dvou ovladačů událostí pro <xref:Microsoft.Office.Tools.Word.Controls.Button> ovládacích prvků.

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7.  Přidejte následující kód k procházení databázových záznamů.

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>Testování v aplikaci

Při otevření aplikace Word, ovládací prvek obsahu zobrazuje data z `AdventureWorksLTDataSet` datové sady. Procházení databázových záznamů po kliknutí **Další** a **předchozí** tlačítka.

### <a name="to-test-the-vsto-add-in"></a>K otestování doplňku VSTO

1.  Stisknutím klávesy **F5**.

     Ovládací prvek obsahu s názvem `customerContentControl` se vytvoří a naplní daty. Současně, objekt datovou sadu s názvem `adventureWorksLTDataSet` a <xref:System.Windows.Forms.BindingSource> s názvem `customerBindingSource` jsou přidány do projektu. <xref:Microsoft.Office.Tools.Word.ContentControl> Je vázán na <xref:System.Windows.Forms.BindingSource>, která je dále vázán na objektu dataset.

2.  Klikněte na tlačítko **Další** a **předchozí** tlačítka Procházet záznamy v databázi.

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
- [Postupy: naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Použití místních souborů databáze v přehled řešení pro systém Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Přehled komponenty BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)