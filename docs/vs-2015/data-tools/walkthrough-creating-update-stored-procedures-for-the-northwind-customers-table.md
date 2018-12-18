---
title: 'Návod: Vytvoření uložené procedury aktualizace pro tabulku zákazníků Northwind | Dokumentace Microsoftu'
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
- Northwind sample database
- stored procedures [Visual Studio]
- O/R Designer, stored procedures
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4972c1341490f78bba03bdd390ac13903c55be84
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204045"
---
# <a name="walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table"></a>Návod: Vytvoření uložené procedury aktualizace pro tabulku zákazníků Northwind
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Témata nápovědy v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] dokumentaci vyžadovat dalších uložených procedur v ukázkové databázi Northwind pro provádění aktualizací (vložení, aktualizace a odstranění) dat v tabulce Zákazníci.  
  
 Tento názorný postup obsahuje pokyny pro vytvoření těchto dalších uložených procedur v ukázkové databáze Northwind pro [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 V části Další kroky dále v tomto tématu obsahuje odkazy na témata, která ukazují, jak pracovat s těmito dalších uložených procedur.  
  
 V tomto návodu se dozvíte, jak provádět následující úlohy:  
  
-   Vytvoření datového připojení k ukázkové databázi Northwind.  
  
-   Vytvořte úložné procedury.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat:  
  
-   Přístup k verzi systému SQL Server z ukázkové databáze Northwind. Další informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="connecting-to-the-northwind-database"></a>Připojení k databázi Northwind  
 Tento návod vyžaduje připojení k SQL serveru verzi databáze Northwind. Následující postup obsahuje pokyny pro vytvoření datového připojení.  
  
> [!NOTE]
>  Pokud už máte datové připojení k databázi Northwind, můžete přejít k další části, vytvoření uložené procedury.  
  
#### <a name="to-create-a-data-connection-to-the-northwind-sql-server-database"></a>Vytvoření datového připojení k databázi Northwind SQL serveru  
  
1.  Na **zobrazení** nabídky, klikněte na tlačítko **Průzkumníka serveru**/**Průzkumník databáze**.  
  
2.  Klikněte pravým tlačítkem na **datová připojení** a klikněte na tlačítko **přidat připojení**.  
  
3.  V **zvolit zdroj dat** dialogové okno, klikněte na tlačítko **Microsoft SQL Server**a potom klikněte na tlačítko **OK**.  
  
     Pokud **přidat připojení** otevře dialogové okno a **zdroj dat** není **Microsoft SQL Server (SqlClient)**, klikněte na tlačítko **změnu** otevřete **Zvolit/změnit zdroj dat** dialogové okno, klikněte na tlačítko **Microsoft SQL Server**a potom klikněte na tlačítko **OK**.  
  
4.  Klikněte na tlačítko **název serveru** v rozevíracího seznamu nebo zadejte název serveru, na kterém je umístěna databáze Northwind.  
  
5.  Na základě požadavků databáze nebo aplikace, klepněte na položku **používat ověřování Windows** nebo použijte konkrétní uživatelské jméno a heslo pro přihlášení k počítači se systémem SQL Server (**ověřovánísystémuSQLServer**).  
  
6.  Klikněte na databázi Northwind v **vyberte nebo zadejte název databáze** seznamu.  
  
7.  Klikněte na tlačítko **OK**.  
  
     Datové připojení se přidá do **Průzkumníka serveru**/**Průzkumník databáze**.  
  
## <a name="creating-the-stored-procedures"></a>Vytvoření uložené procedury  
 Vytvořit úložné procedury spuštěním skriptu SQL na databázi Northwind pomocí [nástroje Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) k dispozici v **Průzkumníka serveru** /  **Průzkumník databáze**.  
  
#### <a name="to-create-the-stored-procedures-by-using-a-sql-script"></a>Vytvoření uložené procedury pomocí skriptu SQL  
  
1.  Rozbalte databázi Northwind v **Průzkumníka serveru**/**Průzkumník databáze**.  
  
2.  Klikněte pravým tlačítkem myši **uložené procedury** uzel a klikněte na tlačítko **přidat novou uloženou proceduru**.  
  
3.  Vložte následující kód do editoru kódu nahraďte `CREATE PROCEDURE` šablony:  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  Vybrat veškerý text v editoru kódu, klikněte pravým tlačítkem na vybraný text a klikněte na tlačítko **spustit výběr**.  
  
     SelectCustomers, InsertCustomers, UpdateCustomers a DeleteCustomers uložené procedury jsou vytvořeny pro databázi Northwind.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když jste vytvořili, uložené procedury, zkuste následující návody, které ukazují, jak pracovat s nimi:  
  
 [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Návod: Vytvoření třídy LINQ to SQL (Návrhář O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)  
  
 [Návod: Přizpůsobení chování tříd entit při vložení, aktualizaci a odstranění](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## <a name="see-also"></a>Viz také  
 [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)