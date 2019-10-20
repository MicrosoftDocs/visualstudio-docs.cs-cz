---
title: 'Návod: vytvoření N-vrstvé datové aplikace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 51
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 720f50fe486c0e625fcd67191f43897eba466698
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660165"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Návod: Vytvoření víceúrovňové datové aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N-vrstvé datové aplikace jsou aplikace, které přistupují k datům a jsou rozdělené do několika logických vrstev nebo *vrstev*. Oddělení součástí aplikace do diskrétních vrstev zvyšuje udržovatelnost a škálovatelnost aplikace. Je to díky tomu, že umožňuje snazší přijímání nových technologií, které se dají použít na jednu vrstvu, aniž byste museli přenavrhovat celé řešení. N-vrstvá architektura zahrnuje prezentační vrstvu, střední vrstvu a datovou vrstvu. Střední vrstva obvykle zahrnuje vrstvu přístupu k datům, vrstvu obchodní logiky a sdílené komponenty, jako je ověřování a ověřování. Datová vrstva zahrnuje relační databázi. N-vrstvé aplikace obvykle ukládají citlivé informace do vrstvy přístupu k datům střední vrstvy, aby zachovaly izolaci od koncových uživatelů, kteří přistupují k prezentační vrstvě. Další informace najdete v tématu [N-vrstvých datových aplikací – přehled](../data-tools/n-tier-data-applications-overview.md).

 Jedním ze způsobů, jak rozdělit různé úrovně v n-vrstvé aplikaci, je vytvořit diskrétní projekty pro každou vrstvu, kterou chcete do aplikace zahrnout. Typové datové sady obsahují vlastnost `DataSet Project`, která určuje, do kterých projektů se má vygenerovaná datová sada a `TableAdapter` kód přejít.

 Tento návod ukazuje, jak oddělit datovou sadu a kód `TableAdapter` do diskrétních projektů knihovny tříd pomocí **Návrhář datových sad**. Po oddělení datové sady a kódu TableAdapter vytvoříte [ve službě Visual Studio službu Windows Communication Foundation Services a WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) budete volat do úrovně přístupu k datům. Nakonec vytvoříte aplikaci model Windows Forms jako prezentační vrstvu. Tato vrstva přistupuje k datům z datové služby.

 V tomto návodu provedete následující kroky:

- Vytvořte nové n-vrstvé řešení, které bude obsahovat více projektů.

- Přidejte dva projekty knihovny tříd do n-vrstvého řešení.

- Vytvořte typovou datovou sadu pomocí **Průvodce konfigurací zdroje dat**.

- Vygenerovaný kód [objekty TableAdapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) a datovou sadu oddělte do diskrétních projektů.

- Vytvořte službu Windows Communication Foundation (WCF), která bude volat do úrovně přístupu k datům.

- Vytvořte ve službě funkce, abyste načetli data z vrstvy přístupu k datům.

- Vytvořte model Windows Formsovou aplikaci, která bude sloužit jako prezentační vrstva.

- Vytvoří model Windows Forms ovládací prvky, které jsou svázané se zdrojem dat.

- Napište kód pro naplnění tabulek dat.

  ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") Verzi videa tohoto tématu naleznete v části [Video postupy: vytváření N-vrstvých datových aplikací](http://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat:

- Přístup k ukázkové databázi Northwind.

## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Vytvoření N-vrstvého řešení a knihovny tříd pro objekt Dataset (DataEntityTier)
 Prvním krokem tohoto návodu je vytvoření řešení a dvou projektů knihovny tříd. První knihovna tříd bude uchovávat datovou sadu (třídu generované typové datové sady a datové tabulky, které budou obsahovat data aplikace). Tento projekt se používá jako vrstva datové entity aplikace a obvykle se nachází v prostřední vrstvě. Návrhář datových sad slouží k vytvoření počáteční datové sady a k automatickému oddělení kódu do dvou knihoven tříd.

> [!NOTE]
> Před kliknutím na tlačítko **OK**nezapomeňte projekt a řešení pojmenovat správně. To vám usnadní dokončení tohoto návodu.

