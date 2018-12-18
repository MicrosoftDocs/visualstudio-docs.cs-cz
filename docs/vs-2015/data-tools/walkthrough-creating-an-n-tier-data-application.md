---
title: 'Návod: Vytvoření vícevrstvé datové aplikace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 37876502a464e263ebd6803216b29bd62b65af5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890176"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Návod: Vytvoření víceúrovňové datové aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
N-úroveň * datové aplikace jsou aplikace, které přístup k datům a jsou rozdělené do několika logické vrstvy, nebo *úrovně*. Rozdělení komponent aplikace do samostatných vrstev zvyšuje udržovatelnost a škálovatelnost aplikace. Dělá to tak, že umožněno snadnější přijímání nových technologií, které lze použít u jedné vrstvě, aniž by bylo potřeba změnit návrh celého řešení. N-vrstvá architektura obsahuje prezentační vrstvu, střední vrstvy, a datové vrstvy. Střední vrstva obvykle zahrnuje vrstvy přístupu k datům, vrstvy obchodní logiky a sdílené komponenty, jako je například ověřování a ověřování. Datová vrstva obsahuje relační databáze. N-vrstvá aplikace obvykle ukládá citlivé informace do vrstvy přístupu k datům z střední vrstvy, aby se zachovala izolace koncovým uživatelům, kteří přistupují k prezentační vrstvy. Další informace najdete v tématu [přehled vícevrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md).  
  
 Jedním ze způsobů k rozdělení různých vrstev v n vrstvé aplikaci je vytvoření samostatných projektů pro každou vrstvu, která chcete zahrnout do vaší aplikace. Typové datové sady obsahují `DataSet Project` vlastnost, která určuje, že generované datová sada projekty, které a `TableAdapter` kódu by měly patřit do.  
  
 Tento návod ukazuje, jak oddělit datové sady a `TableAdapter` kód do samostatné třídy knihovny projektů s použitím **Návrhář Dataset**. Po oddělíte datové sady a TableAdapter kód, vytvoříte [služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) služby, chcete-li volat vrstvě přístupu k datům. Nakonec se vytvoří aplikace Windows Forms jako prezentační vrstvy. Tato úroveň přistupuje k datům z datové služby.  
  
 V tomto návodu provedete následující kroky:  
  
- Vytvořte nové n vrstvé řešení, která bude obsahovat více projektů.  
  
- Přidejte dva projekty knihovny tříd pro n vrstvého řešení.  
  
- Vytvoření typové datové sady s použitím **Průvodce konfigurací zdroje dat**.  
  
- Oddělení generované [objekty TableAdapter](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) a kód datovou sadu do samostatných projektů.  
  
- Vytvoření služby Windows Communication Foundation (WCF) Chcete-li volat vrstvě přístupu k datům.  
  
- Funkce můžete vytvořte ve službě k načtení dat z vrstvě přístupu k datům.  
  
- Vytvoření aplikace Windows Forms, která bude sloužit jako prezentační vrstvy.  
  
- Ovládací prvky Windows Forms, které jsou vázány na zdroj dat vytvořte.  
  
- Napsání kódu pro naplnění dat tabulky.  
  
  ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") video verzi tohoto tématu naleznete v tématu [Video postupy: vytvoření vícevrstvé datové aplikace](http://go.microsoft.com/fwlink/?LinkId=115188).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
-   Přístup k ukázkové databázi Northwind. Další informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Vytvoření N-vrstvého řešení a knihovny tříd pro objekt Dataset (DataEntityTier)  
 Prvním krokem tohoto průvodce je k vytváření řešení a dva projekty knihovny tříd. První třídy knihovny bude obsahovat datovou sadu (generované zadali třídu datové sady a datové tabulky, která bude obsahovat data aplikace). Tento projekt slouží jako vrstva entity dat aplikace a je obvykle umístěn ve střední vrstvě. [Vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md) slouží k vytvoření počáteční datové sady a automaticky rozdělení kódu do knihovny dvou tříd.  
  
> [!NOTE]
>  Nezapomeňte před kliknutím na správně název projektu a řešení **OK**. To usnadní vám k dokončení tohoto návodu.  
  
#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Vytvoření n-vrstvého řešení a knihovny tříd DataEntityTier  
  
