---
title: 'Návod: Vytváření TableAdapter s více dotazy | Dokumentace Microsoftu'
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
- TableAdapter queries, creating
- data [Visual Studio], TableAdapters
- TableAdapters, creating
- data [Visual Studio], walkthroughs
- queries [Visual Studio], TableAdapters
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4226fc805ed0335109d0a6b98f1235ae46de1664
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206697"
---
# <a name="walkthrough-creating-a-tableadapter-with-multiple-queries"></a>Návod: Vytváření TableAdapter s více dotazy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu vytvoříte prvek TableAdapter v datové sadě pomocí [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). Průvodce vás provede procesem vytvoření druhého dotazu v [TableAdapter](../data-tools/tableadapter-overview.md) pomocí [úpravy objektů TableAdapter](../data-tools/editing-tableadapters.md) v rámci [Návrhář Dataset](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření nového **aplikace Windows** projektu.  
  
-   Vytvoření a konfigurace zdroje dat v aplikaci sestavením datové sady s **Průvodce konfigurací zdroje dat**.  
  
-   Otevřít novou datovou sadu v **Návrhář Dataset**.  
  
-   Přidání dotazů do TableAdapter pomocí **Průvodce nastavením dotazu TableAdapter**.  
  
## <a name="prerequisites"></a>Požadavky  
 Pokud chcete dokončit tento návod, potřebujete:  
  
-   Přístup k ukázkové databázi Northwind (verze SQL Server nebo Access). Další informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application"></a>Vytvoření nové aplikace systému Windows  
 Prvním krokem je vytvoření aplikace Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Chcete-li vytvořit nový projekt aplikace Windows  
  
1.  V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], z **souboru** nabídky, vytvořte nový projekt.  
  
2.  Zvolte programovací jazyk v **typy projektů** podokně.  
  
3.  Klikněte na tlačítko **aplikace Windows** v **šablony** podokně.  
  
4.  Pojmenujte projekt `TableAdapterQueriesWalkthrough`a potom klikněte na tlačítko **OK**.  
  
     Visual Studio přidá projekt do **Průzkumníka řešení** a zobrazí nový formulář v návrháři.  
  
## <a name="creating-a-database-data-source-with-a-tableadapter"></a>Vytvoření zdroje dat databáze pomocí prvku TableAdapter  
 Tento krok vytváří zdroj dat pomocí **Průvodce konfigurací zdroje dat** na základě `Customers` tabulky v ukázkové databázi Northwind. Musíte mít přístup k ukázkové databázi Northwind k vytvoření připojení. Informace o instalaci ukázkové databáze Northwind naleznete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.  
  
3.  Vyberte **databáze** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.  
  
4.  Na **vyberte datové připojení** stránka provádění, jednu z následujících akcí:  
  
    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.  
  
         -nebo-  
  
    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno.  
  
5.  Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak klikněte na tlačítko **Další**.  
  
6.  Klikněte na tlačítko **Další** na **uložit připojovací řetězec do konfiguračního souboru aplikace** stránky.  
  
7.  Rozbalte **tabulky** uzlu **zvolte vaše databázové objekty** stránky.  
  
8.  Vyberte **zákazníkům** tabulku a pak klikněte na tlačítko **Dokončit**.  
  
     **NorthwindDataSet** se přidá do vašeho projektu a **zákazníkům** tabulky se zobrazí v **zdroje dat** okna.  
  
## <a name="opening-the-dataset-in-the-dataset-designer"></a>Otevřete datovou sadu v návrháři datových sad  
  
#### <a name="to-open-the-dataset-in-the-dataset-designer"></a>Otevřete datovou sadu v návrháři datových sad  
  
1.  Klikněte pravým tlačítkem na **NorthwindDataset** v **zdroje dat** okna.  
  
2.  V místní nabídce zvolte **upravit DataSet pomocí návrháře**.  
  
     NorthwindDataset otevře **Návrhář Dataset**.  
  
## <a name="adding-a-second-query-to-the-customerstableadapter"></a>Přidání druhého dotazu do CustomersTableAdapter  
 Průvodce vytvořil datovou sadu s **zákazníkům** tabulka dat a **CustomersTableAdapter**. Tato část návodu přidává druhý dotaz, který **CustomersTableAdapter**.  
  
#### <a name="to-add-a-query-to-the-customerstableadapter"></a>Přidání dotazu do CustomersTableAdapter  
  
1.  Přetáhněte **dotazu** z **datovou sadu** kartě **nástrojů** na **zákazníkům** tabulky.  
  
     [Úpravy objektů TableAdapter](../data-tools/editing-tableadapters.md) otevře.  
  
2.  Vyberte **použít SQL příkazy**a potom klikněte na tlačítko **Další**.  
  
3.  Vyberte **SELECT, který vrátí řádky**a potom klikněte na tlačítko **Další**.  
  
4.  Přidejte klauzuli WHERE do dotazu tak, aby vypadal:  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Pokud používáte verzi Access databáze Northwind, nahraďte @City parametr otazníkem. (`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`)  
  
5.  Na **zvolte metody k vytvoření** stránky, zadejte název **naplnit DataTable** metoda `FillByCity`.  
  
    > [!NOTE]
    >  Metoda **vrátit tabulku DataTable** se nepoužívá v tomto podrobném návodu, takže můžete ponechejte políčko nezaškrtnuté, nebo ponechat výchozí název.  
  
6.  Klikněte na tlačítko **Další** a dokončete průvodce.  
  
     **FillByCity** dotazu se přidá do **CustomersTableAdapter**.  
  
## <a name="adding-code-to-execute-the-additional-query-on-the-form"></a>Přidání kódu k provedení dalšího dotazu ve formuláři  
  
#### <a name="to-execute-the-query"></a>Provedení dotazu  
  
1.  Vyberte **Form1** v **Průzkumníka řešení**a klikněte na tlačítko **Návrhář zobrazení**.  
  
2.  Přetáhněte **zákazníkům** uzlu z **zdroje dat** okno **Form1**.  
  
3.  Přejděte na zobrazení kódu tak, že vyberete **kód** z **zobrazení** nabídky.  
  
4.  Nahraďte kód v `Form1_Load` obslužné rutiny události s následujícími možnostmi pro spuštění `FillByCity` dotazu.  
  
     [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
     [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
## <a name="running-the-application"></a>Spuštění aplikace  
  
#### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
-   Stiskněte klávesu F5.  
  
-   Mřížka je plná zákazníků s `City` hodnotu `Seattle`.  
  
## <a name="next-steps"></a>Další kroky  
  
### <a name="to-add-functionality-to-your-application"></a>Přidání funkčnosti do aplikace  
  
-   Přidat <xref:System.Windows.Forms.TextBox> ovládacího prvku a <xref:System.Windows.Forms.Button> řídit a předat hodnotu v textovém poli do dotazu. (`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`).  
  
-   Přidejte logiku ověřování k <xref:System.Data.DataTable.ColumnChanging> nebo <xref:System.Data.DataTable.RowChanging> události tabulek dat v datové sadě. Další informace najdete v tématu [ověření dat v datových sadách](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Viz také  
 [TableAdapter – přehled](../data-tools/tableadapter-overview.md)   
 [Vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [Postupy: vytváření dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)