#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Vytvoření n-vrstvého řešení a knihovny tříd DataEntityTier

1. V nabídce **soubor** vytvořte nový projekt.

    > [!NOTE]
    > **Návrhář datových sad** je podporován v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] a C# projektech. Vytvořte nový projekt v jednom z těchto jazyků.

2. V dialogovém okně **Nový projekt** klikněte v podokně **typy projektů** na možnost **Windows**.

3. Klikněte na šablonu **knihovny tříd** .

4. Pojmenujte projekt **DataEntityTier**.

5. Pojmenujte řešení **NTierWalkthrough**.

6. Klikněte na tlačítko **OK**.

     NTierWalkthrough řešení, které obsahuje projekt DataEntityTier, je vytvořeno a přidáno do **Průzkumník řešení**.

## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Vytvoření knihovny tříd pro objekty TableAdapter (DataAccessTier)
 Dalším krokem po vytvoření projektu DataEntityTier je vytvoření dalšího projektu knihovny tříd. Tento projekt bude obsahovat vygenerované `TableAdapter`s a nazývá se *úroveň přístupu k datům* aplikace. Úroveň přístupu k datům obsahuje informace potřebné pro připojení k databázi a obvykle se nachází na střední úrovni.

#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>Vytvoření nové knihovny tříd pro objekty TableAdapter

1. V nabídce **soubor** přidejte do řešení NTierWalkthrough nový projekt.

2. V dialogovém okně **Nový projekt** v podokně **šablony** klikněte na možnost **Knihovna tříd**.

3. Pojmenujte projekt **DataAccessTier** a klikněte na **OK**.

     Projekt DataAccessTier je vytvořen a přidán do řešení NTierWalkthrough.

## <a name="creating-the-dataset"></a>Vytvoření datové sady
 Dalším krokem je vytvořit typovou datovou sadu. Typové datové sady jsou vytvořeny pomocí třídy DataSet (včetně tříd DataTables) a tříd `TableAdapter` v jednom projektu. (Všechny třídy jsou generovány do jediného souboru.) Když datovou sadu oddělíte a `TableAdapter`sete do různých projektů, jedná se o třídu datové sady, která je přesunuta do jiného projektu, přičemž třídy `TableAdapter` v původním projektu. Proto Vytvořte datovou sadu v projektu, která bude nakonec obsahovat `TableAdapter`s (projekt DataAccessTier). Datovou sadu vytvoříte pomocí **Průvodce konfigurací zdroje dat**.

> [!NOTE]
> Abyste mohli vytvořit připojení, musíte mít přístup k ukázkové databázi Northwind.

#### <a name="to-create-the-dataset"></a>Vytvoření datové sady

1. V **Průzkumník řešení**klikněte na DataAccessTier.

2. V nabídce **data** klikněte na možnost **Zobrazit zdroje dat**.

3. V okně **zdroje dat** klikněte na tlačítko **Přidat nový zdroj dat** a spusťte **Průvodce konfigurací zdroje dat**.

4. Na stránce **Vybrat typ zdroje dat** klikněte na **databáze** a potom klikněte na **Další**.

5. Na stránce **Vyberte datové připojení** proveďte jednu z následujících akcí:

     Pokud je datové připojení k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, klikněte na něj.

     -nebo-

     Kliknutím na **nové připojení** otevřete dialogové okno **Přidat připojení** .

6. Pokud databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a potom klikněte na tlačítko **Další**.

    > [!NOTE]
    > Pokud jste vybrali místní databázový soubor (místo připojení k SQL Server), může se zobrazit dotaz, zda chcete soubor přidat do projektu. Kliknutím na tlačítko **Ano** přidejte soubor databáze do projektu.

7. Klikněte na tlačítko **Další** na stránce **Uložit připojovací řetězec do konfiguračního souboru aplikace** .

8. Rozbalte uzel **tabulky** na stránce **zvolit objekty databáze** .

9. Zaškrtněte políčka pro tabulky **zákazníci** a **objednávky** a poté klikněte na tlačítko **Dokončit**.

     NorthwindDataSet se přidá do projektu DataAccessTier a zobrazí se v okně **zdroje dat** .