1.  Z **souboru** nabídky, vytvořte nový projekt.  
  
    > [!NOTE]
    >  **Návrhář Dataset** je podporována v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] a projekty jazyka C#. Vytvoření nového projektu v jednom z těchto jazyků.  
  
2.  V **nový projekt** v dialogu **typy projektů** podokně klikněte na tlačítko **Windows**.  
  
3.  Klikněte na tlačítko **knihovny tříd** šablony.  
  
4.  Pojmenujte projekt **DataEntityTier**.  
  
5.  Pojmenujte řešení **NTierWalkthrough**.  
  
6.  Klikněte na tlačítko **OK**.  
  
     Řešení NTierWalkthrough obsahující DataEntityTier projekt je vytvořen a přidán do **Průzkumníka řešení**.  
  
## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Vytvoření knihovny tříd pro objekty TableAdapter (DataAccessTier)  
 Dalším krokem po vytvoření projektu DataEntityTier je vytvořte nový projekt knihovny tříd. Tento projekt bude obsahovat generované `TableAdapter`s názvem *vrstvě přístupu k datům* aplikace. Úroveň přístupu dat obsahuje informace, které se nejde připojit k databázi a je obvykle umístěn ve střední vrstvě.  
  
#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>Vytvoření nové knihovny tříd pro objekty TableAdapter  
  
1.  Z **souboru** nabídce, přidat nový projekt do řešení NTierWalkthrough.  
  
2.  V **nový projekt** v dialogu **šablony** podokně klikněte na tlačítko **knihovny tříd**.  
  
3.  Pojmenujte projekt **DataAccessTier** a klikněte na tlačítko **OK**.  
  
     Projektu DataAccessTier je vytvořen a přidán do řešení NTierWalkthrough.  
  
## <a name="creating-the-dataset"></a>Vytvoření datové sady  
 Dalším krokem je vytvoření typové datové sady. Typové datové sady vytvořené pomocí třídy datové sady (včetně DataTables třídy) a `TableAdapter` třídy v jednom projektu. (Všechny třídy jsou generovány, do jediného souboru.) Když oddělíte datové sady a `TableAdapter`s do různých projektů, je třída datovou sadu, která je přesunut do jiného projektu, byste museli opustit `TableAdapter` třídy v původní projekt. Proto vytvořit datovou sadu v projektu, který bude obsahovat takže v konečném důsledku `TableAdapter`s (projektu DataAccessTier). Vytvoříte datovou sadu s použitím **Průvodce konfigurací zdroje dat**.  
  
> [!NOTE]
>  Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o tom, jak nastavit ukázkové databáze Northwind naleznete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-dataset"></a>Vytvoření datové sady  
  
1.  Klikněte na tlačítko DataAccessTier v **Průzkumníka řešení**.  
  
2.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
3.  V **zdroje dat** okna, klikněte na tlačítko **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.  
  
4.  Na **zvolte typ zdroje dat** klikněte na **databáze** a potom klikněte na tlačítko **Další**.  
  
5.  Na **vyberte datové připojení** stránce, proveďte jednu z následujících akcí:  
  
     Pokud připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, klikněte na něj.  
  
     -nebo-  
  
     Klikněte na tlačítko **nové připojení** otevřít **přidat připojení** dialogové okno.  
  
6.  Pokud databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak klikněte na tlačítko **Další**.  
  
    > [!NOTE]
    >  Pokud jste vybrali lokálního databázového souboru (místo připojování k serveru SQL Server) může být vyzváni, pokud budete chtít přidat soubor do projektu. Klikněte na tlačítko **Ano** přidáte databázový soubor do projektu.  
  
7.  Klikněte na tlačítko **Další** na **uložit připojovací řetězec do konfiguračního souboru aplikace** stránky.  
  
8.  Rozbalte **tabulky** uzlu **zvolte vaše databázové objekty** stránky.  
  
9. Klikněte na tlačítko zaškrtnutí políček u **zákazníkům** a **objednávky** tabulky a pak klikněte na tlačítko **Dokončit**.  
  
     NorthwindDataSet se přidá do projektu DataAccessTier a zobrazí se v **zdroje dat** okna.  
  
