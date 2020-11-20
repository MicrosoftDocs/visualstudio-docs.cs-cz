---
title: 'Návod: vytvoření N-vrstvých datových aplikací'
description: V tomto návodu vytvoříte N-vrstvou datovou aplikaci. N-vrstvé datové aplikace jsou aplikace, které přistupují k datům a jsou rozdělené do mnoha logických vrstev nebo vrstev.
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 76bf07e99f9965e88804c51663bcc37053bf74d6
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998080"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>Návod: Vytvoření n-vrstvých datových aplikací
*N-vrstvé* datové aplikace jsou aplikace, které přistupují k datům a jsou rozdělené do několika logických vrstev nebo *vrstev*. Oddělení součástí aplikace do diskrétních vrstev zvyšuje udržovatelnost a škálovatelnost aplikace. Je to díky tomu, že umožňuje snazší přijímání nových technologií, které se dají použít na jednu vrstvu, aniž byste museli přenavrhovat celé řešení. N-vrstvá architektura zahrnuje prezentační vrstvu, střední vrstvu a datovou vrstvu. Střední vrstva obvykle zahrnuje vrstvu přístupu k datům, vrstvu obchodní logiky a sdílené komponenty, jako je ověřování a ověřování. Datová vrstva zahrnuje relační databázi. N-vrstvé aplikace obvykle ukládají citlivé informace do vrstvy přístupu k datům střední vrstvy, aby zachovaly izolaci od koncových uživatelů, kteří přistupují k prezentační vrstvě. Další informace najdete v tématu [N-vrstvých datových aplikací – přehled](../data-tools/n-tier-data-applications-overview.md).

Jedním ze způsobů, jak rozdělit různé úrovně v n-vrstvé aplikaci, je vytvořit diskrétní projekty pro každou vrstvu, kterou chcete do aplikace zahrnout. Typové datové sady obsahují `DataSet Project` vlastnost, která určuje, do kterých projektů se má vygenerovaná datová sada a `TableAdapter` kód přejít.

Tento návod ukazuje, jak oddělit datovou sadu a `TableAdapter` kód do diskrétních projektů knihoven tříd pomocí **Návrhář datových sad**. Po oddělení datové sady a kódu TableAdapter vytvoříte [služby Windows Communication Foundation Services a WCF Data Services ve službě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) Service pro volání do úrovně přístupu k datům. Nakonec vytvoříte aplikaci model Windows Forms jako prezentační vrstvu. Tato vrstva přistupuje k datům z datové služby.

Během tohoto Názorného postupu provedete následující kroky:

- Vytvořte nové n-vrstvé řešení, které obsahuje více projektů.

- Přidejte dva projekty knihovny tříd do n-vrstvého řešení.

- Vytvořte typovou datovou sadu pomocí **Průvodce konfigurací zdroje dat**.

- Vygenerovaný kód [objekty TableAdapter](create-and-configure-tableadapters.md) a datovou sadu oddělte do diskrétních projektů.

- Vytvořte službu Windows Communication Foundation (WCF), která bude volat do úrovně přístupu k datům.

- Vytvořte ve službě funkce, abyste načetli data z vrstvy přístupu k datům.

- Vytvořte model Windows Formsovou aplikaci, která bude sloužit jako prezentační vrstva.

- Vytvoří model Windows Forms ovládací prvky, které jsou svázané se zdrojem dat.

- Napište kód pro naplnění tabulek dat.

![odkaz na video ve ](../data-tools/media/playvideo.gif) verzi videa tohoto tématu naleznete v části [Video postupy: vytváření n-vrstvých datových aplikací](/previous-versions/visualstudio/visual-studio-2008/cc178916(v=vs.90)).

