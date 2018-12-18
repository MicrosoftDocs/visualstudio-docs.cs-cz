---
title: 'Návod: Vytvoření víceúrovňové datové aplikace'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 71c1c8dbaf34613d07ce29fa3f5e08d8e9c6961f
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305698"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>Návod: Vytvoření vícevrstvé datové aplikace
*N-vrstvá* datové aplikace jsou aplikace, které přístup k datům a jsou rozdělené do několika logické vrstvy, nebo *úrovně*. Rozdělení komponent aplikace do samostatných vrstev zvyšuje udržovatelnost a škálovatelnost aplikace. Dělá to tak, že umožněno snadnější přijímání nových technologií, které lze použít u jedné vrstvě, aniž by bylo potřeba změnit návrh celého řešení. N-vrstvá architektura obsahuje prezentační vrstvu, střední vrstvy, a datové vrstvy. Střední vrstva obvykle zahrnuje vrstvy přístupu k datům, vrstvy obchodní logiky a sdílené komponenty, jako je například ověřování a ověřování. Datová vrstva obsahuje relační databáze. N-vrstvá aplikace obvykle ukládá citlivé informace do vrstvy přístupu k datům z střední vrstvy, aby se zachovala izolace koncovým uživatelům, kteří přistupují k prezentační vrstvy. Další informace najdete v tématu [přehled vícevrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md).

Jedním ze způsobů k rozdělení různých vrstev v n vrstvé aplikaci je vytvoření samostatných projektů pro každou vrstvu, která chcete zahrnout do vaší aplikace. Typové datové sady obsahují `DataSet Project` vlastnost, která určuje, že generované datová sada projekty, které a `TableAdapter` kódu by měly patřit do.

Tento návod ukazuje, jak oddělit datové sady a `TableAdapter` kód do samostatné třídy knihovny projektů s použitím **Návrhář Dataset**. Po oddělíte datové sady a TableAdapter kódu, můžete vytvořit [služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) služby, chcete-li volat vrstvě přístupu k datům. Nakonec vytvořte aplikaci Windows Forms jako prezentační vrstvy. Tato úroveň přistupuje k datům z datové služby.

V tomto návodu provedete následující kroky:

-   Vytvořte nové n vrstvé řešení, která obsahuje více projektů.

-   Přidejte dva projekty knihovny tříd pro n vrstvého řešení.

-   Vytvoření typové datové sady s použitím **Průvodce konfigurací zdroje dat**.

-   Oddělení generované [objekty TableAdapter](create-and-configure-tableadapters.md) a kód datovou sadu do samostatných projektů.

-   Vytvoření služby Windows Communication Foundation (WCF) Chcete-li volat vrstvě přístupu k datům.

-   Funkce můžete vytvořte ve službě k načtení dat z vrstvě přístupu k datům.

-   Vytvoření aplikace Windows Forms, která bude sloužit jako prezentační vrstvy.

-   Ovládací prvky Windows Forms, které jsou vázány na zdroj dat vytvořte.

-   Napsání kódu pro naplnění dat tabulky.