## <a name="separating-the-tableadapters-from-the-dataset"></a>Oddělení objektů TableAdapter od objektu DataSet  
 Po vytvoření datové sady, nezávislá na infrastruktuře vytvořenou třídu datové sady objektů TableAdapter. To provedete tak, že nastavíte **projektu DataSet** nastavte na název projektu, do které můžete ukládat oddělených mimo třídu datové sady.  
  
#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Oddělení objektů TableAdapter od objektu DataSet  
  
1. Dvakrát klikněte na panel **NorthwindDataSet.xsd** v **Průzkumníka řešení** otevření datové sady v **Návrhář Dataset**.  
  
2. Klepněte na prázdnou oblast v návrháři.  
  
3. Vyhledejte **projektu DataSet** uzlu **vlastnosti** okna.  
  
4. V **projektu DataSet** klikněte na možnost **DataEntityTier**.  
  
5. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
   Datové sady a objekty TableAdapter jsou rozděleny do projektů knihovny dvou tříd. Projekt, který je původně obsahoval celou datovou sadu (DataAccessTier) teď obsahuje pouze objekty TableAdapter. Projekt je určeno v **projektu DataSet** vlastnost (DataEntityTier) obsahuje typové datové sady: NorthwindDataSet.Dataset.Designer.vb (nebo NorthwindDataSet.Dataset.Designer.cs).  
  
> [!NOTE]
>  Když oddělíte datové sady a objekty TableAdapter (nastavením **projektu DataSet** vlastnost), existující částečné třídy v projektu nebudou automaticky přesunuty. Existující částečné třídy datové sady musí ručně přesunout do projektu datové sady.  
  
## <a name="creating-a-new-service-application"></a>Vytvoření nové aplikace služby  
 Protože tento návod ukazuje, jak získat přístup k vrstvě přístupu k datům s použitím služby WCF, vytvořte nové aplikace služby WCF.  
  
#### <a name="to-create-a-new-wcf-service-application"></a>Vytvoření nové aplikace služby WCF  
  
1.  Z **souboru** nabídce, přidat nový projekt do řešení NTierWalkthrough.  
  
2.  V **nový projekt** v dialogu **typy projektů** podokně klikněte na tlačítko **WCF**. V **šablony** podokně klikněte na tlačítko **knihovny služby WCF**.  
  
3.  Pojmenujte projekt **DataService** a klikněte na tlačítko **OK**.  
  
     Službě DataService projekt je vytvořen a přidán do řešení NTierWalkthrough.  
  
## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Vytvoření metod, které vrací data zákazníků a objednávek, ve vrstvě přístupu k datům  
 Datové služby je volat dvě metody ve vrstvě přístupu k datům: funkcí GetCustomers a GetOrders. Tyto metody vrátí tabulky Northwind zákazníci a objednávky. Vytvoření metod GetCustomers a GetOrders v projektu DataAccessTier.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Vytvoření metody, která vrací tabulku Customers, ve vrstvě přístupu k datům  
  
1.  V **Průzkumníka řešení**, dvakrát klikněte na panel NorthwindDataset.xsd otevřete datovou sadu v [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md).  
  
2.  Klikněte pravým tlačítkem na CustomersTableAdapter a klikněte na tlačítko **přidat dotaz** otevřít [úpravy objektů TableAdapter](../data-tools/editing-tableadapters.md).  
  
3.  Na **zvolit typ příkazu** ponechte výchozí hodnotu **použít SQL příkazy** a klikněte na tlačítko **Další**.  
  
4.  Na **zvolit typ dotazu** ponechte výchozí hodnotu **SELECT, který vrátí řádky** a klikněte na tlačítko **Další**.  
  
5.  Na **zadat příkaz jazyka SQL SELECT** stránce nechejte výchozí dotaz a klikněte na tlačítko **Další**.  
  
6.  Na **zvolte metody k vytvoření** zadejte **GetCustomers** pro **název metody** v **vrátit tabulku DataTable** oddílu.  
  
7.  Klikněte na tlačítko **Dokončit**.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Vytvoření metody, která vrací tabulku Orders, ve vrstvě přístupu k datům  
  
1.  Klikněte pravým tlačítkem na OrdersTableAdapter a klikněte na tlačítko **přidat dotaz**.  
  
2.  Na **zvolit typ příkazu** ponechte výchozí hodnotu **použít SQL příkazy** a klikněte na tlačítko **Další**.  
  
