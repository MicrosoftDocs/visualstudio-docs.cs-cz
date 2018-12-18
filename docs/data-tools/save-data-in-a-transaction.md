---
title: 'Návod: Uložení dat do transakce'
ms.date: 09/08/2017
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f9b4fad02b6b0d8324e13d4465f4602c16ce85ba
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305049"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Návod: Uložení dat do transakce

Tento návod ukazuje, jak uložit data v transakci pomocí <xref:System.Transactions> oboru názvů. V tomto návodu vytvoříte aplikaci Windows Forms. Průvodce konfigurací zdroje dat použijete k vytvoření datové sady pro dvě tabulky v ukázkové databázi Northwind. Přidáte data vázané ovládací prvky do formuláře Windows a upravíte kód BindingNavigator na tlačítko Uložit aktualizace databáze uvnitř objekt TransactionScope.

## <a name="prerequisites"></a>Požadavky

Tento návod používá SQL Server Express LocalDB a ukázkové databáze Northwind.

1.  Pokud nemáte SQL Server Express LocalDB, nainstalujte ji z [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program sady Visual Studio**. V aplikaci Visual Studio Instalační služby systému SQL Server Express LocalDB lze nainstalovat jako součást **vývoj desktopových aplikací .NET** úlohy, nebo jako jednotlivých komponent.

2.  Instalace ukázkové databáze Northwind pomocí následujících kroků:

    1. V sadě Visual Studio, otevřete **Průzkumník objektů systému SQL Server** okna. (Průzkumník objektů systému SQL Server je nainstalován jako součást **ukládání a zpracování dat** úlohy v instalačním programu sady Visual Studio.) Rozbalte **systému SQL Server** uzlu. Klikněte pravým tlačítkem na instanci LocalDB a vyberte **nový dotaz**.

       Otevře se okno editor dotazů.

    2. Kopírovat [Northwind příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind úplně od začátku a naplní daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po chvilce dotaz doběhnutí a vytvořit databázi Northwind.

## <a name="create-a-windows-forms-application"></a>Vytvoření aplikace Windows Forms

Prvním krokem je vytvoření **formulářová aplikace Windows**.

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

3. V prostředním podokně, vyberte **aplikace Windows Forms** typ projektu.

4. Pojmenujte projekt **SavingDataInATransactionWalkthrough**a klikněte na tlačítko **OK**.

     **SavingDataInATransactionWalkthrough** projekt je vytvořen a přidán do **Průzkumníka řešení**.

## <a name="create-a-database-data-source"></a>Vytvoření databázového zdroje dat

Tento krok používá **Průvodce konfigurací zdroje dat** vytvořit zdroj dat na základě `Customers` a `Orders` tabulky v ukázkové databázi Northwind.

1.  Chcete-li otevřít **zdroje dat** okno na **Data** nabídce vyberte možnost **zobrazit zdroje dat**.

2.  V **zdroje dat** okně **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.

3.  Na **zvolte typ zdroje dat** obrazovky, vyberte **databáze**a pak vyberte **Další**.

4.  Na **vyberte datové připojení** obrazovky proveďte následující:

    -   Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

         -nebo-

    -   Vyberte **nové připojení** ke spuštění **přidat/změnit připojení** dialogové okno a vytvořte připojení k databázi Northwind.

5.  Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí důvěrných osobních údajů a pak vyberte **Další**.

6.  Na **uložit připojovací řetězec do konfiguračního souboru aplikace** obrazovky, vyberte **Další**.

7.  Na **zvolte vaše databázové objekty** obrazovky, rozbalte **tabulky** uzlu.

8.  Vyberte `Customers` a `Orders` tabulky a pak vyberte **Dokončit**.

     **NorthwindDataSet** se přidá do vašeho projektu a `Customers` a `Orders` tabulky se zobrazí v **zdroje dat** okna.

## <a name="add-controls-to-the-form"></a>Přidání ovládacích prvků do formuláře

Můžete vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okna do formuláře.

1. V **zdroje dat** okna, rozbalte **zákazníkům** uzlu.

2. Přetáhněte hlavní **zákazníkům** uzlu z **zdroje dat** okna do **Form1**.

   A <xref:System.Windows.Forms.DataGridView> ovládacího prvku a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí ve formuláři. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.

3. Přetáhněte související **objednávky** uzlu (není hlavním **objednávky** uzlu, ale následující související podřízené tabulky uzlu **Fax** sloupce) do níže uvedeného formuláře  **CustomersDataGridView**.

   A <xref:System.Windows.Forms.DataGridView> se zobrazí ve formuláři. `OrdersTableAdapter` a <xref:System.Windows.Forms.BindingSource> zobrazují v panelu komponent.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Přidat odkaz na sestavení System.Transactions

Použití transakce <xref:System.Transactions> oboru názvů. Odkaz na sestavení system.transactions není přidán ve výchozím nastavení, takže je třeba ručně přidat.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Chcete-li přidat odkaz na soubor System.Transactions DLL

1.  Na **projektu** nabídce vyberte možnost **přidat odkaz**.

2.  Vyberte **System.Transactions** (na **.NET** kartu) a pak vyberte **OK**.

     Odkaz na **System.Transactions** se přidá do projektu.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Změňte kód v tlačítko SaveItem prvku BindingNavigator

Kód je jako první tabulku přetaženy do formuláře přidán ve výchozím nastavení `click` události uložení tlačítko <xref:System.Windows.Forms.BindingNavigator>. Budete muset ručně přidat kód pro aktualizaci žádné další tabulky. V tomto návodu budeme Refaktorovat stávající uložit kód mimo uložení tlačítko obslužné rutiny události. Můžeme také vytvořit několik další metody, které poskytují funkce konkrétní aktualizace na základě na, jestli řádku musí být přidány nebo odstraněny.

### <a name="to-modify-the-auto-generated-save-code"></a>Chcete-li změnit automaticky generovanou uložit kódu

1.  Vyberte **Uložit** tlačítko **CustomersBindingNavigator** (tlačítko s ikonou diskety).

2.  Nahradit `CustomersBindingNavigatorSaveItem_Click` metodu s následujícím kódem:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

Sjednocování změn na související data pořadí vypadá takto:

-   Odstraňte podřízené záznamy. (V tomto případě odstranit záznamy `Orders` tabulky.)

-   Odstraňte nadřazené záznamy. (V tomto případě odstranit záznamy `Customers` tabulky.)

-   Vložte nadřazené záznamy. (V tomto případě vkládání záznamů v `Customers` tabulky.)

-   Vložte podřízené záznamy. (V tomto případě vkládání záznamů v `Orders` tabulky.)

### <a name="to-delete-existing-orders"></a>Chcete-li odstranit existující objednávky

-   Přidejte následující `DeleteOrders` metodu **Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>Chcete-li odstranit stávající zákazníci

-   Přidejte následující `DeleteCustomers` metodu **Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>Chcete-li přidat nové zákazníky

-   Přidejte následující `AddNewCustomers` metodu **Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>Chcete-li přidat nové objednávky

-   Přidejte následující `AddNewOrders` metodu **Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Spuštění aplikace

Stisknutím klávesy **F5** ke spuštění aplikace.

## <a name="see-also"></a>Viz také:

- [Postupy: ukládání dat pomocí transakce](../data-tools/save-data-by-using-a-transaction.md)
- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)