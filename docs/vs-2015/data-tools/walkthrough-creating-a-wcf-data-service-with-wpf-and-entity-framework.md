---
title: 'Návod: Vytvoření datové služby WCF s WPF a Entity Framework | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3d115c7ea7b2739f49492fb28fe855e2638d972c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889591"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Návod: Vytvoření datové služby WCF s WPF a Entity Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Tento návod ukazuje, jak vytvořit jednoduchou [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] , která je hostována v [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci a pak k němu přístup z aplikace Windows Forms.  
  
 V tomto návodu se dozvíte, jak:  
  
-   Vytvoření webové aplikace na hostitele [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Vytvoření [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] , který představuje tabulku Customers v databázi Northwind.  
  
-   Vytvoření [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Vytvořit klientskou aplikaci a přidejte odkaz na [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Vytvořit datovou vazbu na službu a vygenerovat uživatelské rozhraní  
  
-   Volitelně přidat do aplikace možnosti filtrování  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Ukázkovou databázi Northwind  
  
     Pokud tuto databázi na vašem vývojovém počítači nemáte, můžete sadu stáhnout z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088). Pokyny najdete v tématu [Downloading Sample Databases](http://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5).  
  
## <a name="creating-the-service"></a>Vytvoření služby  
 Chcete-li vytvořit [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], bude přidáte webový projekt, vytvořte [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]a poté vytvoříte službu z modelu.  
  
 V prvním kroku přidáte webový projekt pro hostování služby.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-the-web-project"></a>Vytvoření webového projektu  
  
1. V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
2. V **nový projekt** dialogového okna rozbalte **jazyka Visual Basic** nebo **Visual C#** a **webové** uzly a klikněte na tlačítko **ASP. Webová aplikace NET** šablony.  
  
3. V **název** textové pole, zadejte **NorthwindWeb**a klikněte na tlačítko **OK** tlačítko.  
  
4. V **nový projekt ASP.NET** v dialogu **vyberte šablonu** klikněte na položku **prázdný**a klikněte na tlačítko **OK** tlačítko.  
  
   V tomto kroku vytvoříte [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] , který představuje tabulku Customers v databázi Northwind.  
  
#### <a name="to-create-the-entity-data-model"></a>Vytvoření modelu Entity Data Model  
  
1. V panelu nabídky zvolte **projektu**, **přidat novou položku**.  
  
2. V **přidat novou položku** dialogového okna zvolte **Data** uzel a klikněte na tlačítko **datový Model Entity ADO.NET** položky.  
  
3. V **název** textové pole, zadejte `NorthwindModel`a klikněte na tlačítko **přidat** tlačítko.  
  
    Zobrazí se Průvodce modelem Entity Data Model.  
  
4. V Průvodci modelem Entity Data na **výběr obsahu modelu** zvolte **EF designeru z databáze** položku a klikněte na tlačítko **Další** tlačítko.  
  
5. Na **vyberte datové připojení** stránce, proveďte jednu z následujících kroků:  
  
   -   Pokud je datové připojení k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.  
  
        -nebo-  
  
   -   Zvolte **nové připojení** tlačítko a nakonfigurujte nové datové připojení. Další informace najdete v tématu [přidat nové připojení](../data-tools/add-new-connections.md).  
  
6. Pokud databáze vyžaduje heslo, zvolte **Ano, zahrnout citlivá data v připojovacím řetězci** přepínač a klikněte na tlačítko **Další** tlačítko.  
  
   > [!NOTE]
   >  Pokud se zobrazí dialogové okno, vyberte **Ano** k uložení souboru do projektu.  
  
7. Na **zvolíte verzi** zvolte **Entity Framework 5.0** přepínač a klikněte na tlačítko **Další** tlačítko.  
  
   > [!NOTE]
   >  Pokud chcete používat nejnovější verzi Entity Framework 6 služby WCF, budete muset nainstalovat balíček zprostředkovatele NuGet pro rozhraní WCF Data Services Entity Framework. Zobrazit [pomocí WCF Data Services – 5.6.0 s Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8. Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky** uzlu, vyberte **zákazníkům** zaškrtněte políčko a klikněte na tlačítko **Dokončit** tlačítko.  
  
    Zobrazí se diagram modelu entit a do projektu bude přidán soubor NorthwindModel.edmx.  
  
   V tomto kroku vytvoříte a otestujete datovou službu.  
  
#### <a name="to-create-the-data-service"></a>Vytvoření datové služby  
  
1. V panelu nabídky zvolte **projektu**, **přidat novou položku**.  
  
2. V **přidat novou položku** dialogového okna zvolte **webové** uzel a klikněte na tlačítko **datová služba WCF 5.6** položky.  
  
3. V **název** textové pole, zadejte `NorthwindCustomers`a klikněte na tlačítko **přidat** tlačítko.  
  
    Tento soubor NorthwindCustomers.svc objeví **Editor kódu**.  
  
4. V **Editor kódu**, vyhledejte první `TODO:` komentáře a nahraďte kód následujícím kódem:  
  
    [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
    [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]  
  
5. Nahraďte komentáře v `InitializeService` obslužné rutiny události s následujícím kódem:  
  
    [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
    [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]  
  
6. V panelu nabídky zvolte **ladění**, **spustit bez ladění** ke spuštění služby. Otevře se okno prohlížeče a zobrazí se schéma XML pro službu.  
  
7. V **adresu** panelu, zadejte `Customers` na konci adresy URL pro soubor NorthwindCustomers.svc a klikněte na tlačítko **ENTER** klíč.  
  
    Zobrazí se reprezentace dat z tabulky Customers v jazyce XML.  
  
   > [!NOTE]
   >  V některých případech bude aplikace Internet Explorer chybně interpretovat data jako informační kanál RSS. Zkontrolujte, zda je zakázána možnost zobrazení informačních kanálů RSS. Další informace najdete v tématu [řešení potíží s odkazy na služby](../data-tools/troubleshooting-service-references.md).  
  
8. Zavřete okno prohlížeče.  
  
   V dalších krocích vytvoříte klientskou aplikaci založenou na modelu Windows Forms, která bude službu používat.  
  
## <a name="creating-the-client-application"></a>Vytvoření klientské aplikace  
 Vytvoříte klientskou aplikaci tak, že přidáte druhý projekt, do projektu přidáte odkaz na službu, nakonfigurujete zdroj dat a vytvoříte uživatelské rozhraní pro zobrazení dat ze služby.  
  
 V prvním kroku přidáte do řešení projekt modelu Windows Forms a nastavíte ho jako spouštěný projekt.  
  
#### <a name="to-create-the-client-application"></a>Vytvoření klientské aplikace  
  
1. Na panelu nabídek zvolte soubor, **přidat**, **nový projekt**.  
  
2. V **nový projekt** dialogového okna rozbalte **jazyka Visual Basic** nebo **Visual C#** uzlu a zvolte **Windows** uzel a klikněte na tlačítko  **Aplikaci Windows Forms**.  
  
3. V **název** textové pole, zadejte `NorthwindClient`a klikněte na tlačítko **OK** tlačítko.  
  
4. V **Průzkumníka řešení**, zvolte **NorthwindClient** uzel projektu.  
  
5. V panelu nabídky zvolte **projektu**, **nastavit jako spouštěný projekt**.  
  
   V tomto kroku přidáte odkaz na službu [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] ve webovém projektu.  
  
#### <a name="to-add-a-service-reference"></a>Přidání odkazu na službu  
  
1. V panelu nabídky zvolte **projektu**, **přidat odkaz na službu**.  
  
2. V **přidat odkaz na službu** dialogového okna zvolte **Discover** tlačítko.  
  
    Adresa URL služby NorthwindCustomers se zobrazí v **adresu** pole.  
  
3. Zvolte **OK** tlačítko pro přidání odkazu na službu.  
  
   V tomto kroku nakonfigurujete zdroj dat, abyste umožnili vytváření datových vazeb na službu.  
  
#### <a name="to-enable-data-binding-to-the-service"></a>Vytvoření datové vazby na službu  
  
1. V panelu nabídky zvolte **zobrazení**, **ostatní Windows**, **zdroje dat**.  
  
2. V **zdroje dat** okna, vyberte **přidat nový zdroj dat** tlačítko.  
  
3. Na **zvolte typ zdroje dat** stránku **Průvodce konfigurací zdroje dat**, zvolte **objekt**a klikněte na tlačítko **Další** tlačítko .  
  
4. Na **vyberte datové objekty** stránce, rozbalte **NorthwindClient** uzel a potom rozbalte **NorthwindClient.ServiceReference1** uzlu.  
  
5. Vyberte **zákazníka** zaškrtněte políčko a klikněte na tlačítko **Dokončit** tlačítko.  
  
   V tomto kroku vytvoříte uživatelské rozhraní, které zobrazí data ze služby.  
  
#### <a name="to-create-the-user-interface"></a>Vytvoření uživatelského rozhraní  
  
1. V **zdroje dat** okno, otevřete místní nabídku pro **zákazníkům** uzlu a zvolte **kopírování**.  
  
2. V **Form1.vb** nebo **Form1.cs** návrháři formuláře, otevřete místní nabídku a zvolte **vložit**.  
  
    A <xref:System.Windows.Forms.DataGridView> ovládací prvek, <xref:System.Windows.Forms.BindingSource> komponenty a <xref:System.Windows.Forms.BindingNavigator> součásti jsou přidány do formuláře.  
  
3. Zvolte **CustomersDataGridView** ovládací prvek a pak v **vlastnosti** okno sady **ukotvení** vlastnost **vyplnit**.  
  
4. V **Průzkumníku řešení**, otevřete místní nabídku **Form1** uzlu a zvolte **zobrazit kód** otevřete Editor kódu a přidejte následující Imports nebo Using příkazu na horní části souboru:  
  
   ```vb  
   Imports NorthwindClient.ServiceReference1  
   ```  
  
   ```csharp  
   using NorthwindClient.ServiceReference1;  
   ```  
  
5. Přidejte následující kód, který `Form1_Load` obslužné rutiny události:  
  
   ```vb  
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
           Dim proxy As New NorthwindEntities _  
   (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))  
           Me.CustomersBindingSource.DataSource = proxy.Customers  
       End Sub  
   ```  
  
   ```csharp  
   private void Form1_Load(object sender, EventArgs e)  
   {  
   NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
   this.CustomersBindingSource.DataSource = proxy.Customers;  
   }  
  
   ```  
  
6. V **Průzkumníka řešení**, otevřete místní nabídku pro soubor NorthwindCustomers.svc a zvolte **zobrazit v prohlížeči**. Spustí se aplikace Internet Explorer a zobrazí se schéma XML pro službu.  
  
7. Zkopírujte adresu URL z panelu Adresa aplikace Internet Explorer.  
  
8. V kódu, který jste přidali v kroku 4, vyberte `http://localhost:53161/NorthwindCustomers.svc/` a nahraďte ji právě zkopírovanou adresu URL.  
  
9. V panelu nabídky zvolte **ladění**, **spustit ladění** ke spuštění aplikace. Zobrazí se informace o zákazníkovi.  
  
   Nyní máte funkční aplikaci, která zobrazuje seznam zákazníků ze služby NorthwindCustomers. Pokud chcete zobrazit další data ve službě, můžete upravit [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] mohli přidat další tabulky z databáze Northwind.  
  
   V dalším volitelném kroku se dozvíte, jak filtrovat data, která služba vrací.  
  
## <a name="adding-filtering-capabilities"></a>Přidání možností filtrování  
 V tomto kroku přizpůsobíte aplikaci tak, aby umožňovala filtrování dat podle města zákazníka.  
  
#### <a name="to-add-filtering-by-city"></a>Přidání filtrování podle města  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **Form1.vb** nebo **Form1.cs** uzlu a zvolte **otevřete**.  
  
2.  Přidat <xref:System.Windows.Forms.TextBox> ovládacího prvku a <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře.  
  
3.  Otevřete místní nabídku pro <xref:System.Windows.Forms.Button> řídit a zvolte **zobrazit kód**a potom přidejte následující kód `Button1_Click` obslužné rutiny události:  
  
    ```vb  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
            Dim proxy As New northwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))  
            Dim city As String = TextBox1.Text  
  
            If city <> "" Then  
                Me.CustomersBindingSource.DataSource = From c In _  
             proxy.Customers Where c.City = city  
            End If  
  
        End Sub  
    ```  
  
    ```csharp  
    private void Button1_Click(object sender, EventArgs e)  
    {  
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));  
    string city = TextBox1.Text;  
  
    if (!string.IsNullOrEmpty(city)) {  
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;  
    }  
  
    }  
    ```  
  
4.  V předcházejícím kódu nahraďte `http://localhost:53161/NorthwindCustomers.svc` adresou URL z `Form1_Load` obslužné rutiny události.  
  
5.  V panelu nabídky zvolte **ladění**, **spustit ladění** ke spuštění aplikace.  
  
6.  V textovém poli zadejte **Londýn**a pak klikněte na tlačítko. Zobrazí se pouze zákazníci z Londýna.  
  
## <a name="see-also"></a>Viz také  
 [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Postupy: Přidání, aktualizace nebo odebrání odkazu na službu WCF Data Service](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)