![odkaz na video](../data-tools/media/playvideo.gif) video verzi tohoto tématu naleznete v tématu [Video postupy: vytvoření vícevrstvé datové aplikace](http://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Požadavky
Tento návod používá SQL Server Express LocalDB a ukázkové databáze Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji z [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program sady Visual Studio**. V **instalační program sady Visual Studio**, jako součást můžete nainstalovat SQL Server Express LocalDB **vývoj desktopových aplikací .NET** úlohy, nebo jako jednotlivých komponent.

2. Instalace ukázkové databáze Northwind pomocí následujících kroků:

    1. V sadě Visual Studio, otevřete **Průzkumník objektů systému SQL Server** okna. (**Průzkumník objektů systému SQL Server** je nainstalován jako součást **ukládání a zpracování dat** úlohy v instalačním programu sady Visual Studio.) Rozbalte **systému SQL Server** uzlu. Klikněte pravým tlačítkem na instanci LocalDB a vyberte **nový dotaz**.

       Otevře se okno editor dotazů.

    2. Kopírovat [Northwind příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind úplně od začátku a naplní daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po chvilce dotaz doběhnutí a vytvořit databázi Northwind.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Vytvoření n vrstvé řešení a třídy knihovny pro objekt dataset (DataEntityTier)
 Prvním krokem tohoto průvodce je k vytváření řešení a dva projekty knihovny tříd. První třídy knihovny obsahuje datovou sadu (generované typy `DataSet` třídy a datové tabulky, které uchovávají data, aplikace). Tento projekt slouží jako vrstva entity dat aplikace a je obvykle umístěn ve střední vrstvě. Datová sada vytvoří počáteční datová sada a automaticky odděluje kód do knihovny dvou tříd.

> [!NOTE]
> Nezapomeňte před kliknutím na správně název projektu a řešení **OK**. To usnadní vám k dokončení tohoto návodu.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Vytvoření n-vrstvého řešení a knihovny tříd DataEntityTier

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

3. V prostředním podokně, vyberte **knihovny tříd** typ projektu.

4. Pojmenujte projekt **DataEntityTier**.

5. Pojmenujte řešení **NTierWalkthrough**a klikněte na tlačítko **OK**.

     Řešení NTierWalkthrough obsahující DataEntityTier projekt je vytvořen a přidán do **Průzkumníka řešení**.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Vytvoření knihovny tříd pro objekty TableAdapter (DataAccessTier)
 Dalším krokem po vytvoření projektu DataEntityTier je vytvořte nový projekt knihovny tříd. Tento projekt obsahuje vygenerované objekty TableAdapter a je volána *vrstvě přístupu k datům* aplikace. Úroveň přístupu dat obsahuje informace, které se nejde připojit k databázi a je obvykle umístěn ve střední vrstvě.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Chcete-li vytvořit samostatné knihovně tříd pro objekty TableAdapter

1. Klikněte pravým tlačítkem na řešení v **Průzkumníka řešení** a zvolte **přidat** > **nový projekt**.

2. V **nový projekt** dialogové okno, v prostředním podokně vyberte **knihovny tříd**.

3. Pojmenujte projekt **DataAccessTier** a zvolte **OK**.

     Projektu DataAccessTier je vytvořen a přidán do řešení NTierWalkthrough.

## <a name="create-the-dataset"></a>Vytvořte datovou sadu
 Dalším krokem je vytvoření typové datové sady. Typové datové sady vytvořené pomocí třídy datové sady (včetně `DataTables` třídy) a `TableAdapter` třídy v jednom projektu. (Všechny třídy jsou generovány, do jediného souboru.) Když oddělíte datové sady a TableAdapters do různých projektů, je třída datovou sadu, která je přesunut do jiného projektu, byste museli opustit `TableAdapter` třídy v původní projekt. Proto se v projektu, který bude obsahovat nakonec objekty TableAdapter (DataAccessTier projekt) vytvořte datovou sadu. Vytvořte datovou sadu s použitím **Průvodce konfigurací zdroje dat**.

> [!NOTE]
> Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o tom, jak nastavit ukázkové databáze Northwind naleznete v tématu [postupy: Instalace ukázkových databází](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>Vytvoření datové sady

1. Vyberte **DataAccessTier** v **Průzkumníka řešení**.

2. Na **Data** nabídce vyberte možnost **zobrazit zdroje dat**.

   **Zdroje dat** otevře se okno.

3. V **zdroje dat** okně **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.

4. Na **zvolte typ zdroje dat** stránce **databáze** a pak vyberte **Další**.

5. Na **vyberte datové připojení** stránce, proveďte jednu z následujících akcí:

     Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

     -nebo-

     Vyberte **nové připojení** otevřít **přidat připojení** dialogové okno.

6. Pokud databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a klikněte na tlačítko **Další**.

    > [!NOTE]
    > Pokud jste vybrali lokálního databázového souboru (místo připojování k serveru SQL Server) může být vyzváni, pokud budete chtít přidat soubor do projektu. Zvolte **Ano** přidáte databázový soubor do projektu.

7. Vyberte **Další** na **uložit připojovací řetězec do konfiguračního souboru aplikace** stránky.

8. Rozbalte **tabulky** uzlu **zvolte vaše databázové objekty** stránky.

9. Zaškrtněte políčka pro **zákazníkům** a **objednávky** tabulky a klikněte na tlačítko **Dokončit**.

     NorthwindDataSet se přidá do projektu DataAccessTier a zobrazí se v **zdroje dat** okna.

## <a name="separate-the-tableadapters-from-the-dataset"></a>Oddělení objektů TableAdapter od objektu Dataset
 Po vytvoření datové sady, nezávislá na infrastruktuře vytvořenou třídu datové sady objektů TableAdapter. To provedete tak, že nastavíte **projektu DataSet** nastavte na název projektu, do které můžete ukládat oddělených mimo třídu datové sady.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Oddělení objektů TableAdapter od objektu DataSet

1. Dvakrát klikněte na panel **NorthwindDataSet.xsd** v **Průzkumníka řešení** otevření datové sady v **Návrhář Dataset**.

2. Vyberte prázdnou oblast v návrháři.

3. Vyhledejte **projektu DataSet** uzlu **vlastnosti** okna.

4. V **projektu DataSet** seznamu vyberte **DataEntityTier**.

5. Na **sestavení** nabídce vyberte možnost **sestavit řešení**.

   Datové sady a objekty TableAdapter jsou rozděleny do projektů knihovny dvou tříd. Projekt, který je původně obsahoval celou datovou sadu (`DataAccessTier`) teď obsahuje pouze objekty TableAdapter. Projekt je určeno v **projektu DataSet** vlastnosti (`DataEntityTier`) obsahuje typové datové sady: *NorthwindDataSet.Dataset.Designer.vb* (nebo  *NorthwindDataSet.Dataset.Designer.cs*).

> [!NOTE]
> Když oddělíte datové sady a objekty TableAdapter (nastavením **projektu DataSet** vlastnost), existující částečné třídy v projektu nebudou automaticky přesunuty. Existující částečné třídy datové sady musí ručně přesunout do projektu datové sady.

## <a name="create-a-new-service-application"></a>Vytvoření nové aplikace služby
Tento návod ukazuje, jak k vrstvě přístupu k datům s využitím služby WCF, takže vytvoření nové aplikace služby WCF.

### <a name="to-create-a-new-wcf-service-application"></a>Vytvoření nové aplikace služby WCF

1. Klikněte pravým tlačítkem na řešení v **Průzkumníka řešení** a zvolte **přidat** > **nový projekt**.

2. V **nový projekt** dialogové okno, v levém podokně vyberte **WCF**. V prostředním podokně vyberte **knihovny služby WCF**.

3. Pojmenujte projekt **DataService** a vyberte **OK**.

     Službě DataService projekt je vytvořen a přidán do řešení NTierWalkthrough.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Vytvoření metod ve vrstvě přístupu k datům pro vrácení dat zákazníci a objednávky
 Datové služby je volat dvě metody ve vrstvě přístupu k datům: `GetCustomers` a `GetOrders`. Tyto metody vrací Northwind `Customers` a `Orders` tabulky. Vytvořte `GetCustomers` a `GetOrders` metody v `DataAccessTier` projektu.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Vytvoření metody, která vrací tabulku Customers, ve vrstvě přístupu k datům

1. V **Průzkumníka řešení**, dvakrát klikněte na panel **NorthwindDataset.xsd** otevřete datovou sadu.

2. Klikněte pravým tlačítkem na **CustomersTableAdapter** a klikněte na tlačítko **přidat dotaz**.

3. Na **zvolit typ příkazu** ponechte výchozí hodnotu **použít SQL příkazy** a klikněte na tlačítko **Další**.

4. Na **zvolit typ dotazu** ponechte výchozí hodnotu **SELECT, který vrátí řádky** a klikněte na tlačítko **Další**.

5. Na **zadat příkaz jazyka SQL SELECT** stránce nechejte výchozí dotaz a klikněte na tlačítko **Další**.

6. Na **zvolte metody k vytvoření** zadejte **GetCustomers** pro **název metody** v **vrátit tabulku DataTable** oddílu.

7. Klikněte na tlačítko **Dokončit**.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Vytvoření metody, která vrací tabulku Orders, ve vrstvě přístupu k datům

1. Klikněte pravým tlačítkem na **OrdersTableAdapter** a klikněte na tlačítko **přidat dotaz**.

2. Na **zvolit typ příkazu** ponechte výchozí hodnotu **použít SQL příkazy** a klikněte na tlačítko **Další**.

3. Na **zvolit typ dotazu** ponechte výchozí hodnotu **SELECT, který vrátí řádky** a klikněte na tlačítko **Další**.

4. Na **zadat příkaz jazyka SQL SELECT** stránce nechejte výchozí dotaz a klikněte na tlačítko **Další**.

5. Na **zvolte metody k vytvoření** zadejte **GetOrders** pro **název metody** v **vrátit tabulku DataTable** oddílu.

6. Klikněte na tlačítko **Dokončit**.

7. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Přidat odkaz na entitu dat a datovou vrstvou přístupu k datové službě
 Vzhledem k tomu, že datová služba vyžaduje informace z datové sady a instancí TableAdapter, přidejte odkazy **DataEntityTier** a **DataAccessTier** projekty.

### <a name="to-add-references-to-the-data-service"></a>Přidání odkazů do datové služby

1. Klikněte pravým tlačítkem na **DataService** v **Průzkumníka řešení** a klikněte na tlačítko **přidat odkaz**.

2. Klikněte na tlačítko **projekty** kartu **přidat odkaz** dialogové okno.

3. Vyberte **DataAccessTier** a **DataEntityTier** projekty.

4. Klikněte na tlačítko **OK**.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Přidání funkcí do služby pro volání metod GetCustomers a GetOrders ve vrstvě přístupu k datům
 Teď, když datová vrstva obsahuje metody, které se vrátí data, vytvářet metody v datové službě dovoluje volat metody ve vrstvě přístupu k datům.

> [!NOTE]
> Pro projekty jazyka C#, je nutné přidat odkaz na `System.Data.DataSetExtensions` sestavení pro následující kód pro kompilaci.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Vytvoření funkcí GetCustomers a GetOrders v datové službě

1. V **DataService** projektu, klikněte dvakrát na **IService1.vb** nebo **IService1.cs**.

2. Přidejte následující kód **přidejte servisní operace zde** komentář:

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

3. Ve službě DataService projektu, klikněte dvakrát na **Service1.vb** (nebo **Service1.cs**).

4. Přidejte následující kód, který **Service1** třídy:

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

5. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Vytvoření prezentační vrstvy zobrazující data z datové služby
 Teď, když řešení obsahuje datové služby, která obsahuje metody, která volá do dat vrstvě přístupu k, vytvořte nový projekt, který volá do datové služby a představují data pro uživatele. V tomto návodu vytvoření aplikace Windows Forms; Toto je prezentační vrstvy n vrstvé aplikace.

### <a name="to-create-the-presentation-tier-project"></a>Vytvoření projektu prezentační vrstvy

1. Klikněte pravým tlačítkem na řešení v **Průzkumníka řešení** a zvolte **přidat** > **nový projekt**.

2. V **nový projekt** dialogové okno, v levém podokně vyberte **Windows Desktop**. V prostředním podokně vyberte **aplikace Windows Forms**.

3. Pojmenujte projekt **PresentationTier** a klikněte na tlačítko **OK**.

    Projektu PresentationTier je vytvořen a přidán do řešení NTierWalkthrough.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>Nastavení projektu PresentationTier jako spouštěného projektu
Nastavíme **PresentationTier** projekt jako projekt po spuštění pro řešení, protože se jedná o skutečné klientská aplikace, která představuje a pracuje s daty.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Nastavení nového projektu prezentační vrstvy jako spouštěného projektu

-   V **Průzkumníka řešení**, klikněte pravým tlačítkem na **PresentationTier** a klikněte na tlačítko **nastavit jako spouštěný projekt**.

## <a name="add-references-to-the-presentation-tier"></a>Přidání odkazů do prezentační vrstvy
 Klientská aplikace PresentationTier vyžaduje odkaz na službu ve službě data k přístup k metodám ve službě. Odkaz na datovou sadu se kromě toho je potřeba povolit typ sdílení ve službě WCF. Dokud nepovolíte sdílení prostřednictvím datové služby typu kódu do částečné třídy není k dispozici do prezentační vrstvy. Vzhledem k tomu obvykle přidáte kód, jako je například kód pro ověření do řádků a sloupců, změna událostí datové tabulky, je pravděpodobné, že budete chtít přístup tento kód z klienta.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>Přidání odkazu do prezentační vrstvy

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **PresentationTier** a vyberte **přidat odkaz**.

2. V **přidat odkaz** dialogové okno, vyberte **projekty** kartu.

3. Vyberte **DataEntityTier** a zvolte **OK**.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Přidání odkazu na službu do prezentační vrstvy

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **PresentationTier** a vyberte **přidat odkaz na službu**.

2. V **přidat odkaz na službu** dialogu **Discover**.

3. Vyberte **Service1** a zvolte **OK**.

    > [!NOTE]
    > Pokud máte několik služeb, které na počítač, vyberte službu, kterou jste vytvořili dříve v tomto názorném postupu (službu, která obsahuje `GetCustomers` a `GetOrders` metody).

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Přidání ovládacích prvků DataGridView do formuláře a zobrazení dat vrácených datovou službou
 Poté, co přidáte odkaz na službu do datové služby **zdroje dat** okno se automaticky načtou data, která je vrácena službou.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Přidání dvou ovládacích prvků DataGridView vázaných na data do formuláře

1. V **Průzkumníka řešení**, vyberte **PresentationTier** projektu.

2. V **zdroje dat** okna rozbalte **NorthwindDataSet** a vyhledejte **zákazníkům** uzlu.

3. Přetáhněte **zákazníkům** uzlu do formuláře Form1.

4. V **zdroje dat** okna, rozbalte **zákazníkům** uzlu a vyhledejte související **objednávky** uzel ( **objednávky** uzel vnořené v  **Zákazníci** uzlu).

5. Přetáhněte související **objednávky** uzlu do formuláře Form1.

6. Vytvoření `Form1_Load` obslužná rutina události dvojitým kliknutím na prázdnou oblast formuláře.

7. Přidejte následující kód, který `Form1_Load` obslužné rutiny události.

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

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Zvětšete maximální velikost zprávy povolené službou
Výchozí hodnota pro `maxReceivedMessageSize` není dostatečně velký pro uložení dat načtených z `Customers` a `Orders` tabulky. V následujícím postupu zvýšíte hodnotu 6553600. Můžete změnit hodnoty na straně klienta, která automaticky aktualizuje odkaz na službu.

> [!NOTE]
> Nižší výchozí velikost je určena k omezení rizika útoky na dostupnost služby (DoS). Další informace naleznete v tématu <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Zvýšení hodnoty maxReceivedMessageSize

1. V **Průzkumníka řešení**, dvakrát klikněte **app.config** ve **PresentationTier** projektu.

2. Vyhledejte **maxReceivedMessage** velikost atribut a změňte hodnotu na `6553600`.

## <a name="test-the-application"></a>Testování aplikace
Spusťte aplikaci stisknutím klávesy **F5**. Data z `Customers` a `Orders` tabulek je načten z datové služby a zobrazí ve formuláři.

## <a name="next-steps"></a>Další kroky
 V závislosti na požadavcích aplikace existuje několik kroků, které můžete chtít provést po uložení souvisejících dat v aplikaci založené na Windows. Může například vytvořit následující vylepšení této aplikace:

-   Přidání ověřování do datové sady.

-   Přidáte další metody pro službu pro aktualizaci dat zpět do databáze.

## <a name="see-also"></a>Viz také:

- [Práce s datovými sadami ve vícevrstvých aplikacích](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Hierarchická aktualizace](../data-tools/hierarchical-update.md)
- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)