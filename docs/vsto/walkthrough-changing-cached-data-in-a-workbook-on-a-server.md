---
title: 'Návod: Změna dat uložených v mezipaměti v sešitu na serveru'
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a88fef7afe198dd15716570b1875ea257d19be8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985519"
---
# <a name="walkthrough-change-cached-data-in-a-workbook-on-a-server"></a>Návod: Změna dat uložených v mezipaměti v sešitu na serveru
  Tento návod ukazuje, jak upravit datovou sadu, která je uložena v mezipaměti v systém Microsoft Office excelovém sešitu bez spuštění aplikace Excel pomocí <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Tento návod znázorňuje následující úlohy:

- Definování datové sady, která obsahuje data z databáze AdventureWorksLT.

- Vytváření instancí datové sady v projektu excelového sešitu a projektu konzolové aplikace.

- Vytvoření <xref:Microsoft.Office.Tools.Excel.ListObject> objektu vázaného na datovou sadu v sešitu a naplnění <xref:Microsoft.Office.Tools.Excel.ListObject> dat daty při otevření sešitu.

- Přidání datové sady do sešitu do mezipaměti dat.

- Úprava sloupce dat v datové sadě uložených v mezipaměti spuštěním kódu v konzolové aplikaci bez spuštění aplikace Excel.

  I když tento návod předpokládá, že spouštíte kód na vašem vývojovém počítači, kód, který je znázorněný v tomto návodu, lze použít na serveru, na kterém není aplikace Excel nainstalována.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Přístup ke spuštěné instanci Microsoft SQL Server nebo Microsoft SQL Server Express, ke které je připojena ukázková databáze AdventureWorksLT. Databázi AdventureWorksLT si můžete stáhnout z [úložiště githubu SQL Server Samples](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Další informace o připojení databáze najdete v následujících tématech:

  - Postup připojení databáze pomocí SQL Server Management Studio nebo SQL Server Management Studio Express naleznete v tématu [How to: Attach a Database (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Postup připojení databáze pomocí příkazového řádku naleznete v tématu [How to: Attach a File Database to SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Vytvoření projektu knihovny tříd, který definuje datovou sadu
 Chcete-li použít stejnou datovou sadu v projektu excelového sešitu a konzolové aplikaci, je nutné definovat datovou sadu v samostatném sestavení, na které se odkazuje oba tyto projekty. Pro tento návod definujte datovou sadu v projektu knihovny tříd.

### <a name="to-create-the-class-library-project"></a>Vytvoření projektu knihovny tříd

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

3. V podokně šablony rozbalte položku **Visual C#** nebo **Visual Basic**a potom klikněte na možnost **Windows**.

4. V seznamu šablon projektu vyberte možnost **Knihovna tříd**.

5. Do pole **název** zadejte **AdventureWorksDataSet**.

6. Klikněte na **Procházet**, přejděte do složky *%USERPROFILE%\My Documents* (pro Windows XP a starší) nebo *%USERPROFILE%\Documents* (pro Windows Vista) a pak klikněte na **Vybrat složku**.

7. V dialogovém okně **Nový projekt** ověřte, zda není zaškrtnuto políčko **vytvořit adresář pro řešení** .

8. Klikněte na **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **AdventureWorksDataSet** do **Průzkumník řešení** a otevře soubor kódu **Class1.cs** nebo **Class1. vb** .

9. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **Class1.cs** nebo **Class1. vb**a pak klikněte na **Odstranit**. Tento soubor nepotřebujete pro tento návod.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definovat datovou sadu v projektu knihovny tříd
 Definujte typovou datovou sadu, která obsahuje data z databáze AdventureWorksLT pro SQL Server 2005. Později v tomto návodu budete odkazovat na tuto datovou sadu z projektu excelového sešitu a projektu konzolové aplikace.

 Datová sada je *typová datová sada* , která představuje data v tabulce produktů databáze AdventureWorksLT. Další informace o zadaných datových sadách naleznete v tématu [nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Definování typované datové sady v projektu knihovny tříd

1. V **Průzkumník řešení**klikněte na projekt **AdventureWorksDataSet** .

2. Pokud není okno **zdroje dat** viditelné, zobrazte ho tak, že v řádku nabídek vyberete možnost **Zobrazit**  >  **ostatní**  >  **zdroje dat**Windows.

3. Zvolením možnosti **Přidat nový zdroj dat** spusťte **Průvodce konfigurací zdroje dat**.

4. Klikněte na **databáze**a potom klikněte na **Další**.

5. Máte-li existující připojení k databázi AdventureWorksLT, vyberte toto připojení a klikněte na tlačítko **Další**.

    V opačném případě klikněte na tlačítko **nové připojení**a vytvořte nové připojení pomocí dialogového okna **Přidat připojení** . Další informace najdete v tématu [Přidání nových připojení](../data-tools/add-new-connections.md).

6. Na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na tlačítko **Další**.

7. Na stránce **Zvolte databázové objekty** rozbalte položku **tabulky** a vyberte možnost **produkt (tabulky SalesLT)**.

8. Klikněte na **Finish** (Dokončit).

    Do projektu **AdventureWorksDataSet** se přidá soubor *AdventureWorksLTDataSet. xsd* . Tento soubor definuje následující položky:

   - Typová datová sada s názvem `AdventureWorksLTDataSet` . Tato datová sada představuje obsah tabulky produktů v databázi AdventureWorksLT.

   - TableAdapter s názvem `ProductTableAdapter` . Tento TableAdapter lze použít ke čtení a zápisu dat v `AdventureWorksLTDataSet` . Další informace najdete v tématu [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Oba tyto objekty budete používat později v tomto návodu.

9. V **Průzkumník řešení**klikněte pravým tlačítkem na **AdventureWorksDataSet** a klikněte na **sestavit**.

     Ověřte, že se projekt vytváří bez chyb.

## <a name="create-an-excel-workbook-project"></a>Vytvoření projektu excelového sešitu
 Vytvořte projekt excelového sešitu pro rozhraní s daty. Později v tomto návodu vytvoříte <xref:Microsoft.Office.Tools.Excel.ListObject> a zobrazíte data a přidáte instanci datové sady do mezipaměti dat v sešitu.

### <a name="to-create-the-excel-workbook-project"></a>Vytvoření projektu excelového sešitu

1. V **Průzkumník řešení**klikněte pravým tlačítkem na řešení **AdventureWorksDataSet** , přejděte na **Přidat**a pak klikněte na **Nový projekt**.

2. V podokně šablony rozbalte položku **Visual C#** nebo **Visual Basic**a potom rozbalte položku **Office**.

3. V rozbaleném uzlu **Office** vyberte uzel **2010** .

4. V seznamu šablon projektu vyberte projekt excelový sešit.

5. Do pole **název** zadejte **AdventureWorksReport**. Neměňte umístění.

6. Klikněte na **OK**.

     Otevře se **Průvodce projektem Visual Studio Tools for Office** .

7. Ujistěte se, že je vybraná možnost **vytvořit nový dokument** , a klikněte na **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevře sešit **AdventureWorksReport** v návrháři a přidá projekt **AdventureWorksReport** do **Průzkumník řešení**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Přidat datovou sadu do zdrojů dat v projektu excelového sešitu
 Než budete moci zobrazit datovou sadu v excelovém sešitu, je nutné nejprve přidat datovou sadu do zdrojů dat v projektu excelového sešitu.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Chcete-li přidat datovou sadu do zdrojů dat v projektu excelového sešitu

1. V **Průzkumník řešení**dvakrát klikněte na **Sheet1.cs** nebo **List1. vb** v rámci projektu **AdventureWorksReport** .

     Sešit se otevře v návrháři.

2. V nabídce **data** klikněte na tlačítko **Přidat nový zdroj dat**.

     Otevře se **Průvodce konfigurací zdroje dat** .

3. Klikněte na **objekt**a potom klikněte na tlačítko **Další**.

4. Na stránce **Vyberte objekt, na který chcete vytvořit vazby** klikněte na **Přidat odkaz**.

5. Na kartě **projekty** klikněte na **AdventureWorksDataSet** a potom klikněte na **OK**.

6. V oboru názvů **AdventureWorksDataSet** sestavení **AdventureWorksDataSet** klikněte na **AdventureWorksLTDataSet** a pak klikněte na **Dokončit**.

     Otevře se okno **zdroje dat** a **AdventureWorksLTDataSet** se přidá do seznamu zdrojů dat.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Vytvoření ListObject vázaného na instanci datové sady
 Chcete-li zobrazit datovou sadu v sešitu, vytvořte objekt <xref:Microsoft.Office.Tools.Excel.ListObject> , který je svázán s instancí datové sady. Další informace o vázání ovládacích prvků na data najdete v tématu [vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Vytvoření ListObject vázaného na instanci datové sady

1. V okně **zdroje dat** rozbalte uzel **AdventureWorksLTDataSet** pod **AdventureWorksDataSet**.

2. Vyberte uzel **produktu** , klikněte na šipku rozevíracího seznamu, která se zobrazí, a v rozevíracím seznamu vyberte **ListObject** .

     Pokud se šipka rozevíracího seznamu nezobrazí, potvrďte, že je sešit otevřený v návrháři.

3. Přetáhněte tabulku **produktů** do buňky a1.

     <xref:Microsoft.Office.Tools.Excel.ListObject>Na listu se vytvoří ovládací prvek s názvem `productListObject` , který začíná v buňce a1. Ve stejnou dobu je do projektu přidán objekt DataSet s názvem `adventureWorksLTDataSet` a <xref:System.Windows.Forms.BindingSource> pojmenovaný `productBindingSource` . <xref:Microsoft.Office.Tools.Excel.ListObject>Je svázán s <xref:System.Windows.Forms.BindingSource> objektem, který je zase svázán s objektem DataSet.

## <a name="add-the-dataset-to-the-data-cache"></a>Přidat datovou sadu do mezipaměti dat
 Chcete-li povolit kód mimo projekt sešitu aplikace Excel pro přístup k datové sadě v sešitu, je nutné přidat datovou sadu do mezipaměti dat. Další informace o mezipaměti dat najdete [v tématu data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu a v datech uložených v](../vsto/cached-data-in-document-level-customizations.md) [mezipaměti](../vsto/caching-data.md).

### <a name="to-add-the-dataset-to-the-data-cache"></a>Přidání datové sady do mezipaměti dat

1. V návrháři klikněte na **AdventureWorksLTDataSet**.

2. V okně **vlastnosti** nastavte vlastnost **modifikátory** na hodnotu **Public**.

3. Nastavte vlastnost **CacheInDocument** na **hodnotu true**.

## <a name="initialize-the-dataset-in-the-workbook"></a>Inicializovat datovou sadu v sešitu
 Než budete moct načíst data z datové sady uložené v mezipaměti pomocí konzolové aplikace, musíte nejdřív naplnit datovou sadu uloženou v mezipaměti daty.

### <a name="to-initialize-the-dataset-in-the-workbook"></a>Inicializace datové sady v sešitu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor **Sheet1.cs** nebo **List1. vb** a klikněte na **Zobrazit kód**.

2. Proměnnou `Sheet1_Startup` obslužné rutiny události nahraďte následujícím kódem. Tento kód používá instanci `ProductTableAdapter` třídy, která je definována v projektu **AdventureWorksDataSet** , aby vyplnila datovou sadu uloženou v mezipaměti daty, pokud je aktuálně prázdná.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>CheckPoint
 Sestavte a spusťte projekt sešitu aplikace Excel, abyste se ujistili, že se zkompiluje a spustí bez chyb. Tato operace také vyplní datovou sadu uloženou v mezipaměti a uloží data v sešitu.

### <a name="to-build-and-run-the-project"></a>Sestavení a spuštění projektu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **AdventureWorksReport** , zvolte možnost **ladit**a pak klikněte na možnost **spustit novou instanci**.

     Projekt je sestaven a sešit se otevře v aplikaci Excel. Zkontrolujte:

    - <xref:Microsoft.Office.Tools.Excel.ListObject>Vyplní data.

    - Hodnota ve sloupci **ListPrice** pro první řádek v poli <xref:Microsoft.Office.Tools.Excel.ListObject> je 1431,5. Později v tomto návodu budete pomocí konzolové aplikace upravovat hodnoty ve sloupci **ListPrice** .

2. Sešit uložte. Neměňte název souboru ani umístění sešitu.

3. Zavřete aplikaci Excel.

## <a name="create-a-console-application-project"></a>Vytvoření projektu konzolové aplikace
 Vytvořte projekt konzolové aplikace, který chcete použít pro úpravu dat v datové sadě uložené v mezipaměti v sešitu.

### <a name="to-create-the-console-application-project"></a>Vytvoření projektu konzolové aplikace

1. V **Průzkumník řešení**klikněte pravým tlačítkem na řešení **AdventureWorksDataSet** , přejděte na **Přidat**a pak klikněte na **Nový projekt**.

2. V podokně **typy projektů** rozbalte položku **Visual C#** nebo **Visual Basic**a potom klikněte na možnost **Windows**.

3. V podokně **šablony** vyberte **Konzolová aplikace**.

4. Do pole **název** zadejte **datawrite**. Neměňte umístění.

5. Klikněte na **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **datawrite** do **Průzkumník řešení** a otevře soubor kódu **program.cs** nebo **Module1. vb** .

## <a name="change-data-in-the-cached-dataset-by-using-the-console-application"></a>Změna dat v datové sadě uložených v mezipaměti pomocí konzolové aplikace
 Použijte <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídu v konzolové aplikaci ke čtení dat do místního `AdventureWorksLTDataSet` objektu, upravte tato data a pak ji uložte zpět do datové sady uložené v mezipaměti.

### <a name="to-change-data-in-the-cached-dataset"></a>Změna dat v datové sadě uložených v mezipaměti

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt pro **zápis k datawrite** a klikněte na **Přidat odkaz**.

2. Na kartě **.NET** vyberte **Microsoft. VisualStudio. Tools. Applications**.

3. Klikněte na **OK**.

4. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt pro **zápis k datawrite** a klikněte na **Přidat odkaz**.

5. Na kartě **projekty** vyberte **AdventureWorksDataSet**a klikněte na **OK**.

6. V editoru kódu otevřete soubor *program.cs* nebo *Module1. vb* .

7. Přidejte následující příkaz **using** (for C#) nebo **import** (for Visual Basic) do horní části souboru kódu.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Do metody `Main` přidejte následující kód. Tento kód deklaruje následující objekty:

   - Instance `AdventureWorksLTDataSet` typu, který je definován v projektu **AdventureWorksDataSet** .

   - Cesta k AdventureWorksReport sešitu ve složce sestavení projektu **AdventureWorksReport** .

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Objekt, který se má použít pro přístup k mezipaměti dat v sešitu.

     > [!NOTE]
     > Následující kód předpokládá, že používáte sešit, který má příponu souboru *. xlsx* . Pokud má sešit v projektu jinou příponu souboru, upravte cestu podle potřeby.

     [!code-csharp[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#6)]
     [!code-vb[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#6)]

9. Do metody přidejte následující kód `Main` po kódu, který jste přidali v předchozím kroku. Tento kód provádí následující úlohy:

   - Používá <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> vlastnost <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy pro přístup k datové sadě uložené v sešitu.

   - Čte data z datové sady v mezipaměti do místní datové sady.

   - Změní `ListPrice` hodnotu každého produktu v tabulce produktů v sadě dat.

   - Uloží změny do datové sady uložené v mezipaměti v sešitu.

     [!code-csharp[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#7)]
     [!code-vb[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#7)]

10. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt pro **zápis k datawrite** , přejděte na **ladění**a potom klikněte na **spustit novou instanci**.

     Konzolová aplikace zobrazuje zprávy, když čte datovou sadu uloženou v mezipaměti do místní datové sady, upravuje ceny produktů v místní datové sadě a ukládá nové hodnoty do datové sady uložených v mezipaměti. Stiskněte klávesu **ENTER** , aby se aplikace zavřela.

## <a name="test-the-workbook"></a>Test sešitu
 Když otevřete sešit, <xref:Microsoft.Office.Tools.Excel.ListObject> zobrazí se nyní změny `ListPrice` ve sloupci dat v datové sadě uložené v mezipaměti.

### <a name="to-test-the-workbook"></a>Test sešitu

1. Zavřete sešit AdventureWorksReport v návrháři aplikace Visual Studio, pokud je stále otevřený.

2. Otevřete sešit AdventureWorksReport, který je ve složce Build projektu **AdventureWorksReport** . Ve výchozím nastavení je složka sestavení v jednom z následujících umístění:

    - *%USERPROFILE%\My Documents\AdventureWorksReport\bin\Debug* (pro Windows XP a starší)

    - *%USERPROFILE%\Documents\AdventureWorksReport\bin\Debug* (pro systém Windows Vista)

3. Ověřte, že hodnota ve sloupci **ListPrice** pro první řádek <xref:Microsoft.Office.Tools.Excel.ListObject> je nyní 1574,65.

4. Zavřete sešit.

## <a name="see-also"></a>Viz také

- [Návod: vložení dat do sešitu na serveru](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
