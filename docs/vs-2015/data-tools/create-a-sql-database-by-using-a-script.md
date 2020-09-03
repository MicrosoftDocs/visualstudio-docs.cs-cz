---
title: Vytvoření databáze SQL pomocí skriptu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bef7c4be2f38d0f50b2a13c7745cb212204769b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670083"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Vytvoření databáze SQL pomocí skriptu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu použijete Visual Studio k vytvoření malé databáze, která obsahuje vzorový kód pro [Vytvoření jednoduché datové aplikace pomocí ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

 **V tomto tématu**

- [Vytvoření skriptu, který obsahuje schéma databáze](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)

- [Vytvoření databázového projektu a import schématu](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)

- [Nasazení databáze](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto Názorného postupu musíte mít nainstalovanou SQL Server Express LocalDB nebo jinou databázi SQL.

## <a name="create-a-script-that-contains-a-database-schema"></a><a name="CreateScript"></a> Vytvoření skriptu, který obsahuje schéma databáze

#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Vytvoření skriptu, ze kterého můžete importovat schéma

1. V nástroji v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] panelu nabídek vyberte **soubor**  >  **Nový**  >  **soubor**.

     Zobrazí se dialogové okno **nový soubor** .

2. V seznamu **kategorie** vyberte **Obecné**.

3. V seznamu **šablony** vyberte možnost **soubor SQL**a pak vyberte tlačítko **otevřít** .

     Otevře se editor Transact-SQL.

4. Zkopírujte následující kód Transact-SQL a vložte ho do editoru Transact-SQL.

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

5. Na řádku nabídek vyberte **soubor**  >  **Uložit SqlQuery_1. SQL jako**.

     Zobrazí se dialogové okno **Uložit soubor jako** .

6. Do pole **název souboru** zadejte `SampleImportScript.sql` , poznamenejte si umístění, kam soubor uložíte, a pak vyberte tlačítko **Uložit** .

7. Na panelu nabídek vyberte **soubor**  >  **Zavřít řešení**.

     Dále vytvořte projekt databáze a pak importujte schéma ze skriptu, který jste vytvořili.

## <a name="create-a-database-project-and-import-a-schema"></a><a name="CreateProject"></a> Vytvoření databázového projektu a import schématu

#### <a name="to-create-a-database-project"></a>Vytvoření databázového projektu

1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

     Zobrazí se dialogové okno **Nový projekt**.

2. V části **nainstalováno**rozbalte uzel **šablony** , rozbalte uzel **ostatní jazyky** , vyberte kategorii **SQL Server** a pak vyberte šablonu **projektu SQL Server databáze** .

    > [!NOTE]
    > Uzel **ostatní jazyky** se nezobrazuje ve všech instalacích sady Visual Studio.

3. Do pole **název** zadejte `Small Database` .

4. Zaškrtněte políčko **vytvořit adresář pro řešení** , pokud již není vybráno.

5. Zrušte zaškrtnutí políčka **Přidat do správy zdrojového kódu** , pokud již není zaškrtnuto, a pak vyberte tlačítko **OK** .

     Projekt databáze se vytvoří a zobrazí se v **Průzkumník řešení**.

     Dále importujte schéma databáze ze skriptu.

#### <a name="to-import-a-database-schema-from-a-script"></a>Import schématu databáze ze skriptu

1. Na panelu nabídek vyberte **Project**  >  **importovat**  >  **skript**projektu.

2. Na stránce **Vítejte** zkontrolujte text a potom klikněte na tlačítko **Další** .

3. Vyberte přepínač pro **jeden soubor** a pak vyberte tlačítko **Procházet** .

     Zobrazí se dialogové okno **importovat skript SQL** .

4. Otevřete složku, do které jste uložili soubor SampleImportScript. SQL, vyberte soubor a pak vyberte tlačítko **otevřít** .

5. Kliknutím na tlačítko **Dokončit** zavřete dialogové okno **importovat skript SQL** .

     Skript se naimportuje a objekty, které skript definuje, se přidají do projektu databáze.

6. Zkontrolujte souhrn a potom kliknutím na tlačítko **Dokončit** zavřete dialogové okno **importovat soubor skriptu SQL** .

7. V **Průzkumník řešení**rozbalte složky prodej, skripty a zabezpečení projektu a ověřte, že obsahují soubory. SQL.

8. V **Průzkumník objektů systému SQL Server**ověřte, zda se databáze zobrazuje v uzlu **projekty** .

     V tomto okamžiku databáze obsahuje pouze systémové objekty, jako jsou tabulky a uložené procedury. Po nasazení bude databáze obsahovat uživatelské tabulky a uložené procedury, které skripty definují.

## <a name="deploy-the-database"></a><a name="DeployDatabase"></a> Nasazení databáze
 Když stisknete klávesu **F5** , nasadíte (nebo publikujete) databázi do databáze LocalDB ve výchozím nastavení. Databázi můžete nasadit do jiného umístění tak, že otevřete stránku vlastností projektu, kliknete na kartu **ladění** a pak změníte připojovací řetězec.
