---
title: Uložení dat v transakci | Microsoft Docs
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
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30f51da001c62166a97c954b1416e35fd8b540f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671090"
---
# <a name="save-data-in-a-transaction"></a>Uložení dat do transakce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak uložit data v transakci pomocí <xref:System.Transactions> oboru názvů. Tento příklad používá `Customers` tabulky a `Orders` z ukázkové databáze Northwind.

## <a name="prerequisites"></a>Předpoklady
 Tento návod vyžaduje přístup k ukázkové databázi Northwind.

## <a name="create-a-windows-application"></a>Vytvoření aplikace pro Windows
 Prvním krokem je vytvoření **aplikace pro Windows**.

#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows

1. V aplikaci Visual Studio v nabídce **soubor** vytvořte nový **projekt**.

2. Pojmenujte projekt **SavingDataInATransactionWalkthrough**.

3. Vyberte **aplikace systému Windows**a pak vyberte **OK**. Další informace najdete v tématu [klientské aplikace](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt **SavingDataInATransactionWalkthrough** je vytvořen a přidán do **Průzkumník řešení**.

## <a name="create-a-database-data-source"></a>Vytvoření zdroje dat databáze
 Tento krok používá [Průvodce konfigurací zdroje dat](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) k vytvoření zdroje dat založeného na `Customers` `Orders` tabulkách a v ukázkové databázi Northwind.

#### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat

1. V nabídce **data** vyberte možnost**Zobrazit zdroje dat**.

2. V okně **zdroje dat** vyberte možnost **Přidat nový zdroj dat** a spusťte **Průvodce konfigurací zdroje dat**.

3. Na obrazovce **Vybrat typ zdroje dat**vyberte **databáze**a pak vyberte **Další**.

4. Na obrazovce **Vybrat datové připojení**proveďte jednu z následujících akcí:

    - Pokud je připojení dat k ukázkové databázi Northwind k dispozici v rozevíracím seznamu, vyberte je.

         -nebo-

    - Vyberte **nové připojení** , aby se spustilo dialogové okno **Přidat/upravit připojení** a vytvořit připojení k databázi Northwind.

5. Pokud vaše databáze vyžaduje heslo, vyberte možnost zahrnutí citlivých dat a pak vyberte **Další**.

6. Na obrazovce **Uložit připojovací řetězec do konfiguračního souboru aplikace** vyberte **Další**.

7. Na obrazovce **zvolit vaše databázové objekty** rozbalte uzel **tabulky** .

8. Vyberte `Customers` tabulky a a `Orders` pak vyberte **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a `Customers` `Orders` tabulky a se zobrazí v okně **zdroje dat** .

## <a name="addcontrols-to-the-form"></a>Addcontrols do formuláře
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři Windows

- V okně **zdroje dat** rozbalte uzel **Customers (zákazníci** ).

- Přetáhněte hlavní uzel **Customers** z okna **zdroje dat** do formuláře **Form1**.

     <xref:System.Windows.Forms.DataGridView>Ovládací prvek a pruh nástrojů ( <xref:System.Windows.Forms.BindingNavigator> ) pro procházení záznamů se zobrazí ve formuláři. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator> se zobrazí v zásobníku komponent.

- Přetáhněte uzel souvisejících **objednávek** (nikoli uzel hlavní **objednávky** , ale související uzel podřízené tabulky pod sloupcem **Fax** ) do formuláře pod **customersDataGridView**.

     <xref:System.Windows.Forms.DataGridView>Ve formuláři se zobrazí. OrdersTableAdapter a <xref:System.Windows.Forms.BindingSource> zobrazí se v zásobníku komponent.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Přidat odkaz na sestavení System. Transactions
 Transakce používají <xref:System.Transactions> obor názvů. Odkaz na projekt sestavení System. Transactions není ve výchozím nastavení přidán, takže ho budete muset přidat ručně.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Přidání odkazu na soubor DLL System. Transactions

1. V nabídce **projekt** vyberte možnost**Přidat odkaz**.

2. Vyberte **System. Transactions**(na kartě **.NET** ) a pak vyberte **OK**.

     Do projektu se přidá odkaz na **System. Transactions** .

## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Modifythe kód v tlačítku SaveItem BindingNavigator
 Pro první tabulku vytaženou do formuláře je ve výchozím nastavení přidán kód pro `click` Událost tlačítka Uložit na <xref:System.Windows.Forms.BindingNavigator> . Je nutné ručně přidat kód pro aktualizaci dalších tabulek. Pro účely tohoto návodu převedeme existující kód uložení z obslužné rutiny události kliknutí na tlačítko Uložit. Vytvoříme také několik dalších metod, které vám poskytnou konkrétní funkce aktualizace na základě toho, jestli je potřeba přidat nebo odstranit řádek.

#### <a name="to-modify-the-auto-generated-save-code"></a>Úprava automatického generovaného kódu pro uložení

1. Vyberte tlačítko **Uložit** na **CustomersBindingNavigator** (tlačítko s ikonou na disketě).

2. Nahraďte metodu `CustomersBindingNavigatorSaveItem_Click` následujícím kódem:

    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]

   Postup pro sjednocení změn souvisejících dat je následující:

- Odstranění podřízených záznamů. (V tomto případě odstraňte záznamy z `Orders` tabulky.)

- Odstranění nadřazených záznamů. (V tomto případě odstraňte záznamy z `Customers` tabulky.)

- Vložení nadřazených záznamů. (V tomto případě vložte záznamy do `Customers` tabulky.)

- Vložení podřízených záznamů. (V tomto případě vložte záznamy do `Orders` tabulky.)

#### <a name="to-delete-existing-orders"></a>Odstranění existujících objednávek

- `DeleteOrders`Do **Form1**přidejte následující metodu:

     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]

#### <a name="to-delete-existing-customers"></a>Odstranění stávajících zákazníků

- `DeleteCustomers`Do **Form1**přidejte následující metodu:

     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]

#### <a name="to-add-new-customers"></a>Přidání nových zákazníků

- `AddNewCustomers`Do **Form1**přidejte následující metodu:

     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]

#### <a name="to-add-new-orders"></a>Přidání nových objednávek

- `AddNewOrders`Do **Form1**přidejte následující metodu:

     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]

## <a name="run-the-application"></a>Spuštění aplikace

#### <a name="to-run-the-application"></a>Spuštění aplikace

- Pro spuštění aplikace vyberte **F5** .

## <a name="see-also"></a>Viz také
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