## <a name="separating-the-tableadapters-from-the-dataset"></a>Oddělení objektů TableAdapter od objektu DataSet
 Po vytvoření datové sady oddělte třídu vygenerovanou datovou sadou z objekty TableAdapter. To provedete tak, že nastavíte vlastnost **projektu DataSet** na název projektu, do kterého chcete uložit třídu odděleného objektu DataSet.

#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Oddělení objektů TableAdapter od objektu DataSet

1. Dvojitým kliknutím na **NorthwindDataSet. xsd** v **Průzkumník řešení** otevřete datovou sadu v **Návrhář datových sad**.

2. Klikněte na prázdnou oblast v návrháři.

3. V okně **vlastnosti** vyhledejte uzel **projekt datové sady** .

4. V seznamu **projekt datové sady** klikněte na **DataEntityTier**.

5. V nabídce **sestavení** klikněte na **Sestavit řešení**.

   Datová sada a objekty TableAdapter jsou rozděleny do dvou knihoven tříd projektů. Projekt, který původně obsahoval celou datovou sadu (DataAccessTier), teď obsahuje jenom objekty TableAdapter. Projekt určený ve vlastnosti **DataSet Project** (DataEntityTier) obsahuje typovou datovou sadu: NorthwindDataSet. DataSet. Designer. vb (nebo NorthwindDataSet.DataSet.Designer.cs).

> [!NOTE]
> Při oddělení datových sad a objekty TableAdapter (nastavením vlastnosti **projektu DataSet** ) existující částečné třídy datové sady v projektu nebudou automaticky přesunuty. Existující částečné třídy datové sady je nutné ručně přesunout do projektu datové sady.

## <a name="creating-a-new-service-application"></a>Vytvoření nové aplikace služby
 Vzhledem k tomu, že tento návod ukazuje, jak získat přístup k vrstvě přístupu k datům pomocí služby WCF, vytvořte novou aplikaci služby WCF.

#### <a name="to-create-a-new-wcf-service-application"></a>Vytvoření nové aplikace služby WCF

1. V nabídce **soubor** přidejte do řešení NTierWalkthrough nový projekt.

2. V dialogovém okně **Nový projekt** v podokně **typy projektů** klikněte na možnost **WCF**. V podokně **šablony** klikněte na možnost **Knihovna služby WCF**.

3. Pojmenujte projekt **DataService** a klikněte na tlačítko **OK**.

     Projekt DataService se vytvoří a přidá do řešení NTierWalkthrough.

## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Vytvoření metod, které vrací data zákazníků a objednávek, ve vrstvě přístupu k datům
 Datová služba musí volat dvě metody ve vrstvě přístupu k datům: GetCustomers a GetOrders. Tyto metody vrátí tabulky zákazníků a objednávek Northwind. V projektu DataAccessTier vytvořte metody GetCustomers a GetOrders.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Vytvoření metody, která vrací tabulku Customers, ve vrstvě přístupu k datům

1. V **Průzkumník řešení**dvakrát klikněte na NorthwindDataSet. xsd a otevřete datovou sadu v Návrhář datových sad.

2. Klikněte pravým tlačítkem na CustomersTableAdapter a kliknutím na **Přidat dotaz** upravte TableAdapter.

3. Na stránce **zvolit typ příkazu** ponechte výchozí hodnotu **použít příkazy SQL** a klikněte na **Další**.

4. Na stránce **Zvolte typ dotazu** ponechte výchozí hodnotu **vybrat, která vrací řádky** , a klikněte na **Další**.

5. Na stránce **Zadejte příkaz SQL SELECT** ponechte výchozí dotaz a klikněte na **Další**.

6. Na stránce **zvolit metody, které mají být generovány** zadejte příkaz **GetCustomers** pro **název metody** v oddílu **návrat objektu DataTable** .

7. Klikněte na tlačítko **Dokončit**.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Vytvoření metody, která vrací tabulku Orders, ve vrstvě přístupu k datům

1. Klikněte pravým tlačítkem na OrdersTableAdapter a klikněte na **Přidat dotaz**.