3.  Na **zvolit typ dotazu** ponechte výchozí hodnotu **SELECT, který vrátí řádky** a klikněte na tlačítko **Další**.  
  
4.  Na **zadat příkaz jazyka SQL SELECT** stránce nechejte výchozí dotaz a klikněte na tlačítko **Další**.  
  
5.  Na **zvolte metody k vytvoření** zadejte **GetOrders** pro **název metody** v **vrátit tabulku DataTable** oddílu.  
  
6.  Klikněte na tlačítko **Dokončit**.  
  
7.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Přidání odkazu na vrstvu datové entity a vrstvu přístupu k datům do datové služby  
 Vzhledem k tomu, že datová služba vyžaduje informace z datové sady a instancí TableAdapter, přidejte odkazy na projekty DataEntityTier a DataAccessTier.  
  
#### <a name="to-add-references-to-the-data-service"></a>Přidání odkazů do datové služby  
  
1.  Klikněte pravým tlačítkem na službě DataService v **Průzkumníka řešení** a klikněte na tlačítko **přidat odkaz**.  
  
2.  Klikněte na tlačítko **projekty** kartu **přidat odkaz** dialogové okno.  
  
3.  Vyberte **DataAccessTier** a **DataEntityTier** projekty.  
  
4.  Klikněte na tlačítko **OK**.  
  
## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Přidání funkcí do služby za účelem volání metod GetCustomers a GetOrders ve vrstvě přístupu k datům  
 Teď, když datová vrstva obsahuje metody, které se vrátí data, vytvářet metody v datové službě dovoluje volat metody ve vrstvě přístupu k datům.  
  
> [!NOTE]
>  Pro projekty jazyka C#, je nutné přidat odkaz na `System.Data.DataSetExtensions` sestavení pro následující kód pro kompilaci.  
  
#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Vytvoření funkcí GetCustomers a GetOrders v datové službě  
  
1.  V **DataService** projektu, dvakrát klikněte na panel IService1.vb nebo IService1.cs.  
  
2.  Přidejte následující kód **přidejte servisní operace zde** komentář:  
  
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
  
3.  Ve službě DataService projektu klikněte dvakrát na Service1.vb (nebo Service1.cs).  
  
4.  Přidejte následující kód do třídy Service1:  
  
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
  
5.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Vytvoření prezentační vrstvy zobrazující data z datové služby  
 Teď, když řešení obsahuje datové služby, který má metody, které volají na vrstvě přístupu k datům, vytvořte nový projekt, který bude provádět volání do datové služby a prezentovat data pro uživatele. V tomto návodu vytvoření aplikace Windows Forms; Toto je prezentační vrstvy n vrstvé aplikace.  
  
#### <a name="to-create-the-presentation-tier-project"></a>Vytvoření projektu prezentační vrstvy  
  
1.  Z **souboru** nabídce, přidat nový projekt do řešení NTierWalkthrough.  
  
2.  V **nový projekt** v dialogu **typy projektů** podokně klikněte na tlačítko **Windows**. V **šablony** podokně klikněte na tlačítko **formulářová aplikace Windows**.  
  
3.  Pojmenujte projekt **PresentationTier** a klikněte na tlačítko **OK**.  
  
4.  Projektu PresentationTier je vytvořen a přidán do řešení NTierWalkthrough.  
  
## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Nastavení projektu PresentationTier jako spouštěného projektu  
 Protože prezentační vrstvy aplikace skutečný klient, který se používá k zobrazení a interakci s daty, je nutné nastavit projektu PresentationTier jako spouštěného projektu.  
  
#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Nastavení nového projektu prezentační vrstvy jako spouštěného projektu  
  
-   V **Průzkumníka řešení**, klikněte pravým tlačítkem na **PresentationTier** a klikněte na tlačítko **nastavit jako spouštěný projekt**.  
  
## <a name="adding-references-to-the-presentation-tier"></a>Přidání odkazů do prezentační vrstvy  
 Klientská aplikace PresentationTier vyžaduje odkaz na službu ve službě data k přístup k metodám ve službě. Odkaz na datovou sadu se kromě toho je potřeba povolit typ sdílení ve službě WCF. Dokud nepovolíte sdílení prostřednictvím datové služby typu kódu do částečné třídy budou dostupné do prezentační vrstvy. Vzhledem k tomu obvykle přidáte kód, jako je třeba ověřování do řádků a sloupců, změna událostí datové tabulky, je pravděpodobné, že budete chtít přístup tento kód z klienta.  
  
