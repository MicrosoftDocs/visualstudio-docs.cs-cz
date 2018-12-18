---
title: Vytvoření databáze SQL pomocí skriptu | Dokumentace Microsoftu
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
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13816c499002f8eaf81067aba8d1854d06a41445
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266588"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Vytvoření databáze SQL pomocí skriptu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
V tomto názorném postupu použijete k vytvoření malé databáze, která obsahuje ukázkový kód pro Visual Studio [vytvoření jednoduché datové aplikace pomocí ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **V tomto tématu**  
  
-   [Vytvořit skript, který obsahuje databázové schéma](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [Vytvořte projekt databáze a importovat schéma](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [Nasazení databáze](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu, musí mít SQL Server Express LocalDB nebo jiné databáze SQL, nainstalována.  
  
##  <a name="CreateScript"></a> Vytvořit skript, který obsahuje databázové schéma  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Postup vytvoření skriptu ze kterého můžete importovat schéma  
  
1.  V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], na panelu nabídek vyberte **souboru** > **nový** > **souboru**.  
  
     **Nový soubor** zobrazí se dialogové okno.  
  
2.  V **kategorie** seznamu vyberte **Obecné**.  
  
3.  V **šablony** seznamu vyberte **soubor Sql**a pak vyberte **otevřít** tlačítko.  
  
     Otevře se editor jazyka Transact-SQL.  
  
4.  Zkopírujte následující kód Transact-SQL a vložte ho do editoru jazyka Transact-SQL.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  Na panelu nabídek vyberte **souboru** > **uložit SqlQuery_1.sql jako**.  
  
     **Uložit soubor jako** zobrazí se dialogové okno.  
  
6.  V **název_souboru** zadejte `SampleImportScript.sql`, poznamenejte si umístění, kde můžete uložit soubor a pak vyberte **Uložit** tlačítko.  
  
7.  Na panelu nabídek vyberte **souboru** > **zavřít řešení**.  
  
     Dále vytvořte projekt databáze a importujte schéma ze skriptu, který jste vytvořili.  
  
##  <a name="CreateProject"></a> Vytvořte projekt databáze a importovat schéma  
  
#### <a name="to-create-a-database-project"></a>Vytvoření projektu databáze  
  
1.  Na panelu nabídek vyberte **souboru** > **nový** > **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
2.  V části **nainstalováno**, rozbalte **šablony** uzlu, rozbalte **jiné jazyky** uzlu, vyberte **systému SQL Server** kategorie a pak Vyberte **databázový projekt SQL Server** šablony.  
  
    > [!NOTE]
    >  **Jiné jazyky** uzlu se nezobrazí ve všech instalacích sady Visual Studio.  
  
3.  V **název** zadejte `Small Database`.  
  
4.  Vyberte **vytvořit adresář pro řešení** zaškrtávací políčko, pokud ještě není vybraná.  
  
5.  Zrušte **přidat do správy zdrojových kódů** zaškrtávací políčko, pokud ještě není nezaškrtnuté a pak vyberte **OK** tlačítko.  
  
     Projekt databáze se vytvoří a zobrazí se v **Průzkumníka řešení**.  
  
     Dále importujte schéma databáze ze skriptu.  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>Chcete-li importovat schéma databáze ze skriptu  
  
1.  Na panelu nabídek vyberte **projektu** > **Import** > **skript**.  
  
2.  Na **úvodní** stránce zkontrolujte text a pak vyberte **Další** tlačítko.  
  
3.  Vyberte **jednoho souboru** přepínač a pak vyberte **Procházet** tlačítko.  
  
     **Import skriptu SQL** zobrazí se dialogové okno.  
  
4.  Otevřete složku, kam jste uložili soubor SampleImportScript.sql, vyberte ho a pak vyberte **otevřít** tlačítko.  
  
5.  Vyberte **Dokončit** tlačítko pro uzavření **Import skriptu SQL** dialogové okno.  
  
     Skript se importuje a objekty, které skript definuje se přidají do databáze projektu.  
  
6.  Zkontrolujte souhrn a pak klikněte na tlačítko **Dokončit** tlačítko pro uzavření **importovat soubor skriptu SQL** dialogové okno.  
  
7.  V **Průzkumníka řešení**, rozbalte prodej, skripty a zabezpečení složky vašeho projektu a ověřte, že obsahují soubory .sql.  
  
8.  V **Průzkumník objektů systému SQL Server**, ověřte, že se databáze zobrazí v části **projekty** uzlu.  
  
     V tomto okamžiku databáze obsahuje pouze systémové objekty, jako jsou tabulky a uložené procedury. Po nasazení bude databáze bude obsahovat uživatelské tabulky a uložené procedury, které definují skripty.  
  
##  <a name="DeployDatabase"></a> Nasazení databáze  
 Po stisknutí klávesy **F5** klíč, nasadit (nebo publikovat) databázi na databázi LocalDB ve výchozím nastavení. Můžete nasadit databázi do jiného umístění otevřením stránky vlastností pro projekt, vyberte **ladění** kartu a potom změnou propojovacího řetězce.