2. Na stránce **zvolit typ příkazu** ponechte výchozí hodnotu **použít příkazy SQL** a klikněte na **Další**.

3. Na stránce **Zvolte typ dotazu** ponechte výchozí hodnotu **vybrat, která vrací řádky** , a klikněte na **Další**.

4. Na stránce **Zadejte příkaz SQL SELECT** ponechte výchozí dotaz a klikněte na **Další**.

5. Na stránce **zvolit metody, které mají být generovány** zadejte **GetOrders** pro **název metody** v oddílu **return a DataTable** .

6. Klikněte na tlačítko **Dokončit**.

7. V nabídce **sestavení** klikněte na **Sestavit řešení**.

## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Přidání odkazu na vrstvu datové entity a vrstvu přístupu k datům do datové služby
 Vzhledem k tomu, že datová služba vyžaduje informace z datové sady a objekty TableAdapter, přidejte odkazy na projekty DataEntityTier a DataAccessTier.

#### <a name="to-add-references-to-the-data-service"></a>Přidání odkazů do datové služby

1. Klikněte pravým tlačítkem na DataService v **Průzkumník řešení** a klikněte na **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** klikněte na kartu **projekty** .

3. Vyberte projekty **DataAccessTier** a **DataEntityTier** .

4. Klikněte na tlačítko **OK**.

## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Přidání funkcí do služby za účelem volání metod GetCustomers a GetOrders ve vrstvě přístupu k datům
 Teď, když vrstva přístupu k datům obsahuje metody pro vrácení dat, vytvořte v datové službě metody, které volají metody v úrovni přístupu k datům.

> [!NOTE]
> Pro C# projekty je nutné přidat odkaz na sestavení `System.Data.DataSetExtensions` pro zkompilování následujícího kódu.

#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Vytvoření funkcí GetCustomers a GetOrders v datové službě

1. V projektu **DataService** poklikejte na IService1. vb nebo IService1.cs.

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

3. V projektu DataService poklikejte na Service1. vb (nebo Service1.cs).

4. Do třídy Service1 přidejte následující kód:

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

5. V nabídce **sestavení** klikněte na **Sestavit řešení**.

## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Vytvoření prezentační vrstvy zobrazující data z datové služby
 Teď, když řešení obsahuje datovou službu, která obsahuje metody, které volají do úrovně přístupu k datům, vytvořte další projekt, který bude volat do datové služby a prezentuje data uživatelům. Pro tento návod vytvořte aplikaci model Windows Forms, Toto je prezentační vrstva aplikace v n-vrstvé aplikaci.

#### <a name="to-create-the-presentation-tier-project"></a>Vytvoření projektu prezentační vrstvy

1. V nabídce **soubor** přidejte do řešení NTierWalkthrough nový projekt.

2. V dialogovém okně **Nový projekt** klikněte v podokně **typy projektů** na možnost **Windows**. V podokně **šablony** klikněte na **model Windows Forms aplikace**.

3. Pojmenujte projekt **PresentationTier** a klikněte na **OK**.

4. Projekt PresentationTier je vytvořen a přidán do řešení NTierWalkthrough.

## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Nastavení projektu PresentationTier jako spouštěného projektu
 Vzhledem k tomu, že prezentační vrstva je skutečná klientská aplikace, která se používá k prezentaci dat a práci s nimi, musíte nastavit projekt PresentationTier jako projekt po spuštění.

#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Nastavení nového projektu prezentační vrstvy jako spouštěného projektu

- V **Průzkumník řešení**klikněte pravým tlačítkem myši na **PresentationTier** a klikněte na **nastavit jako spouštěný projekt**.

## <a name="adding-references-to-the-presentation-tier"></a>Přidání odkazů do prezentační vrstvy
 Klientská aplikace PresentationTier vyžaduje odkaz na službu datové služby, aby mohla získat přístup k metodám ve službě. Kromě toho je vyžadován odkaz na datovou sadu, aby bylo možné povolit sdílení typů službou WCF. Dokud nepovolíte sdílení typů prostřednictvím datové služby, kód přidaný do třídy částečné datové sady nebude k dispozici pro prezentační vrstvu. Vzhledem k tomu, že obvykle přidáte kód, jako je například ověřování, na události, které mění řádek tabulky dat, je pravděpodobně vhodné získat přístup k tomuto kódu z klienta.

