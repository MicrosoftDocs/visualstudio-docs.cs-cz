---
title: 'Návod: Uložení dat do transakce'
description: V tomto návodu naleznete informace v tématu Jak uložit data v transakci pomocí oboru názvů System. Transactions v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 62175e33949b2c6311fba8e9255b237cd8b43e01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858472"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Návod: Uložení dat do transakce

Tento návod ukazuje, jak uložit data v transakci pomocí <xref:System.Transactions> oboru názvů. V tomto návodu vytvoříte aplikaci model Windows Forms. Pomocí Průvodce konfigurací zdroje dat vytvoříte datovou sadu pro dvě tabulky v ukázkové databázi Northwind. Přidáte ovládací prvky vázané na data do formuláře Windows a upravíte kód pro tlačítko Save objektu BindingNavigator, aby se aktualizovala databáze v objektu TransactionScope.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkovou databázi Northwind.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V Instalační program pro Visual Studio lze SQL Server Express LocalDB nainstalovat jako součást úlohy **vývoj desktopových** aplikací pro .NET nebo jako jednotlivé komponenty.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (Průzkumník objektů systému SQL Server je nainstalován v rámci úlohy **úložiště dat a zpracování** v instalační program pro Visual Studio.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editoru dotazů.

    2. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a pak klikněte na tlačítko **Spustit** .

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

## <a name="create-a-windows-forms-application"></a>Vytvoření aplikace model Windows Forms

Prvním krokem je vytvoření **aplikace model Windows Forms**.

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový**  >  **projekt**.

2. V levém podokně rozbalte možnost **Visual C#** nebo **Visual Basic** a pak vyberte možnost **desktopová plocha systému Windows**.

3. V prostředním podokně vyberte typ projektu **aplikace model Windows Forms** .

4. Pojmenujte projekt **SavingDataInATransactionWalkthrough** a klikněte na **tlačítko OK**.

     Projekt **SavingDataInATransactionWalkthrough** je vytvořen a přidán do **Průzkumník řešení**.

## <a name="create-a-database-data-source"></a>Vytvoření zdroje dat databáze

Tento krok používá **Průvodce konfigurací zdroje dat** k vytvoření zdroje dat založeného na `Customers` `Orders` tabulkách a v ukázkové databázi Northwind.

1. Chcete-li otevřít okno **zdroje dat** , vyberte v nabídce **data** možnost **Zobrazit zdroje dat**.

2. V okně **zdroje dat** vyberte možnost **Přidat nový zdroj dat** a spusťte **Průvodce konfigurací zdroje dat**.

3. Na obrazovce **Vybrat typ zdroje dat** vyberte **databáze** a pak vyberte **Další**.

4. Na obrazovce **Vybrat datové připojení** proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

         -nebo-

    - Vyberte **nové připojení** , aby se spustilo dialogové okno **Přidat/upravit připojení** a vytvořit připojení k databázi Northwind.

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a pak vyberte **Další**.

6. Na obrazovce **Uložit připojovací řetězec do konfiguračního souboru aplikace** vyberte **Další**.

7. Na obrazovce **zvolit vaše databázové objekty** rozbalte uzel **tabulky** .

8. Vyberte `Customers` tabulky a a `Orders` pak vyberte **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a `Customers` `Orders` tabulky a se zobrazí v okně **zdroje dat** .

## <a name="add-controls-to-the-form"></a>Přidat ovládací prvky do formuláře

Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře.

1. V okně **zdroje dat** rozbalte uzel **Customers (zákazníci** ).

2. Přetáhněte hlavní uzel **Customers** z okna **zdroje dat** do formuláře **Form1**.

   <xref:System.Windows.Forms.DataGridView>Ovládací prvek a pruh nástrojů ( <xref:System.Windows.Forms.BindingNavigator> ) pro procházení záznamů se zobrazí ve formuláři. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator> se zobrazí v zásobníku komponent.

3. Přetáhněte uzel souvisejících **objednávek** (nikoli uzel hlavní **objednávky** , ale související uzel podřízené tabulky pod sloupcem **Fax** ) do formuláře pod **customersDataGridView**.

   <xref:System.Windows.Forms.DataGridView>Ve formuláři se zobrazí. `OrdersTableAdapter`A <xref:System.Windows.Forms.BindingSource> zobrazí se v zásobníku komponent.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Přidat odkaz na sestavení System. Transactions

Transakce používají <xref:System.Transactions> obor názvů. Odkaz na projekt sestavení System. Transactions není ve výchozím nastavení přidán, takže ho budete muset přidat ručně.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Přidání odkazu na soubor DLL System. Transactions

1. V nabídce **projekt** vyberte možnost **Přidat odkaz**.

2. Vyberte **System. Transactions** (na kartě **.NET** ) a pak vyberte **OK**.

     Do projektu se přidá odkaz na **System. Transactions** .

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Úprava kódu v tlačítku SaveItem objektu BindingNavigator

Pro první tabulku vytaženou do formuláře je ve výchozím nastavení přidán kód pro `click` Událost tlačítka Uložit na <xref:System.Windows.Forms.BindingNavigator> . Je nutné ručně přidat kód pro aktualizaci dalších tabulek. Pro účely tohoto návodu převedeme existující kód uložení z obslužné rutiny události kliknutí na tlačítko Uložit. Vytvoříme také několik dalších metod, které vám poskytnou konkrétní funkce aktualizace na základě toho, jestli je potřeba přidat nebo odstranit řádek.

### <a name="to-modify-the-auto-generated-save-code"></a>Úprava automatického generovaného kódu pro uložení

1. Vyberte tlačítko **Uložit** na **CustomersBindingNavigator** (tlačítko s ikonou na disketě).

2. Nahraďte metodu `CustomersBindingNavigatorSaveItem_Click` následujícím kódem:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

Postup pro sjednocení změn souvisejících dat je následující:

- Odstranění podřízených záznamů. (V tomto případě odstraňte záznamy z `Orders` tabulky.)

- Odstranění nadřazených záznamů. (V tomto případě odstraňte záznamy z `Customers` tabulky.)

- Vložení nadřazených záznamů. (V tomto případě vložte záznamy do `Customers` tabulky.)

- Vložení podřízených záznamů. (V tomto případě vložte záznamy do `Orders` tabulky.)

### <a name="to-delete-existing-orders"></a>Odstranění existujících objednávek

- `DeleteOrders`Do **Form1** přidejte následující metodu:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>Odstranění stávajících zákazníků

- `DeleteCustomers`Do **Form1** přidejte následující metodu:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>Přidání nových zákazníků

- `AddNewCustomers`Do **Form1** přidejte následující metodu:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>Přidání nových objednávek

- `AddNewOrders`Do **Form1** přidejte následující metodu:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Spuštění aplikace

Stisknutím klávesy **F5** spusťte aplikaci.

## <a name="see-also"></a>Viz také

- [Postupy: ukládání dat pomocí transakce](../data-tools/save-data-by-using-a-transaction.md)
- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