## <a name="prerequisites"></a>Požadavky
Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V **instalační program pro Visual Studio** můžete nainstalovat SQL Server Express LocalDB jako součást úlohy **vývoj desktopových** aplikací pro .NET nebo jako jednotlivé komponenty.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (**Průzkumník objektů systému SQL Server** je nainstalován v rámci úlohy **úložiště dat a zpracování** v instalační program pro Visual Studio.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editoru dotazů.

    2. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a pak klikněte na tlačítko **Spustit** .

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Vytvoření n-vrstvého řešení a knihovny tříd pro uložení datové sady (DataEntityTier)
Prvním krokem tohoto návodu je vytvoření řešení a dvou projektů knihovny tříd. První knihovna tříd obsahuje datovou sadu (generovanou typovou `DataSet` třídu a datové tabulky, které obsahují data aplikace). Tento projekt se používá jako vrstva datové entity aplikace a obvykle se nachází v prostřední vrstvě. Datová sada vytvoří počáteční datovou sadu a automaticky odděluje kód do dvou knihoven tříd.

> [!NOTE]
> Před kliknutím na tlačítko **OK** nezapomeňte projekt a řešení pojmenovat správně. To vám usnadní dokončení tohoto návodu.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Vytvoření n-vrstvého řešení a knihovny tříd DataEntityTier

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový**  >  **projekt**.

2. V levém podokně rozbalte možnost **Visual C#** nebo **Visual Basic** a pak vyberte možnost **desktopová plocha systému Windows**.

3. V prostředním podokně vyberte typ projektu **Knihovna tříd** .

4. Pojmenujte projekt **DataEntityTier**.

5. Pojmenujte řešení **NTierWalkthrough** a pak zvolte **OK**.

     NTierWalkthrough řešení, které obsahuje projekt DataEntityTier, je vytvořeno a přidáno do **Průzkumník řešení**.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Vytvoření knihovny tříd pro uchování objekty TableAdapter (DataAccessTier)
Dalším krokem po vytvoření projektu DataEntityTier je vytvoření dalšího projektu knihovny tříd. Tento projekt obsahuje vygenerované objekty TableAdapter a označuje *úroveň přístupu k datům* aplikace. Úroveň přístupu k datům obsahuje informace potřebné pro připojení k databázi a obvykle se nachází na střední úrovni.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Vytvoření samostatné knihovny tříd pro objekty TableAdapter

1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.

2. V dialogovém okně **Nový projekt** v prostředním podokně vyberte možnost **Knihovna tříd**.

3. Pojmenujte projekt **DataAccessTier** a klikněte na **tlačítko OK**.

     Projekt DataAccessTier je vytvořen a přidán do řešení NTierWalkthrough.

## <a name="create-the-dataset"></a>Vytvoření datové sady
Dalším krokem je vytvořit typovou datovou sadu. Typové datové sady jsou vytvořeny pomocí třídy DataSet (včetně `DataTables` tříd) a `TableAdapter` tříd v jednom projektu. (Všechny třídy jsou generovány do jediného souboru.) Když datovou sadu oddělíte a objekty tableadapterete do různých projektů, jedná se o třídu datové sady, která je přesunuta do jiného projektu, takže `TableAdapter` třídy v původním projektu. Proto Vytvořte datovou sadu v projektu, která bude nakonec obsahovat objekty TableAdapter (projekt DataAccessTier). Datovou sadu vytvoříte pomocí **Průvodce konfigurací zdroje dat**.

> [!NOTE]
> Abyste mohli vytvořit připojení, musíte mít přístup k ukázkové databázi Northwind. Informace o tom, jak nastavit ukázkovou databázi Northwind, najdete v tématu [Postup: Instalace ukázkových databází](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>Vytvoření datové sady

1. Vyberte **DataAccessTier** v **Průzkumník řešení**.

2. V nabídce **data** vyberte možnost **Zobrazit zdroje dat**.

   Otevře se okno **zdroje dat** .

3. V okně **zdroje dat** vyberte možnost **Přidat nový zdroj dat** a spusťte **Průvodce konfigurací zdroje dat**.

4. Na stránce **Vybrat typ zdroje dat** vyberte **databáze** a pak vyberte **Další**.

5. Na stránce **Vyberte datové připojení** proveďte jednu z následujících akcí:

     Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

     -nebo-

     Vyberte **nové připojení** , aby se otevřelo dialogové okno **Přidat připojení** .

6. Pokud databáze vyžaduje heslo, vyberte možnost pro zahrnutí citlivých dat a pak zvolte **Další**.

    > [!NOTE]
    > Pokud jste vybrali místní databázový soubor (místo připojení k SQL Server), může se zobrazit dotaz, zda chcete soubor přidat do projektu. Chcete-li přidat soubor databáze do projektu, klikněte na tlačítko **Ano** .

7. Klikněte na tlačítko **Další** na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** .

8. Rozbalte uzel **tabulky** na stránce **zvolit objekty databáze** .

9. Zaškrtněte políčka pro tabulky **zákazníci** a **objednávky** a pak zvolte **Dokončit**.

     NorthwindDataSet se přidá do projektu DataAccessTier a zobrazí se v okně **zdroje dat** .

## <a name="separate-the-tableadapters-from-the-dataset"></a>Oddělit objekty TableAdapter od datové sady
Po vytvoření datové sady oddělte třídu vygenerovanou datovou sadou z objekty TableAdapter. To provedete tak, že nastavíte vlastnost **projektu DataSet** na název projektu, do kterého chcete uložit třídu odděleného objektu DataSet.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Oddělení objektů TableAdapter od objektu DataSet

1. Dvojitým kliknutím na **NorthwindDataSet. xsd** v **Průzkumník řešení** otevřete datovou sadu v **Návrhář datových sad**.

2. Vyberte prázdnou oblast v návrháři.

3. V okně **vlastnosti** vyhledejte uzel **projekt datové sady** .

4. V seznamu **projekt datové sady** vyberte možnost **DataEntityTier**.

5. V nabídce **sestavení** vyberte **Sestavit řešení**.

   Datová sada a objekty TableAdapter jsou rozděleny do dvou knihoven tříd projektů. Projekt, který původně obsahoval celou datovou sadu ( `DataAccessTier` ) nyní obsahuje pouze objekty TableAdapter. Projekt určený v vlastnosti **projektu DataSet** ( `DataEntityTier` ) obsahuje typovou datovou sadu: *NorthwindDataSet. DataSet. Designer. vb* (nebo *NorthwindDataSet.DataSet.Designer.cs*).

> [!NOTE]
> Při oddělení datových sad a objekty TableAdapter (nastavením vlastnosti **projektu DataSet** ) existující částečné třídy datové sady v projektu nebudou automaticky přesunuty. Existující částečné třídy datové sady je nutné ručně přesunout do projektu datové sady.

## <a name="create-a-new-service-application"></a>Vytvoření nové aplikace služby
Tento návod ukazuje, jak získat přístup k vrstvě přístupu k datům pomocí služby WCF, takže vytvoříme novou aplikaci služby WCF.

### <a name="to-create-a-new-wcf-service-application"></a>Vytvoření nové aplikace služby WCF

1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.

2. V dialogovém okně **Nový projekt** v levém podokně vyberte možnost **WCF**. V prostředním podokně vyberte možnost **Knihovna služeb WCF**.

3. Pojmenujte projekt **DataService** a vyberte **OK**.

     Projekt DataService se vytvoří a přidá do řešení NTierWalkthrough.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Vytvoření metod v úrovni přístupu k datům pro vrácení dat zákazníků a objednávek
Datová služba musí volat dvě metody ve vrstvě přístupu k datům: `GetCustomers` a `GetOrders` . Tyto metody vrací Northwind `Customers` a `Orders` tabulky. Vytvořte `GetCustomers` `GetOrders` v projektu metody a `DataAccessTier` .

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Vytvoření metody, která vrací tabulku Customers, ve vrstvě přístupu k datům

1. V **Průzkumník řešení** dvakrát klikněte na **NorthwindDataSet. xsd** a otevřete datovou sadu.

2. Klikněte pravým tlačítkem na **CustomersTableAdapter** a klikněte na **Přidat dotaz**.

3. Na stránce **zvolit typ příkazu** ponechte výchozí hodnotu **použít příkazy SQL** a klikněte na **Další**.

4. Na stránce **Zvolte typ dotazu** ponechte výchozí hodnotu **vybrat, která vrací řádky** , a klikněte na **Další**.

5. Na stránce **Zadejte příkaz SQL SELECT** ponechte výchozí dotaz a klikněte na **Další**.

6. Na stránce **zvolit metody, které mají být generovány** zadejte příkaz **GetCustomers** pro **název metody** v oddílu **návrat objektu DataTable** .

7. Klikněte na **Finish** (Dokončit).

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Vytvoření metody, která vrací tabulku Orders, ve vrstvě přístupu k datům

1. Klikněte pravým tlačítkem na **OrdersTableAdapter** a klikněte na **Přidat dotaz**.

2. Na stránce **zvolit typ příkazu** ponechte výchozí hodnotu **použít příkazy SQL** a klikněte na **Další**.

3. Na stránce **Zvolte typ dotazu** ponechte výchozí hodnotu **vybrat, která vrací řádky** , a klikněte na **Další**.

4. Na stránce **Zadejte příkaz SQL SELECT** ponechte výchozí dotaz a klikněte na **Další**.

5. Na stránce **zvolit metody, které mají být generovány** zadejte **GetOrders** pro **název metody** v oddílu **return a DataTable** .

6. Klikněte na **Finish** (Dokončit).

7. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Přidání odkazu na datovou entitu a úrovně přístupu k datům do datové služby
Vzhledem k tomu, že datová služba vyžaduje informace z datové sady a objekty TableAdapter, přidejte odkazy na projekty **DataEntityTier** a **DataAccessTier** .

### <a name="to-add-references-to-the-data-service"></a>Přidání odkazů do datové služby

1. Klikněte pravým tlačítkem na **DataService** v **Průzkumník řešení** a klikněte na **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** klikněte na kartu **projekty** .

3. Vyberte projekty **DataAccessTier** a **DataEntityTier** .

4. Klikněte na **OK**.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Přidání funkcí do služby pro volání metod GetCustomers a GetOrders ve vrstvě přístupu k datům
Teď, když vrstva přístupu k datům obsahuje metody pro vrácení dat, vytvořte v datové službě metody, které volají metody v úrovni přístupu k datům.

> [!NOTE]
> Pro projekty v jazyce C# je nutné přidat odkaz na `System.Data.DataSetExtensions` sestavení pro zkompilování následujícího kódu.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Vytvoření funkcí GetCustomers a GetOrders v datové službě

1. V projektu **DataService** poklikejte na **IService1. vb** nebo **IService1.cs**.

2. Přidejte následující kód do komentáře **přidat operace služby tady** :

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();
    ```

3. V projektu DataService poklikejte na **Service1. vb** (nebo **Service1.cs**).

4. Do třídy **Service1** přidejte následující kód:

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
             CustomersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();
        return CustomersTableAdapter1.GetCustomers();
    }
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
             OrdersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();
        return OrdersTableAdapter1.GetOrders();
    }
    ```

5. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Vytvoření prezentační vrstvy pro zobrazení dat z datové služby
Teď, když řešení obsahuje datovou službu, která obsahuje metody, které volají do úrovně přístupu k datům, vytvořte další projekt, který volá do datové služby a prezentuje data uživatelům. Pro tento návod vytvořte aplikaci model Windows Forms, Toto je prezentační vrstva aplikace v n-vrstvé aplikaci.

### <a name="to-create-the-presentation-tier-project"></a>Vytvoření projektu prezentační vrstvy

1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.

2. V dialogovém okně **Nový projekt** v levém podokně vyberte možnost **desktopová plocha systému Windows**. V prostředním podokně vyberte **model Windows Forms aplikace**.

3. Pojmenujte projekt **PresentationTier** a klikněte na **OK**.

    Projekt PresentationTier je vytvořen a přidán do řešení NTierWalkthrough.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>Nastavení projektu PresentationTier jako spouštěného projektu
Nastavíme projekt **PresentationTier** jako projekt po spuštění pro řešení, protože se jedná o skutečnou klientskou aplikaci, která prezentuje a komunikuje s daty.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Nastavení nového projektu prezentační vrstvy jako spouštěného projektu

- V **Průzkumník řešení** klikněte pravým tlačítkem myši na **PresentationTier** a klikněte na **nastavit jako spouštěný projekt**.

## <a name="add-references-to-the-presentation-tier"></a>Přidání odkazů do prezentační vrstvy
Klientská aplikace PresentationTier vyžaduje odkaz na službu datové služby, aby mohla získat přístup k metodám ve službě. Kromě toho je vyžadován odkaz na datovou sadu, aby bylo možné povolit sdílení typů službou WCF. Dokud nepovolíte sdílení typů prostřednictvím datové služby, není kód přidaný do třídy částečné datové sady k dispozici pro prezentační vrstvu. Vzhledem k tomu, že obvykle přidáte kód, jako je například ověřovací kód do události změny řádku a sloupce tabulky dat, je pravděpodobně vhodné získat přístup k tomuto kódu z klienta.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>Přidání odkazu do prezentační vrstvy

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **PresentationTier** a vyberte **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** vyberte kartu **projekty** .

3. Vyberte **DataEntityTier** a klikněte na **OK**.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Přidání odkazu na službu do prezentační vrstvy

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **PresentationTier** a vyberte **Přidat odkaz na službu**.

2. V dialogovém okně **Přidat odkaz na službu** vyberte možnost **zjistit**.

3. Vyberte **Service1** a klikněte na **OK**.

    > [!NOTE]
    > Pokud máte v aktuálním počítači více služeb, vyberte službu, kterou jste vytvořili dříve v tomto návodu (službu, která obsahuje `GetCustomers` `GetOrders` metody a).

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Přidejte DataGridViews do formuláře, aby se zobrazila data vrácená datovou službou.
Po přidání odkazu na službu do datové služby se okno **zdroje dat** automaticky vyplní daty vrácenými službou.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Přidání dvou ovládacích prvků DataGridView vázaných na data do formuláře

1. V **Průzkumník řešení** vyberte projekt **PresentationTier** .

2. V okně **zdroje dat** rozbalte **NorthwindDataSet** a vyhledejte uzel **Customers (zákazníci** ).

3. Přetáhněte uzel **Customers** na Form1.

4. V okně **zdroje dat** rozbalte uzel **zákazníci** a vyhledejte související uzel **objednávky** (uzel **objednávky** je vnořen do uzlu **Customers** ).

5. Přetáhněte uzel související **objednávky** na Form1.

6. Vytvořte `Form1_Load` obslužnou rutinu události dvojitým kliknutím na prázdnou oblast formuláře.

7. Přidejte následující kód do `Form1_Load` obslužné rutiny události.

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());
    ```

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Zvýšit maximální velikost zprávy povolenou službou
Výchozí hodnota pro `maxReceivedMessageSize` není dostatečně velká pro uložení dat načtených z `Customers` `Orders` tabulek a. V následujících krocích zvýšíte hodnotu na 6553600. Změníte hodnotu v klientovi, která automaticky aktualizuje odkaz na službu.

> [!NOTE]
> Dolní výchozí velikost je určena k omezení vystavení útokům DOS (Denial of Service). Další informace naleznete v tématu <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Zvýšení hodnoty maxReceivedMessageSize

1. V **Průzkumník řešení** dvakrát klikněte na **app.config** soubor v projektu **PresentationTier** .

2. Vyhledejte atribut size **maxReceivedMessage** a změňte hodnotu na `6553600` .

## <a name="test-the-application"></a>Testování aplikace
Spusťte aplikaci stisknutím klávesy **F5**. Data z `Customers` `Orders` tabulek a se načítají z datové služby a zobrazují se na formuláři.

## <a name="next-steps"></a>Další kroky
V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po uložení souvisejících dat v aplikaci pro systém Windows. Můžete například provést následující vylepšení této aplikace:

- Přidejte ověření do datové sady.

- Do služby přidejte další metody pro aktualizaci dat zpět do databáze.

## <a name="see-also"></a>Viz také

- [Práce s datovými sadami ve vícevrstvých aplikacích](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Hierarchická aktualizace](../data-tools/hierarchical-update.md)
- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
