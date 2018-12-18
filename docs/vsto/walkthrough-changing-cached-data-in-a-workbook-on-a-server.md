---
title: 'Návod: Změna dat uložených v mezipaměti ze sešitu na serveru'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], changing server data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f9f2ac3873bf59b30f8efa3e45d6cbdd0aebd4f6
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672860"
---
# <a name="walkthrough-change-cached-data-in-a-workbook-on-a-server"></a>Návod: Změna dat uložených v mezipaměti ze sešitu na serveru
  Tento návod ukazuje, jak změnit datové sady, které se uloží do mezipaměti v sešitu aplikace Microsoft Office Excel bez spuštění pomocí aplikace Excel <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- Definování datové sady, který obsahuje data z databáze AdventureWorksLT.

- Vytvoření instance datové sady v projektu sešitu aplikace Excel a projektu konzolové aplikace.

- Vytváření <xref:Microsoft.Office.Tools.Excel.ListObject> , která je vázaná k datové sadě v sešitu a naplnění <xref:Microsoft.Office.Tools.Excel.ListObject> s daty při otevření sešitu.

- Přidání datovou sadu do mezipaměti dat v sešitu.

- Úprava sloupce dat v datové sady v mezipaměti spouštěním kódu v konzolové aplikaci, bez spuštění Excelu.

  I když Tento názorný průvodce předpokládá, že používáte kód ve svém vývojovém počítači, kód jsme vám ukázali v rámci tohoto návodu je možné na server, který nemá nainstalovanou aplikaci Excel.

> [!NOTE]
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

