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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671090"
---
# <a name="save-data-in-a-transaction"></a>Uložení dat do transakce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak uložit data v transakci pomocí oboru názvů <xref:System.Transactions>. V tomto příkladu se používá tabulka `Customers` a `Orders` z ukázkové databáze Northwind.

## <a name="prerequisites"></a>Požadavky
 Tento návod vyžaduje přístup k ukázkové databázi Northwind.

## <a name="create-a-windows-application"></a>Vytvoření aplikace pro Windows
 Prvním krokem je vytvoření **aplikace pro Windows**.

#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows

1. V aplikaci Visual Studio v nabídce **soubor** vytvořte nový **projekt**.

2. Pojmenujte projekt **SavingDataInATransactionWalkthrough**.

3. Vyberte **aplikace systému Windows**a pak vyberte **OK**. Další informace najdete v tématu [klientské aplikace](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt **SavingDataInATransactionWalkthrough** je vytvořen a přidán do **Průzkumník řešení**.

## <a name="create-a-database-data-source"></a>Vytvoření zdroje dat databáze
 Tento krok používá [Průvodce konfigurací zdroje dat](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) k vytvoření zdroje dat založeného na tabulkách `Customers` a `Orders` v ukázkové databázi Northwind.

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

8. Vyberte tabulky `Customers` a `Orders` a pak vyberte **Dokončit**.

     **NorthwindDataSet** je přidán do projektu a tabulky `Customers` a `Orders` se zobrazí v okně **zdroje dat** .

## <a name="addcontrols-to-the-form"></a>Addcontrols do formuláře
 Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do formuláře.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Vytvoření ovládacích prvků vázaných na data ve formuláři Windows

- V okně **zdroje dat** rozbalte uzel **Customers (zákazníci** ).

- Přetáhněte hlavní uzel **Customers** z okna **zdroje dat** do formuláře **Form1**.

     Na formuláři se zobrazí ovládací prvek <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů. V zásobníku komponent se zobrazí [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator>.

- Přetáhněte uzel souvisejících **objednávek** (nikoli uzel hlavní **objednávky** , ale související uzel podřízené tabulky pod sloupcem **Fax** ) do formuláře pod **customersDataGridView**.

     Ve formuláři se zobrazí <xref:System.Windows.Forms.DataGridView>. OrdersTableAdapter a <xref:System.Windows.Forms.BindingSource> se zobrazí v zásobníku komponent.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Přidat odkaz na sestavení System. Transactions
 Transakce používají obor názvů <xref:System.Transactions>. Odkaz na projekt sestavení System. Transactions není ve výchozím nastavení přidán, takže ho budete muset přidat ručně.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Přidání odkazu na soubor DLL System. Transactions

1. V nabídce **projekt** vyberte možnost**Přidat odkaz**.

2. Vyberte **System. Transactions**(na kartě **.NET** ) a pak vyberte **OK**.

     Do projektu se přidá odkaz na **System. Transactions** .

## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Modifythe kód v tlačítku SaveItem BindingNavigator
 Pro první tabulku, která je na formuláři vložená, se ve výchozím nastavení přidá do události `click` tlačítka Uložit na <xref:System.Windows.Forms.BindingNavigator>. Je nutné ručně přidat kód pro aktualizaci dalších tabulek. Pro účely tohoto návodu převedeme existující kód uložení z obslužné rutiny události kliknutí na tlačítko Uložit. Vytvoříme také několik dalších metod, které vám poskytnou konkrétní funkce aktualizace na základě toho, jestli je potřeba přidat nebo odstranit řádek.

#### <a name="to-modify-the-auto-generated-save-code"></a>Úprava automatického generovaného kódu pro uložení

1. Vyberte tlačítko **Uložit** na **CustomersBindingNavigator** (tlačítko s ikonou na disketě).

2. Metodu `CustomersBindingNavigatorSaveItem_Click` nahraďte následujícím kódem:

    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]

   Postup pro sjednocení změn souvisejících dat je následující:

- Odstranění podřízených záznamů. (V takovém případě odstraňte záznamy z `Orders` tabulky).

- Odstranění nadřazených záznamů. (V takovém případě odstraňte záznamy z `Customers` tabulky).

- Vložení nadřazených záznamů. (V tomto případě vložte záznamy do tabulky `Customers`.)

- Vložení podřízených záznamů. (V tomto případě vložte záznamy do tabulky `Orders`.)

#### <a name="to-delete-existing-orders"></a>Odstranění existujících objednávek

- Do **Form1**přidejte následující metodu `DeleteOrders`:

     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]

#### <a name="to-delete-existing-customers"></a>Odstranění stávajících zákazníků

- Do **Form1**přidejte následující metodu `DeleteCustomers`:

     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]

#### <a name="to-add-new-customers"></a>Přidání nových zákazníků

- Do **Form1**přidejte následující metodu `AddNewCustomers`:

     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]

#### <a name="to-add-new-orders"></a>Přidání nových objednávek

- Do **Form1**přidejte následující metodu `AddNewOrders`:

     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]

## <a name="run-the-application"></a>Spuštění aplikace

#### <a name="to-run-the-application"></a>Spuštění aplikace

- Pro spuštění aplikace vyberte **F5** .

## <a name="see-also"></a>Viz také
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