#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Přidání odkazu do prezentační vrstvy  
  
1.  V **Průzkumníka řešení**PresentationTier pravým tlačítkem myši a klikněte na tlačítko **přidat odkaz**.  
  
2.  V **přidat odkaz** dialogové okno, klikněte na tlačítko **projekty** kartu.  
  
3.  Vyberte **DataEntityTier** a klikněte na tlačítko **OK**.  
  
#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Přidání odkazu na službu do prezentační vrstvy  
  
1.  V **Průzkumníka řešení**PresentationTier pravým tlačítkem myši a klikněte na tlačítko **přidat odkaz na službu**.  
  
2.  V **přidat odkaz na službu** dialogové okno, klikněte na tlačítko **Discover**.  
  
3.  Vyberte **Service1** a klikněte na tlačítko **OK**.  
  
    > [!NOTE]
    >  Pokud máte několik služeb, které na počítač, vyberte službu, kterou jste vytvořili dříve v tomto názorném postupu (službu, která obsahuje metod GetCustomers a GetOrders).  
  
## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Přidání ovládacích prvků DataGridView do formuláře a zobrazení dat vrácených datovou službou  
 Poté, co přidáte odkaz na službu do datové služby **zdroje dat** okno se automaticky načtou data, která je vrácena službou.  
  
#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Přidání dvou ovládacích prvků DataGridView vázaných na data do formuláře  
  
1.  V **Průzkumníka řešení**, vyberte projektu PresentationTier.  
  
2.  V **zdroje dat** okna rozbalte **NorthwindDataSet** a vyhledejte **zákazníkům** uzlu.  
  
3.  Přetáhněte **zákazníkům** uzlu do formuláře Form1.  
  
4.  V **zdroje dat** okna, rozbalte **zákazníkům** uzlu a vyhledejte související **objednávky** uzel ( **objednávky** uzel vnořené v  **Zákazníci** uzlu).  
  
5.  Přetáhněte související **objednávky** uzlu do formuláře Form1.  
  
6.  Vytvoření `Form1_Load` obslužná rutina události dvojitým kliknutím na prázdnou oblast formuláře.  
  
7.  Přidejte následující kód, který `Form1_Load` obslužné rutiny události.  
  
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
 Protože služba vrátí data z tabulky Zákazníci a objednávky, výchozí hodnota pro maxReceivedMessageSize není dostatečně velký pro uložení dat a musí být zvýšena. V tomto návodu změníte hodnotu na 6553600. Změní hodnotu na straně klienta, a tím se automaticky aktualizuje odkaz na službu.  
  
> [!NOTE]
>  Nižší výchozí velikost je určena k omezení rizika útoky na dostupnost služby (DoS). Další informace naleznete v tématu <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.  
  
#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Zvýšení hodnoty maxReceivedMessageSize  
  
1.  V **Průzkumníka řešení**, poklikejte na soubor app.config v projektu PresentationTier.  
  
2.  Vyhledejte **maxReceivedMessage** velikost atribut a změňte hodnotu na `6553600`.  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Spusťte aplikaci. Data jsou načtena z datové služby a zobrazí ve formuláři.  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Stiskněte klávesu F5.  
  
2.  Data z tabulky Zákazníci a objednávky je načten z datové služby a zobrazí ve formuláři.  
  
## <a name="next-steps"></a>Další kroky  
 V závislosti na požadavcích aplikace existuje několik kroků, které můžete chtít provést po uložení souvisejících dat v aplikaci založené na Windows. Může například vytvořit následující vylepšení této aplikace:  
  
-   Přidání ověřování do datové sady. Informace najdete v tématu [návod: Přidání ověření do N-vrstvá aplikace Data](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265).  
  
-   Přidáte další metody pro službu pro aktualizaci dat zpět do databáze.  
  
## <a name="see-also"></a>Viz také  
 [Práce s datovými sadami ve vícevrstvých aplikacích](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [Hierarchická aktualizace](../data-tools/hierarchical-update.md)   
 [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