-   Přístup ke spuštěné instanci serveru Microsoft SQL Server nebo Microsoft SQL Server Express, který má k němu připojené ukázkové databáze AdventureWorksLT. Můžete stáhnout z databáze AdventureWorksLT [webu CodePlex](http://go.microsoft.com/fwlink/?linkid=87843). Další informace o připojení databáze naleznete v následujících tématech:

    -   Připojení databáze pomocí SQL Server Management Studio nebo SQL Server Management Studio Express, naleznete v tématu [postupy: připojení databáze (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

    -   Připojení databáze pomocí příkazového řádku, naleznete v tématu [postupy: připojení souboru databáze pro SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Vytvořte projekt knihovny tříd, který definuje datovou sadu
 Pokud chcete použít stejné datové sady v projektu sešitu aplikace Excel a konzolové aplikace, musí definovat datové sady v samostatné sestavení, který je odkazován oba z těchto projektů. V tomto návodu definování datové sady v projektu knihovny tříd.

### <a name="to-create-the-class-library-project"></a>Chcete-li vytvořit projekt knihovny tříd

1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.

3.  V podokně šablony rozbalte **Visual C#** nebo **jazyka Visual Basic**a potom klikněte na tlačítko **Windows**.

4.  V seznamu šablon projektu vyberte **knihovny tříd**.

5.  V **název** zadejte **AdventureWorksDataSet**.

6.  Klikněte na tlačítko **Procházet**, přejděte k vaší *%UserProfile%\My dokumenty* (pro Windows XP a starší) nebo *%UserProfile%\Documents* (pro Windows Vista) složku a potom klikněte na **Vyberte složku**.

7.  V **nový projekt** dialogového okna zkontrolujte, zda **vytvořit adresář pro řešení** není zaškrtnuté políčko.

8.  Klikněte na tlačítko **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **AdventureWorksDataSet** projektu **Průzkumníka řešení** a otevře **Class1.cs** nebo **Class1.vb** soubor kódu.

9. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Class1.cs** nebo **Class1.vb**a potom klikněte na tlačítko **odstranit**. Tento soubor není nutné v tomto návodu.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definování datové sady v projektu knihovny tříd
 Definujte typové datové sady, který obsahuje data z databáze AdventureWorksLT pro SQL Server 2005. Později v tomto návodu bude odkazovat tento objekt dataset z projektu sešitu aplikace Excel a projektu konzolové aplikace.

 Tato datová sada je *zadaná datová sada* , která představuje data v tabulce Product databázi AdventureWorksLT. Další informace o definovaných datových sadách najdete v tématu [datovou sadu nástrojů v sadě Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Chcete-li definovat typové datové sady v projektu knihovny tříd

1. V **Průzkumníka řešení**, klikněte na tlačítko **AdventureWorksDataSet** projektu.

2. Pokud **zdroje dat** okno se nezobrazuje, zobrazit ho tím, na panelu nabídek, výběrem **zobrazení** > **ostatní Windows**  >   **Zdroje dat**.

3. Zvolte **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.

4. Klikněte na tlačítko **databáze**a potom klikněte na tlačítko **Další**.

5. Pokud máte existující připojení k databázi AdventureWorksLT, vyberte toto připojení a klikněte na tlačítko **Další**.

    V opačném případě klikněte na tlačítko **nové připojení**a použít **přidat připojení** dialogové okno pro vytvoření nového připojení. Další informace najdete v tématu [přidat nové připojení](../data-tools/add-new-connections.md).

6. V **uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na **Další**.

7. V **zvolte vaše databázové objekty** stránce, rozbalte **tabulky** a vyberte **produkt (SalesLT)**.

8. Klikněte na tlačítko **Dokončit**.

    *AdventureWorksLTDataSet.xsd* přidá soubor **AdventureWorksDataSet** projektu. Tento soubor definuje následující položky:

   - Typové datové sady s názvem `AdventureWorksLTDataSet`. Tato datová sada představuje obsah tabulky produktů v databázi AdventureWorksLT.

   - TableAdapter s názvem `ProductTableAdapter`. Této třídy TableAdapter lze číst a zapisovat data `AdventureWorksLTDataSet`. Další informace najdete v tématu [TableAdapter – přehled](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Obě tyto objekty použijete později v tomto názorném postupu.

9. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **AdventureWorksDataSet** a klikněte na tlačítko **sestavení**.

     Ověřte, že projekt se sestaví bez chyb.

## <a name="create-an-excel-workbook-project"></a>Vytvoření projektu sešitu aplikace Excel
 Vytvoření projektu sešitu aplikace Excel pro rozhraní pro data. Později v tomto návodu vytvoříte <xref:Microsoft.Office.Tools.Excel.ListObject> , která zobrazuje data, a přidáte instance datové sady do mezipaměti dat v sešitu.

### <a name="to-create-the-excel-workbook-project"></a>Vytvoření projektu sešitu aplikace Excel

1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **AdventureWorksDataSet** řešení, přejděte na **přidat**a potom klikněte na tlačítko **nový projekt**.

2.  V podokně šablony rozbalte **Visual C#**  nebo **jazyka Visual Basic**a potom rozbalte **Office**.

3.  V rozbalených **Office** uzlu, vyberte **2010** uzlu.

4.  V seznamu šablon projektu vyberte projekt Excelový sešit.

5.  V **název** zadejte **AdventureWorksReport**. Neprovádějte žádné změny umístění.

6.  Klikněte na tlačítko **OK**.

     **Visual Studio Tools for Office Project Wizard** otevře.

7.  Ujistěte se, že **vytvoříte nový textový dokument** je vybraná a klikněte na tlačítko **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otevře **AdventureWorksReport** sešit v návrháři a přidá **AdventureWorksReport** projektu **Průzkumníka řešení**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Přidat datovou sadu do zdroje dat v projektu sešitu aplikace Excel
 Než budete moci zobrazit datovou sadu v sešitu aplikace Excel, musíte nejprve přidat datové sady ke zdrojům dat v projektu sešitu aplikace Excel.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Chcete-li přidat datové sady ke zdrojům dat v projektu sešitu aplikace Excel

1.  V **Průzkumníka řešení**, dvakrát klikněte na panel **Sheet1.cs** nebo **Sheet1.vb** pod **AdventureWorksReport** projektu.

     Sešit se otevře v návrháři.

2.  Na **Data** nabídky, klikněte na tlačítko **přidat nový zdroj dat**.

     **Průvodce konfigurací zdroje dat** otevře.

3.  Klikněte na tlačítko **objekt**a potom klikněte na tlačítko **Další**.

4.  V **vyberte objekt chcete vytvořit vazbu k** klikněte na **přidat odkaz**.

5.  Na **projekty** klikněte na tlačítko **AdventureWorksDataSet** a potom klikněte na tlačítko **OK**.

6.  V části **AdventureWorksDataSet** obor názvů **AdventureWorksDataSet** sestavení, klikněte na tlačítko **AdventureWorksLTDataSet** a potom klikněte na tlačítko **dokončit** .

     **Zdroje dat** otevře se okno, a **AdventureWorksLTDataSet** se přidá do seznamu datových zdrojů.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Vytvoření objektu ListObject, který je vázán k instanci datové sady
 Chcete-li zobrazit datovou sadu v sešitu, vytvořte <xref:Microsoft.Office.Tools.Excel.ListObject> , která je svázána s instancí datové sady. Další informace o vázání ovládacích prvků na data, najdete v části [vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>K vytvoření objektu ListObject, který je vázán k instanci datové sady

1.  V **zdroje dat** okna, rozbalte **AdventureWorksLTDataSet** pod uzlem **AdventureWorksDataSet**.

2.  Vyberte **produktu** uzel, klikněte na šipku rozevíracího seznamu, která se zobrazí a vyberte **ListObject** v rozevíracím seznamu.

     Pokud na šipku rozevíracího seznamu se nezobrazí, zkontrolujte, že sešit je v Návrháři otevřený.

3.  Přetáhněte **produktu** tabulky do buňky A1.

     A <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek s názvem `productListObject` je vytvořen na listu, počínaje buňku A1. Současně, objekt datovou sadu s názvem `adventureWorksLTDataSet` a <xref:System.Windows.Forms.BindingSource> s názvem `productBindingSource` jsou přidány do projektu. <xref:Microsoft.Office.Tools.Excel.ListObject> Je vázán na <xref:System.Windows.Forms.BindingSource>, která je dále vázán na objektu dataset.

## <a name="add-the-dataset-to-the-data-cache"></a>Přidat datovou sadu do mezipaměti dat
 Pokud chcete povolit kód mimo projektu sešitu aplikace Excel přístup k datové sadě v sešitu, musíte přidat datovou sadu do datové mezipaměti. Další informace o mezipaměti dat najdete v tématu [data v přizpůsobeních na úrovni dokumentu v mezipaměti](../vsto/cached-data-in-document-level-customizations.md) a [ukládat data do mezipaměti](../vsto/caching-data.md).

### <a name="to-add-the-dataset-to-the-data-cache"></a>Přidat datovou sadu do mezipaměti dat

1.  V návrháři, klikněte na tlačítko **adventureWorksLTDataSet**.

2.  V **vlastnosti** okno, nastaveno **modifikátory** vlastnost **veřejné**.

3.  Nastavte **CacheInDocument** vlastnost **True**.

## <a name="initialize-the-dataset-in-the-workbook"></a>Inicializovat datové sady v sešitu
 Předtím, než můžete načíst data z datové sady v mezipaměti pomocí konzolové aplikace, musíte nejprve naplnění datové sady v mezipaměti s daty.

### <a name="to-initialize-the-dataset-in-the-workbook"></a>Inicializovat datové sady v sešitu

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **Sheet1.cs** nebo **Sheet1.vb** souboru a klikněte na tlačítko **zobrazit kód**.

2.  Nahradit `Sheet1_Startup` obslužné rutiny události s následujícím kódem. Tento kód používá instanci `ProductTableAdapter` třídu, která je definována v **AdventureWorksDataSet** projekt tak, aby vyplnil datové sady v mezipaměti s daty, pokud je aktuálně prázdný.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>Kontrolní bod
 Sestavení a spuštění projektu sešitu aplikace Excel k zajištění, že se zkompiluje a spustí bez chyb. Tato operace také vyplní celé datové sady v mezipaměti a ukládá data v sešitu.

### <a name="to-build-and-run-the-project"></a>Sestavení a spuštění projektu

1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **AdventureWorksReport** projektu, zvolte **ladění**a potom klikněte na **zahájit novou instanci**.

     Sestavení projektu a otevře sešit v Excelu. Ověřte následující:

    -   <xref:Microsoft.Office.Tools.Excel.ListObject> Vyplní daty.

    -   Hodnota v **ListPrice** sloupec prvního řádku <xref:Microsoft.Office.Tools.Excel.ListObject> je 1431.5. Dále v tomto názorném postupu použijete konzolovou aplikaci umožní úpravy hodnot v **ListPrice** sloupce.

2.  Uložte sešit. Neprovádějte žádné změny názvu souboru nebo umístění v sešitu.

3.  Zavřete aplikaci Excel.

## <a name="create-a-console-application-project"></a>Vytvořte projekt konzolové aplikace
 Vytvořte projekt konzolové aplikace, které chcete použít ke změně dat v datové sady v mezipaměti v sešitu.

### <a name="to-create-the-console-application-project"></a>Chcete-li vytvořit projekt konzolové aplikace

1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **AdventureWorksDataSet** řešení, přejděte na **přidat**a potom klikněte na tlačítko **nový projekt**.

2.  V **typy projektů** podokně rozbalte **Visual C#** nebo **jazyka Visual Basic**a potom klikněte na tlačítko **Windows**.

3.  V **šablony** vyberte **konzolovou aplikaci**.

4.  V **název** zadejte **datawriter nesmí být**. Neprovádějte žádné změny umístění.

5.  Klikněte na tlačítko **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **datawriter nesmí být** projektu **Průzkumníka řešení** a otevře **Program.cs** nebo **Module1.vb** soubor kódu.

## <a name="change-data-in-the-cached-dataset-by-using-the-console-application"></a>Změna dat v datové sady v mezipaměti pomocí konzolové aplikace
 Použití <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy v konzolové aplikaci k načtení dat do místního `AdventureWorksLTDataSet` objektu, tato data upravit a uložit je zpět do datové sady v mezipaměti.

### <a name="to-change-data-in-the-cached-dataset"></a>Chcete-li změnit data v datové sadě v mezipaměti

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **datawriter nesmí být** projektu a klikněte na tlačítko **přidat odkaz**.

2. Na **.NET** kartu, vyberte možnost **Microsoft.VisualStudio.Tools.Applications**.

3. Klikněte na tlačítko **OK**.

4. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **datawriter nesmí být** projektu a klikněte na tlačítko **přidat odkaz**.

5. Na **projekty** kartu, vyberte možnost **AdventureWorksDataSet**a klikněte na tlačítko **OK**.

6. Otevřít *Program.cs* nebo *Module1.vb* souboru v editoru kódu.

7. Přidejte následující **pomocí** (pro C#) nebo **importy** (pro jazyk Visual Basic) příkaz do horní části souboru kódu.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Přidejte následující kód, který `Main` metody. Tento kód deklaruje následující objekty:

   - Instance `AdventureWorksLTDataSet` typ, který je definován v **AdventureWorksDataSet** projektu.

   - Cesta k sešitu AdventureWorksReport ve složce sestavení **AdventureWorksReport** projektu.

   - A <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> objektu, který chcete použít pro přístup k mezipaměti dat v sešitu.

     > [!NOTE]
     >  Následující kód předpokládá, že používáte sešit, který má *.xlsx* příponu souboru. Pokud sešit v projektu má jinou příponu souboru, změňte cestu podle potřeby.

     [!code-csharp[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#6)]
     [!code-vb[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#6)]

9. Přidejte následující kód, který `Main` metoda po kódu přidaném v předchozím kroku. Tento kód provede následující:

   - Používá <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> vlastnost <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> pro přístup k datové sady v mezipaměti v sešitu.

   - Čte data z datové sady v mezipaměti do místní datové sady.

   - Změní `ListPrice` hodnotu každého produktu do tabulky Product datové sady.

   - Uloží změny do datové sady v mezipaměti v sešitu.

     [!code-csharp[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#7)]
     [!code-vb[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#7)]

10. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **datawriter nesmí být** projektu, přejděte na **ladění**a potom klikněte na **zahájit novou instanci**.

     Konzolová aplikace zobrazuje zprávy, když načte datové sady v mezipaměti do místní datové sady, upraví ceny produktů v místní datové sady a uloží nové hodnoty do datové sady v mezipaměti. Stisknutím klávesy **Enter** zavřít aplikaci.

## <a name="test-the-workbook"></a>Sešit testování
 Při otevření sešitu <xref:Microsoft.Office.Tools.Excel.ListObject> nyní zobrazí změny provedené `ListPrice` sloupec dat do datové sady v mezipaměti.

### <a name="to-test-the-workbook"></a>K otestování sešitu

1.  Zavřete AdventureWorksReport sešit v návrháři aplikace Visual Studio, pokud je stále otevřen.

2.  Otevřete sešit AdventureWorksReport, který je ve složce sestavení testovaného **AdventureWorksReport** projektu. Výchozí složka sestavení je v jednom z následujících umístění:

    -   *%USERPROFILE%\My Documents\AdventureWorksReport\bin\Debug* (pro Windows XP a starší)

    -   *%USERPROFILE%\Documents\AdventureWorksReport\bin\Debug* (pro Windows Vista)

3.  Ověřte, že hodnota ve **ListPrice** sloupec prvního řádku <xref:Microsoft.Office.Tools.Excel.ListObject> je nyní 1574.65.

4.  Zavření sešitu.

## <a name="see-also"></a>Viz také:

- [Návod: Vložení dat do sešitu na serveru](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)