---
title: 'Návod: Jednoduchá datová vazba v projektu doplňku VSTO'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0e174782c46d24b7743d50faa9fac69d38c3d6c6
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255184"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Návod: Jednoduchá datová vazba v projektu doplňku VSTO

Můžete navazovat data na hostitelské ovládací prvky a model Windows Forms ovládací prvky v projektech doplňku VSTO. Tento návod ukazuje, jak přidat ovládací prvky do systém Microsoft Office dokumentu aplikace Word a navazovat ovládací prvky na data v době běhu.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

Tento návod znázorňuje následující úlohy:

- <xref:Microsoft.Office.Tools.Word.ContentControl> Přidání k dokumentu v době běhu.

- Vytvoření objektu <xref:System.Windows.Forms.BindingSource> , který spojuje ovládací prvek s instancí datové sady.

- Povoluje uživateli procházení záznamů a jejich zobrazení v ovládacím prvku.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Přístup ke spuštěné instanci SQL Server 2005 nebo SQL Server 2005 Express s `AdventureWorksLT` připojenou ukázkovou databází. `AdventureWorksLT` Databázi si můžete stáhnout z [webu CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Další informace o připojení databáze najdete v následujících tématech:

  - Postup připojení databáze pomocí SQL Server Management Studio nebo SQL Server Management Studio Express najdete v tématu [How to: Připojit databázi (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Postup připojení databáze pomocí příkazového řádku najdete v tématu [How to: Připojte k SQL Server Express](/previous-versions/sql/)databázový soubor.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Prvním krokem je vytvoření projektu doplňku VSTO aplikace Word.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt doplňku VSTO aplikace Word s názvem **vyplňování dokumentů z databáze**pomocí Visual Basic nebo C#.

     Další informace najdete v tématu [jak: Vytváření projektů Office v sadě Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

     Visual Studio otevře soubor *ThisAddIn. vb* nebo *ThisAddIn.cs* a přidá **vyplňování dokumentů z databázového** projektu do **Průzkumník řešení**.

2. Pokud je projekt cílen na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]nebo, přidejte odkaz na sestavení *Microsoft. Office. Tools. Word. v 4.0. Utilities. dll* . Tento odkaz je nutný k programovému přidání model Windows Formsch ovládacích prvků do dokumentu dále v tomto návodu.

## <a name="create-a-data-source"></a>Vytvoření zdroje dat

Pomocí okna **zdroje dat** přidejte do projektu typovou datovou sadu.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Chcete-li přidat typovou datovou sadu do projektu

1. Pokud není okno **zdroje dat** viditelné, zobrazte ho tak, že v řádku nabídek vyberete možnost **Zobrazit** > **ostatní** > **zdroje dat**Windows.

2. Zvolením možnosti **Přidat nový zdroj dat** spusťte **Průvodce konfigurací zdroje dat**.

3. Klikněte na **databáze**a potom klikněte na **Další**.

4. Máte-li existující připojení k `AdventureWorksLT` databázi, vyberte toto připojení a klikněte na tlačítko **Další**.

    V opačném případě klikněte na tlačítko **nové připojení**a vytvořte nové připojení pomocí dialogového okna **Přidat připojení** . Další informace najdete v tématu [Přidání nových připojení](../data-tools/add-new-connections.md).

5. Na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na tlačítko **Další**.

6. Na stránce **Zvolte databázové objekty** rozbalte položku **tabulky** a vyberte možnost **Zákazník (tabulky SalesLT)** .

7. Klikněte na tlačítko **Dokončit**.

    Do **Průzkumník řešení**se přidá soubor *AdventureWorksLTDataSet. xsd* . Tento soubor definuje následující položky:

   - Typová datová sada s `AdventureWorksLTDataSet`názvem. Tato datová sada představuje obsah tabulky **Customer (tabulky SalesLT)** v databázi AdventureWorksLT.

   - TableAdapter s názvem `CustomerTableAdapter`. Tento TableAdapter lze použít ke čtení a zápisu dat v `AdventureWorksLTDataSet`. Další informace najdete v tématu [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Oba tyto objekty budete používat později v tomto návodu.

## <a name="create-controls-and-binding-controls-to-data"></a>Vytváření ovládacích prvků a vázání ovládacích prvků na data

Rozhraní pro zobrazení záznamů databáze v tomto návodu je základní a vytvoří se přímo v dokumentu. Jeden <xref:Microsoft.Office.Tools.Word.ContentControl> zobrazí jeden záznam databáze najednou a dva <xref:Microsoft.Office.Tools.Word.Controls.Button> ovládací prvky vám umožní procházet záznamy zpět a zpátky. Ovládací prvek obsahu používá <xref:System.Windows.Forms.BindingSource> pro připojení k databázi.

Další informace o vázání ovládacích prvků na data najdete v tématu [vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-the-interface-in-the-document"></a>Vytvoření rozhraní v dokumentu

1. Ve třídě deklarujte následující ovládací prvky pro zobrazení a procházení `Customer` tabulky `AdventureWorksLTDataSet` databáze. `ThisAddIn`

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2. V metodě přidejte následující kód pro inicializaci datové sady, vyplňte datovou sadu informacemi `AdventureWorksLTDataSet` z databáze. `ThisAddIn_Startup`

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3. Do `ThisAddIn_Startup` metody přidejte následující kód. Tím se vygeneruje Hostitelská položka, která rozšiřuje dokument. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4. Na začátku dokumentu Definujte několik rozsahů. Tyto rozsahy určují, kam vložit text a umístit ovládací prvky.

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5. Přidejte ovládací prvky rozhraní do dříve definovaných rozsahů.

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6. Navažte na ovládací prvek `AdventureWorksLTDataSet` obsahu <xref:System.Windows.Forms.BindingSource>pomocí. Pro C# vývojáře přidejte dvě obslužné rutiny události pro <xref:Microsoft.Office.Tools.Word.Controls.Button> ovládací prvky.

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7. Přidejte následující kód pro procházení záznamů databáze.

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>Test doplňku

Když otevřete aplikaci Word, ovládací prvek obsahu zobrazí data z `AdventureWorksLTDataSet` datové sady. Procházejte záznamy databáze kliknutím na tlačítko **Další** a **předchozí** .

### <a name="to-test-the-vsto-add-in"></a>Test doplňku VSTO

1. Stiskněte klávesu **F5**.

     Vytvoří se ovládací prvek `customerContentControl` obsahu s názvem a naplní se daty. Ve stejnou dobu je do projektu přidán objekt DataSet `adventureWorksLTDataSet` s názvem <xref:System.Windows.Forms.BindingSource> a `customerBindingSource` pojmenovaný. Je svázán s objektem, který je zase svázán s objektem DataSet. <xref:System.Windows.Forms.BindingSource> <xref:Microsoft.Office.Tools.Word.ContentControl>

2. Kliknutím na tlačítko **Další** a **předchozí** můžete procházet záznamy databáze.

## <a name="see-also"></a>Viz také:

- [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Postupy: Naplnění listů daty z databáze](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Postupy: Naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Postupy: Naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Postupy: Naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Postupy: Procházení databázových záznamů na listu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Postupy: Aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Návod: Jednoduchá datová vazba v projektu na úrovni dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Návod: Složitá datová vazba v projektu na úrovni dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Přehled použití místních souborů databáze v řešeních pro systém Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md)
- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Postupy: Naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Postupy: Aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Přehled použití místních souborů databáze v řešeních pro systém Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Přehled komponenty BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)