#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Přidání odkazu do prezentační vrstvy

1. V **Průzkumník řešení**klikněte pravým tlačítkem na PresentationTier a klikněte na **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** klikněte na kartu **projekty** .

3. Vyberte **DataEntityTier** a klikněte na **OK**.

#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Přidání odkazu na službu do prezentační vrstvy

1. V **Průzkumník řešení**klikněte pravým tlačítkem na PresentationTier a klikněte na **Přidat odkaz na službu**.

2. V dialogovém okně **Přidat odkaz na službu** klikněte na možnost **zjistit**.

3. Vyberte **Service1** a klikněte na **OK**.

    > [!NOTE]
    > Pokud máte v aktuálním počítači více služeb, vyberte službu, kterou jste vytvořili dříve v tomto návodu (službu, která obsahuje metody GetCustomers a GetOrders).

## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Přidání ovládacích prvků DataGridView do formuláře a zobrazení dat vrácených datovou službou
 Po přidání odkazu na službu do datové služby se okno **zdroje dat** automaticky vyplní daty vrácenými službou.

#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Přidání dvou ovládacích prvků DataGridView vázaných na data do formuláře

1. V **Průzkumník řešení**vyberte projekt PresentationTier.

2. V okně **zdroje dat** rozbalte **NorthwindDataSet** a vyhledejte uzel **Customers (zákazníci** ).

3. Přetáhněte uzel **Customers** na Form1.

4. V okně **zdroje dat** rozbalte uzel **zákazníci** a vyhledejte související uzel **objednávky** (uzel **objednávky** je vnořen do uzlu **Customers** ).

5. Přetáhněte uzel související **objednávky** na Form1.

6. Vytvořte obslužnou rutinu události `Form1_Load` dvojitým kliknutím na prázdnou oblast formuláře.

7. Do obslužné rutiny události `Form1_Load` přidejte následující kód.

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

## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Zvětšení maximální velikosti zprávy povolené službou
 Vzhledem k tomu, že služba vrací data z tabulek Customers a Orders, výchozí hodnota pro třídu maxReceivedMessageSize není dostatečně velká pro uchovávání dat a je nutné ji zvýšit. V tomto návodu změníte hodnotu na 6553600. Změníte hodnotu v klientovi a tato akce automaticky aktualizuje odkaz na službu.

> [!NOTE]
> Dolní výchozí velikost je určena k omezení vystavení útokům DOS (Denial of Service). Další informace najdete v tématu <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Zvýšení hodnoty maxReceivedMessageSize

1. V **Průzkumník řešení**dvakrát klikněte na soubor App. config v projektu PresentationTier.

2. Vyhledejte atribut size **maxReceivedMessage** a změňte hodnotu na `6553600`.

## <a name="testing-the-application"></a>Testování aplikace
 Spusťte aplikaci. Data se načítají z datové služby a zobrazují se na formuláři.

#### <a name="to-test-the-application"></a>Testování aplikace

1. Stiskněte klávesu F5.

2. Data z tabulek Customers a Orders se načítají z datové služby a zobrazují se na formuláři.

## <a name="next-steps"></a>Další kroky
 V závislosti na požadavcích vaší aplikace existuje několik kroků, které můžete chtít provést po uložení souvisejících dat v aplikaci pro systém Windows. Můžete například provést následující vylepšení této aplikace:

- Přidejte ověření do datové sady. Informace najdete v tématu [Návod: Přidání ověřování do N-vrstvých datových aplikací](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265).

- Do služby přidejte další metody pro aktualizaci dat zpět do databáze.

## <a name="see-also"></a>Viz také
 [Práce s datovými sadami v n-vrstvých aplikacích](../data-tools/work-with-datasets-in-n-tier-applications.md) [Hierarchická aktualizace](../data-tools/hierarchical-update.md) pro [přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
