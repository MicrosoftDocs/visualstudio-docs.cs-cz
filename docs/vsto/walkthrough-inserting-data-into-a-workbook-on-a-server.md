---
title: 'Návod: vložení dat do sešitu na serveru'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
- workbooks [Office development in Visual Studio], inserting data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d9dcd22ca124ee5ea4002277f91071727a3e9e1
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985433"
---
# <a name="walkthrough-insert-data-into-a-workbook-on-a-server"></a>Návod: vložení dat do sešitu na serveru
  Tento návod ukazuje, jak vložit data do datové sady, která je ukládána do mezipaměti v systém Microsoft Office excelovém sešitu bez spuštění aplikace Excel pomocí <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- Definování datové sady, která obsahuje data z databáze AdventureWorksLT.

- Vytváření instancí datové sady v projektu excelového sešitu a projektu konzolové aplikace.

- Vytvoření <xref:Microsoft.Office.Tools.Excel.ListObject> vázaného na datovou sadu v sešitu.

- Přidání datové sady do sešitu do mezipaměti dat.

- Vložení dat do datové sady uložených v mezipaměti spuštěním kódu v konzolové aplikaci bez spuštění aplikace Excel.

  I když tento návod předpokládá, že spouštíte kód na vašem vývojovém počítači, kód, který je znázorněný v tomto návodu, lze použít na serveru, na kterém není aplikace Excel nainstalována.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Přístup ke spuštěné instanci Microsoft SQL Server nebo Microsoft SQL Server Express, ke které je připojena ukázková databáze AdventureWorksLT. Databázi AdventureWorksLT si můžete stáhnout z [webu CodePlex](https://archive.codeplex.com/?p=SqlServerSamples). Další informace o připojení databáze najdete v následujících tématech:

  - Postup připojení databáze pomocí SQL Server Management Studio nebo SQL Server Management Studio Express naleznete v tématu [How to: Attach a Database (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Postup připojení databáze pomocí příkazového řádku naleznete v tématu [How to: Attach a File Database to SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Vytvoření projektu knihovny tříd, který definuje datovou sadu
 Chcete-li použít stejnou datovou sadu v projektu excelového sešitu a konzolové aplikaci, je nutné definovat datovou sadu v samostatném sestavení, na které se odkazuje oba tyto projekty. Pro tento návod definujte datovou sadu v projektu knihovny tříd.

### <a name="to-create-the-class-library-project"></a>Vytvoření projektu knihovny tříd

1. Spusťte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

3. V podokně šablony rozbalte  **C# vizuál** nebo **Visual Basic**a potom klikněte na **Windows**.

4. V seznamu šablon projektu vyberte možnost **Knihovna tříd**.

5. Do pole **název** zadejte **AdventureWorksDataSet**.

6. Klikněte na **Procházet**, přejděte do složky *%USERPROFILE%\My Documents* (pro Windows XP a starší) nebo *%USERPROFILE%\Documents* (pro Windows Vista) a pak klikněte na **Vybrat složku**.

7. V dialogovém okně **Nový projekt** ověřte, zda není zaškrtnuto políčko **vytvořit adresář pro řešení** .

8. Klikněte na tlačítko **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **AdventureWorksDataSet** do **Průzkumník řešení** a otevře soubor kódu **Class1.cs** nebo **Class1. vb** .

9. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **Class1.cs** nebo **Class1. vb**a pak klikněte na **Odstranit**. Tento soubor nepotřebujete pro tento návod.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definovat datovou sadu v projektu knihovny tříd
 Definujte typovou datovou sadu, která obsahuje data z databáze AdventureWorksLT pro SQL Server 2005. Později v tomto návodu budete odkazovat na tuto datovou sadu z projektu excelového sešitu a projektu konzolové aplikace.

 Datová sada je *typová datová sada* , která představuje data v tabulce produktů databáze AdventureWorksLT. Další informace o zadaných datových sadách naleznete v tématu [nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Definování typované datové sady v projektu knihovny tříd

1. V **Průzkumník řešení**klikněte na projekt **AdventureWorksDataSet** .

2. Pokud není okno **zdroje dat** viditelné, zobrazte ho tak, že v řádku nabídek vyberete možnost **Zobrazit** > **jiné** **zdroje dat** > Windows.

3. Zvolením možnosti **Přidat nový zdroj dat** spusťte **Průvodce konfigurací zdroje dat**.

4. Klikněte na **databáze**a potom klikněte na **Další**.

5. Máte-li existující připojení k databázi AdventureWorksLT, vyberte toto připojení a klikněte na tlačítko **Další**.

    V opačném případě klikněte na tlačítko **nové připojení**a vytvořte nové připojení pomocí dialogového okna **Přidat připojení** . Další informace najdete v tématu [Postup: připojení k datům v databázi](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md).

6. Na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** klikněte na tlačítko **Další**.

7. Na stránce **Zvolte databázové objekty** rozbalte položku **tabulky** a vyberte možnost **produkt (tabulky SalesLT)** .

8. Klikněte na tlačítko **Dokončit**.

    Do projektu **AdventureWorksDataSet** se přidá soubor *AdventureWorksLTDataSet. xsd* . Tento soubor definuje následující položky:

   - Typová datová sada s názvem `AdventureWorksLTDataSet`. Tato datová sada představuje obsah tabulky produktů v databázi AdventureWorksLT.

   - TableAdapter s názvem `ProductTableAdapter`. Tento TableAdapter lze použít ke čtení a zápisu dat v `AdventureWorksLTDataSet`. Další informace najdete v tématu [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Oba tyto objekty budete používat později v tomto návodu.

9. V **Průzkumník řešení**klikněte pravým tlačítkem na **AdventureWorksDataSet** a klikněte na **sestavit**.

     Ověřte, že se projekt vytváří bez chyb.

## <a name="create-an-excel-workbook-project"></a>Vytvoření projektu excelového sešitu
 Vytvořte projekt excelového sešitu pro rozhraní s daty. Později v tomto návodu vytvoříte <xref:Microsoft.Office.Tools.Excel.ListObject>, které zobrazí data, a přidáte instanci datové sady do mezipaměti dat v sešitu.

### <a name="to-create-the-excel-workbook-project"></a>Vytvoření projektu excelového sešitu

1. V **Průzkumník řešení**klikněte pravým tlačítkem na řešení **AdventureWorksDataSet** , přejděte na **Přidat**a pak klikněte na **Nový projekt**.

2. V podokně šablony rozbalte položku **Visual C#**  nebo **Visual Basic**a potom rozbalte položku **Office/SharePoint**.

3. V rozbaleném uzlu **Office/SharePoint** vyberte uzel **Doplňky Office** .

4. V seznamu šablon projektu vyberte **sešit excel 2010** nebo projekt **Excelu 2013** .

5. Do pole **název** zadejte **AdventureWorksReport**. Neměňte umístění.

6. Klikněte na tlačítko **OK**.

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
 Chcete-li zobrazit datovou sadu v sešitu, vytvořte <xref:Microsoft.Office.Tools.Excel.ListObject>, která je svázána s instancí datové sady. Další informace o vázání ovládacích prvků na data najdete v tématu [vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Vytvoření ListObject vázaného na instanci datové sady

1. V okně **zdroje dat** rozbalte uzel **AdventureWorksLTDataSet** pod **AdventureWorksDataSet**.

2. Vyberte uzel **produktu** , klikněte na šipku rozevíracího seznamu, která se zobrazí, a v rozevíracím seznamu vyberte **ListObject** .

     Pokud se šipka rozevíracího seznamu nezobrazí, potvrďte, že je sešit otevřený v návrháři.

3. Přetáhněte tabulku **produktů** do buňky a1.

     Na listu se vytvoří ovládací prvek <xref:Microsoft.Office.Tools.Excel.ListObject> s názvem `productListObject`, který začíná v buňce a1. Ve stejnou dobu je do projektu přidán objekt DataSet s názvem `adventureWorksLTDataSet` a <xref:System.Windows.Forms.BindingSource> s názvem `productBindingSource`. <xref:Microsoft.Office.Tools.Excel.ListObject> je svázána s <xref:System.Windows.Forms.BindingSource>, která je zase svázána s objektem DataSet.

## <a name="add-the-dataset-to-the-data-cache"></a>Přidat datovou sadu do mezipaměti dat
 Chcete-li povolit kód mimo projekt sešitu aplikace Excel pro přístup k datové sadě v sešitu, je nutné přidat datovou sadu do mezipaměti dat. Další informace o mezipaměti dat najdete [v tématu data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu a v datech uložených v](../vsto/cached-data-in-document-level-customizations.md) [mezipaměti](../vsto/caching-data.md).

### <a name="to-add-the-dataset-to-the-data-cache"></a>Přidání datové sady do mezipaměti dat

1. V návrháři klikněte na **AdventureWorksLTDataSet**.

2. V okně **vlastnosti** nastavte vlastnost **modifikátory** na hodnotu **Public**.

3. Nastavte vlastnost **CacheInDocument** na **hodnotu true**.

## <a name="checkpoint"></a>Kontrolní bod
 Sestavte a spusťte projekt sešitu aplikace Excel, abyste se ujistili, že se zkompiluje a spustí bez chyb.

### <a name="to-build-and-run-the-project"></a>Sestavení a spuštění projektu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **AdventureWorksReport** , zvolte možnost **ladit**a pak klikněte na možnost **spustit novou instanci**.

     Projekt je sestaven a sešit se otevře v aplikaci Excel. <xref:Microsoft.Office.Tools.Excel.ListObject> v **List1** je prázdné, protože objekt `adventureWorksLTDataSet` v mezipaměti dat ještě neobsahuje žádná data. V další části použijete konzolovou aplikaci k naplnění objektu `adventureWorksLTDataSet` daty.

2. Zavřete aplikaci Excel. Neukládat změny.

## <a name="create-a-console-application-project"></a>Vytvoření projektu konzolové aplikace
 Vytvořte projekt konzolové aplikace, který se použije k vložení dat do datové sady v mezipaměti v sešitu.

### <a name="to-create-the-console-application-project"></a>Vytvoření projektu konzolové aplikace

1. V **Průzkumník řešení**klikněte pravým tlačítkem na řešení **AdventureWorksDataSet** , přejděte na **Přidat**a pak klikněte na **Nový projekt**.

2. V podokně **typy projektů** rozbalte položku **Visual C#**  nebo **Visual Basic**a potom klikněte na možnost **Windows**.

3. V podokně **šablony** vyberte **Konzolová aplikace**.

4. Do pole **název** zadejte **datawrite**. Neměňte umístění.

5. Klikněte na tlačítko **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **Datawriteer** do **Průzkumník řešení** a otevře soubor kódu **program.cs** nebo **Module1. vb** .

## <a name="add-data-to-the-cached-dataset-by-using-the-console-application"></a>Přidání dat do datové sady v mezipaměti pomocí konzolové aplikace
 Pomocí třídy <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> v konzolové aplikaci naplňte datovou sadu uloženou v mezipaměti v sešitu daty.

### <a name="to-add-data-to-the-cached-dataset"></a>Přidání dat do datové sady v mezipaměti

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt pro **zápis k datawrite** a klikněte na **Přidat odkaz**.

2. Na kartě **.NET** vyberte **Microsoft. VisualStudio. Tools. Applications. ServerDocument**.

3. Klikněte na tlačítko **OK**.

4. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt pro **zápis k datawrite** a klikněte na **Přidat odkaz**.

5. Na kartě **projekty** vyberte **AdventureWorksDataSet**a klikněte na **OK**.

6. V editoru kódu otevřete soubor *program.cs* nebo *Module1. vb* .

7. Přidejte následující příkaz **using** (for C#) nebo **Import** (for Visual Basic) do horní části souboru kódu.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Do metody `Main` přidejte následující kód. Tento kód deklaruje následující objekty:

   - Instance `AdventureWorksLTDataSet` a `ProductTableAdapter` typů, které jsou definovány v projektu **AdventureWorksDataSet** .

   - Cesta k AdventureWorksReport sešitu ve složce sestavení projektu **AdventureWorksReport** .

   - Objekt <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>, který se má použít pro přístup k mezipaměti dat v sešitu.

     > [!NOTE]
     > Následující kód předpokládá, že používáte sešit, který má příponu souboru *. xlsx* . Pokud má sešit v projektu jinou příponu souboru, upravte cestu podle potřeby.

     [!code-csharp[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#3)]
     [!code-vb[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#3)]

9. Přidejte následující kód do metody `Main` po kódu, který jste přidali v předchozím kroku. Tento kód provede následující:

   - Vyplní typový objekt DataSet pomocí adaptéru tabulky.

   - Pro přístup k datové sadě uložené v sešitu používá vlastnost <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy.

   - Pomocí metody <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> naplní datovou sadu uloženou v mezipaměti daty z místní typové datové sady.

     [!code-csharp[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#4)]
     [!code-vb[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#4)]

10. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt pro **zápis k datawrite** , přejděte na **ladění**a potom klikněte na **spustit novou instanci**.

     Projekt je sestaven a Konzolová aplikace zobrazuje několik stavových zpráv, když je místní datová sada vyplněna a když aplikace ukládá data do datové sady uložených v mezipaměti v sešitu. Stiskněte klávesu **ENTER** , aby se aplikace zavřela.

## <a name="test-the-workbook"></a>Test sešitu
 Když otevřete sešit, <xref:Microsoft.Office.Tools.Excel.ListObject> nyní zobrazuje data přidaná do datové sady v mezipaměti pomocí konzolové aplikace.

### <a name="to-test-the-workbook"></a>Test sešitu

1. Zavřete sešit AdventureWorksReport v návrháři aplikace Visual Studio, pokud je stále otevřený.

2. V Průzkumníku souborů otevřete sešit AdventureWorksReport, který je ve složce Build projektu **AdventureWorksReport** . Ve výchozím nastavení je složka sestavení v jednom z následujících umístění:

    - *%USERPROFILE%\My Documents\AdventureWorksReport\bin\Debug* (pro Windows XP a starší)

    - *%USERPROFILE%\Documents\AdventureWorksReport\bin\Debug* (pro systém Windows Vista)

3. Ověřte, že <xref:Microsoft.Office.Tools.Excel.ListObject> po otevření sešitu naplní data.

## <a name="next-steps"></a>Další kroky

Další informace o práci s daty uloženými v mezipaměti najdete v těchto tématech:

- Změna dat v datové sadě uložených v mezipaměti bez spuštění aplikace Excel. Další informace najdete v tématu [Návod: Změna dat uložených v mezipaměti v sešitu na serveru](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>Viz také:

- [Návod: Změna dat uložených v mezipaměti v sešitu na serveru](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
